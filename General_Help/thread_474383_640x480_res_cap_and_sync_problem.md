---
title: "640x480 res cap and sync problem"
date: 2007-06-15
forum: General Help
---

### Post by InfernalEternal on 2007-06-15
Upon the intial bootup I recieved an error message, something along the lines of 'Failed to start the X Server' (Your graphical interface). Upon reading further I recieved:
(EE) 1810(0) No video BIOS modes chosen for depth.
(EE) Screen(s) found, but none have a usable configuration.

I did some soul seeking and found the 'sudo dpkg-reconfigure xserver-xorg' command. Through the use of 'startx' I was able to actually gain access to the desktop but at a severly limited resolution. Currently its 640x480 and god knows what depth. To make matters worse the screen is off center, about a fifth being unviewable. Ouch.

Any options? I have one of those terrible Intel GPU's, I'm pretty sure its a 82845G. Any ideas on how to fix the resolution [I'm aiming for 1024x768]? The colour depth? The positioning of the actual desktop?

I've installed the intel driver which has the file name 'dri-I915-v1.1' if thats any help.

Much appreciated. Running xUbuntu 6.06.1 'Dapper Drake' btw.

---

### Post by Cilionelle on 2007-06-15
As a fellow 845G user, I totally empathise with you...  please refer to my "Right, resolution still buggy" thread (recently bumped) for more info.  I think you'll find that the driver you want is the i810 (technically the i845 part, but don't worry about that!) one.

But let me tell you, I understand your pain!

Edit: sorry, forgot to mention that the thread is in the "Absolute Beginner Talk" bit...

---

