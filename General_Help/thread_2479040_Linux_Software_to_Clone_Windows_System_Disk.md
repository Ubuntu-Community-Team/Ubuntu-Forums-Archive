---
title: "Linux Software to Clone Windows System Disk?"
date: 2022-09-12
forum: General Help
---

### Post by fran_3 on 2022-09-12
I run two machines... a Windows 10 Pro machine and a Ubuntu machine.

The Windows machine system drive (C:) is crashing every few minutes. It will boot back up but only run a few minutes.

I was going to clone it with Macruim Reflect 8 which is free Windows software to clone a Windows system disk but I didn't act fast enough.

Is there a Linux program that will clone the Windows 10 system drive to my new SSD drive?

Most of the data is backed up but the big problem is all the programs I have installed on the machine. It will take days and days and days to reinstall all that software.

This is a 911 for me  so thanks for any help.

---

### Post by dragonfly41 on 2022-09-12
There are several broad ideas which come to mind.

Using Azure or other cloud subscription service create Windows 10 and try to import assets from your failing Windows 10.
There is a free trial option.
Personally I find Jelastic very useful since you can use it on a "pay as you go" basis, shutting down when not in use.

Or you could try running a virtual machine in Ubuntu then from within that scan your failing Windows 10.

There must be other options. From Ubuntu you can view mounted ntfs Windows files using R-Linux.

---

### Post by HermanAB on 2022-09-13
Copying the disk is the easy part.  The good old kitty cat will do it. Convincing the copy to run is the hard part.

---

### Post by Tadaen_Sylvermane on 2022-09-13
live boot clonezilla and put it somewhere, i run mine from my network boot ubuntu. then change the drive, reload the netboot and clonezilla the image to the new drive.

---

