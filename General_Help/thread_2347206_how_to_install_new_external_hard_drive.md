---
title: "how to install new external hard drive"
date: 2016-12-22
forum: General Help
---

### Post by jerry50 on 2016-12-22
I have a new System 76 running Ubuntu 16.04,  I bought an external hard drive, Toshiba Canvio Connect II.  I have plugged it in and then turned on the computer, and I've also tried turning on the computer first then plugging it in, but when I double click the set up.exe or any other set up in any other file on the hard drive, I always get  "An error occurred while loading the archive."  I probably have to do something in the terminal, but I don't have a clue.  Please tell me, step by step, what to do.  Rather new at this Linux thing. 

I  tried "fdisk -l" but I get Permission denied for all 18 files listed.

---

### Post by oldfred on 2016-12-22
Any .exe is a Windows executable. Will not work in Linux.

It looks like it has cloud software & other software that the setup.exe probably configures. With Linux you should not need that.

Does gparted show drive? 
Will you use drive with Windows also? If so then NTFS may be better format. But if Linux only use ext4 as you need Windows to occasionally repair NTFS.

---

