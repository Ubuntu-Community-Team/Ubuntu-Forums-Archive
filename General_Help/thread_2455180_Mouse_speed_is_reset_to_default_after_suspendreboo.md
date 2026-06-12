---
title: "Mouse speed is reset to default after suspend/reboot"
date: 2020-12-14
forum: General Help
---

### Post by EpsilonDelta on 2020-12-14
Ever since I upgraded from 18.04 to 20.04 my mouse speed keeps resetting every time I log in.
When I go to settings after logging in, the mouse speed slider is still how I set it before, but the actual mouse speed is the default mouse speed.
To make the mouse speed setting take effect, I have to move the slider a little in either direction.
I had mouse issues in the past on 18.04 and may have changed something then that caused this bug after I upgraded.

Is it possible to automatically apply mouse speed setting on login so I don't have to go into settings every time?

---

### Post by The EYE13 on 2020-12-19
Same here with 20.04 but only after a suspend.

---

### Post by albertsko on 2020-12-27
I have been running 20.04 for months and this just started happening a few days ago. Not sure but I think it started right after the last time I ran Software Updater..

---

### Post by albertsko on 2021-01-13
For anyone else having this problem, after tons of searching I finally found that it seems like it is getting fixed:

[https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1899206](https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1899206)
[https://gitlab.gnome.org/GNOME/mutter/-/issues/1505](https://gitlab.gnome.org/GNOME/mutter/-/issues/1505)

In the process I came across several suggested workarounds using xset or rmmod/modprobe but nothing that seems to work for me. Did anyone else come up with something?

Edit:
Actually, I finally read to the end of the Launchpad issue and it seems the fix actually made it into the updates just yesterday! I never noticed the issue was also triggered by unplugging my USB receiver, but I verified that it no longer happens after a 
```
apt-get update && apt-get upgrade
```
And a reboot. I was not able to reproduce the issue every time with suspend even before the update but hopefully it will no longer happen after suspend either!

---

