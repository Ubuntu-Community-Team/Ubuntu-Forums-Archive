---
title: "Screen trouble"
date: 2008-06-07
forum: General Help
---

### Post by adden93 on 2008-06-07
Hope you can help...

My laptop Toshbia Portege 2000 running ubuntu doesn't seem to find the correct resolution and as a result I have a small screen in the centre of the monitor.I will post a copy of "lspci" for you can see my driver and graphics card...I have tried a few post in editing "/etc/X11/xorg.conf" but there dosen't seem to be anything configured in the file...Ill post you an example also.

Im having the exact same problems as this post

[http://ohioloco.ubuntuforums.org/showthread.php?t=695399](http://ohioloco.ubuntuforums.org/showthread.php?t=695399).

lspci..

[IMG]http://i261.photobucket.com/albums/ii57/adden93/Screenshot-jasonubuntu.png[/IMG]

/etc/X11/xorg.conf...

[IMG]http://i261.photobucket.com/albums/ii57/adden93/Screenshot-xorgconf-etc-X11-gedit.png[/IMG]

Need anymore info then just ask.

Many thanks (again)
Adden

---

### Post by adden93 on 2008-06-08
Anybody any suggestion at all here.

---

### Post by japhyr on 2008-06-08
I am trying to work through resolution issues as well.  Here is a relevant part of my conf file:

```
Section "Device"
	Identifier	"ATI RADEON 9000"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	DisplaySize	339 254
	HorizSync	30-65
	VertRefresh	50-75
EndSection
```

You might try setting a DisplaySize, which is just the measurement in mm of your physical screen.  You can measure this with a ruler if you're not sure.  Make sure you back up your conf file, if you're not doing so already.  I would guess the display size alone would not fix the problem, but it might change the size of that window, and then you could work from there.

---

### Post by adden93 on 2008-06-23
Hi all tried the above no luck...Im still finding it really hard with a small screen so help is really needed !!!

---

### Post by avtolle on 2008-06-23
Don't know whether this is going to be of any help, but from the terminal```
gksudo displayconfig-gtk
```See how your screen is detected, look at the choices and test various ones that seem logical. Also, you might click on the graphics card tab to be sure the correct card is detected. HTH.

---

### Post by adden93 on 2008-08-07
Hi,

I know its been a while but still got the same problem none of the above posts worked. Any people know anymore about this...Is there a fix yet

---

