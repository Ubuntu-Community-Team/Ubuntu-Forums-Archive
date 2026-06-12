---
title: "file system"
date: 2007-08-22
forum: General Help
---

### Post by colddayinapril on 2007-08-22
Ok, so i have this Western Digital book drive that i want to format. Simple enough, eh? Well, nothing with me is ever simple :)

I'll be going to school for film studies, and will no doubt wind up having several very large raw video files and edited films on the drive at any one time. The problem is that I run linux on my home machine, the school teaches editing and prossesing using Adobe and Avid on Windows machines, and, being that I'll be in film school, i'm bound to run into a situation where i'll have to use a Mac.

so, what I need it a file system that i can format the drive in that will:
A) be able to store very large (in the 6 to 10 gig range) contigious files.
and,
B) Be readable by Windows, Linux, and OSX.

also, a poney and a million dollars would be nice :biggrin:

---

### Post by kidders on 2007-08-23
Hi there,

You have a choice of several nice filesystems ... until you say the word "Windows", that is! Unfortunately, NTFS is probably your only practical option.

---

### Post by LaRoza on 2007-08-23
EXT3, with the EXT3 driver for Windows, or NTFS with the NTFS driver for Linux.

---

### Post by kidders on 2007-08-23
> **LaRoza said:**
> EXT3, with the EXT3 driver for Windows, or NTFS with the NTFS driver for Linux.Getting Ext3 to work on a Windows box the poster has no administrative control over, or getting it to work *at all* on a Mac could be tricky ... which is why I suggested NTFS.

If the poster *can* install drivers on the Windows boxes he'll be using, HFS becomes the best option, I'd say.

---

### Post by ddrichardson on 2007-08-24
> **kidders said:**
> Getting Ext3 to work on a Windows box the poster has no administrative control over, or getting it to work *at all* on a Mac could be tricky ... which is why I suggested NTFS.

If the poster *can* install drivers on the Windows boxes he'll be using, HFS becomes the best option, I'd say.

Seconded ;-)

---

### Post by colddayinapril on 2007-08-27
I guess installing an NTFS driver on my machine beats having to install a driver or program on every other box i want to work with.

...Can a Mac read NTFS.
forgive my ignorance here, but my knowledge of Macs is limited to the pretty Aqua theme I got off gnome-look :)

---

