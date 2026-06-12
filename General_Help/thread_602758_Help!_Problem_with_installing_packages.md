---
title: "Help! Problem with installing packages"
date: 2007-11-04
forum: General Help
---

### Post by PhilipB on 2007-11-04
Hi there, I'm Philip, new time Ubuntu user from the UK. I'm currently running Gutsy Gibbon in VMware Player with Windows XP in the background; no problems at the moment, sound is working fine, great internet connection, USB ports and printer working, everything was running fine just until recently.

I was installing a package for LimeWire Pro when it halted and was like that for some time. I thought that something had happened and so decided to close the window. Now whenever I try to open up Synaptic Package Manager or Update Manager I get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

But whenever I try to run 'dpkg --configure -a' in Terminal I get this message:

dpkg: requested operation requires superuser privilege

It's getting annoying :mad: Does anyone know how to solve this problem? If so, please reply.

Also, the log-in screen always seems to be a resoultion too high for my screen, but I can't find a way to change this either, even in the Log-In Screen settings. Does anyone know how to fix this too? Thanks.

---

### Post by oldos2er on 2007-11-04
Try "sudo dpkg --configure -a"

 The "sudo" part is superuser privilege.

---

### Post by PhilipB on 2007-11-04
I've tried that, but when I try to type my password in it won't let me :(

Edit: I must have done something because just now it worked :S But now I need to know, did it do anything? This text came up:

Setting up java-common (0.26ubuntu1) ...

Setting up odbcinst1debian1 (2.2.11-16) ...

Setting up unixodbc (2.2.11-16) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

And I could hear the computer doing its work, but now it has stopped. Has it been fixed?

Edit 2: It did! Thank you so much. Now could someone help me with the screen resoultion problem? Thanks.

---

### Post by Six_Digits on 2007-11-06
Do you have the drivers for your video card?

If so, open your xorg.conf file like this:
```
sudo gedit /etc/X11/xorg.conf

```
Then change the resoloutions listed under "Modes" in the "Screens" section to what you need. 

For example-

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GTS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection
```

Save, restart, and apply the resolution you want, should do the trick.

---

