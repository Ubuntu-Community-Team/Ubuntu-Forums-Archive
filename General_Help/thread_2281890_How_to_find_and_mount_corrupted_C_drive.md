---
title: "How to find and mount corrupted C: drive?"
date: 2015-06-10
forum: General Help
---

### Post by samir6 on 2015-06-10
My HP laptop recently crashed and the hard drive has been corrupted. I don't know what i did wrong, seeing as I bought it about a month ago, and had my older hard drive replaced with this one.
I have somewhat of a backup on my external hard drive. It's not recent, the last time I backed up was 3 weeks ago if i remember correctly.
Anyways, that older hard drive also crashed on me (this was before i bought the new hard drive), so I put Ubuntu on my USB and booted my laptop using that USB (i didn't install ubuntu, i only used the Live CD thing), and I tried accessing my hard drive, but I couldn't even find it.
I don't know how, but I managed to find and mount the drive, and copy all my files to my external hard drive before it was too late.
Fast forward to today, and I have the exact same problem. I don't know how to make that work again. The problem is that it doesn't even show up in my list of drives. It didn't show initially when I tried it a month ago, but I managed to make it work using some suggestions from solved forum posts.
The next problem with my old hard drive was that it wouldn't open. That was a lot easier to fix, because I just had to enter a command in terminal. After that I was able to copy my files to my external hard drive.
So how do I find the C drive? And how do I mount it (as I said, all I need is for it to show up in the list of drives.)?
This is urgent as I have an english assignment due in 5 days which I've been working on before it crashed.. 
Can anyone help?

---

### Post by yancek on 2015-06-10
Boot the Ubuntu from the flash drive, open a terminal and type in the following command, no password needed:  sudo fdisk -l(Lower Case Letter L in the command) and post the output here which will show the hard drives and partitions and someone should then be able to make a suggestion.

---

### Post by samir6 on 2015-06-10
I got this:

Disk /dev/sda: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00095919

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          32     7821311     3910640   12  Compaq diagnostics

---

### Post by yancek on 2015-06-10
The fdisk command will generally show all hard drives plugged into the computer as well as partitions.  The output you posted only shows one diagnostic partition on a 4GB drive, flash drive?  Do you see the different physical hard drives recognized in the BIOS?

---

### Post by samir6 on 2015-06-10
That 4GB drive is the flash drive I'm running Ubuntu on. I don't know if this is what you mean but in the boot options menu in the BIOS, I can see "OS Boot Manager" in the UEFI Boot Order list and "Notebook Hard Drive" in the Legacy Boot Order list.

---

### Post by SeijiSensei on 2015-06-10
Does the BIOS show the computer's hard drive?  The fact that fdisk cannot find it suggests the drive is so broken as to be unmountable, but fdisk has trouble with some newer types of drives.  Try running "sudo parted" from the command prompt, then type "p" at the "(parted)" prompt.  What does that show?

---

### Post by samir6 on 2015-06-11
I don't know if the BIOS actually recognizes the hard drive :/ Here's what I get when I run sudo parted

Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sda: 4005MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  4005MB  4004MB  primary  fat32        boot, diag

Ubuntu only recognizes the USB which it's running on. I don't understand how my hard drive got corrupted so quickly. It's only been a month since I got it. 
I think I might be on to something, though; I saw a forum post that says using Puppy Linux might work. I put it on another USB using Universal USB Installer, but my laptop doesn't recognize it when I try to boot it.

---

### Post by dragonfly41 on 2015-06-11
Since you are on a tight deadline (5 days and counting) I'll throw in another suggestion.

In your LiveUSB you should have testdisk installed. If not install it from Ubuntu Software Centre.
description: Partition scanner and disk recovery tool.

Then scan your entire drive with testdisk from command line and post back here the summary log results.

---

