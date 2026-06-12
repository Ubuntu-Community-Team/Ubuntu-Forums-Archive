---
title: "Deleted logical drive, now getting Grub error 17..."
date: 2008-06-05
forum: General Help
---

### Post by s8v4o on 2008-06-05
Hi all, a linux newb here needing a little help.  On one of my computers I'm running a dual boot setup with XP and Ubuntu 7.10.  Everything was fine till I started running out of disc space in ubuntu.  I tried using Gparted to resize my windows data partition and even though I had that partition unmounted the option to resize was greyed out.  This isn't a problem on my other box running Ubuntu 8.04 as it seems to have much better NTFS support right out the box.  
I HAD the drive setup as three partitions initially. A windows patrition (hdb1), ubuntu root (hdb2), ubuntu swap (hdb3), and the data partition (hdb4), and the boot loader was installed on hdb0.  So I booted into windows to deleted the data partition so I could then go into linux and resize my small ubuntu partition.  I should have left it alone after deleting the partition but my dumb **** deleted the logical drive as well thus getting rid of the swap partition that windows saw as free space I'm assuming.  At first I thought I lost everything in linux but after looking this morning using the live CD I still have my root partition and my XP partition.  It appears that all I lost was the swap partition.  If all I lost was the swap partition why is grub having problems?  Is it because grub is actually okay and my only issue is the missing swap partition or am I totally wrong here?
I going off of memory here as I'm currently at work.  I actually browsed my root partition using the live disc and all seems to be fine there.  So my question is what should I do to repair my linux install?  I realize that I'll have to redo the swap partition but is there anything else?  Did I screw up grub somehow?  I tried booting with the live disc and running "fixmbr" but it said it couldn't find the kernel.  Thanks for reading all this crap.

---

### Post by VMC on 2008-06-05
Getting swap back:
mkswap /dev/hdax
swapon /dev/hdax

Boot with livecd type output the following from hdb2: /etc/fstab & /boot/grub/menu.lst

---

