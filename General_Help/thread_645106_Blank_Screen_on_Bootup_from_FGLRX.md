---
title: "Blank Screen on Bootup from FGLRX"
date: 2007-12-19
forum: General Help
---

### Post by kingace on 2007-12-19
Hi all,

I just installed Gutsy Gibbon with no problems, but when i booted it up, it started up normally, but instead of usplash coming up, all I saw was a blank screen. I let this go for about 20 minutes and then restarted, and booted into recovery mode. I did a reconfigure of xserver-xorg, and set the driver to ATI, and this time there was still no usplash, but the log-in screen did eventually come up. I ran all the updates and enabled the ATI restricted drivers (FGLRX), and when I restarted the blank screen had come back. One thing to note is that there is hard drive activity despite the black screen for around 3-5 minutes and then it just hangs. When I reverted to the driver "ati" it worked again, but I need FGLRX to work.

Any thoughts?

Thanks In Advanced

---

### Post by approaching on 2007-12-19
what card are you running? make and model please, mine is a Sapphire x1950. i am not exactly sure if that will help out, but it may make a search on google more specific. (that and not all ati need that fglrx driver, only specific ones)

---

### Post by kingace on 2007-12-19
Ati Radeon x800

Update: I found a fix for usplash online and performed it; now usplash comes up for about 2 or 3 seconds and then the blank screen reappears and it freezes.

---

### Post by RomeReactor on 2007-12-19
Hi. I'm not certain about this (don't have an ATI card) but I think you need to install **xserver-xgl**, at least until the new ATI drivers reach the repositories.
```
sudo apt-get install xserver-xgl
```

---

