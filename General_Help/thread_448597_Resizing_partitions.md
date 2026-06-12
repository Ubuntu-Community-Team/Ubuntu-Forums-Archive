---
title: "Resizing partitions?"
date: 2007-05-19
forum: General Help
---

### Post by miggols99 on 2007-05-19
I am trying to make my home partition larger and shrink my root partition. I tried doing this in qtparted, gparted on the live cd, but it won't let me resize the partition to the left. Can I do this with the terminal? Does anyone know how to do any of this?

---

### Post by miggols99 on 2007-05-19
Will I have to reinstall (again :()?

---

### Post by cborga1985 on 2007-05-19
> **miggols99 said:**
> Will I have to reinstall (again :()?

What filesystem did you use? Without providing more information I am unable to help you.

---

### Post by miggols99 on 2007-05-19
The home partition and root partition are both ext3.

---

### Post by Irony on 2007-05-19
You don't have to reinstall, just copy your installation to an external drive, resize your partitions then copy the installation back;

[http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

---

### Post by pseudolobster on 2007-05-19
Is there any way of doing this on-the-fly, leaving the filesystem intact? (I don't have anywhere to copy my current system to save for my xbox (but I'm almost absolutely positive that wouldn't work...)

I'm trying to do something similar, but by shrinking an ntfs partition and enlarging an efs3...

I've defragged the ntfs so I can shrink it, but gparted won't let me prepend space to an efs3 part... ie, "move it to the left"

like the original poster, I'd like to know if there's a way to do this manually with fdisk or whatnot.

Cheers,

-Pseudolobster

---

### Post by Irony on 2007-05-19
If you can create and format a partition on your xbox as ext3 then you can copy your installation to it.

---

### Post by confused57 on 2007-05-19
You might be able to resize, using the gparted live cd:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)
it's a later version of gparted and allows resizing from the beginning of the partition

One thing to note is since you're using Feisty, the UUID's will change for the partitions that you resize.  You would need to boot the Ubuntu live cd, run "blkid" from a terminal, then mount the partitions, then copy & paste the new UUID to your fstab & your menu.lst kernel root line.

---

