---
title: "Problems with screen resolution after reboot."
date: 2013-01-12
forum: General Help
---

### Post by NDAC on 2013-01-12
Hi guys. 

New Ubuntu 12.10 X64 user here. 

I have quite a problem with my Geforce GTX 560 Ti, everytime I start my computer after a good nights sleep my resolution is 640x480@75Hz, when it's supposed to be 1680x1050@60Hz. 

When I boot the computer up I'm met with this message: 

(It's translated, so it might not be totally accurate)

[I]Could not apply the stored configuration for the monitor.

none of the selected modes were compatible with the possible states:
Tries state of CRTC 633
CRTC 633: trying mode 640x480 @ 75Hz with output at 1680x1050 @ 60Hz (pass 0) [This is repeated 6 times]


Tries state of CRTC 634
CRTC 634: trying mode 640x480 @ 75Hz with output at 1680x1050 @ 60Hz (pass 0) [Also repeated 6 times]
[/I]

The fix is quite easy, but it's such a pain to run this everytime I start my computer up for the day: 

[I]
sudo apt-get update
sudo apt-get remove linux-headers-3.5.0-17-generic
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get --purge remove nvidia-current
sudo apt-get install nvidia-current
sudo nvidia-xconfig[/I]

(I don't use the 3.5.0-17-generic anymore, I use 3.5.0-21-generic)

And everything is back to normal.

Any tips on how to avoid this?

---

### Post by NDAC on 2013-01-12
Bump!

---

### Post by NDAC on 2013-01-13
Bump again. This is really putting me off Ubuntu :(

---

### Post by InonS on 2013-01-13
I found that a Synaptic complete removal of both the nvidia-current and  nvidia-settings packages, and then installation of those packages,  followed by a reconfiguration of the nvidia X Server Settings returned  things to their proper state...

32-bit ubuntu 12.01.1, GeForce 8500 GT

---

### Post by Tralce on 2013-01-17
> **InonS said:**
> I found that a Synaptic complete removal of both the nvidia-current and  nvidia-settings packages, and then installation of those packages,  followed by a reconfiguration of the nvidia X Server Settings returned  things to their proper state...

32-bit ubuntu 12.01.1, GeForce 8500 GT

"Complete removal?" Any way you know of to do that from command line? I'm having a similar issue, except that once that error appears, X is so messed up that I can only access this computer from ssh on another host.

---

### Post by InonS on 2013-01-18
Hey Tralce

Not sure if Synaptic "Complete Removal" is the same as apt-get --purge remove (in NDAC's original post). You could try checking online...

G'Luck!

---

