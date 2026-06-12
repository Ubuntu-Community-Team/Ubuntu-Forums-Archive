---
title: "X.org ati tv-out"
date: 2004-11-22
forum: General Help
---

### Post by gfg on 2004-11-22
Hi! I have now set up Ubuntu too suit my needs. I dualboot with windows now, because I often use Tv-out.  I was wondering if it's possible to have tv out with ATI and Xorg or Xfree if xorg dosn't work. If someone could help me with this I would appreciate it. If i get Tv-out to work i could finally migrate form Windows to Linux. 

I have tried many distros from gentoo to mandrake, but it wasn't before i found Ubuntu i got comfertable. Thanks for a great distro and a great community. Keep up the good work people  :-D

---

### Post by ulrich on 2004-11-22
hi,
i just know how this works with the ati fglrx-binaries. 
i really DONT know if this works with dri-drivers!

after you installed them through apt or synaptic run
```
fglrxconfig
```
and answer 'yes' for tv-out and enter the appropriate tv-settings.

after that, edit your XF86Config-4 or xorg.conf. and add something like
```

Section "Monitor" #this is your tv
    Identifier  "Monitor1"
    HorizSync   31.5 - 37.9
    VertRefresh 50 - 70
    Option "DPMS"
EndSection

```
```

Section "Device"
	Identifier		"ATI TV-Out"
	Driver			"fglrx"
	BusID "PCI:2:0:0"
	Screen 1
EndSection

```
```

Section "Screen"
	Identifier  "Screen1"
	Device      "ATI TV-Out"
	Monitor     "Monitor1"
	DefaultDepth 24
    Subsection "Display"
	Depth		24
	Modes		"800x600"
	ViewPort	0 0  # initial origin if mode is smaller than desktop
    EndSubsection
EndSection

```
```

Section "ServerLayout"
    Identifier  "Server Layout"
    Screen "Screen0"
    Screen "Screen1" RightOf "Screen0"
EndSection

```

this works for me with xfree and xorg.

unfortunately i wasnt able to get gmplayer working the way i want it, so i have to use mplayer instead of gmplayer.

for watching a movie fullscreen on the tv i then use
```

DISPLAY=":0.1" mplayer -fs -vm -zoom -stop-xscreensaver -screenw 800 -screenh 600 theMovieIWannaWatch.avi

```

check the HUGE manpage for mplayer!
there are better ways to do all this (xinerama, aspect....) i for myself was too lazy to  check all the options out, i havent used tv-out lately.

hope this helps

ulrich

---

### Post by gfg on 2004-11-22
When i try to get flgrx binaries throug apt i get an error. The package can't be installed because it needs XFree. How can i fix this without removing Xorg?

---

### Post by mjpowersjr on 2004-11-23
[QUOTE=gfg]When i try to get flgrx binaries throug apt i get an error. The package can't be installed because it needs XFree. How can i fix this without removing Xorg?[/QUOTE]
 gfg, There are a few issuses with gunning the ati fglrx drivers with xorg (workaround: [http://www.linuxquestions.org/questions/history/243287](http://www.linuxquestions.org/questions/history/243287) ) -not i havent tried the workaround. ATI is working on getting a new version of the driver out that supports xorg, and is rumored to be out in december ( [http://ubuntuforums.org/showpost.php?p=21693&postcount=27](http://ubuntuforums.org/showpost.php?p=21693&postcount=27) ) so I doubt that the current driver will be repackaged to work with xorg,. you may just want to wait for the new driver like me. -mike powers

---

### Post by gfg on 2004-11-24
I have now switched back to XFree. I have configured tv-out through fglrcxconfig, but when I restart Ubuntu won't boot and I can't really see no errors in the log except from some missing fonts. Anyone know what to do?

---

### Post by jdodson on 2004-11-24
run a forum search for ati tv out.

---

### Post by gfg on 2004-11-24
Ok, I have now fixed the problem with X not starting and I have a little question. Is the tv supposed to flicker a lot? In windows I can change some settings to get less flickering is there an equal alternative in linux also?

---

