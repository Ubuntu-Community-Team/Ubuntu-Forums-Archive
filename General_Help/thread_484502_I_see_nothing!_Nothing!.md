---
title: "I see nothing! Nothing!"
date: 2007-06-25
forum: General Help
---

### Post by Daniel Stange on 2007-06-25
Hello!

I had a flawless installation, however when i boot up ubuntu i can't see anything.

I do see the ubuntu logo has the OS starts, and when the screen is pitch black i can hit the enter key to hear the sound of bongos. Would love to know how to fix this, thanks!

---

### Post by jimrz on 2007-06-25
> **Daniel Stange said:**
> Hello!

I had a flawless installation, however when i boot up ubuntu i can't see anything.

I do see the ubuntu logo has the OS starts, and when the screen is pitch black i can hit the enter key to hear the sound of bongos. Would love to know how to fix this, thanks!

sounds like Xserver is unable to display. probably an issue with your video card and/or your monitor settings.
please post the make and model of both

---

### Post by Daniel Stange on 2007-06-25
Nivida Geforce 7600GS, my monitor is made by Dell, it's 19 inch's at 4:3.

Hope that's what you need to know.

---

### Post by tuxcantfly on 2007-06-26
Ctrl-Alt-F1, that'll get you into a login screen, login, then enter these commands:

```
sudo apt-get update
sudo apt-get install linux linux-restricted-modules-$(uname -r) linux-restricted-modules-common nvidia-kernel-common nvidia-glx
sudo nvidia-glx-config enable
```

Then reboot.

---

### Post by tuxcantfly on 2007-06-26
If my previous comment's instructions don't work, Ctrl-Alt-F1, that'll get you into a login screen, login, then enter this command:

```
sudo dpkg-reconfigure xserver-xorg
```

Try fiddling with the options; for video driver try "nvidia", "nv", and "vesa", one of them should work, the rest, accept the defaults, and in the monitor section, select the proper resolution and refresh rates (your monitor manual should have them), reboot after each configuration attempt

---

