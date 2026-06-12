---
title: "Desktop Backup"
date: 2019-06-17
forum: General Help
---

### Post by Shibblet on 2019-06-17
We use a program called "Macrium Reflect" for the Windows 10 PC's at the office.  It works great, but doesn't have a Linux client.  You make a bootable thumb-drive, and after booting into the restore software on the thumb-drive, you choose your backup image, and restore it.  Plus, it only takes about 5 minutes to restore a 25gig image.  And the image restores the PC to the exact way it was when you made the image.

Is there a way to make an image of my Kubuntu PC, so I can just reload that image, and be back to where I was setup in a few minutes, instead of having to go through the whole install process again?

---

### Post by tea for one on 2019-06-17
Have a look at Clonezilla [https://clonezilla.org/](https://clonezilla.org/)

The first time you use it, the interface can be a bit daunting but don't let that be a stumbling block.

I also suggest you read/view a few of the many tutorials on the internet.

Good luck

---

### Post by Artim on 2019-06-17
I believe this will work for the later Ubuntu versions as well.  It's called **systemback** and it allows you to set restore points and to make a bootable copy of your installed system *and* copy it to a thumbdrive!  It's no longer officially supported, but it works flawlessly on Ubuntu-based Linux Lite for me.  Easy interface, no challenging learning curve.  Installation instructions [here]("https://www.linuxbabe.com/ubuntu/install-systemback-ubuntu-18-04-bionic-18-10").

A still-supported app called **TimeShift** is similar.  Clicky [here]("http://tipsonubuntu.com/2018/03/17/create-system-restore-points-ubuntu-18-04/") for into.

---

### Post by TheFu on 2019-06-17
Any tool that makes an image will work regardless of the OS.  If Macrium Reflect makes an image, it will work.
Other options off the top of my head are:
* dd, ddrescue
* partimage, clonezilla, 
* fsarchiver - it works at the partition level, not the disk level.

Generally, using images for backups just takes too long to use.  Using file-based backup tools will allow a number of things that images don't.
* backups can take just a few minutes.
* backups can be performed without taking the system down and using alternate boot media.
* versioned backups can be stored in extremely efficient ways.
* backups can be 100% automatic, no users involved at all.

The most powerful backup tools for Unix don't have a GUI.  This is because a GUI cannot be run automatically at 3am.  In short, point-n-click is too inefficient.

[https://en.wikipedia.org/wiki/Comparison_of_disk_cloning_software](https://en.wikipedia.org/wiki/Comparison_of_disk_cloning_software) has some other ideas.  If you google "clonezilla vs", that will show options and comparisons.

If I'm moving everything from 1 disk to an other and I don't have any advanced storage being used like zfs or lvm, and I want a bit-for-bit copy, I use **ddrescue**.  It is bonehead simple.

---

