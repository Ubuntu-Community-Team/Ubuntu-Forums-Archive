---
title: "klibido and kTorrent writing to FAT 32 partition"
date: 2006-09-26
forum: General Help
---

### Post by yeehawjared on 2006-09-26
For some reason klibido (newsbin for linux) and kTorrent can't write to my fat32 partition.  I can read/write files to the partition all day long.. it's only when other programs write to it that I get errors

/etc/fstab looks like this: 
/dev/sda5       /media/STORAGE     vfat    rw,users,gid=users,umask=000,       0       0

Attached are screenshots of my settings, then the error message.  The error message says "Cannot symlink /media/STORAGE/temp....   to /media/STORAGE/torrents"

Anyone know why I can write to my /home/jared folder just fine, but not my /media/STORAGE/ hard drive?

---

### Post by Mr Frosti on 2006-09-26
If it is just these two programs, then it could be the way that it configures its information. The program is failing with the message "Cannot symlink /media/STORAGE/temp". Does the folder "/media/STORAGE/temp" exist? If not, then creating the symlink will fail. Try manually creating this folder, and give it the "chmod 757" command.

Also, running these programs from a terminal (Konsole), will give you more output and might give a clue as to what is going on.

Let us know the results...

---

### Post by stoeptegel on 2006-10-06
> **yeehawjared said:**
> 
Anyone know why I can write to my /home/jared folder just fine, but not my /media/STORAGE/ hard drive?

Your /home/jared uses a file system that supports symlinks, the fat32 system used for /media/STORAGE on the other hand does not support symlinks. KTorrent uses symlinks between temp folder and data folder, so if it can't make a symlink because of fat32 it'll behave like this. Solution would be to set the temp folder to a partition that supports symlinks.

---

### Post by yeehawjared on 2006-10-06
gotchya...  the problem was that I had Ubuntu on a 5 gig partition.  I had a 55Gb fat32 partition I'd use between XP/Ubuntu.

How I solved it - backed up everything in the storage partition to an external HD.  Reformatted my storage drive to ext3.

I use fsdrive in XP to mount that partition.  It works flawlessly.  
[http://fs-driver.org/index.html](http://fs-driver.org/index.html)

I read somewhere that fat32 is really old, has fragmentation issues, 4.xGB file limitations, etc.  and that it shouldn't be used anymore.  Ext3 is a great filesystem and works great under XP for storage drives.

Here's how I have my 80Gb laptop drive set up:
15Gb - NTFS (XP)
58Gb - Ext3 (/home)
06Gb - Ext3 (/)
01Gb - Ext3 (swap)

---

