---
title: "After Ubuntu upgrade from 14.04 to 16.04, graphics won't work"
date: 2016-08-10
forum: General Help
---

### Post by popfulfrost on 2016-08-10
When I first upgraded, I was given a "system is running in low  graphics mode" message, then everything ran just fine, graphics  apparently normal. When I restarted it some time after, however, after  selecting Ubuntu on grub, it gives me a screen that, to my memory  (didn't have the time to screencap), seems to imply that something is  wrong with the disk, after which it goes blank for a bit, then very  briefly shows a bunch of rainbow static combined with a mosaic of my  desktop. When I looked the Ubuntu partition over in Windows using  DiskInternals Linux Reader, all my files were fine (and yes, I did  immediately make a backup).

  I reinstalled Ubuntu, taking care to set everything as it was (same  mount point, same username, etc.), and this did not fix the problem.  When I try Ctrl + Alt + F1 in Ubuntu, the terminal does show up. Here's a screenshot I took of the terminal. [http://oi64.tinypic.com/kbrldw.jpg](http://oi64.tinypic.com/kbrldw.jpg) The "lspci" at the bottom was something I tried typing.


While rebooting, I noticed something odd about the Boot  Options Menu, namely that there are two options for Ubuntu. I tried them  both, and they did the same thing.

I also took this screenshot of something that makes me suspect this is more than a graphics error.
[http://tinypic.com/r/del30g/9](http://tinypic.com/r/del30g/9)  Failed to start Load Kernel Modules? Was this because I only allocated  about 20 GB to the Ubuntu partition when I first installed? I remember  having to restart the upgrade process after cleaning a few things out,  but considering that it worked fine until I restarted it after the  upgrade, I honestly have no idea what went wrong here.
 I tried running it in failsafe graphics mode, yet when I tried the  "reconfigure graphics" option, regardless whether I picked generic or  backed-up, I ended up with the window disappearing for a split second,  and nothing happening. Running "default" in failsafe just gives me a  black screen with the X cursor. I can literally do nothing apart from  move the cursor around, and press Ctrl + Alt + F1 to get what I took  pictures of above, after which nothing happens no matter what I type, so  I have to hold the power button to restart.

Does anyone know how to fix this?

---

### Post by popfulfrost on 2016-08-11
Bump.

---

