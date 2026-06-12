---
title: "changing file permission separately from directory permission using umask"
date: 2013-11-24
forum: General Help
---

### Post by rtrampert on 2013-11-24
I'm running Ubunto server 12.04 and uploading files with Ubuntu desktop 12.04 using FileZilla SFTP. How can I change file permissions separately from directory permissions (i.e. file 644, diectory 755) with the umask command?
I'm also using PuTTY SSH for server administration.
What I need to do is automatically set permissions for directories to 755 and files to 644 when I upload with FileZilla SFTP.

---

### Post by jamesisin on 2013-11-25
For my own edification, what do you lose by making the directories 644?

---

