---
title: "Can't Boot With LSI Megaraid SCSI"
date: 2008-05-07
forum: General Help
---

### Post by ML570 on 2008-05-07
Hello friends!

I need some help with my ML570 that runs 6 15k drives on a LSI MegaRAID SCSI 320-2 Dual-channel [
[http://www.lsi.com/storage_home/products_home/internal_raid/megaraid_scsi/megaraid_scsi_3202/index.html](http://www.lsi.com/storage_home/products_home/internal_raid/megaraid_scsi/megaraid_scsi_3202/index.html) ] with the latest BIOS.

I had FreeBSD installed (no problem), but need to use VMware for work so I chose to switch to Ubuntu.

I am a *NIX newbie.

1. Server boots with Ubuntu 8.0.4 Desktop
2. I select language
3. Server goes through the loading animations
4. Server spits out error
5. No more progress is made



Here is the error I get when I try to install Ubuntu:

```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [  133.830297] sd 2:2:0:0: [sda] Asking for cache data failed
[  133.830387] sd 2:2:0:0: [sda] Assuming drive cache: write through
[  133.830734] sd 2:2:0:0: [sda] Asking for cache data failed
[  133.830826] sd 2:2:0:0: [sda] Assuming drive cache: write through
```



I did some research and it seems that Ubuntu for some reason has problems with LSI Megaraid controllers (I think):

[http://ubuntuforums.org/archive/index.php/t-208510.html](http://ubuntuforums.org/archive/index.php/t-208510.html)


[SIZE="2"]> ssjoholm
September 2nd, 2006, 07:48 AM
Hi,

I don't have that RAID controller, but I found following info;

Intel SRCS16 and SRCS28X Serial ATA RAID Controller PCI cards &#8212; real hardware RAID. These are six-port PCI and eight-port PCI-X cards (respectively) for servers, based on an LSI Logic MegaRAID chipset, driving SATA-I output using Silicon Image SiI3112A SATA-I chips (one for each channel pair) and an Intel GC80302 or IOP331 (respectively) dedicated I/O processor with 64MB or 128 MB of ECC SDRAM (respectively) for processing XOR logic. Use the kernel's "megaraid2" driver (For LSI Logic MegaRAID). The Silicon Image chips are not the system-facing chipsets (1 2), and so don't determine driver support. An optional battery-backup daughterboard is available.

source:[http://linuxmafia.com/faq/Hardware/sata](http://linuxmafia.com/faq/Hardware/sata)

It's seem that "megaraid2" has to be inserted to the kernel, maybe this should be checked if it's loaded correctly.[/SIZE]



Please help. I have no idea how to build a custom kernel. I am not even sure if this is my problem. It is very urgent that I get this system up and running asap.

Thank you in advance!

---

### Post by ML570 on 2008-05-07
These threads could be of value to a more experienced user:

[http://ubuntuforums.org/showthread.php?t=661598](http://ubuntuforums.org/showthread.php?t=661598)
[http://ubuntuforums.org/showthread.php?t=201858](http://ubuntuforums.org/showthread.php?t=201858)

---

### Post by ML570 on 2008-05-07
It seems that both of the links that I posted, even though related (MegaRAID issue) do not describe hardware I run.

The former link is about SAS card and the later about seemingly antiquated SCSI card.



What is the deal with Linux an MegaRAID cards?

How to fix this?

---

### Post by fjgaude on 2008-05-07
The first thing to consider is, "Can we install onto a SCSI drive?"

I don't know anything about the hardware you have, but I know that if you are trying to install Ubuntu onto a filesystem using a drive name that it can't understand, then you are into troulbe.

Normally you have a driver disk that Ubuntu can use to install itself when you use the Alternate LiveCD, not the normal one.

That's about all I can say or know.

---

### Post by ML570 on 2008-05-07
Thank you for reply.

I am surprised that FreeBSD autodetects things right off the bat and Linux does not.


I hoe a kind soul chimes in with a solution to this driver issue.

:confused:

---

### Post by ML570 on 2008-05-08
Is there a better place to post this question :confused: ?

---

### Post by fjgaude on 2008-05-08
You might look over the Forums list and try something like Servers.

Good luck.

---

