---
title: "[SOLVED] Can't get past kdm login screen"
date: 2007-12-22
forum: General Help
---

### Post by janarene on 2007-12-22
I've been running my current install for quite awhile without problems and tonight when I boot the machine I can't get past the username/pw login screen.  Looking at /var/log/kdm.log I see something I don't like:

(EE) Failed to load module "type1" (module does not exist, 0)

I'm clueless on this one.  Searching Google didn't find much.  Anyone have an idea?

---

### Post by der_joachim on 2007-12-23
Type1 is a class of fonts. I think it is highly unlikely that your xorg will crash when it cannot find a certain type of fonts.

You'd better check /var/log/Xorg.0.log for errors.

To get rid of the type1 error, you can do two things:
1) Open up your /etc/X11/xorg.conf in your favourite text editor. Make sure you have root access though. In the Files section, find the following line and comment it by putting a # in front of it.
```

   FontPath        "/usr/share/X11/fonts/Type1"

```
Save and exit and restart Xorg. 
2) Install any type1 fonts, although I do not know which package that is.

However, I do not think that the font problem crashes your xorg, so I would not fiddle with font paths.

---

### Post by janarene on 2007-12-23
Thanks for your thoughts  der_joachim.  kdm.log does specifically state that it can't load a module called type1.  My files section has no reference to type1 fonts.  Xorg.0.log doesn't show I have an error (The expected LoadModule: "type1" line is even missing) . And placing a comment (#) before the Load "type1" in the Module section doesn't change the scenario.

xorg.conf files section:

```
Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

```

xorg.conf modules section:

```
Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

```

Since there doesn't seem to be any reference to "type1" in the xorg.0.log, I'm refraining from posting it so this thread doesn't get too noisy - but if anyone wants to see it..... ;)

---

### Post by janarene on 2007-12-23
SOLVED:

I reinstalled onto another partition and when I booted into the new partition fsck decided it needed to check the partition that the problem install was on because of it's 21 day timeout or whatever value it is.  Regardless - fsck ran and reported nothing... but it took longer than I'm used to, so just for giggles I rebooted the computer again and chose the problem partition from grub and MAGIC!  It booted just fine and I'm writing to everyone while using the OS I couldn't boot into lastnight.

So... if all else fails... fsck it!    :popcorn:

---

### Post by janarene on 2007-12-24
The fsck solution didn't hold.  I awoke this morning to the same kdm login screen looping back to the login screen after entering my name/pw.  I can only assume at this point that I have a hardware problem and my next step would be to scrub the surface of my hard drive and/or replace it.

	](*,)

---

### Post by der_joachim on 2007-12-24
Hmmm... X does start. I'm sorry I misread. The type1 error is no problem. I get the same error and I am quite happily using xorg. I assume that you are using KDE, since you use kdm. Are you sure that it is correctly installed or that your kde settings are not corrupt? You can rename the .kde folder in your /home directory and see whether KDE starts. 

Another thought: you did not incidentally install KDE4, did you? I had a similar problem when I did...

As for hardware problems: you could check your hard disk for bad blocks with the badblocks program. You'll probably need a boot disk for that (the Kubuntu desktop CD will probably do), but I'd consult the badblocks manpage. This could damage your system, so be careful. 

Good luck.

---

### Post by janarene on 2007-12-27
I feel like burying my head in the sand over this one - but in all fairness to the rest of the community I've got to report what the problem actually was.

A full root partition.

Apparently running fsck the first time freed up just enough for a boot but that just wasn't enough to sustain the machine.  After freeing up a few gig on the / partition I've been running smoothly for the last couple of days.

That'll teach me!

---

