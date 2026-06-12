---
title: "HELP!! kernel panic, unknown block(0,0) -- Load Ubuntu from GNU Grub"
date: 2015-08-08
forum: General Help
---

### Post by Apolymoxic on 2015-08-08
[COLOR=#111111][FONT=Ubuntu]I've been trying to find out how to load unbuntu for a few days now, but I am at a point where I have no clue what I am doing... I'm not that savvy when it comes to Linux OS anyway...[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I've read this: [How can I load Ubuntu when all I have is Grub?]("http://askubuntu.com/questions/21342/how-can-i-load-ubuntu-when-all-i-have-is-grub")[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]But that doesn't seem to get me where I need to be.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Problem started when there was a power outage. The next time that the computer was turned on, the error "kernel panic-not syncing: VFS: unable to mount root fs on unknown block(0,0)" was given. I read the following:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][http://ubuntuforums.org/showthread.php?t=1751574](http://ubuntuforums.org/showthread.php?t=1751574)

**DISCLAIMER:** [/FONT][/COLOR]

[LIST]
[*]Yes, this topic is still alive, but it's ancient and rarely gets answers. Plus, it's not very pertinent to my problem, thus the new post
[*]Yes, I've posted this question elsewhere...  [http://askubuntu.com/questions/659159/how-do-i-load-ubuntu-from-gnu-grub](http://askubuntu.com/questions/659159/how-do-i-load-ubuntu-from-gnu-grub), but I am not sure if these two forums are linked, so I thought I'd ask here as well.
[/LIST]
[COLOR=#111111][FONT=Ubuntu]Found this to be a similar problem, and after playing around with it, I got the error to go away, but now I just get the "grub>" bash menu.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I can load from a liveCD... if that's any help.[/FONT][/COLOR]

[LIST]
[*]ls returns "(hd0) (hd0,msdos5) (hd0,msdos1)"
[*]ls (hd0,1)/ returns alot of stuff... Not really sure what I am looking for
[*]ls (hd0,1)/boot/ returns "grub/"
[*]ls (hd0,1)/boot/grub returns "i386-pc/ locale/ fonts/ grubenv"
[/LIST]
[COLOR=#111111][FONT=Ubuntu]Any ideas on how to get this thing to load?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thank you in advance[/FONT][/COLOR]

---

### Post by ajgreeny on 2015-08-08
Boot to the live DVD and when you get to the GUI open terminal and run ```
sudo fdisk -l
```which will show us the partitions on the hard disk, and we should be able to see which is the ubuntu root partition.

Having figured that out we can now run a filesystem check on that with ```
sudo e2fsck /dev/[COLOR="#FF0000"]sdx#[/COLOR]
``` where [COLOR="#FF0000"]sdx#[/COLOR] is the root partition found with fdisk.  Now reboot to your installed system and with luck you will get back to a full desktop.

---

### Post by Apolymoxic on 2015-08-08
Thank you for the reply. I did the above steps and this is what I get:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c66a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1465147391   732322817    5  Extended
/dev/sda5          501760  1465147391   732322816   8e  Linux LVM

Disk /dev/mapper/ubuntu--vg-root: 747.8 GB, 747756322816 bytes
255 heads, 63 sectors/track, 90909 cylinders, total 1460461568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 2139 MB, 2139095040 bytes
255 heads, 63 sectors/track, 260 cylinders, total 4177920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

Disk /dev/sdb: 16.4 GB, 16358768640 bytes
255 heads, 63 sectors/track, 1988 cylinders, total 31950720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe7fdf203

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    31950719    15975328+   c  W95 FAT32 (LBA)

```

I am assuming that the asterisk marks what device is the current boot - in this case sda1? So I used:

```

ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.42.9 (4-Feb-2014)
/dev/sda1: clean, 623/62248 files, 243313/248832 blocks

```

This makes it where it boots to the "grub>" prompt. Nothing else. 

I look at the above, and it looks like Linux LVM is on sda5? Again, I am not too savvy on linux so I am not sure what I am supposed to be looking at, but I tried:

```

ubuntu@ubuntu:~$ sudo e2fsck /dev/sda5
e2fsck 1.42.9 (4-Feb-2014)
/dev/sda5 is in use.
e2fsck: Cannot continue, aborting.

```

That obviously didn't work. 

What am I missing?

---

### Post by Apolymoxic on 2015-08-08
Oh...
I tried to use "boot" at the "grub>" prompt... it says 
"error: you need to load the kernel first"

I don't know if that helps or not.

---

### Post by ajgreeny on 2015-08-09
Sorry but as you are using LVM I'm afraid I am totally lost, so can not help you any more with this.  Hopefully others will be along and will know more about LVM partition management.

---

