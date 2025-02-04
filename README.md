# LeakFinder
**Credential Leak Detection using Chrome DevTools & Burp Suite**

## Overview

This guide provides step-by-step instructions to search for leaked credentials using **Google Chrome's Developer Tools** and **Burp Suite**, leveraging regex for efficient detection.

---

## 🔍 Using Google Chrome Developer Tools

1. **Open DevTools:**  
   - Press `Ctrl+Shift+I` (Windows/Linux) or `Cmd+Option+I` (macOS).

2. **Go to Network Tab:**  
   - Click on the **"Network"** tab.

3. **Enable Regex Search:**  
   - Click the regex icon in the filter bar to enable regex mode.

4. **Refresh Page:**  
   - Reload the webpage to capture all network requests.

5. **Apply Regex Search:**  
   - Paste the following regex into the filter bar:

   ```regex
   (access_key|access_token|admin_pass|admin_user)
   ```

6. **Review Matches:**  
   - Inspect the filtered requests manually for potential leaks.

---

## 🔍 Using Burp Suite

1. **Launch Burp Suite:**  
   - Start Burp Suite and configure your browser to route traffic through it.

2. **Browse Your Target:**  
   - Navigate through your target site and subdomains to capture traffic.

3. **Use Regex in Search:**  
   - Go to **"Burp" > "Search"** tab.
   - Select **"Regular Expression"** as the search type.
   - Paste the following regex:

   ```regex
   (?i)((access_key|access_token)[a-z0-9_ .\-,]{0,25})(=|>|:=|\|\|:|<=|=>|:).{0,5}['"]([0-9a-zA-Z\-_=]{8,64})['"]
   ```

4. **Inspect Results:**  
   - Review the search results for credential leaks.

---

## ⚠️ Disclaimer

This guide is intended for ethical security research and penetration testing within **authorized** environments only. Unauthorized use may violate legal and ethical boundaries.

