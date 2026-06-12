---
title: "&quot;Black&quot; screen after Xubuntu loading screen (Startup)"
date: 2008-05-05
forum: General Help
---

### Post by kontr4st on 2008-05-05
Hello,

(Using 8.04, fluxbox, if that matters)

After I choose my Xubuntu installation in the grub menu, my installation will load the entire bar for the loading screen, and the screen will go blank, then show the cursor loading on a black screen. After, it will go blank again then black (display is showing black, not blank screen). I've tried getting into failsafe terminal, restarting X, etc. I even tried typing in my username/password incase the login just wasnt showing right. No success, but when i do go into recovery mode via grub, I can do the xFix and it will load sucessfully and let me login. It simply says overwriting possibly customized xorg-conf. Here's my current xorg-conf and one of the many backup's of an overwritten one (seemingly the same)

/etc/X11/xorg.conf
```
# xorg.conf (X.Org X Window System server configuration file)

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

/etc/X11/xorg.conf.20080505165755
```
# xorg.conf (X.Org X Window System server configuration file)

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

Thanks

---

### Post by kontr4st on 2008-05-06
After another day, I have still come up with no solution. Anyone have any idea?

---

### Post by kontr4st on 2008-05-08
Still no idea how this is happening.

---

### Post by kontr4st on 2008-05-10
Anyone?

---

### Post by fireput on 2008-05-12
Actually, I am facing the same problem too. I had my Ubuntu 8.04 installed, everything went well with the default GNOME Desktop Environment except for a little laggy and freeze once a while. After reading some articles on XFCE, I proceeded to download Xubuntu Desktop using Synaptic Package Manager. After reboot, and login to XFCE session, I experienced this **blank screen** (mine is blue in color). I couldn't do anything much except for command interface at CTRL-ALT-F2. I appreciate any help, thanks alot.

---

### Post by postmortymn on 2008-11-18
This happened to me... after updating from 7.10 to 8.04 (server) and adding xubuntu-desktop

This is what I did... After several beers and more "f-words" than a Tarrentino movie, I: 
- loaded a Ubuntu 8.04 live cd 
- copied the xorg.conf to a flash drive
- rebooted into recovery mode (ESC at grub loader)
- copied the Live xorg.conf into X11 (no, i didnt back up... it wasnt working anyway... so what?)
- rebooted again, feeling kind of windowish....
- let X see that the xorg was all screwed up and chose to reconfigure
- rebooted again...
- it worked
- rebooted again
- still worked
- took it back to the business that wanted a gui on the server (go figure) and got mah moneh!!!

haven't heard anything yet...

hope that works for everyone

---

