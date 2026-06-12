---
title: "can't get refresh rate working"
date: 2006-09-23
forum: General Help
---

### Post by iand675@gmail.com on 2006-09-23
I just got a GeForce 7600 card as well as some other new hardware. I've done a fresh install as well as installed the nvidia proprietary drivers, but I can't seem to get my monitor to use any refresh rates above 60 for anything above 1024x768. I'm trying to get my monitor to have a refresh rate of 75 at 1600x1200. AI've tried to do dpkg-reconfigure xeserver-xorg, but even when I set the highest monitor refresh rate to be 75hz at 1600x1200 during the config, I still can't change the refresh rate. :( Any suggestions?

---

### Post by orb9220 on 2006-09-23
During the setup did you autodetect monitor or manual and enter the freqs yourself. You need to get the info for monitor and see what the horiz and vert frequencies are and enter those during manual setup of monitor.

Warning do not get them mixed up. And backup your xorg.conf file so you can restore it if something goes wrong.

---

