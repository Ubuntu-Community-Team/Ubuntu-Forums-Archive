---
title: "NFS Client Issue with 4294967295 UID - Ubuntu 14.04.1 LTS"
date: 2014-11-17
forum: General Help
---

### Post by amarcionek on 2014-11-17
Hi,

I'm having a problem listing directory contents of an NFS mounted directory if the remote system has the value 4294967295 on any UID or GID. The error that comes from the shell is:

ls -l
ls: reading directory .: Invalid argument
total 0

I do not have this problem with Ubuntu 12, Solaris 10 or CentOS 6.6. Using one of these clients, I am able to ls the directory and see the contents. Using one of these clients, if I change the 1 file entry to use 4294967294 instead, then the Ubuntu client properly displays the results. 

ls -l
total 0
-rw-r--r-- 1 4294967294 root 0 Nov 17 08:45 1

Does anyone have a clue why this is happening? I realize that value is 0xFFFFFFFF or -1. This particular NFS server and file system uses that value for files created not through NFS or Linux but through other protocols (such as SMB.)

Thanks,
Adam

---

