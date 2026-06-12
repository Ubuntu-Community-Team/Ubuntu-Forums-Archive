---
title: "File/Directory Rights/Permissions question"
date: 2019-02-04
forum: General Help
---

### Post by sidetrack on 2019-02-04
First thank you for anyone who is willing to help solve this issue.  I really appreciate it.

Ubuntu Version: 16.04

I am having issues with one of my websites and I need help from the manufacturer of a specific piece of software to ftp in and help me out.  I have the ftp user setup and its working fine. However, he needs to create/edit/delete files within the Apache2 root directory /var/www which is owned by www-data:www-data . I need to know the best way to allow another user to create/edit/delete files within a directory that is under /var/www/xyz.   I have tried adding them to the group and changing the folder permissions from 755 to 775 but that did not seem to do it.  The xyz directory contains a website and it needs to have the file owner be www-data and the group be www-data.  because this company only uses ftp to access the system, they can not sudo or su for root access (unless I am missing something there).

thanks for any help you can offer.

Rob

---

### Post by TheFu on 2019-02-04
Only sftp or ssh should be allowed.  Setup a chroot.  ssh has a guide for doing that which google easily locates.  You can also limited the source IP for the connections in the sshd_config file.

Plain FTP should have died in 1996. Any company allowing/demanding plain FTP the last 15 yrs needs to be fired. Today.  IMHO.  If you elect to ignore this advice, use the hosts.allow and hosts.deny to at least block everyone from using FTP from anywhere in the world, now that those credentials have been sent like  postcard over the internet.

Any userid that you want to have write, change, delete to files/directories needs to be a member of the group and the group must allow w access.  There are guides for setting up groups of userids so thy can work together in Unix.  

A summary for Working Together

    Put everyone into the same group.
    Create a directory where they can share files.
    Make the group on that empty directory have rws permissions
```

           $ sudo gpasswd -M  user1,user2,user3  ourgroup
           $ mkdir -p /tmp/Workspace
           $ chmod g=rwxs Workspace
           $ ls -l Workspace
              drwxrws---   owner    group    Workspace/ 
           $ chgrp ourgroup Workspace
           $ ls -l Workspace
              drwxrws---   owner    ourgroup    Workspace/
```

---

### Post by HermanAB on 2019-02-04
Ayup - FTP is only good for Anonymous use and preferably only on a LAN, not a WAN.  There is no security in FTP.  

The only way to get some semblance of security with it on a WAN, is to make separate upload and download directories, otherwise your system will be turned into a pr0n repository pretty soon.

---

