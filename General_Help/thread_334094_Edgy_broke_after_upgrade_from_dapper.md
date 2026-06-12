---
title: "Edgy broke after upgrade from dapper"
date: 2007-01-08
forum: General Help
---

### Post by whee on 2007-01-08
I installed Dapper on my brothers computer and all seemed well.
I thought i'd upgrade to edgy and all seemed ok except for Nautilus which kept on crashing on bootup.
So after reading the forums i decided to upgrade nautilus via synaptic.
So i did that and it required a reboot, so i rebooted, but now X won't even start.
And there is only a garbly arcane looking error message which doesn't really say anything.
So my question is this.
Is there a possibility to fix/repair this by reinstalling edgy from a cd or by somehow reverting back to Dapper?
Repairing Ubuntu without a complete disk reformat would be preferred, so that i can keep things which were already installed on Dapper.

---

### Post by floke on 2007-01-08
Can you boot in failsafe terminal mode?
If so, you could try:

sudo dpkg-reconfigure -phigh xserver-xorg

This will allow you to reset X

Hope it helps

---

### Post by whee on 2007-01-08
I tried something similar.
I made some progress but everything isn't fixed yet, see here: [http://ubuntuforums.org/showthread.php?p=1985229#post1985229](http://ubuntuforums.org/showthread.php?p=1985229#post1985229)

---

### Post by taurus on 2007-01-08
Can you please not double post?

---

