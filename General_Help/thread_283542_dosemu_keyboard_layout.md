---
title: "dosemu keyboard layout"
date: 2006-10-24
forum: General Help
---

### Post by threegremlins on 2006-10-24
I'm trying to dosemu up and running but, keeps hanging on 

ERROR: Unable to open console to evaluate the keyboard map.
Please specify your keyboard map explicitly via the $_layout option


I've gone through the config file in /etc/dosemu, trying the various options in the keyboard layout section. Nothing seems to work, Years and years ago I had this worked out but for the life of me can't remember how iI did it. Anybody out there  that can refresh my memory?

---

### Post by clandestino81 on 2006-11-11
I have the same problem and can't find a solution. Anyone knows how to make dosemu work?

---

### Post by emendelson on 2006-11-12
sudo gedit /etc/dosemu/dosemu.conf

Find $_layout and change it from "auto" to "us" or some other specific layout.

However, you may find that dosemu still crashes in Edgy; there's something wrong with the version in the repositories, I think.

---

### Post by slumcat05 on 2007-01-24
Also note the '#' sign in the config file in front of the $_layout setting. This comments out the line, so to set the layout manually, I think you have to remove the '#' character. I did this and no longer get this error. dosemu seems to start running, but then suddenly it disappears and I get sent back to the linux terminal. If anyone has gotten any further, please enlighten me.

---

