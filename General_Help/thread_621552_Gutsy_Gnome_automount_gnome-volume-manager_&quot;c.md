---
title: "Gutsy Gnome automount gnome-volume-manager &quot;check-foreground-console returned with 1&quot;"
date: 2007-11-23
forum: General Help
---

### Post by Despot on 2007-11-23
Having beaten my head against the wall on this for some time, I'm turning to you, the community for help:

**Nothing** (USB drives, DVDs, iPods) will automount in Gutsy (upgrade from Feisty). I've done the removable device debug procedure and scoured the forums and Google for tips, even logged a [bug report]("https://bugs.launchpad.net/ubuntu/+bug/157939") (which has been ignored). 

From what I can tell, udev and the HAL daemon are handling things correctly. However, the gnome-volume-manager does not take appropriate action. Instead, when a device is plugged in I get the following message in the g-v-m log:

> manager.c/3306: gvm_user_active_at_console: check-foreground-console returned with 1

If you kill the G-V-M instance and restart it, *then* any attached devices are mounted correctly. But this has to be done every time you want to mount a device.

I've tested this with a separate login and have the same problems, so it's not an issue with a user setting. Devices mount fine when running KDE, and this is a dual-boot machine, so I can test things in Windows--works perfectly.

Any advice would be greatly appreciated.

---

### Post by Despot on 2007-11-25
anyone? :(

---

