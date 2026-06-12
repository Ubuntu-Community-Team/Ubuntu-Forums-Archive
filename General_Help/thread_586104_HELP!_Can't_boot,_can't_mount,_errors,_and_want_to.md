---
title: "HELP! Can't boot, can't mount, errors, and want to die."
date: 2007-10-22
forum: General Help
---

### Post by yesjoshyes on 2007-10-22
Alright, this is my first post.  I am a long-time Windows user, and making the switch to Ubuntu was TERRIFIC.

I was dual-booting vista and gutsy, with vista installed first.  Everything was fine until I wanted to give some more space to the gutsy partition, so I did it using a partition editor in Windows.  

Well, that's when everything hit the fan.  It somehow corrupted the windows partition, and I was forced to format.  Lost a lot of data, but most of it is backed up, so no worries.

I reinstalled windows on the same partition (after formating it to NTFS), and that messed the GRUB up, or specifically, wiped it out.  It was just booting into Windows without ever seeing GRUB.

After searching these forums, I made a SuperGrub Disk, and have tried almost every option in there with the intent of reinstalling GRUB.  When I finally got it going, I would launch the first option at the loader, and it hit me with the ERROR 17 message.

More forum searching (via liveCD), found out that I apparently need to mount my linux partition from the liveCD terminal and change menu.lst, but I can't even do that because when I try to mount, I get this:

```
wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

running sudo fdisk -l gets me this

```
root@ubuntu:~# sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1        5258    42234853+  83  Linux
/dev/sda3            5521        6690     9398025    7  HPFS/NTFS
/dev/sda4            6691        9729    24410767+   f  W95 Ext'd (LBA)
/dev/sda5            6691        9729    24410736    7  HPFS/NTFS

```

I can't boot into Windows anymore, and can't boot to Linux either.  I'm at the end of my rope, and have been trying to search and find answers for about 6 hours.  Please help if you can.  Thanks.

---

### Post by Pop_A_Squat on 2007-10-22
When i started getting the error 17 message i downloaded G-Part and had to set a disklabel for somereason, don't know if this will help but it fixed the problem right away for me.

---

### Post by yesjoshyes on 2007-10-22
changing the disklabel did nothing...  but thanks for the reply :)

about to throw in the towel, guys... anyone?

---

### Post by Soarer on 2007-10-22
It sounds like you corrupted the Ubuntu partition when changing the size of the Vista partition.

Can you run the Live CD and then, in a terminal, do

```
sudo fsck -f /dev/sda2
```

If it's really corrupted, you might need to re-install.

---

### Post by yesjoshyes on 2007-10-22
thanks for the reply, soarer, here's what that returned:

```
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Group descriptors look bad... trying backup blocks...
Corruption found in superblock.  (blocks_count = 0).

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 32768 <device>

```

I assume that means you were right about the corruption.  A few questions

1) Any way to salvage/repair it without losing data?

2) If not, any way to back up the data on that partition some way?

3) How do I prevent this in the future?

---

### Post by Soarer on 2007-10-22
Found this on Google:

> You could try using using mkfs -S , to just recreate the SuperBlock,
check man mkfs before u do that.......

take a data backup too

then after superblock is recreated ...mount file system readonly..and
then run fsck...once fsck has fixed the bugs....u can remount
read/write..and ur fs is up and running

Answer to 3 is - backup first, and make sure you know what you are doing when you partition. It is not a simple process (at least for me) and I have chickened out more than once when I realised I wasn't sure that I was doing the right thing.

I have (IIRC) also had to recreate the Superblock before, so you are not alone :)

---

### Post by RFScheer on 2007-10-22
Sorry about all the frustration.  It is technically likely that much of the data on your hard drive can be rescued but if you have most of it backed up and you're already "at the end of your rope" it will be too frustrating and time-consuming and you'd be better off wiping and installing from scratch.

If I were you, I'd go through the forum and find the best advice on dual-booting with Vista before going any further.  Lucky for me, I haven't been anywhere near Vista, but that means I shouldn't give advice on how to set it up to work well with Ubuntu.

Logically though, I'd start with Ubuntu and then deal with Vista.

A really good set of advice in the following thread on installing Gutsy...

[http://ubuntuforums.org/showthread.php?t=583007&highlight=artificial+intelligence]("http://ubuntuforums.org/showthread.php?t=583007&highlight=artificial+intelligence")

- Robert

---

