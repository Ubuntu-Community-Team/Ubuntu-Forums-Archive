---
title: "Grub Error 17"
date: 2007-04-16
forum: General Help
---

### Post by MrWashy on 2007-04-16
I am consistently getting an Error 17 from grub on startup.  After searching the forums, I've tried several things to get it corrected: reinstalling grub to the mbr using the live cd, fsck (sudo fsck.ext3 /dev/hda2) etc.. i'm about at my wits end.  

cat /etc/fstab lists the ubuntu partition as hda2 and the grub menu.lst points to it correctly: hd(0,2)  I can mount the partition manually using the live cd and can see all of my files.   However actually starting up Ubuntu isn't possible.  I can't even log into the recovery prompt, as it gives an error 17.

I'd rather not reinstall everything (although waiting until the official release of Feisty on Thursday is tempting).  Any suggestions on how I can get ubuntu to fire up?


Thanks!

---

### Post by agrewal on 2007-04-16
Could you post the exact grub.conf? and the output of fdisk -L?

---

### Post by Bigbluecat on 2007-04-16
/dev/hda2 will be hd(0,1) for grub. It starts counting at 0.

---

### Post by MrWashy on 2007-04-16
My fdisk -l reads:
```
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7354    59070973+   7  HPFS/NTFS
/dev/hda2            7355        9319    15783862+  83  Linux
/dev/hda3            9320        9964     5180962+  82  Linux swap / Solaris

```

However I got the following error this time when trying to mount the drive:
```
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

When I run dmesg | tail I get this:

```
[17179696.864000] Bluetooth: Core ver 2.8
[17179696.864000] NET: Registered protocol family 31
[17179696.864000] Bluetooth: HCI device and connection manager initialized
[17179696.864000] Bluetooth: HCI socket layer initialized
[17179697.312000] Bluetooth: L2CAP ver 2.8
[17179697.312000] Bluetooth: L2CAP socket layer initialized
[17179697.568000] Bluetooth: RFCOMM socket layer initialized
[17179697.568000] Bluetooth: RFCOMM TTY layer initialized
[17179697.568000] Bluetooth: RFCOMM ver 1.7
[17180022.156000] EXT3-fs: journal inode is deleted.

```

However I don't have Bluetooth on anything.  I'm guessing the problem lies with the  "EXT3-fs journal inode is deleted".  The EXT3-fs is referring to my file system, is it not?  What is the journal inode?

---

### Post by yamswirl on 2007-04-18
Did you get that figured out?  I'm having the same problem and so far haven't found much to help.

---

### Post by raffytaffy on 2007-04-18
just a thought. i have custom kernel. everytime i install/unistal/mess with kernels...and my grub gets updated....my "root=/dev/hda1" gets replaced with "root=UUID ##############" for some reason the UUID gives me the error u guys are getting..so what i do is 
1. live session
2. sudo mkdir /mnt/test
3. sudo mount /dev/hda1 /mnt/test
4. sudo gedit /mnt/test/boot/grub/conf.lst

scroll down to the kernel in question and manually change UUID to /dev/hda1 ( mines is hda1, yours could be dif) . save. reboot.. and error seems fixed.

---

### Post by dcstar on 2007-04-18
> **MrWashy said:**
> 
.......
I'd rather not reinstall everything (although waiting until the official release of Feisty on Thursday is tempting).  Any suggestions on how I can get ubuntu to fire up?


[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by MrWashy on 2007-04-18
I hate to say it but I wound up reinstalling.  The problem wasn't actually with Ubuntu or grub, but rather a hdd going bad.  

Luckily I was able to get all of my data off of the drive before it completely died.  A new hdd and reinstall of Ubuntu and xp and we're cooking again.  Actually I just finished relaoding everything today.

---

### Post by yamswirl on 2007-04-18
When I enter

sudo mount  /dev/sda1 /mnt/test

I still get:

mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or other error.

What's up?

I'm not ready to give up and reinstall yet but just in case, how'd you get all your files off?  I'm running from the disk (6.01) and it's probably very obvious but I haven't figured that out yet.

---

### Post by MrWashy on 2007-04-18
I probably should have phrased that a little better.  All of my personal files were on a seperate partition.  I was able to use xp to make a back up of them before trashing my hdd.  The hdd was about 6 years old; I'm surprised hat it lasted as long as that.  I was lucky that my ubuntu partiton went bad first.  Had my own stuff gotten fraged I'd be screwed.  I literally had to install a new hdd.

---

