---
title: "Changing default mount options for CD drive"
date: 2007-06-07
forum: General Help
---

### Post by SquirrelHavoc on 2007-06-07
Hello, newbie with a little problem with Feisty Fawn today. I went to update software through the package manager, and it asked for the CD. So I put it in like I have before. But then nautilus  opened a window with the contents, package manager kept complaining that it couldn't find the disc, and the eject button wasn't working. I then right clicked the icon for the drive and told it to eject that way, and it did just fine. But from then on, it still wouldn't read the disc in the package manager. I later found out that the disc wasn't mounted on /media/cdrom like the package manager expected, but /media/(disc label). So I though I would change the mount point in the properties window when you right click the drive icon on the desktop. I pointed it to /media/cdrom, and now I can't get it to auto mount at all, so I can't get to the properties window to undo what I did.


So my questions are: How can I change the new mount point for a cd drive, and why does it mount on a directory with the cd label now? I can't install the software without it being on /media/cdrom (as far as I know)


Anyway, thanks in advance. Kinda stuck here ;)

---

### Post by BatsotO on 2007-06-08
First to start is to look at your /etc/fstab . you can change mount point from there, just make sure the mount folder exist.

---

### Post by SquirrelHavoc on 2007-06-08
Thanks, it took me a bit to figure out what to do, but I got it to work. Seems like it will be OK from now on. Thanks for the help

---

