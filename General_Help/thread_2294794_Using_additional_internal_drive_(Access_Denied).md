---
title: "Using additional internal drive? (Access Denied)"
date: 2015-09-13
forum: General Help
---

### Post by roo-m on 2015-09-13
**SOLVED. Just taught myself about nautilus.**


[s]Hello! First off, I'd like to say that I love linux so far, though I am still **extremely** new to it (2nd day).
-Using Ubuntu 15.04

I have 3 internal Hard Drives that I'd like to use;
Disk 1 is for /, and Swap
Disk 2 is for /home
Disk 3 is for "misc" (games, saved images/videos/projects, etc)

During the installation of Ubuntu, it was very easy to set up /, and Swap, as well as dedicating a secondary drive for /home...
However now that I'm ready to start using my 3rd drive, I can't seem to figure out how to save files to it (steam games, etc). Heck. I can't even find it in the file system (if it's even supposed to be there?)
> **Mark Phelps said:**
> You can certainly use the third drive for  data storage, but executables, including apps and games, are not going  to get stored there.

How would I go about making the drive accessible? I've managed to make  it read-only lol. Does it need to be mounted as an Extended Filesystem?  ext4?
Primary Partition?

I think I've already tried to make it a ext4/primary, and it was read-only.[/s]

---

### Post by Mark Phelps on 2015-09-13
You're not going to be able to do what you want.  In Linux, apps and games are installed where the installation package puts them, generally NOT giving you the chance to select a drive or directory.  You can certainly use the third drive for data storage, but executables, including apps and games, are not going to get stored there.

---

### Post by roo-m on 2015-09-13
> **Mark Phelps said:**
> You can certainly use the third drive for data storage, but executables, including apps and games, are not going to get stored there.

How would I go about making the drive accessible? I've managed to make it read-only lol. Does it need to be mounted as an Extended Filesystem? ext4?
Primary Partition?

I think I've already tried to make it a ext4/primary, and it was read-only.

---

