---
title: "green stripes after Installation"
date: 2007-05-12
forum: General Help
---

### Post by Mjosch on 2007-05-12
Hey,
I have installed an Ubuntu Ultimat Gamers edition on my pc (geforce 6600, intel 3600+) but now all that I see when I start it is green and grey stripes. I have tried the "dpkg-reconfigure xserver.org" and "dpkg-reconfigure -phigh xserver-xorg" command but nothing has worked. When I booted from the DVD I had to set the resolution from normal VGA to 1024 X 768 X 32 to be able to see the OS then, so I think that now after the instalation the resolution has gone back to VGA and my Graphicscard can´t handle it in some way. If any one nows how to manage this problem or somehow change the resolution it would be grand. Please I really need help.

//Simon

---

### Post by merlinus on 2007-05-12
Take a look at /etc/X11/xorg.conf for information that may help, especially in terms of the video driver.

For example, here is the approriate section from mine:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"

hth...

-merlin

---

### Post by Mjosch on 2007-05-12
hey thanks, but when I tried it it just said, "bash:/etc/X11/xorg.conf:Permission Denied" I dont know what to do becous this is when I write the line in recovery mode, becouse when I run the OS and then press CTR+ALT+F1 it just shows stripes.:( and I cant read or type anything.

//Simon

---

### Post by merlinus on 2007-05-12
You need to be running as su in order to edit the file.

Try this at a terminal prompt:

gksudo gedit /etc/X11/xorg.conf

But first make a backup of xorg.conf by doing a save-as, then re-open xorg.conf.

-merlin

---

