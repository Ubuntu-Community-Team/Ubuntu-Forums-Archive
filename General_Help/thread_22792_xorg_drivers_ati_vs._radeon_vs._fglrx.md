---
title: "xorg drivers: ati vs. radeon vs. fglrx"
date: 2005-03-29
forum: General Help
---

### Post by diwakergupta on 2005-03-29
I know that the xorg fglrx driver enables 3d acceleration, but breaks suspend to ram/disk. So I usually use the "ati" driver. However, it seems there is one "radeon" driver as well, so I was wondering if anyone knew what that was for. 

Also, when using the "ati" or "radeon" drivers, I get the following on glxinfo:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".

I saw another thread talk about it, but couldn't find a concrete solution. 

Relevant packages installed:
xorg-common
xorg-driver-fglrx
xserver-xorg

And my xorg.conf:
Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

TIA

---

### Post by Dracontopes on 2005-03-29
I thought that the fglrx-driver is the only driver that support Direct Rendering (DRI). The ati and radeon modules do not. That might explain your error, try commenting ```
Load "dri"
```

---

### Post by diwakergupta on 2005-03-31
Actually installing the xorg-fglrx driver package had created symlinks to its own GL.so files which was causing the problems. Since fglrx breaks suspend anyways, I've removed it for now and life is good (modulo 3d acceleration of course)

---

### Post by sir-gold on 2005-05-21
here is some info that I picked up during the week I spent trying to get dual monitors to work right ](*,) :

Im not sure what the 'ati' driver is, it might just be a link to the generic vesa driver

The 'fglrx' from apt is an old version of the proprietary ATI 3D driver, it does support DRI, but it does not support Xinerama
The current driver from ATI is also called fglrx, but has a different package name and will refuse to install unless you remove the previous xorg-fglrx driver or force the install

The 'radeon' driver is an open source driver that offers more features than 'ati'
like 2d acceleration of both screens in a dual-screen configuration using an option called MergedFB, it also supports DRI, and atleast in my case, was the only driver that supported window transparency and shadows

I ended up creating 2 layout sections in xorg.conf, one layout using the newest fglrx driver from ATI in single screen mode for 3d acceleration when i want to play games, and one layout using the radeon driver in dual-monitor MergedFB mode for normal day-to-day use

One bug I have not been able to get around is that if you use the fglrx driver, and then switch to the radeon driver without restarting the computer first, the radeon driver will give a mostly corrupt display

---

### Post by Taro on 2005-08-07
The ATI driver is very old for very old cards.  I believe that if you get 'ati' and 'radeon' confused, then one will switch to the other depending on how it detects the card, but I forget which will switch to the other, or if they both do.  When in doubt, use 'radeon' and try 'ati' if it fails.

The Radeon driver is modern, use it for all Radeon cards up to and including the 9200 SE (RV280 and below).  It supports full 2D and 3D capabilities.  For more information on this driver, just "man radeon" !!!

The closed-source driver from ATI (fglrx I think is its name) is the opposite of the radeon.  It supports the 9200SE and above (maybe R200 chipsets and above).  Basically, if your card is very new, you need this one, but since this doesn't support the very old cards, you'll need radeon.

Now .. supposedly, the binary ati driver has some good features, but I can't see any real difference, except that EVERYONE seems to have problems with the binary driver in one way or another and the radeon driver is stable.   Performance ...

Since I have a 9200SE and both drivers support this card, I can compare.  Note that for faster cards, the regular radeon driver won't give you all the features, if it works at all, but for this card ... I literally changed my Xorg and libGL drivers and restarted X and retested, both as root, nothing else running.  Good consistent results ...

glxgears .... 
    ATI fglrx binary driver 8.12.10 = 512.8 fps
    Xorg 6.8.2-r2 radeon driver   = 707.2 fps

Yup ... Xorg is faster!

I suggest you keep the Xorg libGL and the ati libGL drivers seperate and just make symlinks to them.  Find out if Ubunto does this for you ... I'm just browsing from a google hit!  Enjoy

---

### Post by dudus on 2006-04-05
Someone could give more information on this. 
I have this radeon 9200SE. And it would be nice to try this radeon driver. I found that this is not very popular as looking in the forums most people use the ati for normal usag and fglrx only if they need 3d acceleration.

Does ubuntu do this symlink to change the driver?

---

### Post by chadian22 on 2006-12-03
So I am running a 9700 pro ( newer than a 9200 ?? ) then I want the fglrd or do I want ati ? I am so confused... Just got W3 working on Cedega but its uber slow and I have a 9700 pro so this shouldnt be the case.

---

### Post by fng on 2006-12-03
> **chadian22 said:**
> So I am running a 9700 pro ( newer than a 9200 ?? ) then I want the fglrd or do I want ati ? I am so confused... Just got W3 working on Cedega but its uber slow and I have a 9700 pro so this shouldnt be the case.

you should use the fglrx drivers

---

### Post by CatKiller on 2006-12-03
In case anyone ends up confused by this terribly old thread, **man ati** says:

> **DESCRIPTION**
       **ati**  is  an  Xorg  wrapper  driver for ATI video cards.  It autodetects
       whether your hardware has a Radeon, Rage  128,  or  Mach64  or  earlier
       class  of  chipset,  and  loads  the  radeon(4), r128(4), or atimisc(4)
       driver as appropriate.


---

### Post by jonj on 2006-12-12
> **CatKiller said:**
> In case anyone ends up confused by this terribly old thread, **man ati** says:
DESCRIPTION
ati is an Xorg wrapper driver for ATI video cards. It autodetects
whether your hardware has a Radeon, Rage 128, or Mach64 or earlier
class of chipset, and loads the radeon(4), r128(4), or atimisc(4)
driver as appropriate.


That may be what the man page says, but on my system the ati driver doesn't work, but the radeon driver does. My suggestion is therefore to **try both**!

The system:
```
Device          "ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
Monitor         "DELL 1905FP"
```


running 'dpkg-reconfigure xserver-xorg' gives me the "ati" driver in /etc/X11/xorg.conf but after rebooting I get the bluescreen and an error "No device found" somewhere in the log file.

If I manually change  
```
Driver          "ati"
```
to
```
Driver          "radeon"
```
and restart X with 'sudo /etc/init.d/gdm restart'
then it works.

(as an aside for the benefit of any devs who may read this: with this hardware, I always have to fall back to 'safe graphics mode' on the ubuntu live CD's which indicates it's not being detected properly)

---
[http://know.homelinux.com/](http://know.homelinux.com/)

---

