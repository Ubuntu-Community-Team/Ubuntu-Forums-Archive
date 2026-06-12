---
title: "Can I make an Ubuntu Persistent file on NTFS?"
date: 2022-02-09
forum: General Help
---

### Post by heroksiddiqi on 2022-02-09
Hello, 
I have a USB drive and If I try to creat e persistent file which is larger than 4GB, it doesn't happen.
MMy question is can I install a persistent UBS which supports more than 4GB persistent file?
I tried Rufus but it creats another ext3 partition but I want ot to be on Ntfs. Is it possible?

---

### Post by dragonfly41 on 2022-02-09
I have created one partition ntfs fprmat for sharing files between Windows and Ubuntu.
Created using GParted in Live USB session.
I have never placed a 4 GB file in there so I can't answer that.

---

### Post by TheFu on 2022-02-09
**mkusb** can.  There is a slider to choose how much of the flash storage on the boot USB flash drive is ext4 or NTFS.  

There are lots of different tools for this sort of thing.  I've used one that is a multi-boot manager, but cannot recall the name now. Sorry.  Just by placing an ISO file into the first partition, any of the ISO files there will be booted. There are other partitions on the device that we can size to be anything we like and put whatever file system we like on it.

There's also MultiBootManager.

Because I just want to install the OS onto a SATA disk, I tend to use **sudo cp /path/to/iso  /dev/sdZ** to create my USB Flash installation drives. "sdZ" is the full name of the storage device, not to a partition. Everything on "sdZ" is wiped as the ISO is shoved onto it. Not for everyone and the media is read-only after, until it gets reformatted to something else.  In the Linux world, it is smart to always have 1 of these flash drives read with the OS, to troubleshoot issues from read-only media or just to have a Try Ubuntu environment for any needed purpose ... like online banking.

---

### Post by guiverc on 2022-02-09
I don't think I've ever created a persistent *fs* less than 4GB (*I've always used thumb-drives where smaller would make no sense*), but I've almost always used `[mkusb]("https://help.ubuntu.com/community/mkusb")` as TheFu has already suggested does it.

---

### Post by C.S.Cameron on 2022-02-10
I also vote for mkusb, it will create a persistent USB with a FAT32 boot partition, a ISO9660 root partition, a ext4 persistence partition and a NTFS data partition. If you are using windows, Rufus, YUMI and Ventoy will also create a persistent USB without the 4GB limit.

---

### Post by TheFu on 2022-02-10
Ventoy - that's the name of the tool most of the guys in my LUG recommend for multi-boot.  I've played with it. Worked well enough.  Being able to just copy 1 or 30 ISO files into a directory is nice. I remember ventoy had some failures in my environment, but I seem to be in the minority. Nearly everyone else swore by it.

---

### Post by C.S.Cameron on 2022-02-11
I find it a lot easier creating a Persistent flash drive with mkusb than with Ventoy.
Ventoy sure makes it easy if you need to try multiple OS.
Just drag and drop most OS to the drive and they are bootable.

---

### Post by TheFu on 2022-02-11
I've been confused by both. I find the interfaces less than clear. Usually takes me 2-3 attempts to get close to what I want.

---

