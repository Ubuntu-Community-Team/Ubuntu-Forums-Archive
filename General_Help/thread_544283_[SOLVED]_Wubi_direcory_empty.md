---
title: "[SOLVED] Wubi direcory empty"
date: 2007-09-06
forum: General Help
---

### Post by moulin on 2007-09-06
I am really messing things up today. Ubuntu does not want to boot anymore. When I look in Windows XP I have no access to the c:/wubi directory with windows explorer. When I have a look in dos it states the directory is empty. Beside this I cannot find Wubi in my installed programs list. What can I do?
:confused:

---

### Post by ago on 2007-09-06
depends on what happened, you can try chkdsk /r

---

### Post by yagogak on 2008-03-27
Same problem, chkdsk run succesfully but wubi root folder is still empty,
any other idea ?

I'm using wubi for 6 month without any problem before this... :confused:

---

### Post by ago on 2008-03-27
It's extremely unlikely for wubi to affect files outside of /wubi/disks/ other than via a hard-reboot
So if other files are missing within /wubi and chkdsk is fine, looks more like an accidental deletion from windows or other windows problem.

---

### Post by yagogak on 2008-03-27
no boot under window for month, except today... after the problem.

Actually , when i selected wubi, the window boot loader display the following message :

File : \ubuntu\winboot\wubildr.mbr

satus : \0xc000000f

Info : ( translate from french ) Impossible to load selected entry, missing or dammaged.

thx for your help.

---

### Post by ago on 2008-03-27
Quick googling points to a windows error or fs corruption (possibly due to hard reboot).

[http://www.google.com/search?q=0xc000000f](http://www.google.com/search?q=0xc000000f)

I haven't seen that before, see if you can find any solution that work in the link above and in case post it here for others that my run into the same situation. Sorry if I cannot be of more help.

---

### Post by yagogak on 2008-03-28
Finally i solve my problem ! My ubuntu is back.

the steps : 

 - windows showed an empty hard drive ( wubi stand on a specific partition ) 

- i boot under window and with testdisk  ( open source )[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")
 i browse the dead partition and i found a folder found.000 and restore it on a other disk. This folder contain the full wubi structure ( great ! )

- then I've formatted the damaged partition
- copy all the restored file on the freshly formatted partition.

- and try to reboot. But the startup process failed with a error because UUID of disk have change ( due to the format process i think ).

- then i get to initramfs, and type 
ls -l /dev/disk/by-uuid/ 
to retreive the new UUID

- reboot

- edit the grub entry and replace the old UUID with the new one

- it works !

i think now i will backup the full wubi structure once a month

---

