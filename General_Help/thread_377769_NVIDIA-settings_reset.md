---
title: "NVIDIA-settings reset"
date: 2007-03-06
forum: General Help
---

### Post by Pieboy337 on 2007-03-06
I recently installed drivers for my NVIDIA card (v9746) onto kubuntu. I changed the settings in the NVIDIA-settings for my resolution to change. It changed it, but whenever I restart it will go back to the previous settings. I tried clicking the save into x configuration file button, but no luck unfortunately. I found a way to fix this in GNOME, but how do I do this in KDE? Someone please save this damsel in distress.

---

### Post by tribble222 on 2007-03-06
You will probably need to edit your /etc/X11/xorg.conf file and specify the resolution in there.  Do a search for xorg.conf and you should find lots of info on this.

---

### Post by kpkeerthi on 2007-03-06
It works in gnome and not in KDE. Thats strange. How did you fix it in gnome?

---

### Post by ~LoKe on 2007-03-06
Try adding this to your session startup applications.

> nvidia-settings --load-config-only

---

### Post by Pieboy337 on 2007-03-07
> **~LoKe said:**
> Try adding this to your session startup applications.
yeah, thats how I fixed it in GNOME. I dont know how you get to that in KDE. Any ideas?

---

### Post by codered867 on 2007-03-07
I could be wrong but you might not have the permissions to write to your xorg.conf. Try running nvidia-settings as root or with sudo.

---

### Post by igknighted on 2007-03-07
> **Pieboy337 said:**
> yeah, thats how I fixed it in GNOME. I dont know how you get to that in KDE. Any ideas?

Make a script to run it and place it in ~/.kde/Autostart

---

### Post by Pieboy337 on 2007-03-07
> **igknighted said:**
> Make a script to run it and place it in ~/.kde/Autostart
I apologize for being a bit of a noob, but how do I do this?

---

### Post by igknighted on 2007-03-07
:confused: that I can't tell you, cause I don't do any scripting myself.  I was hoping that someone who knows this stuff could post it.  I think it's just a line or two, but I don't know the syntax well enough to venture a guess.

---

### Post by Pieboy337 on 2007-03-07
> **codered867 said:**
> I could be wrong but you might not have the permissions to write to your xorg.conf. Try running nvidia-settings as root or with sudo.
I recently tried doing this as root, unfortunately after restarting the computer, it reset as usual. I would just edit the xorg file myself, but I wanted to be able to get dual monitor support working through the nvidia-settings as well. I guess I just have to someway get it in the autostart, and I dont think I would be able to manage any scripting. If anyone can, please help (all the input so far has been greatly appreciated. Thank you all).

---

