---
title: "INTEL Braswell HDMI issue : Display blank after power cycling TV (DDR DVFS Issue)"
date: 2015-12-19
forum: General Help
---

### Post by nroclaed on 2015-12-19
I am running a fresh install of Ubuntu-15.10-server-amd64 with xorg and xfce4 on a Braswell motherboard (ASRock N3700-ITX).  I use HDMI to connect to my TV.  When I either power cycle the TV or switch modes from PC to TV, my PC screen goes blank and I must reboot (using a virtual console).  There was a previous post of this issue in a "solved" Kubuntu post ([http://ubuntuforums.org/showthread.php?t=2305079&highlight=braswell](http://ubuntuforums.org/showthread.php?t=2305079&highlight=braswell)) but the solution was not detailed.  Dmesg|tail reports: "[drm:valleyview_update_wm [i915]] *ERROR* timed out waiting for Punit DDR DVFS request".

---

