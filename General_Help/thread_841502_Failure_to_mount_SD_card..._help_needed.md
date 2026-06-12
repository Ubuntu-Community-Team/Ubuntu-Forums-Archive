---
title: "Failure to mount SD card... help needed"
date: 2008-06-26
forum: General Help
---

### Post by Birchlabs on 2008-06-26
My friend got an Eee PC and an 8GB SD Card to go with it. He plugged it into his Windows system first, so it got stuck with some kind of (I think proprietary variant on) FAT32 filesystem. When I put the card into the Eee PC (running fully-updated Xubuntu), I get the error message:

Unable to mount "8G Removable Volume"
mount: wrong fs type, bad option, bad superblock on /dev/sdb1. missing codepage or helper program, or other error in some cases useful info is found in syslog - try dmesg|tail or so

It needs to be read/writeable by Windows, and at least readable by Linux, so I'm pretty sure FAT32 is my only option. I found a terminal command I was able to use to mount the disk correctly before I formatted it, but it wasn't a permanent solution; it would have to be run every time the card was inserted, and that's not ideal.

About 6 hours I've been scouring Google, reading Terminal man pages, writing over the SD Card in 0s, formatting it with fdisk, etc... it'd really mean a lot to me if someone could give me an idea of how I can get this working properly.

---

### Post by chewearn on 2008-06-27
I'm not familiar with Eee PC, but couldn't you use Partition Editor (gparted) to do what you wanted?

---

### Post by Birchlabs on 2008-06-27
Okay, ended up fixing it myself. For future reference, I did this...

sudo mkdir /mnt/vfat
sudo nano /etc/fstab

Then changed the line regarding the treatment of sdb1, which said:

/dev/sdb1  /media/cdrom0  udf,iso9660 user,noauto,exec,utf8,utf8  0  0

to:

/dev/sdb1  /mnt/vfat  vfat  rw,user,umask=000  0  0

Hope that helps anyone else!

---

