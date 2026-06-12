---
title: "cloning a hard drive"
date: 2017-08-31
forum: General Help
---

### Post by Autodave on 2017-08-31
I currently run a dual boot system: Win10 on spinning HD and Xubuntu on a 120G SSD. I would like to clone the SSD for the inevitable day when it dies. I have another 120G SSD to use. What is the best way or program to do that with?

---

### Post by TheFu on 2017-09-01
It depends.  For cloning, there are a number of methods.
* dd
* ddrescue
* fsarchiver
* clonezilla
* partimage
* and 50 others.

However, imaging is a terrible method for backups. It is wasteful.  It is impossible to use without booting from alternate media, so downtime is required.  And it lacks versioning, which is needed to protect against data corruption.  Versioned backups really are the best solution.

But if I need to image 1 disk to another, I use **ddrescue**. It takes longer, but if I need a clone, that is the way.  Clone at the device level (/dev/sda) to clone the partition tables too.  You can clone at the partition level (/dev/sda1), if you prefer.

---

### Post by Autodave on 2017-09-01
All of my files that I need to keep are on a separate HD and are also backed up off line in 2 different places. My goal / desire is to have a working copy of my current system for if/when the SSD goes south. In other words, I want to be able to disconnect the SSD, plug in its replacement, and boot the system to a working system.

---

### Post by leunam12 on 2017-09-01
I use Clonezilla for that

---

