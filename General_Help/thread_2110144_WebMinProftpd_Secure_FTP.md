---
title: "WebMin/Proftpd Secure FTP"
date: 2013-01-29
forum: General Help
---

### Post by ihthisham007 on 2013-01-29
Hi All,
I have created a ftp site on Ubuntu server 10.04 and use the Webmin Interface to create users and grant ftp access.

I have a /ftp/"X" directory where I create sub folder for each user. and give them access to that particular directory.

ftp works fine. but when you use WinScp other users are able to access the /ftp directory 

how do I prevent other users accesing the root /ftp directory when they use a FTP client program?

thanks

---

### Post by raja.genupula on 2013-01-29
changing those file permissions could help you.[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by ihthisham007 on 2013-01-29
Permission may fix the issue but I am new to Linux.
if I make a user called "Test" with a group "Test"

how do I make User "Test" access the /ftp/test directory only?

thanks

---

