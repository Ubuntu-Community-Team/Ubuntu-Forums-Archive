---
title: "HP Photosmart C4280 - v4l:/dev/video0 - says USB cable not connected"
date: 2007-09-10
forum: General Help
---

### Post by FunkyCat on 2007-09-10
As of 09/14/07 this problem is declared HALF SOLVED (read my adventures below).



Hiya all... your friendly linux-wimp with yet another problem.  Hopefully -this- one can be solved.

Okay, I bought a nice shiny new printer al-in-one to use with my crafty business.

Its a HP Photosmart C4280.  It prints and copies like it was born to do it.

I go through GIMP or just to xsane to try and scan and it says this:   v4l:/dev/video0

Also, the printer itself says (on the LCD screen) that the USB cable is not connected.  Although it is.  And it prints stuff just fine.

I've got.. um... Breezy Badge, I think O.o Whatever the latest is! I try to avoid doing anything but proper lazy *** computer stuff on here, so I don't even remember what I have :-p  Yeah I suck and need help.

If the USB bit has something to do with the video error bit and it fixes it, fine.  But I don't need to try to go out of my way to fix the USB bit if its not going to cause any troubles.  I.E.  my priority is the SCANNER.  

And I did search around on this fist a bit, but found no leads (except my printer/scanner IS supported by HPLIP, of which I have the latest version).

Thanks ahead of time!

*ETA*  Its Fiesty that I have.  Sorry, forgot to fix that :)

---

### Post by Sef on 2007-09-10
> I've got.. um... Breezy Badge, I think O.o

If you install Feisty, then likely will work.   

Also Breezy is no longer supported, which is another reason to upgrade.

---

### Post by FunkyCat on 2007-09-11
Hiya Sef.  I do have Fiesty.  Sorry, I forgot to fix my mistake after I triple checked.

---

### Post by FunkyCat on 2007-09-14
Okay people, I'm panicking here.  I -really- need this scanner to work (for business purposes).  I've still been looking into it.  I can't find anything.  Help?

---

### Post by FunkyCat on 2007-09-14
Okay so I tried dpkg -l hplip
and it says: 

xeen@misskudos:~$ dpkg -l hplip
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
iF  hplip          1.7.3-0ubuntu1 HP Linux Printing and Imaging System (HPLIP)



I don't know how I got the idea that I had the latest version, but apparently I don't.

So I go to the HPLIP to download and install the latest version.  Did the reboot and pointed it to the printer.  Its STILL saying the USB cable isn't connected and STILL isn't scanning.

So I try dpkg -l hplip again, it's still saying the same version.

WTF?

I am SO lost.

---

### Post by FunkyCat on 2007-09-14
OKAY nevermind.  I went through GIMP, just for, youknowwhat&giggles.  There was something new under aquire... xscanimage.  I must have installed it trying out different scanning deals. O.o

Well, it WORKS now! O.o  I didn't try xsane, but its the middle of the night here and I've made enough racket.  I'll update here if I get anything new ironed out!

Sucks making myself look like an idjit, but maybe somebody else can learn from my Ubun-funery.

---

