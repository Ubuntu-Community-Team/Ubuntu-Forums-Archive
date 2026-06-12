---
title: "unable to get xserver with nvidia 5200.."
date: 2008-05-10
forum: General Help
---

### Post by Mia_tech on 2008-05-10
after installing my nvidia 5200 pci card, my ubuntu 8.04 boots up but it won't load the x session, it stops at the command line....could someone advise me how could I get this solved?

thanks

---

### Post by Fixel on 2008-05-10
hiya

when at the command line: edit the xorg.conf

by typing

sudo nano /etc/X11/xorg.conf

where it says "Driver        "[something like nv or nvidia]""
instead of the clamps put "vesa"
this will boot it into the gfx standard vesa.. from here you will be able to install the restricted driver.. you'll get a popup when you enter the system

---

### Post by CREEPING DEATH on 2008-05-10
This used to be a fairly simple fix```
sudo dpkg-reconfigure xserver-xorg
```but I don't think that works any more.  The "unbreakable X" requires different commands and I'm not sure of the new ones, the old command just reconfigures the keyboard now.
I'm sure somebody will be along shortly to help you out better than I can, but I'll give you a bump in the mean time!

CD

---

### Post by kabads on 2008-05-10
> **Mia_tech said:**
> after installing my nvidia 5200 pci card, my ubuntu 8.04 boots up but it won't load the x session, it stops at the command line....could someone advise me how could I get this solved?

thanks

Perhaps posting /etc/X11/xorg.conf would help? 

Also, what runlevel is your machine booting to? 

What .iso file did you install, was it a server insallation, or desktop?

---

### Post by Mia_tech on 2008-05-11
> **kabads said:**
> Perhaps posting /etc/X11/xorg.conf would help? 

Also, what runlevel is your machine booting to? 

What .iso file did you install, was it a server insallation, or desktop?
sorry for the delay, been a bit busy... 
here's my xorg.conf file...
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

 had installed 7.10 and upgraded to 8.04 using the alternate cd... now the card is new just got it and I'm trying to get it working...also the box of the video card doesn't say vesa it says xfx...does that change the configuration of the file....I changed the driver portion of the file to vesa rebooted hoping to get the restricted drivers but it didn't work either like someone suggested in this thread.....any help appreciated

thanks

---

### Post by mrreality13 on 2008-05-11
I had issues and used this worked like a charm

```
http://howtoforge.org/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200
```

---

### Post by Mia_tech on 2008-05-11
> **mrreality13 said:**
> I had issues and used this worked like a charm

```
http://howtoforge.org/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200
```

well that guide is no good to me since I'm only able to get to the shell prompt in recovery mode...can't get all the way to the x session

thanks

---

