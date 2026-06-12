---
title: "GNOME Screen Sharing Missing on Wayland (Ubuntu 20.04)"
date: 2020-07-25
forum: General Help
---

### Post by voltageamperage on 2020-07-25
Hello!

I'm trying to use a plugin for OBS so I can record on Wayland. However, they all require me to enable screen sharing in my GNOME settings, which is missing. I have vino installed, as well as xdg-desktop-portal, xdg-desktop-portal-gtk, and pipewire. Does anybody know what am I missing, and how I can fix this?

Many thanks!

---

### Post by HermanAB on 2020-07-26
You are missing Xorg unfortunately.

Wayland is supposed to be a simpler system and doesn't do a lot of things that Xorg does and which all the developers insisted nobody uses - except for all the millions of people who do of course.

---

### Post by voltageamperage on 2020-07-29
Aw, that's a bummer. Well, thank you for the information! Hopefully that will change in the near future.

---

