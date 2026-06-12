---
title: "How do I change the resolution and refresh rate in recovery mode"
date: 2007-10-27
forum: General Help
---

### Post by burritoking924 on 2007-10-27
So it all worked out on the Gusty live CD. Installed, restarted, took out disk. Selected Ubuntu from the boot loader, and my monitor gives me something along the lines of ranges not possible. Then some refresh rates. What I want to know is two things, there both essentially the same question but different numbers.

[B]1: How do I set the resolution and refresh rate to 1680x1050 at 75Hz
2: How do I set the resolution and refresh rate to 800x600 65Hz
[/B]

Number two is just in case the first one doesn't work, so I dont have to reboot into Window and ask again. Thanks in advanced.

---

### Post by taurus on 2007-10-27
You can set your resolutions in /etc/X11/xorg.conf with

```
nano -Bw /etc/X11/xorg.conf
```
Save it with <Ctrl>o and exit with <Ctrl>x.  

Then, reboot with

```
shutdown -r now
```

---

### Post by squallx840 on 2007-11-28
How about the refresh rate? How to change it in recovery mode?

---

