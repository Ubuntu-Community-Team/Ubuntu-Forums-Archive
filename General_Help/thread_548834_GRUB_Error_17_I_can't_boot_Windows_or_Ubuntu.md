---
title: "GRUB Error 17: I can't boot Windows or Ubuntu"
date: 2007-09-11
forum: General Help
---

### Post by mahasmb on 2007-09-11
I have a 60 GB HDD on my laptop which is half Windows XP and half Feisty Fawn.

Everything was fine the other day. I remember, all I did was get 3ddesk working, change my Gnome themes, and backup my Feisty install by zipping everything into a .bz2 file.

Then the next day, when GRUB loads up I get a GRUB error 17. The menu doesn't even show up for me to select either partition. This is all I see.

> GRUB Loading stage1.5.

GRUB loading, please wait...
Error 17

> 17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

When I use a Live CD, I can mount Windows, but whenever I try to mount Ubuntu I get the following:

```
mount -t ext3 /dev/hda3 /mnt/ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/hda3,
             missing codepage or other error
             In some cases useful info is found in syslog - try
             dmesg | tail or so

```

So I can't even access any of my Ubuntu files to even checkout my menu.lst or anything else. 

I tried Super GRUB disk, but nothing gives.  I get this error with Super GRUB disk:

18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older

What can I do? Please help. My laptop's useless as is. I've done everything I could think of.

