---
title: "Resolution help"
date: 2007-12-30
forum: General Help
---

### Post by shadows123 on 2007-12-30
Well,
i have a screen 1680 x 1050 pixels..
And.. i'm running ubuntu feisty fawn 7.04..
I can't choose higher than 1024x768..
Is there any update for this?
Or should i install the new ubuntu 7.10 ? does that one have my resolution?
Thanks!

---

### Post by lleonard on 2007-12-30
Try:

* Run "sudo dpkg-reconfigure -phigh xserver-xorg"
* Logout / login or CTRL+ALT+BKSP

---

### Post by shadows123 on 2007-12-31
I did exactly what you said, i logged back in, still 1024x768..
Anyone else an idea?
Also lol it changed my keyboard xD
Thanks!

---

### Post by CatKiller on 2007-12-31
Gutsy does have better hardware-detection and -configuration routines. If you don't have much invested in your Feisty install (in case you don't like Gutsy) then you could see if that fixes your problems. Otherwise, make a backup with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``` and use ```
gksudo gedit /etc/X11/xorg.conf
``` to edit the configuration. Add the resolution you want in the Screen section, on the Modes line, like so: ```
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
``` and you could also find out the details for your monitor and put those in the Monitor section, like so: ```
	HorizSync	30-70
	VertRefresh	50-160
``` These are values for my monitor - you'll need to find those for your monitor. This information is supposed to be passed on by your graphics card to enable the resolution to be picked out automatically, but sometimes it doesn't happen.

Restart X as above for the settings to take effect. If it all goes hideously wrong, you can use ```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```to restore your backup.

---

### Post by bigken on 2007-12-31
> **lleonard said:**
> Try:

* Run "sudo dpkg-reconfigure -phigh xserver-xorg"
* Logout / login or CTRL+ALT+BKSP

try this again but use the space to select your resolutions :)

---

### Post by bigken on 2007-12-31
sorry run this instead 

sudo dpkg-reconfigure xserver-xorg 

then use the space to select your screen sizes

---

### Post by shadows123 on 2007-12-31
ah.. oops!!
Yes!!
it works!!
This' awesome!! lol :D
Thanks guys!!
(used space thingy lol)

---

### Post by CatKiller on 2008-01-01
Don't forget to mark this thread as solved.

---

