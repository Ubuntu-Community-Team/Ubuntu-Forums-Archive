---
title: "New graphics card?"
date: 2006-08-06
forum: General Help
---

### Post by ELD on 2006-08-06
Hi all i used to have an nvidia geforce 440 mx and upgraded to a geforce FX 5500, do i need to do anything to the drivers?

It seems to work fine, but then do i need to change anything or does it somehow know or something?

---

### Post by richbarna on 2006-08-06
> **ELD said:**
> Hi all i used to have an nvidia geforce 440 mx and upgraded to a geforce FX 5500, do i need to do anything to the drivers?

It seems to work fine, but then do i need to change anything or does it somehow know or something?

Take a look at my "sig"
|
|  and get the latest nVidia drivers, you will be able to enable 3D, it's a      LOT faster.
v

---

### Post by ELD on 2006-08-06
Well it seems to run all 3D programs and games and such fine without changing anything.

Could it be that the setup is the same for all nvidia cards so i don't have to change anything?

Note: i installed the drivers with automatix on my old card.

---

### Post by orb9220 on 2006-08-06
just do a term and

gedit /etc/X11/xorg.conf

and look at the drivers section and see if it says "nv" or "nvidia" which if it says "nvidia" you are using the latest with bell's and whistle's.

---

### Post by ELD on 2006-08-06
Well it says nvidia but has the wrong card name (has the name of the old card), would the card name matter?

---

### Post by orb9220 on 2006-08-06
No that's the "nvidia" which is for all mine is fx-5200 and it says that.
This is mine

Section "Device"
	[COLOR="Red"]Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"[/COLOR]
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option		"TwinView" "on"
        Option          "NvAGP" "3"
	Option		"MetaModes" "1280x1024,1280x1024; 1280x1024,NULL; 1024x768,1024x768; 1024x768,NULL"
	Option		"SecondMonitorHorizSync" "30-70"
	Option		"SecondMonitorVertRefresh" "60"
	Option		"TwinViewOrientation" "RightOf"		
	Option		"ConnectedMonitor" "CRT,CRT"
	Option 		"AllowGLXWithComposite" "true"
	Option		"RenderAccel" "true"
EndSection

In red is just an Identifier tag for display info. You could manually change it to your card if you wish.

sudo gedit /etc/X11/xorg.conf in a term then save after making changes.

---

