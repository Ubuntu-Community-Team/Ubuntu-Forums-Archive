---
title: "X server in 18.04 keeps killing desktop"
date: 2018-08-29
forum: General Help
---

### Post by anewbie on 2018-08-29
Since I upgraded from 16.04.x to 18.04 whenever the monitor wakes up the sync with Xorg is 1080p instead of the previous 1440p causing it to kill the desktop. This problem did not exist in 16.04.
-
I thought maybe it was related to xwayland so i disabled xwayland
I have a 2500K (intel hd200?)
I see nothing in the logs to indicate what is happening.

---

### Post by anewbie on 2018-08-30
here is what i see in the logs but no clue why this is happening:
Aug 30 01:22:22 pc1 rtkit-daemon[3043]: Supervising 4 threads of 1 processes of 1 users.
Aug 30 01:22:22 pc1 rtkit-daemon[3043]: Supervising 4 threads of 1 processes of 2 users.
Aug 30 01:22:23 pc1 rtkit-daemon[3043]: message repeated 13 times: [ Supervising 4 threads of 1 processes of 2 users.]
Aug 30 01:22:30 pc1 systemd[1]: session-c5.scope: Killing process 29463 (lightdm) with signal SIGTERM.
Aug 30 01:22:30 pc1 systemd[1]: session-c5.scope: Killing process 29483 (lightdm-greeter) with signal SIGTERM.
Aug 30 01:22:30 pc1 systemd[1]: session-c5.scope: Killing process 29484 (unity-greeter) with signal SIGTERM.
Aug 30 01:22:30 pc1 systemd[1]: session-c5.scope: Killing process 29486 (at-spi-bus-laun) with signal SIGTERM.
Aug 30 01:22:30 pc1 systemd[1]: session-c5.scope: Killing process 29492 (dbus-daemon) with signal SIGTERM.
Aug 30 01:22:30 pc1 systemd[1]: session-c5.scope: Killing process 29494 (at-spi2-registr) with signal SIGTERM.
Aug 30 01:22:30 pc1 systemd[1]: session-c5.scope: Killing process 29521 (nm-applet) with signal SIGTERM.
Aug 30 01:22:30 pc1 systemd[1]: session-c5.scope: Killing process 29524 (unity-settings-) with signal SIGTERM.
Aug 30 01:22:30 pc1 systemd[1]: Stopping Session c5 of user lightdm.

---

### Post by anewbie on 2018-08-30
One more detail when the monitor comes back it is 1080p and not 1440p. The only way i can get it back to 1440p is to reboot.

---

### Post by anewbie on 2018-08-30
[ 15468.417] (WW) modeset(0): hotplug event: connector 62's link-state is BAD, t
ried resetting the current mode. You may be leftwith a black screen if this fail
s...

---

### Post by anewbie on 2018-08-30
This thread suggest the problem is with kernel 4.15.x; and downgrading to 4.14 will fix the problem. Is there an easy way to downgrade (I ubuntu packaging of zfs).
--
[https://bbs.archlinux.org/viewtopic.php?id=235027](https://bbs.archlinux.org/viewtopic.php?id=235027)

---

### Post by anewbie on 2018-09-11
I ended up fixing the issue by getting a cheap amd gpu. Seems kind of pia that to have this regression after 4+ years but whatever.

---

