---
title: "FTP with mounted samba share - write error"
date: 2016-06-08
forum: General Help
---

### Post by alex548 on 2016-06-08
Hello guys,

I have vsftpd installed which works ok. However, the space is very limited therefore I decided to mount a samba share which is located on another server. It is mounted using cifs to a folder within the ftp tree. From samba server I provided full read/write permission (777). Ftp user on vsftpd setup also has full read/write permission on ftp. But, it is possible to write only to a directories which resides on vsftpd host, write is not permited on mounted share - only read and directory creation allowed, cant write files.
When doing ls -la on vsftpd host to check mounted share permission it has 777 permission... Can you advise, please?

---

### Post by howefield on 2016-06-08
Thread closed.

Duplicate here : [http://ubuntuforums.org/showthread.php?t=2327160](http://ubuntuforums.org/showthread.php?t=2327160)

---

