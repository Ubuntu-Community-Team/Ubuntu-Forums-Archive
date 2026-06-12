---
title: "Can't log in!"
date: 2008-03-24
forum: General Help
---

### Post by KMJones1 on 2008-03-24
I have the similar problem to one described here (can't log in due to bad hard disk):
[http://ubuntuforums.org/showthread.php?t=733977](http://ubuntuforums.org/showthread.php?t=733977) 

I can get into a safe terminal session (but nothing else-no safe gnome session).
 
I have 2 disks: hdc has Ubuntu on it, and sda has data only.
My hdc is OK (I can list its contents etc)
My sda disk exists OK, but seems to have errors. I know this because I ran Gparted and it shows the disk exactly as expected: /dev/sda - 110GB, part used all as expected.
Bash "mount -a" gives this message:
wrong fs type, bad option, bad superblock on /dev/sda, missing codepage or other error.

Any suggestions please? I don't mind reformatting since the data are all backups from other machines.
:confused:

---

### Post by pointone on 2008-03-24
Post the outputs of "fdisk -l /dev/sda" and "cat /etc/fstab".

---

### Post by KMJones1 on 2008-03-24
Thanks for that:

1." fdisk -l /dev/sda" produces "cannot open /dev/sda"

2."cat/etc/fstab" produces relevant lines (ignoring hdc etc):

# /dev/sda /files fat32 defaults 0 0
#/dev/sda1  /media/sda1 vfat rw,utf8,user,uid=1000,gid=1000, 0 0
#/dev/sda1 /sda1 vfat rw,utf8,user,uid=1000,gid=1000,dmask 0750,fmask 640 0 0
#/dev/sda /filestore ext3 rw,uid=1001,gid=1001,dmask 0770,fmask 0640
/dev/sda /filestore ext3 defaults 0 0

The directories "filestore" and "files" and "sda1" were what I set up once but then removed (I thought!).
I think maybe I'd better start again with a clean format!?

---

### Post by KMJones1 on 2008-03-24
By the way, it all seemd to be working fine yesterday, but today cannot get logged in.
I had directories /media/disk/kev and /media/disk/laura looking fine, with files accessible, both ways from Windows network.
I have been struggling to get the Ubuntu machine accessible from WinXP machines, but yesterday it worked properly.

---

