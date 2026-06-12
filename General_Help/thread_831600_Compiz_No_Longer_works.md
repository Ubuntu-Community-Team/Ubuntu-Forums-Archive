---
title: "Compiz No Longer works"
date: 2008-06-17
forum: General Help
---

### Post by jimbo99 on 2008-06-17
I don't know if there's a school for those that do these patches, etc., but after some patches today compiz no longer works.  I did my normal updates and then did a reboot later in the day to swap out a video card.

The Nvidia logo shows when I start up the GDM.  No compiz tho.

I checked by typing compiz --replace in a terminal window.  Get some message about xgl not present, etc.

This worked prior to the last reboot and had consistently worked for since I Installed 8.04.  It worked for the past year or so.  It isn't my hardware.  Something in one of the recent updates screwed this up.

I hope these brainiacs at Canonical can understand that they should never EVER make changes that disable features like this, even accidentally.

---

### Post by James_mtl on 2008-06-17
What video card do you have and how did you install it ? 
I had the same problem with Nvidia geforce 7900 using the driver from Nvidia web site 173.14.05

I just needed to execute the install script again to fix the problem.  If your setup is similar give it a try.  The script reported an error with glx.so ( or something like that just running by memory ).  On a side note 173.14.09 is the latest release so you might want to use the opportunity to upgrade at the same time !

Give me more info I'll try to help.

---

### Post by rainwalker on 2008-06-17
It's hard to prevent accidents, otherwise they wouldn't be called accidents :P

Anyway, try this command:
```
SKIP_CHECKS=yes compiz
```
If that doesn't work, you're missing something big (I'm actually not sure what exactly, because that command has always worked for me).

---

### Post by onero on 2008-06-17
> **James_mtl said:**
> What video card do you have and how did you install it ? 
I had the same problem with Nvidia geforce 7900 using the driver from Nvidia web site 173.14.05

I just needed to execute the install script again to fix the problem.  If your setup is similar give it a try.  The script reported an error with glx.so ( or something like that just running by memory ).  On a side note 173.14.09 is the latest release so you might want to use the opportunity to upgrade at the same time !

Give me more info I'll try to help.

I had the same problem and this solution worked for me, thanks. A recent update probably borked something, but installing the latest Nvidia driver fixed it.

---

### Post by sveterv on 2008-06-17
I had to reinstall NVIDIA drivers, but I'm using binary package from their official website not this from Ubuntu repository. 

One file was changed by xorg update yesterday, this file was libglx.so, and I could work only in 2d mode, but when I've opened Google Earth I had crash and got back to the GDM login screen. I'm not using compiz, so I was able to login and normally work until applications needed 3d support.

---

### Post by GenesisV2.0 on 2008-06-17
is it possible your update black listed your card or updated a file you took a black listed item off?

---

