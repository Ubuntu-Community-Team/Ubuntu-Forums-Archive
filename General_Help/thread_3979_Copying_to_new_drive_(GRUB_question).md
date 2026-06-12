---
title: "Copying to new drive (GRUB question)"
date: 2004-11-10
forum: General Help
---

### Post by negativ on 2004-11-10
in the [other thread](http://www.ubuntuforums.org/showthread.php?t=2923) I explained that I was trying to copy my Ubuntu installation to another HDD.

After searching around, I've done all I know how to do, and this is either gonna work or not.  As best I can tell, I'm at the point where I need to install GRUB on the new hard drive.

So....

> (chroot)> grub
(grub)> root (hdx,y) <- with your new root partition
(grub)> setup (hdx) <- where you want to install the boot loader

Considering that once I'm done, I'm going to move this new drive to the position of the old drive, how do I do this?

The new drive is currently hdg (or, hd3,0 in GRUB-ese) and when I'm done, it will be hda (hd0,0)

Do I do root (hd0,0) and setup (hd0), or do I do root (hd3,0) and setup (hd3,0) ? 
 #-o

---

### Post by negativ on 2004-11-10
well, crap... I can't do either one, since according to instructions I didn't copy /dev or /proc, the "new" system doesn't see hd0 or hdanything.... bleh.   ](*,)  ](*,)  ](*,)

---

