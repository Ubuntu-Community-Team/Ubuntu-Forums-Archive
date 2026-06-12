---
title: "Icon won't start program, has picture of lock on it"
date: 2014-07-19
forum: General Help
---

### Post by RogerDavis on 2014-07-19
I have installed a program, an icon appears on the desktop, but it has a picture of a lock on it, and clicking it does nothing.

How do I fix this?

---

### Post by westie457 on 2014-07-19
Which program and how did you install it?
The small padlock picture usually means it is locked by 'root' and a user does not have access.

---

### Post by RogerDavis on 2014-07-19
It's a program I installed from a file.  /home/roger/Downloads/General_PSS-Linux_Eng_Suse_IS_V1.00.0.R.120618.tar.bz2   

I have root access, but have not been able to change the permissions.  
gksudo Nautilus won't work for me

sudo su won't work for me

@^&^&((&%^ - change you %$%&^*(+ doesn't work either.

I'm probably not going about it correctly.  

What do you advise?

---

### Post by RogerDavis on 2014-07-20
I was able to change all the permissions to myself, but it still won't run.  At first click I hear the hard drive for a couple of seconds, but nothing else happens.

Does anyone want a copy of the file to see if it works for you?

Don't know for sure what I did wrong, but got these messages in sudo nautilus : roger@roger-desktop:~$ gksudo nautilus. Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory Please ask your system administrator to enable user sharing. (nautilus:4372): GLib-CRITICAL **: Source ID 99 was not found when attempting to remove it (nautilus:4372): GLib-CRITICAL **: Source ID 101 was not found when attempting to remove it roger@roger-desktop:~$ &#8211;  

any other ideas?

---

### Post by RogerDavis on 2014-07-20
It may be loooking for a file called libXV.so.1 that doesn't exist.

./PSS : error while loading shared libraries: libXV.so.1 : cannot open shared object file : no such file or directory

What can I do about this?

---

### Post by westie457 on 2014-07-23
I really do hate to say this.
I tried to install the program into Ubuntu and a opensuse vm neither would work. In Ubuntu it would not install and in Opensuse it would not run.
Unfortunately I amnot able to help you further with this issue.

Hope you somehow get it working.

---

### Post by RogerDavis on 2014-07-24
I got it to install into Ubuntu easily, just won't run.  So it's a bit different.  I guess you searched for the file and downloaded it.

Here is the exact file I used :  [https://www.sendspace.com/file/ejdh9v](https://www.sendspace.com/file/ejdh9v)

Thanks!

---

### Post by RogerDavis on 2014-07-25
I had this same program working in 12.04, but haven't been able to get it working in 14.04 .

---

