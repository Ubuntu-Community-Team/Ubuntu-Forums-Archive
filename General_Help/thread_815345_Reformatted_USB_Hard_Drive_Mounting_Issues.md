---
title: "Reformatted USB Hard Drive Mounting Issues"
date: 2008-06-01
forum: General Help
---

### Post by hapkidoan86 on 2008-06-01
Ok, I am fairly new at the whole linux thing. I have a very basic working knowledge and a book (Ubuntu Linux Toolbox) but thats about it. I switched to Ubuntu last week because I was tired of XP problems. I have had few problems and I could solve them all. Now, I have a 400GB USB hard drive I used for music/movies/installer storage that I formatted to ext3 from ntfs using gparted, and though ubuntu sees the drive, it wont mount. The drive would mount when it was ntfs and was working but had a few problems, now it wont mount at all. Here is the message I get when I click on the icon in PLACES:

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,   missing codepage or helper program or other error   In some cases useful into is found in syslog - try  

Then I tried a force mount using: "sudo mount -t ext3/dev/sdb1 /media/disk -o force" and got the same message in the terminal.

So I thought maybe I needed a new mount point since I reformatted using a different file system, so I executed: "sudo mkdir /mnt/external" and then "sudo mount -t ext3 /dev/sdb1 /mnt/external" and got the same message again. I am out of ideas. Please advise.

---

### Post by didac on 2008-06-02
Do a 

[CODE]sudo fdisk -l[\CODE]

It will tell you the filesystem on the disk. Check it is really ext3

Then run

[CODE]sudo fsck /dev/sdb1[\CODE]

---

### Post by Prospero2006 on 2008-06-02
cfdisk is also a useful tool for creating partitions. 
gparted works nicely too. 
Once you create a partition, I think you still need to format the sucker

--WARNING: THIS COMMAND WILL DESTROY ALL DATA ON YOUR DISK--

HOW TO FORMAT THE DRIVE SO YOU CAN MOUNT IT:
```

mke2fs /dev/xxxx

```
(Preface with sudo)

Then try to mount it

---

