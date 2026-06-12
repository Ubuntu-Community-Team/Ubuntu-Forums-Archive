---
title: "[SOLVED] Went To Command Line?"
date: 2008-01-26
forum: General Help
---

### Post by UnsafeData on 2008-01-26
Okay so I went to use Ubuntu and all I got was a command line with a bunch of "800 x 600 failed", "1024 x 768 failed" etc. I don't know the command line and ironically I was going into Ubuntu to try it out, since I found some sort of tutorial site that teaches it.. 

Ironic.

Oh and I'm a Linux n00b. I've used Ubuntu in the past but stopped for some reason, but I'm still pretty much a n00b.



I went to the display settings and it said "Generic Monitor" and I only had 800 x 600 to use, so I changed it to Plug n Play for some reason and then logged out, logged back in, changed resolution and it worked. Then I went to use Windows for a few days since there was stuff I was doing on there, and then when I tried to use Ubuntu yesterday I got nothing but a command line..

EDIT: I"M ON Ubuntu 7.10. I used the 7.10 installer I found. (Had to Google it since it was on some directory on the site..)

---

### Post by erykroom on 2008-01-26
So if I understand you have ubuntu installed but it shows only the command line. Right? If that is the case you should try to type startx to the command line and if that does'nt work then you should reconfigure your xorg settings.   (sudo dpkg-reconfigure xserver-xorg)

And maybe this post can help you [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by UnsafeData on 2008-01-27
the startx didn't work but the sudo dpkg-reconfigure xserver-xorg thing worked fine.

i'm on ubuntu now and everything works, thanks.

---

