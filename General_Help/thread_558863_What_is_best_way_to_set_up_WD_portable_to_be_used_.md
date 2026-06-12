---
title: "What is best way to set up WD portable to be used with dual boot - Vista and Ubuntu"
date: 2007-09-24
forum: General Help
---

### Post by giboman on 2007-09-24
Sorry to ask such a simple question, I am new at this.

I have a dual boot on my laptop - Ubuntu and Vista.
I just bought a Western Digital Portable 120GB, I would like to be able to use this for both operating systems. The spec. that came with the drive only refers to windows XP, no mention of Linux.
Vista is formatted for NTFS.
Linux is formatted for ext3.

What would be the best way to proceed.
Any help would be welcomed:?::?:

---

### Post by fjgaude on 2007-09-24
Well, I don't know anything about this portable, but under Ubuntu you can access it using Samba. You need it set such up from the Ubuntu menu, System/Administration/Shared Folders. I think you can take it from there, but if not, ask more questions.

I suppose you format the portable for Windows, i.e., NTFS, and then Ubuntu can access the files therein using Samba and Shared Folders, and Windows sees the drive as a normal one. Of course when in Ubuntu you will have to mount the drive.

Is this portable USB or on the wired net using a NIC?

---

### Post by giboman on 2007-09-24
Thank you for your help.

It is a USB portable

---

### Post by fjgaude on 2007-09-24
Under Linux it will show up as a mountable drive with like /dev/usb tag. I wish I could give you more help, but what you are doing is doable and will work once you get the info to set it up correctly.

---