I tried this approach: [http://ubuntuforums.org/showthread.php?t=442945](this approach)

But I have PhoenixBIOS and not Phoenix Award BIOS.

> **sub7 said:**
> 

[IMG]http://lab.zio-matrix.net/doc/doc-img/se7505vb2/se7505vb2_bios_main.gif[/IMG]

Similar except i dont have that system menu option.

Edit: Also, whenever I use the Live CD. I always get a series of these messages. The Live CD boots, but it takes forever (20 minutes):

> [17180071.348000] Buffer I/0 error on device hda3, logical block 2
The block # is either 0, 1 or 2.

---

### Post by geraldm on 2007-09-11
Since "Primary Master" shows up as "NONE" try entering the BIOS and change to 
whatever options it offers, such as "AUTO" or "DETECT" 

If it offers "DETECT", the BIOS would normally do it right then, which should provide
you with the correct entry.  If it does not, then do NOT change or update the BIOS
when it asks as you exit.  What I do is power down, take my box apart and rock the
hard disk cable gently back and forth to create some movement on the pins.  Then
put it back together, and look into the BIOS again.  That has always worked for me,
as the cable connection was the problem.

Gerald

---

### Post by mahasmb on 2007-09-11
Uhhh... no. That's not even my picture. I just quoted someone from the thread I linked to.

I don't even have that option.

---

### Post by JBAlaska on 2007-09-11
I'm guessing that screenshot is not of your system or you wouldn't  be able to access windoze.

When you made a backup to that .bz2, did you use a move option instead of copy? and possibly moved your whole linux system to the compressed file.

If so maybe you can reverse the process and restore.

Good luck.

Edit That's what I thought.

---

### Post by Dylnuge on 2007-09-11
Please, call it Windows, and not Windoze or anything else. Windows is an OS, it exists, and it is somewhat mature. Sure, it has problems, but so does Linux. I use Linux and only Linux, but there is no need to come up with clever names for other OSes.

OK, it sounds like something is wrong with the drive. Can you post the results of 
```
fdisk -l
```
Using your LiveCD?

Here is what I think the problem is:

1. There is something wrong with your Linux partition, including /boot. /boot is where grub is stored, so this would cause grub to give an Error 17 (meaning that the MBR, which points to grub, cannot find grub).

2. If we diagnose what happened with Linux and fix it, you should be fine.

3. Even if we can't do this, worst case scenario we save what we can from Linux and reinstall Linux. If you can mount Windows, everything in Windows should be fine.

---

### Post by mahasmb on 2007-09-11
To backup my Linux partition, I used a variant of the following command

```
tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys --exclude=/media /
```

fdisk -l gives me:

```

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device              Boot        Start           End              Blocks             Id           System
/dev/hda1                               1        3916               31455238+      c            W95 FAT32 (LBA)
/dev/ hda2                         3917       4014                 787185          82          Linux swap / Solaris
/dev/hda3          *             4015        7296               26362665         83          Linux

```

---

### Post by JBAlaska on 2007-09-11
Try running [e2fsck](http://linux.die.net/man/8/e2fsck) and see if you have a corrupted superblock.

If you need to access winblows...erm windows you can overwrite grub by going into the recovery console and using the fixmbr option (or fdisk with the fdisk/mbr switch)
Be advised if you do that you will have to reinstall grub to dual boot again, but your probably going to have to do that anyways.

Edit: I just noticed your bootflag is set to /dev/hda3, On my systems (3) the active partition is /dev/hda1

---

### Post by mahasmb on 2007-09-12
So would I use a command like the following?

e2fsck -b /dev/hda3

---

### Post by JBAlaska on 2007-09-12
You might start with;
sudo e2fsck -y -f -v /dev/hda2 <--Substitute for your partition

If that doesn't work and e2fsck reports bad blocks try;
sudo e2fsck -c -c -k -v /dev/hda2

If still no joy you can try the -b switch

Run: man e2fsck to list all the options.

**Caution: you shold only run e2fsck on a UNMOUNTED ext2 or ext3 partition (From a live CD), never on a FAT or NTFS partition.**

Good luck.

---

### Post by mahasmb on 2007-09-12
It always gives me the following for either

sudo e2fsck -y -f -v /dev/hda3

or

sudo e2fsck -c -c -k -v /dev/hda3


> 
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/hda3
Could this be a zero-length partition?



for

sudo e2fsck -b 83 /dev/hda3

I get> 
e2fsck: Bad magic number in super-block while trying to open /de/hda3

The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an althernate superblock:
   e2fsck -b 8193 <device>





---

### Post by Dylnuge on 2007-09-12
Try Testdisk. Install with
```
sudo apt-get install testdisk
```
And run with
```
sudo testdisk
```.

Of course, if it is not already on the liveCD, you are out of luck (unless you find a LiveCD that has testdisk on it or a friend who is willing to make you one). I am not sure if it is.

Either way, it worked wonders for me. Windows dumped my whole drive a month ago, and I thought I had lost everything. Instead of freaking out, I calmly posted here-and someone recomended testdisk (and then e2fsck if that failed). Testdisk actually let me recover my entire drive (I only needed some things, though). It was wonderful.

Of course, you could do a lot more then just try copying. But it seems as if we may need to reinstall Linux. If you do that, then try this:

1. Find a Jump Drive. Preferably something with a lot of space-2 or more GB, so you can save the most stuff. If you have more then 2GB in your home part, you may need to use more then one jump drive.

2. Mount it. Usually it is /dev/sda, but if you are using a SCSI or SATA drive, it will be /dev/sdb (from what your fdisk -l shows, it will be /dev/sda).

3. Run testdisk and copy.

Oh, and by the way, I still can't see what could have caused this. JB had a good idea, but the corrupted superblock message means something more is wrong then just missing files. Also, bootflag does not matter-it is just the part the HDD would boot from if the MBR were at its default settings. Since the MBR has GRUB, it either displayes a menu or automatically boots-either way, the Boot flag does not matter. How about the themes? I have not seen anything like it, but since the files for themes can contain anything, maybe one of them corrupted something?

---

### Post by mahasmb on 2007-09-13
Testdisk is telling me that it's an *unkown* partition so I can't even copy my files.

---

### Post by mahasmb on 2007-09-14
Is there anything else I can do short of doing a fresh install?

It'll take me days to configure feisty all over again. Please tell me there's something else I can do.

Edit: Any ideas at all why I got this problem so I can prevent it from happening again?

Please?

Please?

Please?

Anything?

---

