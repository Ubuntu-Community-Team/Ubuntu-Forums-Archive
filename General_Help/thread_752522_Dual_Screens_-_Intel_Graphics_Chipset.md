---
title: "Dual Screens - Intel Graphics Chipset?"
date: 2008-04-11
forum: General Help
---

### Post by igfud on 2008-04-11
Hello,

I wanted to get dual screens working in Ubuntu 7.10 on my laptop, a Gateway 6518GZ with an Intel 82852 graphics chipset.  I'm not really sure where to start--I've seen guides on editing X.org.  There seems to be a screen tool in the administrator's "Administration" menu that would allow dual screens, but all the options are grayed out (if I plug in a second monitor, it recognizes the brand/model, but I still can't enable dual monitors).  Most everything seems to be geared towards ATI or nVIDIA cards--nothing for Intel chipsets.

Because my computer is a laptop, I'd like to be able to disable dual screens occasionally so I could use my computer portably  I think there was a project for this on the web awhile back, but I can't seem to find it, and I'm not sure how successful it was.

Are there any guides or programs that might be of help to me, or are there driver/chipset restrictions that prevent this?  I transitioned from Windows to Linux a few months ago and love everything Linux has to offer.  I really liked my dual screens, though.

If there is no reliable means for laptop users to have dual screens, are there any plans to add such features in future Ubuntu distributions?  I've seen dual screen questions asked in many Linux forums, but everyone's solution seems to be different.

Thanks!
igfud

---

### Post by SorryGoFish on 2008-04-12
Check out xrandr: [http://www.x.org/wiki/Projects/XRandR]("http://www.x.org/wiki/Projects/XRandR") especially check out the howto at thinkwiki (link on that site). It works great on my intel video card.

---

### Post by igfud on 2008-04-13
Perfect!! Works great as far as I can tell, it only requires one command, and I didn't have to install anything.

My laptop's resolution is 1280x800 and my second monitor is 1024x768.  If I just plug in my second monitor, it uses a 1280x800 resolution by default and that just doesn't look nice....

The needed command is:

```
xrandr --output VGA --mode 1024x768 --left-of LVDS
```

This sets my second (VGA) monitor's resolution to 1024x768, and extends the desktop to the left of my laptop (other parameters are right-of, above, and below).  If you get an error about maximum screen resolution, open up xorg.config (in terminal enter:

```
sudo gedit /etc/X11/xorg.conf
```

and change the "Virtual" property to values that will at least equal the combined width and height of the monitors.)

igfud

---

