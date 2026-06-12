---
title: "Cannot properly format external usb drive - URGENT"
date: 2008-02-20
forum: General Help
---

### Post by Stoffer on 2008-02-20
I've been trying for days to format my Maxtor One Touch 4 Mini external usb hard drive.  It was fine originally, and in hindsight I should have left it how it was, but for some reason Ubuntu cannot mount an external NTFS drive (documented issue).  Instead of trying to find a work around for that glitch, I just used gparted to format the drive as fat32.  Big mistake.

I'm gonna use the drive in 2 days (hopefully) to transfer large files, many of which are probably over 2GB, and therein lies the problem with fat32.  So I tried formatting back to NTFS or even ext2, but NOTHING works.  Not gparted, not mkntfs, nor mkfs.ext2.  Not even the windows xp disk manager (I dual boot).  This is the output I get when I try to format the drive as NTFS with gparted:

```
GParted 0.3.3

Libparted 1.7.1

Format /dev/sda1 as ntfs  06:37    ( ERROR )
     	
calibrate /dev/sda1  01:17    ( SUCCES )
     	
path: /dev/sda1
start: 63
end: 156296384
size: 156296322 (74.53 GiB)
set partitiontype on /dev/sda1  01:21    ( SUCCES )
     	
new partitiontype: ntfs
create new ntfs filesystem  00:00    ( ERROR )
     	
mkntfs -Q -vv /dev/sda1
     	
The device doesn't exist; did you specify it correctly?
```

The only thing it'll successfully format as with gparted is fat32.  But here's the kicker:  I can't even go into XP and try programs there because XP won't even read the drive anymore!  I accidentally deleting the partition and remade it in Linux, which I think is the issue.  Even now that it's fat32 it'll install fine in windows, but will not show up as a hard drive in My Computer, which leaves editing or formatting it through XP impossible.

I really need to get this thing working by Wednesday night, which I suppose leaves me 1 day.  Can anyone help me out?

---

### Post by blueturtl on 2008-02-20
Maxtor is currently owned by Seagate. You could search their site for support. I think they had a toolset called Seatools or something that allows you to both test and format drives. This is for Windows naturally but seeing as you dual-boot it shouldn't be an issue.

---

### Post by TenPlus1 on 2008-02-20
Goto Add/Remove and select NTFS Configuration Tools which will let you mount, read and write to internal AND external NTFS drives...

Make sure NTFStools are installed in the repository and finally use Gparted to format your external drive to NTFS...  Everything will work fine and both Ubuntu and Windows will be able to read and write to the drive...

---

### Post by Carl H on 2008-02-20
/dev/sda1 is a partition, the device itself will be /dev/sda.

Have you tried cfdisk?

```
cfdisk -z /dev/sda
```

---

### Post by Stoffer on 2008-02-20
I have NTFS Config and NTFS progs already installed.  Is NTFS tools different?  Nothing came up in the Synaptic Package Mananger

---

### Post by Stoffer on 2008-02-21
Well finally since NTFS refused to work by any means, I ended up formatting to ext2 and downloading the ext2 driver for Windows from fs-driver.org, which I put on my flash drive.

Not the ideal solution I suppose, but pretty close.

---

