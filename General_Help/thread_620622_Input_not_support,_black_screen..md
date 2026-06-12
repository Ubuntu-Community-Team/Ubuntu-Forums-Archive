---
title: "Input not support, black screen."
date: 2007-11-22
forum: General Help
---

### Post by CorlanMcD on 2007-11-22
Hey guys, 

Yesterday, I installed Ubuntu Gutsy Gibbon on a freshly made partition (dual booting with Windows XP), but from the beginning (Live CD), I've had problems.

With the Live CD, if I wanted to enter the desktop, I had to remove "quiet splash" from the command line. After installation, with the absence of the command line, I had to enter Ubuntu via recovery (usuing "dpkg-reconfigure xserver-xorg" and when finished, used the command "exit.").

Now, before signing up [for the boards] I've read many threads here and elsewhere, but nothing suggested seems to help (in fact, one just borked my Ubuntu installation and I can't access "recovery".)

Before I forget, the problem seems to be with my monitor, the Acer AL2216Wbd (trying to run a native res 1680 x 1050) which is connected to my PC via VGA, and I've pretty much tried everything from editing the menu.lst to the usplash.conf.

I'd post my xorg.conf, but I can't logon to Ubuntu! If I try recovery, it tries to go through but knocks me to a shell and no commands work...

Anyway to fix this? I'm going to reformat the partition later tonight or tomarrow.


Thanks,
Corlan

---

### Post by jken146 on 2007-11-23
You could edit the xorg.conf via the live cd, set it to your correct resolution etc.

---

### Post by gigaferz on 2007-12-24
hello , i hope it is no too late, 
I have the same monitor with a weird behavior
In feisty it wouldnt allow me to display 600*400 (mainly games/emulators)
Now in Gutsy the only way that i made it work is to set it up manually in the  *new* sections scrrens & graphics to 1600 * 1200. And also i  can not run somethings in 800 * 600.

I have the old intel 845 graphics card most of the people have, so it is not something  restricted.
i didnt have a bad experience with the live cd .

Is this a monitor problem or a driver thing?

---

### Post by gigaferz on 2007-12-25
[http://myy.helia.fi/~karte/acer_al2216w_-_22_inch_monitor_with_linux.html](http://myy.helia.fi/~karte/acer_al2216w_-_22_inch_monitor_with_linux.html)

I found this website and  what I did on my xorg.conf file was:
change driver to intel
replaced the whole "monitor" section
and added a depht 8 subsection under Screen 

Also Monitor identifier and Screen monitor should be the same in this case "myal2216w"

If somebody needs more help i can send you my "original xorg.conf and the new one so its easier to understand.

Now i can see 800x 600 in Urban Terror !!

Acer Al2216w

---

