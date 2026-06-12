---
title: "share files"
date: 2014-12-26
forum: General Help
---

### Post by sarower2 on 2014-12-26
how can i share my files through wifi like any share/ shareit in android ???

---

### Post by TheFu on 2014-12-28
Setup ssh, then use sftp from anywhere in the world. sftp clients exist for **every** OS.
Best to use fail2ban to secure the connection against brute force attacks and to never use passwords for remote access - use ssh-keys.  ssh is extremely secure, unlike most other file sharing options - including HTTP,  HTTPS, FTP, CIFS - none of those are secure.

---

