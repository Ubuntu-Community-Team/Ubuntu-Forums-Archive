---
title: "Rotated login screen on Lubuntu"
date: 2020-06-03
forum: General Help
---

### Post by nostrafredmesitrus on 2020-06-03
I installed Lubuntu on my Acer One 10. When I booted it up the screen was rotated 90 degrees so that it was lying down. I figured out how to rotate the screen when I'm logged in, but I don't understand how to rotate the login screen. Does anyone know how I can do this?

---

### Post by guiverc on 2020-06-03
The release of Lubuntu you are using is pretty essential.  For example the greeter is `lightdm` if you're using Lubuntu 18.04 LTS, however it's `sddm` for all modern releases.

If using a modern Lubuntu (eg. Lubuntu 20.04 LTS), the manual page for configuring `sddm` can be found at

[https://manual.lubuntu.me/stable/3/3.1/3.1.9/sddm_configuration.html]("https://manual.lubuntu.me/stable/3/3.1/3.1.9/sddm_configuration.html?highlight=sddm")

though I've never tried to rotate the greeter, so I'd need to look at the upstream documentation to see if its catered for, however I currently don't know if that's your DM/greeter (ie. your release).

---

### Post by nostrafredmesitrus on 2020-06-03
Hi, thank you for helping out. I'm using the lastest version (Lubuntu 20.04).

---

### Post by guiverc on 2020-06-04
I have no experience with this sorry, however the following I believe will be helpful

Arch wiki - [https://wiki.archlinux.org/index.php/SDDM#Rotate_display](https://wiki.archlinux.org/index.php/SDDM#Rotate_display)

That will take you to [https://wiki.archlinux.org/index.php/Xrandr#Configuration](https://wiki.archlinux.org/index.php/Xrandr#Configuration)

which mentions 

> [FONT=sans-serif]Both KDM and GDM have startup scripts that are executed when X is initiated. For GDM, these are in [/FONT]/etc/gdm/[FONT=sans-serif], while for KDM this is done at [/FONT]/usr/share/config/kdm/Xsetup[FONT=sans-serif] and for SDDM at [/FONT]/usr/share/sddm/scripts/Xsetup[FONT=sans-serif]. This method requires root access and [/FONT]

I won't advise further as I've not done it, if you have problems you can reach out and I'll experiment a little, but I'm hoping this will provide enough detail for you to solve your issue.  FYI: I didn't use upstream doco, as I felt this looked more useful.

FYI: I did a QA-test install of groovy (will be 20.10 on release), and did a quick play as that box has two displays, one landscape & one portrait.. the xrandr command for my box was
```
xrandr --output DIN --off --output DVI-0 --mode 1024x768 --pos 0x0 --rotate normal --output DVI-1 --mode 1024x768 --pos 1024x0 --rotate left
```
which won't match your system, but as example maybe helpful. I also didn't write it, I used Lubuntu's LXQt GUI to alter the display, and then installed `arandr` and saved it.. If you get stuck you could always be as lazy as I was!

---

