---
title: "Uh oh, I just screwed up - Grub error 2"
date: 2007-03-25
forum: General Help
---

### Post by Fireblend on 2007-03-25
I have 4 partitions: Windows, Linux, Grub and data. I decided I wanted to reinstall Linux so I deleted both the Linux and grub partitions from the Windows disk manager. I rebooted the computer after this expecting Windows to load (since I had deleted everything linux-related plus grub) but instead I get grub trying to load and giving me error 2. I thought I had deleted it! Where did it come from?

So I put my alt. install CD inside and start reinstalling Linux... it gets stuck while setting up the partitioner! I suspect the hard drive with the windows partition is corrupted, so the partitioner can't somehow get past it.

So right now, I can either: Boot from hard drive and get grub error 2 (after which nothing happens at all) OR try to install Ubuntu, which will make the partitioner get stuck (with same results). I can't access my data, which I really need. 

:confused: 

HELP.

---

### Post by confused57 on 2007-03-25
> **Fireblend said:**
> I have 4 partitions: Windows, Linux, Grub and data. I decided I wanted to reinstall Linux so I deleted both the Linux and grub partitions from the Windows disk manager. I rebooted the computer after this expecting Windows to load (since I had deleted everything linux-related plus grub) but instead I get grub trying to load and giving me error 2. I thought I had deleted it! Where did it come from?

So I put my alt. install CD inside and start reinstalling Linux... it gets stuck while setting up the partitioner! I suspect the hard drive with the windows partition is corrupted, so the partitioner can't somehow get past it.

So right now, I can either: Boot from hard drive and get grub error 2 (after which nothing happens at all) OR try to install Ubuntu, which will make the partitioner get stuck (with same results). I can't access my data, which I really need. 

:confused: 

HELP.
If you have a Windows install cd(not a recovery cd) or a Win98 boot floppy, you could reinstall Window's IPL to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by Cappy on 2007-03-25
Basically, from a boot CD with rescue mode/floppy: "fixmbr" or maybe "fixboot" to boot back to windows. The problem is the mbr can't find linux now (where your boot files are!).

You can avoid this problem entirely if you have 2 hard drives, with one you can put the MBR for windows and the other the Grub MBR. You would have to swap which hard drive the BIOS initially boots from when you install the second OS, however.

---

### Post by deanlinkous on 2007-03-26
You do have backups of your data, right?

Boot from a win98 boot disk or similar and use the command **fdisk /mbr** and hope that is it. If you have a seriously corrupted partition table you may need to wipe all the partitions and start over.

---

