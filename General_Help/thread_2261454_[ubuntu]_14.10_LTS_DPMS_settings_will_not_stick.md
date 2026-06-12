---
title: "[ubuntu] 14.10 LTS DPMS settings will not stick"
date: 2015-01-19
forum: General Help
---

### Post by pmatil on 2015-01-19
So, I recently installed 14.10 LTS into my Dell D620 laptop. Immediately I switched the desktop to gnome classic. Didn't like the fact that it kept locking my screen when I just wanted it to blank it (screen saver) and then turn the screen off so I disabled gnome-screensaver and switched to xscreensaver. In xscreensaver settings I have set "quick power-off in blank only mode".

The screensaver works fine (blank screen after 10 minutes) but the problem is that the screen does not suspend, standby or turn off. Never. The power settings say "turn off the screen after 30 minutes" in gnome power management.

I googled some threads on this and found that using xset I can set these parameters. Turned out that DPMS was disabled completely. So I set the parameters:

xset +dpms
xset 600 7200 14400

It worked once and after checking the settings wth xset -q DPMS is disabled again and the timeouts are 7200 7200 28320.

So the question is, what application is really controlling these timeouts? I'm using cinnamon desktop. Some versions:

cinnamon 2.2.16
kernel 3.16.10-29-generic
graphics Intel 945GM/GMS, 943/940GML

---

