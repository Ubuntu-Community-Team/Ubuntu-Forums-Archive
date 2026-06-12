---
title: "System freezes after a few hours idle"
date: 2007-05-04
forum: General Help
---

### Post by canadianwriterman on 2007-05-04
With the final Feisty, I bit the bullet and let Feisty install over my entire HD, overwriting the beta and XP. Since then, the system will freeze if left idle for a few hours. Here are some factors:

[LIST]
[*]In Festy, the freeze kills the monitor completely, but the CPU is still running.
[*]As a comparison, I installed Edgy as dual boot. What happens to Edgy is that the monitor stays on, but the desktop is frozen after a few hours.
[*]In both cases, the keyboard is dead and the only solution is a hard reboot.
[*]I have set power management choices to "never," although this is a desktop, not a laptop.
[*]I have tried disabling the screen saver and just turning the monitor off.
[*]I have tried disabling gnome-power-manager in the sessions menu.
[*]This problem never occured when Ubuntu was dual-booted with XP, it has started when Ubuntu became the only OS on the system.
[/LIST]

Is there something in the system logs that I should be looking for? I can see in the logs the time that the system stopped responding, but there doesn't look to me to be anything unusual happening at that time... but I'm not much of a technical expert. Advice will be appreciated.

---

### Post by phidia on 2007-05-04
Not sure how much help this will be but I would try disabling the propritary video driver. e.g edit xorg.conf to run the open source driver "nv" and then see if it still freezes. At least that will eliminate the video as the culprit.

---

### Post by canadianwriterman on 2007-05-04
I'll try that phidia. I've had to install the Nvidia drivers to eliminate weirdness when I am in certain programs. For example, in Frostwrite, the screen writes very slowly without the prop driver. However, it's funny that I ran for six months fine with the Feisty beta with the Nvidia driver. This problem has only come up when I wiped Windows from my system and went with a pure Ubuntu PC. Can't help but think there's a connection between this issue and not having Windows.

---

### Post by canadianwriterman on 2007-05-06
See thread: [http://ubuntuforums.org/showthread.php?p=2605462#post2605462]("http://ubuntuforums.org/showthread.php?p=2605462#post2605462")

---

