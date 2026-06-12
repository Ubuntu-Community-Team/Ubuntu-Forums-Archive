---
title: "Taskbar Battery Icon Disappeared After Upgrade"
date: 2015-05-09
forum: General Help
---

### Post by b0ng0 on 2015-05-09
I recently booted up my netbook and did an upgrade to 15.04 from version 14 (or whatever the specific number for the previous major version is).

All went smoothly except that the battery status icon has gone from the task bar. I have tried add it back in, as there is a "Battery Monitor" applet, but it's just a very thin black and yellow bar - not the nice little battery icon which showed a "time remaining" estimate and so on.

I've also tried to check "Default Applications for LxSession" under preferences, then Autostart. There is something called Power Manager which is still ticked - so I'm now at a bit of a loss as to how to get this back??

---

### Post by Dennis N on 2015-05-09
It's likely we may be victims of this bug:

[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1446247](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1446247)

If you think you are, I suggest you indicate on Launchpad that the bug affects you:

After logging in (at upper right on page), there is a line (which is a link) that appears in the upper left, right after "Bug #1446247 reported by Pablo César Galdo Regueiro on 2015-04-20" which reads: "This bug affects 9 people. Does this bug affect you?". Click on it and you can register in a little dialog box that you are affected.

---

### Post by b0ng0 on 2015-05-09
Ah, that's a shame then. I suppose we'll just have to wait for the next version...

Edit: registered that I am affected on Launchpad, really hope it can be fixed in the next version, it was a slick applet.

---

