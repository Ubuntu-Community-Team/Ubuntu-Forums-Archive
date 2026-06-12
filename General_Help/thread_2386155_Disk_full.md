---
title: "Disk full"
date: 2018-03-01
forum: General Help
---

### Post by vee123 on 2018-03-01
Hi.. Guys.. I mounted second harddrive over a folder more than once.. Now my disk says it's full.. Df says only 16gb of 400gb used... I tried bind mount but cannot seem to find what is taking up the space..

---

### Post by cruzer001 on 2018-03-01
Hello

Its not your /boot full of old kernels?
```
df -h /boot
```
[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

---

### Post by vee123 on 2018-03-01
Nope
. Cleaned that out...

---

### Post by oldfred on 2018-03-01
Have you emptied trash?
And if using sudo , emptied root's trash which can be difficult to do?

Post this:

df -H

       [https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean)
Do yourself a favor and avoid bleachbit. 
   Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)
[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels) 
   RecoverLostDiskSpace
[URL="https://help.ubuntu.com/community/RecoverLostDiskSpace"]https://help.ubuntu.com/community/RecoverLostDiskSpace

[/URL]
 # check sizes of 
Partition sizes
df -Th | grep sd| sort
Inodes:
 df -i
cd / or cd /home
sudo du -hc --max-depth=1
Shows just /
sudo du -hx --max-depth=1 / 2> /dev/null
to also see hidden in /root folder
sudo du -sh /root/.[A-z]* /root/*
#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
sudo -H nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files. 

[URL="https://help.ubuntu.com/community/RecoverLostDiskSpace"]
[/URL]

---

### Post by deadflowr on 2018-03-01
What do you mean by
> I mounted second harddrive over a folder more than once
Please clarify this.

---

### Post by vee123 on 2018-03-01
2 hardrives.. Sda which the maindrive and a second harddrive Sdb... Mounted sdb1 partion onto media folder.. Media/hardrive2... Ran rsync to copy changes from sda to sdb1 via folder media/hardrive2 mounted folder... Rsync would complete and the Ubuntu os would unmount hardrive2 folder...Then we would remount media/hardrive2... However we were not aware that when we remount the old mount was still there and the rsync files were copied into hardrive2 folder... The os overlays or 'hides' the first folder and writes to the second folder.. This  is what I suspect has taken up the space.. Based on my reading... I have tried mount - - bind which did show one folder under mrdia/hardrive2 mount with info on it.. Which I unmount... However the hard drive sda says still full.... I suspect that remount multiple times cause multiple overlays.. Which I cannot seem to locate in media/hardrive2 via bind mount... Please help

---

### Post by vee123 on 2018-03-01
hi emptied trash and tried all commands...these files seem to be hidden by the mount command ...tried mount --bind folder  one hidden folder..but there are more that i cannot find...

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       451G  451G     0 100% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            7,8G  4,0K  7,8G   1% /dev
tmpfs           1,6G  844K  1,6G   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            7,8G     0  7,8G   0% /run/shm
none            100M     0  100M   0% /run/user
overflow        1,0M  8,0K 1016K   1% /tmp
```

---

### Post by deadflowr on 2018-03-01
post the mount commands used.

---

### Post by vee123 on 2018-03-01
```
sudo mount /dev/sdb1 /media/hardrive2
``` .

---

### Post by vasa1 on 2018-03-01
Please use code tags!

---

### Post by vee123 on 2018-03-01
> **vee123 said:**
> sudo mount /dev/sdb1 /media/hardrive2

sorry newbie

---

### Post by QIII on 2018-03-01
Hello!

Welcome to the Forums!

Please use code tags to contain all terminal commands and their results.  That preserves terminal formatting and makes your posts much easier to read.

To use code tags, you may either:

Highlight text and click the # button in the text box header or click the # button first, place your cursor between the code tags and type or paste your text.

- or -

Type [noparse]```
[/noparse] at the beginning of your text and [noparse]
```[/noparse] at the end.  The square brackets are required.

Thanks!

---

