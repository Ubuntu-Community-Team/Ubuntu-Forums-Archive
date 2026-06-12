---
title: "disabling AMD GPU, boot pauses until return"
date: 2013-03-02
forum: General Help
---

### Post by aeronutt on 2013-03-02
Over many versions, I've used the following edits to successfully disable the AMD GPU:

Add the following to /etc/rc.local
```
modprobe radeon
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

```

And, add the following to /etc/modprobe.d/blacklist.conf
```
blacklist radeon
```

In my 12.04 gnome-shell remix, booting stops until I hit 'return', then it seems to boot normally to log in screen. It also does the same thing randomly in my ubuntu 12.04 load.

Ideas?

---

### Post by aeronutt on 2013-03-03
Any ideas?  Is there another way to disable the AMD graphics h/w other than the above and other than installing AMD Catalyst (that has problems too). With AMD enabled, battery usage is about 2.5x compared to disabled. My i3 graphics handles my needs just fine.

UPDATE: I've found the culprit to be the 'modprobe radeon' line in rc.local. But it's needed to reduce battery power.  Thoughts?

---

### Post by aeronutt on 2013-03-05
I just tried Linux Mint w/Cinnamon, and none of these problems show up (hanging on boot or shutdown depending on how I turn off AMD GPU). So, I guess I'll head that way.

---

