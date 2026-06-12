---
title: "FTP Upload pure-ftpd"
date: 2007-11-07
forum: General Help
---

### Post by ratcateme on 2007-11-07
I am new to CLI Linux and im using Ubuntu server 7.10
i am trying use pure ftpd with dreamweaver
i was using vsftpd but had to many problems and switched

now when i upload a file Dreamweaver says:
Started: 8/11/2007 5:12 p.m.

userlog.php - error occurred - An FTP error occurred - cannot put userlog.php.  Access Denied.  The file may not exist, or there could be a permission problem.

File activity incomplete. 1 file(s) or folder(s) were not completed.

Files with errors: 1
userlog.php

Finished: 8/11/2007 5:12 p.m.
and the FTP log says
 > PASV
 < 227 Entering Passive Mode (10,1,1,4,216,161)
 > TYPE I
 < 200 Switching to Binary mode.
 > SIZE userlog.php
 < 213 336
 > RETR userlog.php
 < 150 Opening BINARY mode data connection for userlog.php (336 bytes).
 < 226 File send OK.

i have tried to fix this but i don't understand how to set up the configuration 

it will download files fine but i cant upload

---

