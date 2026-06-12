---
title: "vftpd - anonymous user cannot access through soft link"
date: 2005-06-05
forum: General Help
---

### Post by yccheok on 2005-06-05
Hi, 
I am using vsftpd.

I try to let anonymous to access a user directory through the soft link. the user directory had opened up access to the world. however, it seems not work.

Here is the detail:

Create soft link
-----------------------
yccheok@ubuntu:/home/ftp$ sudo ln -s /home/yccheok/Movies/a/ a
yccheok@ubuntu:/home/ftp$ ls -al
total 8
drwxr-xr-x  2 root nogroup 4096 2005-06-05 23:01 .
drwxr-xr-x  4 root root    4096 2005-05-30 22:12 ..
lrwxrwxrwx  1 root root      23 2005-06-05 23:01 a -> /home/yccheok/Movies/a/
yccheok@ubuntu:/home/ftp$


The yccheok home directory has the following access: ( I opened up all the access explicitly)


Open up access to the world
---------------------------------------------
yccheok@ubuntu:/home/ftp$ ls -al /home/yccheok/Movies/
total 12
drwxrwxrwx   3 yccheok yccheok 4096 2005-06-05 22:52 .
drwxr-xr-x  41 yccheok yccheok 4096 2005-06-05 22:51 ..
drwxrwxrwx   2 yccheok yccheok 4096 2005-06-05 21:22 a

I do expected anonymous has access to the directory "a" through the soft link. However, wat I think is not true.

How anoymous access the user directory through soft link
-------------------------------------------------------------------------------------------
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
lrwxrwxrwx    1 0        0              23 Jun 05 15:01 a -> /home/yccheok/Movies/a/
226 Directory send OK.
ftp> cd a
550 Failed to change directory.
ftp>

Can anyone let me know what I can do to let anoymous can access certain director y( with access opened to the world) through soft link?

Thank you.

-cheok

---

### Post by [pl]ice on 2005-06-16
hi, i could be worng, but is there a setting that WILL allow for links to follow up for vsftpd? i think by itself it has been disabled to follow the links; but i could be wrong... just setting up mine.

---

