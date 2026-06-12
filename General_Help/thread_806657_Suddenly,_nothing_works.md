---
title: "Suddenly, nothing works?"
date: 2008-05-25
forum: General Help
---

### Post by lisaril on 2008-05-25
First of all, I must say that this is my fourth day using Ubuntu, so bear with my nubiness

This morning the power to my computer suddenly stopped for some reason and consequently my computer immediately shut down. I rebooted, and was able to get back in without problems. Gnome worked and my appearance settings seems to be alright. However, once I started up nautilus (clicked on a shortcut) nothing happened. The same would go for firefox, pidgin, everything, even when i got there using the Applications menu. Then, nothing worked. I couldn't click on applications, or anything, and the only things that worked were Trash, Deskbar Applet, System Monitor, Volume control and Session manager. Even terminal doesn't work (I got it to launch using a shortcut). Terminal launches (unlike other apps), but all it displays is a black screen (i set it to be semi-transparent) with no text, and white borders (left, right and bottom). After rebooting i tried out fdisk and fcsk, and apparently there were errors in the filesystem. the fixes were done and I booted into ubuntu once again. The same. 

Is there any way to change this? 

I do not think the newly installed applications would have made any differences, as the day before the only things i installed were Enemy Territory, esound and libstdc++5

Any help is appreciated

PS: I know i can just install a new system, but that will be a great hassle and i have alot of important files on the ubuntu partition (currently dualbooting ubuntu and xp).

Computer Details:
Quadcore 2.5 ghz q9300
2x 9600 GT SLI
500GB HDD (Seagate)
A-Data DDR2 800 RAM (2x2gigs)
XFX nforce 780i 3 way SLI Mobo
Coolermaster 600 watt PSU

---

### Post by shifty_powers on 2008-05-25
did you build that computer yourself?

600w is possibly a little on the low side for that setup.....

---

### Post by lisaril on 2008-05-25
I actually think it's more than 600w
Should be okay though, as I can play Crysis on high without lag or overheating (is 53C GPU temp okay during gaming?)

but yeah i built it

EDIT: without lag meaning at about 40FPS

---

### Post by shifty_powers on 2008-05-25
heh, don't get me wrong, sure it was a good build, and 600w probably is enough, just suspicious that the power suddenly stopped like that. a psu under strain can act in a strange ways....

have you tried installing the [http://www.fs-driver.org/](http://www.fs-driver.org/) ?

it will give you access to your ubuntu partition from windows. then you can get out your needed data. Maybe think about reinstalling ubuntu after that...

---

### Post by danwood76 on 2008-05-25
That PSU should be fine for that job.

Log in in recovery mode and do an fsck
```

fsck -yp

```
The y and p options fix errors automatically and say yes to all qs.
I would have thought that some config file may be screwed caused by the power loss.

If that doesnt fix it try to login in a failsafe GNOME session (selectable from the login screen botttom left) if the shortcuts work in the failsafe session and not in your default session then you may have a config error.

---

### Post by lisaril on 2008-05-25
That's pretty cool but it says ext2 and I'm using ext2 for my ubuntu partition right now...

and about my new build, you don't even want to know my old build (which was actually bought so yeah...). Basically, it sucked.

---

### Post by lisaril on 2008-05-25
sorry just noticed the ext3 part in fs-driver's FAQ and didn't notice Danwood posting 

I didn't try fsck -yp but i did try fsck -y
is that the same?

and about the shortcuts. Only some of them work, but even terminal doesn't. Why?

And also, I tried rebooting again just now, and I *could* get calculator up but once i closed it, everything was bad again. Basically, everything is working until I click on a shortcut on the panel (like firefox on ubuntu's default load), and some applications would work (like calculator). However, after that nothing does.

---

### Post by shifty_powers on 2008-05-25
if you look at the page, it has  alink that lets you knwo how to get at least read access for ext3...

---

### Post by danwood76 on 2008-05-25
Ext3 is basically ext2 with journaling.

Run fsck first, and if you need to recover data/reinstall its better (easier) if you boot up with the live CD and save it from your linux partition to your windows partition in there.

---

### Post by lisaril on 2008-05-25
I already ran fsck (fsck -y) and it worked (as in it finished wihtout errors)
and i already recovered my files with fs driver but is there any way to retain my old files (like appearance, games, etc) by just copying it onto an external drive and replacing it in the newly installed ubuntu?
if yes, how?

---

### Post by danwood76 on 2008-05-25
all of those settings are contained in hidden files in your home directory (folder starting with a .) so if you copy all of the files in your home directory (including hidden) it should return back to how you had it.

---

### Post by lisaril on 2008-05-25
so basically I:
-copy all files from my current linux drive 
-put it on an external drive/usb/etc
-install new ubuntu (yay!)
-get the external drive/usb/etc 
-paste all files?

---

### Post by danwood76 on 2008-05-25
Yes, but you only need the files in your home directory.
and yes just paste them over the initial install home files.

---

### Post by danwood76 on 2008-05-25
Also it might be useful to backup your /etc directory if you have many any changes to any files in there (fstab for example)

---

