---
title: "Dual booting Windows and ubuntu: How do I get windows going again?"
date: 2006-12-11
forum: General Help
---

### Post by Muximori on 2006-12-11
This morning I tried to dual boot windows an linux for the first time. So, I deleted all partitions from my drive, made an ntfs partition at the beginning, and installed linux on the next ext3 partition, with and extended partition containing a linux swap partition and a shared fat32 partition.

Ubuntu boots no problem. I was planning to install windows on the first partition and use the windows boot loader to chose between the two on startup. However, after installing windows, I get an "Error starting Operating system" from my bios.

Looks like the MBR is stuffed. I tried reinstalling grub and pointing it to the windows partition, no dice, it just hangs. I've also used the "FIXMBR" command in the windows recovery console, and still I get the same error.

Is there any way to reinstall windows and have it work at all?

---

### Post by smoker on 2006-12-11
i'm no expert, but i think it is generally wiser to install a windows operation system first, then ubuntu, that way ubuntu can set up grub so that you can dual boot.

---

### Post by landcross12 on 2006-12-11
Try this
Boot off of a clean Windows XP cd ( your bios has to be set to boot from cd rom 1st )
choose Install ( Not > To Repair a Windows XP installation using Recovery Console, press R ) at the first prompt.

It will then search for a previous copy of windows.

When it finds your copy, it will stop at the next prompt and ask if you want to do a repair. Hit R at this screen.


If it does'nt mention a repair > DO NOT continue.

It will then copy a lot of files and appear to be doing a reinstall ( But its not. All your programs and data are safe, all you will lose, are your windows updates

Hope this helps

---

