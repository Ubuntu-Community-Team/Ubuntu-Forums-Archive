---
title: "Wine + Dragon Naturally Speaking 9 = Disk eject problem"
date: 2007-04-30
forum: General Help
---

### Post by ebeyer on 2007-04-30
After reading this post in forbiddenweb archive, I thought I had an even shot at getting DNS9 to work with Wine on Feisty:

[http://www.forbiddenweb.org/topic/156172/index.html](http://www.forbiddenweb.org/topic/156172/index.html)

However, I seem to be unable to get the installer under Wine to acknowledge that I inserted the second disk.  

So in a shell, I navigate to my cd drive (/media/cdrom0) and enter 'wine setup.exe &'.

The installshield wizard launches, I enter my registration code and install options.  The install proceeds normally and the system asks for disk 2.  The cd-rom eject button does not work.  So I open a new terminal window and enter 'wine eject'.  This physically ejects the first disk.  I insert the second disk, closing the door.  The installer keeps asking for disk 2 ("Uh.. I already gave you disk 2.").

I tried unmounting the drive by doing 'umount -l /media/cdrom0' after ejecting, which makes the cd symbol disappear from the desktop.  But when I click on the cdrom icon in Nautilus, it shows the CD installed as DNS9_CD1 even though it's DNS9_CD2 in the drive.  

Clearly there are issues with wine that are causing most (all?) of my problem here.  What I'm asking, I guess, is whether there's a clever way around this problem so it will acknowledge disk 2 and complete the install.

Advance thanks, 


EB

---

### Post by neuralnet on 2008-04-14
you will love this (if you haven't solved this already)

```
wine eject
```

thank you Odin :)

---

### Post by neuralnet on 2008-04-14
you may also find [this post](http://ubuntuforums.org/showthread.php?t=168711) helpful in your quest too :)

Good luck.

---

