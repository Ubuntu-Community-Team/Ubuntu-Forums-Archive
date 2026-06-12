---
title: "Graphical glitch"
date: 2008-02-13
forum: General Help
---

### Post by Dajosa on 2008-02-13
Hey all

I've recently installed Ubuntu 7.10 on my desktop computer (Pentium D 925 @ 3.0Ghz, 1GB Ram, 80gb HDD, Nvidia 6200). To install it I had to run in safe graphics mode because of this graphical glitch. The reboot after install didn't need safe mode so I thought all was well. I rebooted due to internet problems and now this happens every time instead of a proper bootup.

[IMG]http://img180.imageshack.us/img180/6445/img6535cb5.jpg[/IMG]

The small square is the cursor, which isn't frozen. It doesn't respond to keyboard commands. Any thoughts? :confused:

---

### Post by R13120(1&lt; on 2008-02-13
holly crap!!!
 congratulations you have sucessfully made your computer$#!t it'self try putting your ubuntu disk back in the drive and see if it will boot from that.

---

### Post by Dajosa on 2008-02-13
Yep, runs fine from the disc.

Edit: Live mode that is, but only in Safe graphics mode :|

---

### Post by R13120(1&lt; on 2008-02-13
eesh... lots of fun... 
it could be the graphics card but if you had winblows on it before and it worked fine you just need to download the driver for you card. 
it could also have been a problem with your install but i don't see how unless your cd was watermarked or something.

---

### Post by TheOrangePeanut on 2008-02-13
Did you try installing the restricted drivers?

---

### Post by Juffo-Wup on 2008-02-13
Well... this is odd.

Does pressing the keys <Ctrl><Alt>+<F1> land you in a black login screen?

If so, you could log in (you won't see anything while you write your password, you can delete whatever you typed by pressing <Ctrl>+U) and try ye olde ```
sudo dpkg-reconfigure xserver-xorg
``` command, and answer the questions that the 'wizard' makes...

..if you haven't already tried that, of course.

When asked for the name of the driver, answer 'nv'. It —unlike the 'nvidia' driver— won't give you hardware acceleration (and thus, no compiz), but it's reliable.

I hope this helps.

---

### Post by Dajosa on 2008-02-15
<Ctrl><Alt>+<F1> has no effect on the glitchy screen. :(  Can I install drivers for the installed version by using the Live CD boot?

---

### Post by Juffo-Wup on 2008-02-16
> **Dajosa said:**
> <Ctrl><Alt>+<F1> has no effect on the glitchy screen. :(  Can I install drivers for the installed version by using the Live CD boot?

I think not. You could manually edit your xorg.conf (found at /etc/X11/xorg.conf, which holds the configuration for Ubuntu's the graphics server), but if you don't have the right drivers (the proprietary 'nvidia' ones?), I don't think you could do much more from the Live CD.

There are options on the nVidia's command line installer for the driver —downloadable from their webpage— that may allow you to install it from the live session (after mounting the partition where your Ubuntu installation resides), but it would take quite a bit of googling and browsing of the file system to pull it off (as it allows you to specify where the different files should be placed).

---

