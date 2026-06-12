---
title: "Hidden HPFS/NTFS"
date: 2008-06-08
forum: General Help
---

### Post by 4XDOR on 2008-06-08
Hi,
I am a new Linux user, and already managed to mess-up...:(

However, I have freshly installed Ubuntu 8.04, on my Pentium 4 (1.5Ghz), after allocating a specific partition on one of my (2)  IDE disks.
Previously the PC was a Windows VISTA machine with NTFS partitions on both disks. ;)
For a couple of days, I could mount & access all my NTFS volumes (partitions) via the 'Places->Removable Media' pull down menu.
Stupidly enough, I have tried to change one of the volumes name (via Ubuntu), and since, I can not mount it, but getting a pop-up with no text (but with OK button), followed with another POP-UP: "Cannot mount Volume."
The detailed message: "$MFTMirr does not match $MFT (record 0). Failed to mount /dev/sda3 ...."

sudo fdisk -l provided the following:

ubuntu@ubuntu:~$ sudo fdisk -l

[INDENT]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c874c86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2996    24065338+  83  Linux
/dev/sda2            2997        9729    54082822+   f  W95 Ext'd (LBA)
/dev/sda3            9730       17418    61761477   17  Hidden HPFS/NTFS
/dev/sda4           17418       19458    16384000   83  Linux
/dev/sda5            2997        6443    27687996    7  HPFS/NTFS
/dev/sda6            6444        9729    26394763+   7  HPFS/NTFS
[/INDENT]

I have booted the PC from an emergency CD with DOS and DOSNTFS anf managed to access the volume and the data. I could not do so when  when connected and booted from another PC (Windows XP SP2).

Am I about to sing :guitar: goodbye ):P to my 60Gbytes NTFS partition? :cry:

Who is the magician that can help me?

Thanks in advance,

4XDOR

---

### Post by ultraloveninja on 2008-06-08
Try using the fstab.  There is more info about it here:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

If you also want to make partition space for shares later on, use gparted.  I downloaded it and used it as a live CD.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Hope that helps!

---

### Post by 4XDOR on 2008-06-08
> **ultraloveninja said:**
> Try using the fstab.  There is more info about it here:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

If you also want to make partition space for shares later on, use gparted.  I downloaded it and used it as a live CD.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Hope that helps!

Tnx U.L.N,

I am not sure what the syntax should be. However, I have rebooted the system & tried to mount again (the same method using the "Places->Removable Media") and now got a single pop-up:
[INDENT]
Cannot mount volume.
Unable to mount the volume 'New Volume'
Details:
mount_point cannot contain the following
characters: newline, G_DIR_SEPARATOR (usually /)
[/INDENT]

gparted shows the following message on my terminal:

======================
libparted : 1.7.1
======================
Can't have overlapping partitions.

The window for /dev/sda shows a single 149.05 GiB unallocated... :(

Furthermore, please have a look and see that there are over lapping block allocation within different partitions. Could it be the problem's source? :confused:

---

### Post by 4XDOR on 2008-06-09
Hey Guys,

I need your **help**!!!

Pleeeeaaaase ???[-o<

---

### Post by 4XDOR on 2008-06-09
Here is Some more information I came out with, during my unresulted ](*,)efforts:

[INDENT]
I have tried to run cfdisk on /dev/sda and failed due to:
**FATAL ERROR: Bad Primary partition 3: Partition ends in the final partial cylinder.**
[/INDENT]

I guess partition /dev/sda3 has to be changed, and the ending should be 17417, since the next partition starts with the same current ending address.

/dev/sda3            9730       17418    61761477   17  Hidden HPFS/NTFS
/dev/sda4           17418       19458    16384000   83  Linux


Is it so? If yes, how can one do it? What are the risks?:confused:


thanks in advance, 4XDOR

---

