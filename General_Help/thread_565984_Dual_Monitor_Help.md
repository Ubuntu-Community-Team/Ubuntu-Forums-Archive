---
title: "Dual Monitor Help"
date: 2007-10-02
forum: General Help
---

### Post by tipsqueal on 2007-10-02
I have an XFX 7600 GT, one Dell 17" LCD monitor (1280x1024) and one Viewsonic 22" widescreen monitor (1680x1050), and I've been wanting to set them up for dual monitors. Today I finally got a second DVI cable so now I can actually use the spare Dell monitor I have. I plugged it in and set it up using nvidia-settings. I had it set up for Twinview and configured it to have the dell to the left of my Viewsonic monitor. 

It all worked great until I restarted X and/or logged out and then back in. If I did either of these, when I logged back in it would set the 22" monitor at some random low resolution. Once it set it at 640x480, then 800x600, then 1152x768, then some weird resolution that ended in 964. After every login I reset the resolutions to the correct ones then logged out to see what happened. I eventually got too frustrated and disabled the Dell monitor.

After I disabled the Dell monitor I found out my mouse (Logitech G5) is no longer working the way it used to. For some reason the 4th mouse button is now disabled. It used to be set up for copy/paste and to open a new tab in Firefox, and it was set up like this automatically.

Anyways I was wondering if anyone could help solve either of those issues or at least tell me why any of this has happened. Any help is appreciated.

Thanks, 
Tipsqueal.

---

### Post by bodhi.zazen on 2007-10-03
Your mouse - I have no idea, hardware failure ?

Your monitors, run nvidia settings as root and save to xorg.conf (save the settings)

```
gksu nvidia-settings
```

If you run as a user you can not save your changes (because /etc/X11/xorg.conf is owned as root)

---

### Post by tipsqueal on 2007-10-03
The mouse issue is not a hardware failure. I've read into it and people that were doing the Dual Monitor setups were also having issues with their mouse. My mouse isn't freezing like theirs, I just don't have the full functionality. My guess is it's because Nvidia setup overwrote my xorg. Also I was running nividia-settings as root user, it saved the twinview options, just not the proper resolutions. I've been using Ubuntu full time now for over a year so I am pretty well versed in the ways of root user and whatnot.

Does anyone else know what the issue may be?

Thanks, 
Tipsqueal.

---

