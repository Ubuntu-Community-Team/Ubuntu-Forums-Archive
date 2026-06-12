---
title: "Enabling Restricted Driver for NVIDIA Geforce2 MX 400 causing problems"
date: 2007-06-21
forum: General Help
---

### Post by Cohech on 2007-06-21
I've recently installed Ubuntu for the first time (7.04 - Feisty) but having problems with my graphics card or the driver supporting it.  A driver for my graphics card was, I assume, automatically installed during the Ubuntu installation.

If the "NVIDIA accelerated graphics driver" is enabled using the Restricted Drivers Manager and the system rebooted, it initially appears to work correctly.  The problems start when I tried to switch users.  After clicking on the 'Switch Users' button the screen instantly goes blank and I have to turn the PC off to recover.  I've also noticed that with this driver enabled hardly any (about 10%) of the screensavers work (the remainder simply show a blank screen).

If this driver is disabled I can successfully switch users and the majority (all that I've tested) of screensavers work but *very* slowly - obviously because I have the driver disabled.

My box (1GHz PIII) is fitted with a NVIDIA Geforce MX 400 card, which according to the following page "works perfectly":
[http://doc.gwos.org/index.php/Nvidia/Geforce2](http://doc.gwos.org/index.php/Nvidia/Geforce2)

In Device Manger the graphics cards has a device name of 'NV11 [GeForce2 MX/MX 400]'

Does anyone have any ideas what the problem is or how to investigate further?  I'm unsure how to determine whether it's a hardware or software problem.

---

### Post by renzokuken on 2007-06-21
use envy to install the nvidia drivers instead of the "restricted drivers manager"

check out [www.albertomilone.com](www.albertomilone.com) for envy

---

### Post by Cohech on 2007-06-21
Thanks for the suggestion but I've tried running Envy and it's *completely* hosed my system!  Ubuntu can no longer load the desktop.

Is there anything (short of reinstalling Ubuntu) anyone can suggest?  Is there any method of returning back to the previous configuration?

Any help would be appreciated!

-----

When starting the system I get the following message:
"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"

I will try and manually transcribe (!) the relevant bits from the logs when I have a chance later... great evening for me!

---

### Post by Cohech on 2007-06-21
The end of the Xorg.0.log file shows:

(EE) NVIDAI(0): Failed to initialze the NVIDIA kernel module! Please ensure
(EE) NVIDAI(0):       that there is a supported NVIDIA GPU in the system, and
(EE) NVIDAI(0):       that the NVIDIA device files have been created properly.
(EE) NVIDAI(0):       Please consult the NVIDIA README for details.
(EE) NVIDAI(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

---

