---
title: "VSFTPD Logged in but cannot chmod"
date: 2013-10-25
forum: General Help
---

### Post by vmikalinis2 on 2013-10-25
Hello, I've installed vsftpd and configured it so that I can login as user arcftp who is a member of the root group.  vsftpd is also running as root and I've added **chmod_enable=YES** and **write_enable=YES** to my vsftpd.conf file.  I am able to log in and browse any directory on the server but I can't chmod directories.  I'm confused at this point.....Write is enabled, chmod is enabled, vsftpd is running as root, the directory is owned by root, and the ftp user is a member of the root group.  I've noticed that I can chmod the folder if I change the ownership to my ftpuser but it's a joomla web directory and that may cause other problems.  I just need my ftp user who is a member of root to be able to chmod a directory owned by root.  Thanks to anyone that can help.

*getent group root*
root:x:0:arcftp

*ps aux | grep vsftpd*
root     19464  0.0  0.2  27152  1460 ?        Ss   13:12   0:00 /usr/sbin/vsftpd
root     19491  0.0  0.1   7640   908 pts/0    S+   13:49   0:00 grep --color=auto vsftpd

*ls -al *
drwxrwxrwx  3 root root  4096 2013-10-25 11:55 tmp

*ftp> chmod 0777 tmp*
550 SITE CHMOD command failed.

Log shows:
Fri Oct 25 13:13:23 2013 [pid 19470] [arcftp] FAIL CHMOD: Client "127.0.0.1", "/var/www/virtuals/ArcJoom3/tmp 0777"

---

