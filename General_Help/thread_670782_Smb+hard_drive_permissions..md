---
title: "Smb+hard drive permissions."
date: 2008-01-17
forum: General Help
---

### Post by lonegeek on 2008-01-17
I'm trying to set up my shares to connect to with osx. My one drive works fine without a password, however the other one wants a password. The difference between the drives is that one is owned by root , which mounts, and the other is owned by zach, which doesn't. 

sudo chown root:root /media/MEDIA/

That does not work either. 

Any ideas?

---

### Post by rufius on 2008-01-17
Can you post your smb.conf somewhere or here even? Preferably with all the superfluous comments stripped out. 

A posting of "ls -al /media" would also be helpful.

:)

---

### Post by lonegeek on 2008-01-17
Tv Archive is the one working. Media is the one not working.

> [global]
workgroup = ZR
server string = %h server (Samba, Ubuntu)
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
dns proxy = no
security = share

[TV Archive]
path = /media/TV Archive
available = yes
browsable = yes
public = yes
writable = no

[MEDIA]
path = /media/MEDIA
available = yes
browsable = yes
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user= = nobody
force group = nogroup



> total 96
drwxr-xr-x  6 root root  4096 2008-01-08 15:24 .
drwxr-xr-x 21 root root  4096 2007-10-24 11:07 ..
lrwxrwxrwx  1 root root     6 2007-10-24 10:52 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2007-10-24 10:52 cdrom0
lrwxrwxrwx  1 root root     7 2007-10-24 10:52 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2007-10-24 10:52 floppy0
-rw-r--r--  1 root root   175 2008-01-08 15:24 .hal-mtab
-rw-------  1 root root     0 2007-12-31 21:54 .hal-mtab-lock
drwx------ 13 zach root 65536 2008-01-13 15:29 MEDIA
drwxrwxrwx  1 root root 12288 2007-11-18 16:57 TV Archive

---

### Post by lonegeek on 2008-01-18
Basically, How can I change the permissions of my drive to root? chown command doesn't work.

---

