---
title: "Setting my own touchpad settings in gnome 16.10?"
date: 2016-12-27
forum: General Help
---

### Post by steven66 on 2016-12-27
In Ubuntu Unity distro I use synclient to set my touchpad settings. There is no synclient in gnome. I have found that most settings need to be adjusted for each PC.  Here are my settings for my touchpad I wish to use in Gnome 16.10:

vert edge scroll =0
hor edge scroll =0
vert two finger scroll =1
hor two finger scroll =0
max speed =1.5
accel factor =0.05
coasting speed =0
hor hystereses =5
vert hystereses =5
vert scroll delata =150
max tap time =0

How can I set all these touchpad settings in gnome 16.10?

---

### Post by mc4man on 2016-12-27
You can search out how to input changes to libinput or you could try adding the xserver-xorg-input-synaptics package & removing the xserver-xorg-input-libinput package, then reboot.

---

### Post by steven66 on 2016-12-28
Yes, I see that Ubuntu gnome is the only distro that uses libinput as the touchpad driver. I found it easier to switch to another distro :)

---

