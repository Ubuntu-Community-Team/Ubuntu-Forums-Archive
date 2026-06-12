---
title: "Well...breaking X is never fun..."
date: 2007-10-06
forum: General Help
---

### Post by blithen on 2007-10-06
Well I hate breaking X. I was just changing screen resolution to make it 
now crazy big...then I logged out then it, then everything is like 4 
blurring screens, I guess I would need to take a screen of it to 
actually show you it, but it's really messed up.

Anyone else done something like this?
Also how did you fix it?

OPPS. Thought I was in cafe, please move this when possible mods!

---

### Post by matthew on 2007-10-06
> **blithen said:**
> OPPS. Thought I was in cafe, please move this when possible mods!Moved to General Help, which is a better location for this thread than the Cafe would be.

---

### Post by GSF1200S on 2007-10-06
> **blithen said:**
> Well I hate breaking X. I was just changing screen resolution to make it 
now crazy big...then I logged out then it, then everything is like 4 
blurring screens, I guess I would need to take a screen of it to 
actually show you it, but it's really messed up.

Anyone else done something like this?
Also how did you fix it?

OPPS. Thought I was in cafe, please move this when possible mods!

First, if you remember exactly what you changed, you can change it back from the command line using nano:

```
sudo nano /etc/X11/xorg.conf
``` 

then make your changes, and then start up the gui:

```
sudo /etc/init.d/gdm restart
```

If that doesnt work, did you happen to make a backup of Xorg before modifying the screen resolution? You could always start the backup kernel option(at the grub menu) and restore the backup from the command line...

To do this, first navigate to the location of your xorg.conf and its backups- at the command line type:

```
cd /etc/X11
```

and then once the directory is changed, type:

```
ls
```

Look through what it lists. Find the backup and note what its name is. Then restore it as the primary xorg:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

where xorg.conf.backup is the name of the backup xorg listed above.

If all else fails, you can try and create a new one. Youll have to reinstall your video driver this way, or at least properly note the new xorg.conf you create with the proper info. If you need to do this, use:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then, select the VESA driver and your screen resolution and type:

```
startx
```

This should work- I hope it helps out and good luck ;)

---

### Post by joao82 on 2007-10-06
you can also run the live CD, see which are the right options on the xorg.conf under live mode or even copy the whole file to some place, and then modify the old xorg.conf on your hard drive.
or you can use the live CD to search a backup of xorg.conf saved automatically on hard drive. then just delete the original xorg.conf and rename the backup file to xorg.conf. that's what saved me last time it happened, thanks to the good people on this forum.

---

### Post by GSF1200S on 2007-10-06
> **joao82 said:**
> you can also run the live CD, see which are the right options on the xorg.conf under live mode or even copy the whole file to some place, and then modify the old xorg.conf on your hard drive.
or you can use the live CD to search a backup of xorg.conf saved automatically on hard drive. then just delete the original xorg.conf and rename the backup file to xorg.conf. that's what saved me last time it happened, thanks to the good people on this forum.

Very good idea here. I actually HAD to do this setting up my moms Xorg because for some reason the text was off the screen whenever it was at a command line state. I simply couldnt see what I was editing. So, I threw in the live cd and modded the Xorg from it instead. It may be a little easier. I might suggest looking at how all that CLI i listed works.. ive tried very hard to get as dirty with the CLI as I can to avoid being screwed when im forced to face it. 

This is a good one too.. one of these options should have you up and running again in no time. If you still need to change the resolution, post another thread and we can get rolling there too (ive seen you around, so you may know all of this already).

---

