---
title: "Partimage - Help needed"
date: 2007-11-27
forum: General Help
---

### Post by errolgreer on 2007-11-27
As a complete novice with Linux, I have intalled Ubuntu 7.10 (dual boot with Windows) on a 2nd hard drive. I need simple howto instructions to save and restore an image file to/from a DVD using Systemrescuecd. I do not know the Linux commands, so I need step by step instructions. The manual assumes you know Linux, which I do not at this stage. I have a bootable systemrescuecd CD. 

Thanks

Errol

---

### Post by TidusBlade on 2007-11-27
If by image file you mean like an ISO, then try Gnomebaker or K3B, but I think K3B is much better, and still works perfectly under GNOME ;)

---

### Post by errolgreer on 2007-11-27
Basically I need to back up my Ubuntu installation partition to a DVD so as to bring it back if I somehow corrupt it. I use Norton Ghost for my Windows partition, but It doesn't work with Linux. Do the apps you mention do this ? The Systemrescuecd app does this but it assumes you are a Linux expert, which I am not !

---

### Post by TidusBlade on 2007-11-27
Im not an expert :P Just started about 4 months ago xD I thought you meant ot burn ISOs, so K3B is a burning suite. IF your looking for backup, I remember using Acronis some time back, and it sucessfully backed up my 44GB linux partition to another windows partition. I am sure theres an open-source program to do that for you ;) Ill look around and post back.

---

### Post by Clancy_s on 2007-11-28
I can't actually help you - I'm about to try it for the first time.  There's detailed instructions / discussion (still active) here:

[http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)

It looks doable...

---

### Post by indytim on 2007-11-28
During the Partimage front end inputs, you will have the option of saving the output into a specific file size upper limit.  If you specify ~4 G, then the partition image will be broken down to discreet parts saved with the extension of .000 , .001 etc.

You will need adequate space to store these output files (remember you cannot backup your currently booted partition).  After Partimage has completed it's thing, then burn each of the images to a respective DVD (or CD as the case may be).

For recovery, I've never used a segmented partition, but I believe you will have to do a restore by each file (DVD with noting the .000, .001 extensions).

A much easier approach is to set up a dedicated partition for storing your image file if you have the space.

Hope this helps,

IndyTim

---

