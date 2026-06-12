---
title: "Ubuntu 13.04 applied updates, now I get a blank screen"
date: 2013-05-27
forum: General Help
---

### Post by Jason Spaceman on 2013-05-27
I'm running Ubuntu 13.04 on a triple boot system with Win7 and OS X.  Last week I downloaded and installed some updates that were released for 13.04.  The updates were downloaded and installed and everything seemed to go fine.  I rebooted the system and selected Ubuntu, now I get a blank screen instead of the Ubuntu login screen.  Is there a way to fix this?  Could this be an Nvidia driver issue?


Thanks,
Jason

---

### Post by Charlotte18 on 2013-05-27
Have you tried choosing the failsafe graphics option in grub?

---

### Post by Jason Spaceman on 2013-06-12
> **Charlotte18 said:**
> Have you tried choosing the failsafe graphics option in grub?

I tried that but it didn't work.

When I try to boot Ubuntu I just get a black screen, although sometimes I do get a login screen but the resolution is all off.  When I log in I just see my wallpaper and no menus or taskbar across the top to click on.  I did bring up a terminal window with Ctrl+Alt+T and installed KDE.  I do get a menu with KDE, but the resolution is still off.

I'm wondering if this is an issue with the Nvidia driver?  I tried running glxgears and I get the following:

```
Xlib:  extension "GLX" missing on display ":1".
Error: couldn't get an RGB, Double-buffered visual
```

Running the nvidia-settings app I get the message:

```
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```

xorg.conf lists 'nvidia' as my driver, so it should work, no?

---

### Post by Jason Spaceman on 2013-06-13
After poking around a little here is what is happening.

When I log into Unity I just get my wallpaper, no icons, no bar at the side of my screen with icons to click on.  Also, the resolution is all out of whack.  It should be 1920x1080 (I'm using my TV as a monitor), instead it appears kind of fuzzy, it appears to be running at a non-native resolution.

Uninstalling nvidia-current fixes the resolution problem, but still no icons or menu to click on and start programs; just wallpaper.

Also, when everything was working and Ubuntu was booting up, I used to get a quick Nvidia logo flash on my screen just before the login screen appeared.  This no longer happens, even when nvidia-current is installed.

Help.

---

