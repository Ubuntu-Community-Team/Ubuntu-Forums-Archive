---
title: "Need Help (x-server won't load)"
date: 2005-10-25
forum: General Help
---

### Post by longshot5000 on 2005-10-25
Okay - when I read on the forum I thought maybe this was an AMD64 problem but I am not sure if it is.

X-Server will not load - I have tried this with Ubuntu 5.10 (64bit) and also Ubuntu 5.04 live cd for Intel x86.

When trying the ATI module I am told the device is missing.

Failed to load module ATI 
Module does not exist. (sorry I have to hand write this...errors down)

lib GLcore.a:m_debug>norm.0 No Sybmols Found
 

I have tried loading fglrx and this is what I get

Loading /usr/X11R6/lib/modules/drivers/fglrx-drv.0 Duplicate Symbol rol_log in


if you need more details..I will reload and try again.

My current system is

Athlon 3000+
Asus A8N Nforce 4 Motherboard
ATI x800 pro PCI Express 
1 Gig of DDR 100
LG 19 Inch LCD monitor


help please..if possible..

---

### Post by ecobuntu on 2005-10-25
hmm...maybe try
at terminal:
sudo dpkg-reconfigure xserver-xorg

see if you can fix your problem there

---

### Post by longshot5000 on 2005-10-25
I have tried this command - went thru it all.  That is also the way I was able to choose fglrx as the driver...didn't work:(

---

### Post by longshot5000 on 2005-10-26
okay i tried again and wrote better notes this time..

using Config File "/etc/X11/xorg.conf
Skipping "/usr/X11R6/lib/modules/extensions/libGlore.a:m_debug_clip.0" No Symbols Found
Skipping "/usr/X11R6/lib/modules/extensions/libGlore.a:m_debug_norm.0" No Symbols Found
Skipping "/usr/X11R6/lib/modules/extensions/libGlore.a:m_debug_xform.0" No Symbols Found

(EE) No Device Found

XIO:  Fatal Error 104 (Connection reset by Peer) on xserver ":0.0 after 0 REquest (0 Known Processed) with 0 events remaining

---

### Post by RAOF on 2005-10-26
Edit: I needed to read your post better.

Try selecting the "vesa" driver when you do dpkg-reconfigure xserver-xorg.  If that doesn't work there's something really wrong.  Then, when you have a working X, it'll be easier to figure out how to get an ati driver working...

---

### Post by longshot5000 on 2005-10-26
nps..i wil try that again..did last time and the screen goes blank..is it the when I try from the live cd it tells me I need to be in the root..to do that command...how do i do that from the cd?

---

### Post by jeffmills on 2006-04-30
Did you fix this problem? I have the exact same problem.

---

### Post by webbcm01 on 2006-05-14
having the same problem here too with a geforce 7900 gtx

---

