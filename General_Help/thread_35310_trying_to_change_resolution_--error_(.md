---
title: "trying to change resolution --error :("
date: 2005-05-18
forum: General Help
---

### Post by hiptrop on 2005-05-18
hi ! 

i am trying to change my resolution and i get an error :(

xserver isnot compatible with the XRandR-expansion. changing of resolution is not able when running 

ps: i guess a bad translation from german into english :P 

well :) can somebody help me out with tha tproblem ?

actually i want to change the color depth from 24 bit to 32 bit cause a program i want to sue does not run with 24 bit color depth ! 

any help on this one ??

thanks :)

---

### Post by StacyWebb on 2005-05-18
edit it directly in the xorg.conf file when you open it you will see how it is setup.
located in 
/etc/X11/xorg.conf

---

### Post by hiptrop on 2005-05-18
mhmhm i tried :P

all i changed was the default color depth to 16 ( and 32 ) 

and xserver won't start anymore :) 

is there a reason for that ? it says that the fglx driver won't support 16 and 32 bit !!

who can that be if 24 works ? ( at least the 16 bit should work right ?? ) 

well maybe someone can clear things up again :) thanks alot !!

---

### Post by az on 2005-05-19
[QUOTE=hiptrop]mhmhm i tried :P

all i changed was the default color depth to 16 ( and 32 ) 

and xserver won't start anymore :) 

is there a reason for that ? it says that the fglx driver won't support 16 and 32 bit !!

who can that be if 24 works ? ( at least the 16 bit should work right ?? ) 

well maybe someone can clear things up again :) thanks alot !![/QUOTE]

Instead of editing the file, either use Synaptic to configure the package (select the package and then click on configure in the drop down menu

or
go to a console and type 

sudo dpkg-reconfigure xserver-xorg

Then, restart your X server.  CTRL-ALT-Backspace.

---

### Post by poofyhairguy on 2005-05-19
[QUOTE=hiptrop]
is there a reason for that ? it says that the fglx driver won't support 16 and 32 bit !!
[/QUOTE]

The reason Linux (and therefore fglx) won't support 32 bit is because 32 bit is wasteful BS that is only good marketing. Look at this link:

[http://www.scantips.com/basics11.html](http://www.scantips.com/basics11.html)

I quote from it:

> The 24 bit color mode and so-called 32 bit video mode show the same 24 bit colors, the same 3 bytes RGB per pixel. 32 bit mode simply discards one of the four bytes (wasting 25% of video memory), because having 3 bytes per pixel severely limits video acceleration functions. 

Windows uses 32 bit mode because it sounds better for the most part. 

16 bit should work, but it might not because ATI drivers are pretty poor qualitywise. There is nothing Ubuntu can do about that- its ATI's problem!

---

