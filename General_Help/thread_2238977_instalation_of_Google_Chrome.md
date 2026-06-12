---
title: "instalation of Google Chrome"
date: 2014-08-11
forum: General Help
---

### Post by mahboob218 on 2014-08-11
Hi friends.

i have problem with the installation of latest google chrome, 
my chrome is not supported by chrome app, thats why i need help 
plz help if someone know about it , i m waiting,

---

### Post by JetStorm on 2014-08-11
All you have to do is download the appropriate .deb file for your architecture (32 or 64 bit) from this page
[https://www.google.com/intl/en/chrome/browser/?platform=linux](https://www.google.com/intl/en/chrome/browser/?platform=linux)

After the download is complete type the following in terminal:

sudo dpkg -i /path/chrome_package.deb

(you have to replace "path" above with the directory you've downloaded the file and "chrome_package.deb" with the name of the downloaded file)

After the installation is finished a new repo will be added to your apt sources.list and you'll be notified for new updates when they're available.

---

