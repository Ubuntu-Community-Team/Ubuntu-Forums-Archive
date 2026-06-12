---
title: "samba problem Access right"
date: 2007-01-24
forum: General Help
---

### Post by moonhk on 2007-01-24
Below is diff between original smb.conf.2* (backup)  file

 

moonhk@hex:/etc/samba$ diff smb.conf smb.conf.2*
138d137
< logon path = \home\shared
145d143
< logon home = \home\shared
301,302d298
< realm=HEX
< security=ADS
304,328d299
< [sourcedocs]
< path = /home/shared
< read list=@hex
< write list=@moonhk
< admin users=moonhk
<
< [moonhk]
< path =/home/moonhk
< read list=@hex
< write list=@moonhk
< admin users=moonhk
<
< [disk2]
< path =/mnt/disk2
< read list=@hex
< write list=@moonhk
< admin users=moonhk
<
< [cdrom]
< path = /media/cdrom
< read list=@hex
< write list=@moonhk
< admin users=@moonhk
<
< #
moonhk@hex:/etc/samba$

**When Write data into shared drive, the own is root, How to set to "moonhk" ?**

moonhk@hex:/mnt/disk2/Example/newyear$ ls -lt
total 20
**-rwxr--r-- 1 root   moonhk 13824 2007-01-25 11:21 laisee.xls**
-rw-r--r-- 1 moonhk moonhk   305 2007-01-25 10:49 laisee.txt
moonhk@hex:/mnt/disk2/Example/newyear$

---

