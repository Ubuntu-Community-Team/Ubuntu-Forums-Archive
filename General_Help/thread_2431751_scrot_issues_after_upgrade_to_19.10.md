---
title: "scrot issues after upgrade to 19.10"
date: 2019-11-21
forum: General Help
---

### Post by xadder on 2019-11-21
I have used scrot for years to capture images from my screen, typically 'scrot -s myfig.png'. After upgrading to 19.10 it still seems to work, but the lines marking the capture area rectangle behave strangely. Jumping around, and making it hard to know what's happening. If one ignores the jumping lines I think it still grabs the right area, but  this behaviour is very confusing.

---

### Post by 0x656b694d on 2019-11-27
try disabling Wayland:
either in the [FONT=Courier New]/etc/gdm3/custom.conf[/FONT]:
```

# Uncomment the line below to force the login screen to use Xorg
WaylandEnable=false
```
or during login, choose the Xorg based environment (like GNOME on Xorg).

Optionally, try using gnome-screenshot command to see if it works better.

---

### Post by xadder on 2019-11-28
I don't have gdm3, or gnome-screenshot, but I tried xfce4-screenshooter, and that seems to work fine. Thanks for the suggestions.

---

