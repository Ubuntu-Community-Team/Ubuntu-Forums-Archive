---
title: "Can't get translucency for desklets... :o("
date: 2005-10-26
forum: General Help
---

### Post by TomG on 2005-10-26
Hi,

I'm trying to enable translucency for gdesklets but it does not work. 

I have :

 - Ubuntu (Gnome) 5.10
 - Xorg 6.8.2
 - xcompmgr 1.1.1
 - gDesklets 0.35.2

I did : 

1. Put this into /etc/X11/xorg.conf :
Section "Extensions"
        Option "Composite" "On"
EndSection 

2. Installing xcompmgr 1.1.1 with Synaptics

3. Run from cmd line "xcompmgr"

4. "gdesklets --translucent start" was already started at boot time

5. Restart serverX and desklets 

-> Does not work !

I searched on forums and web but I cant find why it fails.
What's wrong ? :( 

Tx,
Tom

---

### Post by jasay on 2005-10-26
Hi Tom, 

I don't have xcompmgr installed but all I had to do to make the desklets appear transparent was to *disable *translucency in the Configuration window.  I'm not sure why that works for me, but you might give it a shot.  I think this only creates "fake" transparency (ie drawing the background as part of the desklet as opposed showing whatever is behind the desklet).  I'm not sure what exactly the translucency is suppposed to do and how it is different.

---

### Post by cagljevic on 2005-10-26
i too noticed that when i checked the option to enable translucency it in fact made a big black square around the desklets.  i have nvidia drivers 1.0-7676 installed and without checking the option, the desklets are infact drawn correctly with translucency.  i tried checking the box thinking i was missing out on something great, apprently not :P

-mark

---

### Post by TomG on 2005-10-27
Thanks for your answers.
Yes it gives a big black box around desklets. Will check the drivers for my graphical card.
Tom

---

### Post by TomG on 2005-10-28
I installed Nvidia drivers. 
It was a little bit "better" as I got a rectangle with wallpaper install of black bok...
[ATTACH]3212[/ATTACH]

It worked until I restart. On next boot X server was unable to start.
I had to change the Driver in /etc/X11/xorg.conf from "nvidia" to "nv" to start X again : :( 

Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

I even lose my customized theme (???).
I followed the method from Wiki to install NVidia drivers. Any idea to start with nvidia instead of nv ?

Thanks,
Tom

---

