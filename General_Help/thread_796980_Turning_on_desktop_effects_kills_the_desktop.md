---
title: "Turning on desktop effects kills the desktop"
date: 2008-05-16
forum: General Help
---

### Post by usarmykr on 2008-05-16
When I turn on the desktop effects its like X just totally dies.  My screen goes black and nothing helps.  I am not familiar with all commands in kubuntu and hitting ctrl alt del makes a blank white box pop up.  The only way I could fix it was reinstalling.  It was a clean install with no updates from the 8.04 livecd, maybe thats why?  does anyone know why this is happening or where to find out?  Im not going to turn them on this time because I am actually updating and dont want to reformat again.  thanks in advance.

---

### Post by NightwishFan on 2008-05-16
Not sure why. When it happens though, you might be able to fix, just press ctrl+alt+f1 and type:
(for kubuntu)
```
kwin --replace
```
(for ubuntu)
```
metacity --replace
```

Then press ctrl+alt+f7 to go back to desktop. If nothing, just kill x with ctrl+alt+backspace and log in again and you should be back without compiz. (the terminal is your friend)

EDIT: I would like to ask. What is the model of your graphics card?

---

### Post by PaulEdwards on 2008-05-27
I'm having the same trouble using the restricted nvidia driver on my PC...

It seems to become enabled just fine, but when I restart to use it, I get a black screen when GDM loads. I can hear the login sound, but the display goes black and into DPMS sleep mode...

I have to go into the console and revert to the nv driver by editing the xorg.conf and restarting GDM to get a login screen again. I've even tried logging in blind to see if it would work after login, but it does not. I then have to kill X via Ctrl-Alt-Backspace.

Relevant system specs:
[LIST]
[*]AMD64 3500+
[*]2gb RAM
[*]nVidia 6600GT AGP 8x 256mb
[/LIST]

---

### Post by Forlong on 2008-05-27
Post the output of ```
grep -v ^# /etc/X11/xorg.conf
``` and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by PaulEdwards on 2008-05-27
After a closer look at my Xorg log files, I determined the cause...

```
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 GT at PCI:1:0:0:
(--) NVIDIA(0):     DELL2407WFPHC (CRT-1)
(--) NVIDIA(0):     DELL2407WFPHC (DFP-0)
(--) NVIDIA(0): DELL2407WFPHC (CRT-1): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): DELL2407WFPHC (DFP-0): 155.0 MHz maximum pixel clock
(--) NVIDIA(0): DELL2407WFPHC (DFP-0): Internal Single Link TMDS
**(II) NVIDIA(0): Assigned Display Device: CRT-1**
```

I'm using a Digital Flat Panel via the DVI connection, but Xorg is assuming an analog VGA connection.

I googled a bit and found the syntax to use in the Device section to force the DVI connection. It is bold in the example below which is actually the current xorg.conf file I'm using. I wanted to strip it down to remove all possible conflicts. ;)

```
Section "Device"
	Identifier	"Default Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
**	Option		"ConnectedMonitor"	"DFP-0"**
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Defaultdepth	24
EndSection
```

Working great now; in fact I've been up all night configuring and playing with it. :KS

---

