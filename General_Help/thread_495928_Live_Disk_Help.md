---
title: "Live Disk Help"
date: 2007-07-08
forum: General Help
---

### Post by cessna_89702 on 2007-07-08
I have a live disk of feisty 7.04 64bit version. When I put it in my computer and start it, it goes to where it should switch for a login and start up. Altough it doesnt start, it just shows a lot of colorful lines going through the screen and will never start. This is an hp dv9000. I have gotten it close to start by typing ```
acpi=off
``` but then the sound starts playing the same part over and over and it freezes.
I have an nvidia graphics card. 

Anyone have a solution???


btw fedora did the same thing on there live disk until I put acpi=off

---

### Post by cessna_89702 on 2007-07-08
anyone

---

### Post by confused57 on 2007-07-08
When you get the corrupted login screen, press "Ctrl+Alt+F1", then enter:
```
sudo dpkg-reconfigure xserver-xorg
```
choose defaults for most screens, but select the "vesa" video driver...once you've completed configuring the xserver, type in "startx", without the quotes...this should get you to a GUI.

---

