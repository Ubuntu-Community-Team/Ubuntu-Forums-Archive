---
title: "Either X or Nautilus isn't quitting properly on shutdown/restart"
date: 2008-05-10
forum: General Help
---

### Post by rainwalker on 2008-05-10
When I go to System > Quit and choose either Shut Down or Restart, the process will hang at shutting down either Nautilus or X (I'm not sure which). My panels, windows, screenlets, etc will disappear but my wallpaper will still be displayed. The shut down/restart process won't continue until I do Control + Alt + Backspace to kill X, then it resumes like it should (showing the usplash progress bar emptying). The weird thing is, Hibernate works fine (in terms of being able to power off). 
This only happens when I try to shut down/restart via the Quit menu; I can shut down successfully if I use ```
sudo shutdown -h now
```
How can I find out if it's X or Nautilus causing the problem (or something else, for that matter)? Even better, does anyone have any ideas as to what's going wrong?

---

### Post by rainwalker on 2008-05-11
Am I really the only one who is having this problem?

---

### Post by ghost_ryder35 on 2008-05-11
switch to a vty and issue sudo halt, it should display the steps of the shutdown process and then you can see where it is hanging (right?)  might have to get rid of the quiet in /boot/grub/menu.lst not positive though

---

### Post by rainwalker on 2008-05-11
What is a vty?

---

### Post by ghost_ryder35 on 2008-05-11
a virtual terminal (probally should of said that, my english no good ;))
ctrl + alt + f1 through f6

---

### Post by rainwalker on 2008-05-11
It didn't tell me anything useful, or if it did things went by too fast for me to see it. Is there a way I can log the shut down process?

---

### Post by ghost_ryder35 on 2008-05-11
idk if this will work but how bout
```

sudo halt > /home/rainwalker/Desktop/shutdownlog.txt

```

---

### Post by rainwalker on 2008-05-11
Hmm...well that created the file, but it's empty; there's nothing in it :?
The shutdown process does take a little while at "Stopping the GNOME display manager", but it always gets an "OK" and the system shuts down. Via System > Quit, I've waited a good 2 or 3 minutes and it never shuts down.

---

### Post by TheExplorer on 2008-05-11
Strange. Seems like you've tweaked your system a little otherwise it shouldn't be so. First look into your Preferences - Sessions (the gnome-power-manager should be ON). And tell us some more info upon your system specs (hardware, video card/video driver) and what have done to your system configuration recently, please.

---

### Post by rainwalker on 2008-05-11
> **TheExplorer said:**
> Strange. Seems like you've tweaked your system a little otherwise it shouldn't be so. First look into your Preferences - Sessions (the gnome-power-manager should be ON). And tell us some more info upon your system specs (hardware, video card/video driver) and what have done to your system configuration recently, please.

This is what I have listed under Startup Programs:

Beagle Search Daemon - ON
Beagle Search Tool - ON
Bluetooth Manager - OFF
Check for new hardware drivers - ON
Evolution Alarm Notifier - OFF
Network Manager - ON
PidginScreenlet - ON
Power Manager - ON
Print Queue Applet - ON
PulseAudio Session Management - ON
Screenlets Daemon - ON
Tracker - OFF
Tracker Applet - OFF
Update Notifier - ON
User folders update - ON
Visual Assistance - ON
Volume Manager - ON
WaterMarkScreenlet - ON

Attached is a screenshot of what I currently have running; nothing special.

I'm running a fresh install of Hardy (official release, not a beta or the RC) on a Dell Inspiron 8600 with an ATI Technologies Inc RV350 [Mobility Radeon 9600 M10], 1gig of ram, and Compiz running (with "SKIP_CHECKS=yes"). Everything worked fine in Gutsy (fresh install), including Compiz (I didn't need to force it).
The most customization I've done is change some Compiz settings and install some programs (Amarok, Screenlets, etc.), nothing like editing my Xorg.conf or patching the kernel.

---

### Post by rainwalker on 2008-05-17
This is disappointing.

---

### Post by Ozzin on 2008-05-18
Have you installed Keytouch? This seems to cause problems for some people.

Check out [https://bugs.launchpad.net/ubuntu/+bug/186713](https://bugs.launchpad.net/ubuntu/+bug/186713)

---

### Post by rainwalker on 2008-05-18
> **Ozzin said:**
> Have you installed Keytouch? This seems to cause problems for some people.

Check out [https://bugs.launchpad.net/ubuntu/+bug/186713](https://bugs.launchpad.net/ubuntu/+bug/186713)

As a matter of fact...yes!
I really hope that's not it, I love KeyTouch! It's the only thing I've found that can get my multimedia keys to work

I'll try uninstalling it

---

### Post by rainwalker on 2008-05-18
Well it looks like it is KeyTouch that's messing things up...that's a shame :(

---

