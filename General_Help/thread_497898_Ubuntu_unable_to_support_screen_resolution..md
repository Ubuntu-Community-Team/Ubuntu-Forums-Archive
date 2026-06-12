---
title: "Ubuntu unable to support screen resolution."
date: 2007-07-10
forum: General Help
---

### Post by estebanf on 2007-07-10
Thanks for reading and your time. I'm asking to the ubuntu expert community to help me solve the annoying problem of my screen resolution. The main thread for my issue is [here]("http://ubuntuforums.org/showthread.php?t=493314"). I don't want to spam, so please if you have time visit that thread.

Best regards,

---

### Post by fragos on 2007-07-10
It's easy to add resolutions to xorg.conf but the driver you're using will determine which resolutions can be displayed.  Driver "vesa" is limited but works with any display hardware.  If you select a driver that matches your video hardware you will have more options but you will still need to add them to xorg.conf.  On a command line do "lspci |grep VGA" and you'll see what video chipset used.

---

### Post by estebanf on 2007-07-12
I´m using nvidia (binary.. not nv) drivers.

---

### Post by fragos on 2007-07-12
For various reasons, its in your best intewrest to use the nvidia drivers in the Ubuntu repositories.  there are three and your selection depends on your hardware.  All three package names include "nvidia-glx" and can be found with a search in synaptic.  I use 1440x900 with my Nvidia card and installed the "nvidia-glx" package.  I did edit xorg.conf to get that resolution.  Exactly what are you trying to set as resolution and what does your /etc/X11/xorg.conf lopk like?

---

### Post by bdtgp on 2007-07-12
I would install the new nvidia drivers like so:
```
sudo apt-get install nvidia-glx-new
```
It appears that you have those already so then try to have your nvidia settings write directly to your xorg.conf file like so:
```
sudo nvidia-xconfig --no-composite
```
After you do that, log out and restart the x-server (Ctrl+Alt+bkspc)
Then open up your terminal and type:
```
nvidia-settings
```
Check and see if the resolution you want is there.

Let me know how that goes and we can try to work it out.

---

