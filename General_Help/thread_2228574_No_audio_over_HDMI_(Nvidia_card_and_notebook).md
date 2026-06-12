---
title: "No audio over HDMI (Nvidia card and notebook)"
date: 2014-06-08
forum: General Help
---

### Post by kenny14 on 2014-06-08
Hi guys, I've been troubleshooting for days and I couldn't find any solution. Most of the solutions from Google are to add a line to GRUB or update alsa. But then mine is the latest 14.04 ubuntu and the alsa version is

root@ducky-N55SF:~# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version k3.13.0-29-generic.


The nvidia sound seems totally dissapear when I check with

root@ducky-N55SF:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


My HDMI cable manage to project to my monitor but not the sound. I am also currently using the Nvidia binary driver.

---

### Post by kenny14 on 2014-06-15
Hmm...still no solution? I guess that's something in the current Ubuntu?

More reference here: [http://ubuntuforums.org/showthread.php?t=2216196&page=3&highlight=HDMI](http://ubuntuforums.org/showthread.php?t=2216196&page=3&highlight=HDMI)

---

