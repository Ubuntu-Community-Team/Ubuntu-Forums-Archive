---
title: "Help with uncommon resolution not found: 1768x992"
date: 2013-01-17
forum: General Help
---

### Post by iTeRRoRiz3 on 2013-01-17
I have searched all over and it seems everyone has issues with ubuntu and proper resolutions. I have installed the latest stable drivers for my GTX 670 on 12.04 LTS. The basic resolutions are there but 1920x1080 on my screen does not work it is too big for my screen therefore I have to use 1768x992 on windows and hackintosh but on ubuntu there is no option. I have tried to use xrandr but I did not know if anyone had any advice or if this is even possible.

---

### Post by mcduck on 2013-01-17
I doubt there really is a single display panel in existence with such a resolution... :o

I bet it's more a question of using the 1920x1080 (or whatever the panel's native resolution is) resolution, and if the display is a TV or something like that making sure the display itself is set to pixel-per-pixel mode and that there is no overscan enabled in your graphics card's options.

You *can* define any resolution you want manually in xorg.conf, but like I said I doubt that it's really the correct solution for getting your display to work. If you choose to go against my advice, then here's a modeline generator you can use: [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl")

---

### Post by iTeRRoRiz3 on 2013-01-17
> **mcduck said:**
> I doubt there really is a single display panel in existence with such a resolution... :o

I bet it's more a question of using the 1920x1080 (or whatever the panel's native resolution is) resolution, and if the display is a TV or something like that making sure the display itself is set to pixel-per-pixel mode and that there is no overscan enabled in your graphics card's options.

You *can* define any resolution you want manually in xorg.conf, but like I said I doubt that it's really the correct solution for getting your display to work. If you choose to go against my advice, then here's a modeline generator you can use: [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl")


It is a TV and it is 32 inches and according to the specs I found on it a while back when I looked into it because I always thought it was weird even in windows when I used 1920x1080 it was just too big for my screen. But anyways where do I set that pixel per pixel mode, is it on the TV? By the way the TV is old as **** if you want the model just let me know all help is appreciated, and no I did not go against your advice I have not messed with that yet until I figure out this problem.

---

### Post by bab1 on 2013-01-18
> **iTeRRoRiz3 said:**
> ...By the way the TV is old as **** And there in lies the rub.  The monitor is analog and the latest Xorg expects a digital monitor supplying an ID that provides the resolution to be use.  

I struggled with this for a long time with a Samsung monitor until one day I used the DVI output instead of the old video output.  Magically I had the correct video rez.  I know this doesn't help you directly, but maybe it will point you in the correct direction.

You will need to figure out the correct modeline and create your own xorg.conf file.  Be aware it is confusing and not well documented.

---

### Post by iTeRRoRiz3 on 2013-01-18
Yeah, I am trying to do it in terminal got far then got to an error regarding 

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  41
  Current serial number in output stream:  42

---

### Post by iTeRRoRiz3 on 2013-01-26
anything?

---

