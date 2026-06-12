---
title: "Cannot boot into Ubuntu Gutsy after update"
date: 2007-12-04
forum: General Help
---

### Post by Planets on 2007-12-04
Hello,

I recently installed Gutsy Gibbon and installed all available updates. Now, I cannot boot into the system. I select it from the boot loader, and the screen goes black and stays that way. The monitor doesn't seem to lose signal. Any help out would be appreciated. Thanks.

---

### Post by abcuser on 2007-12-04
Hi,
have you tried rescue recovery mode?
Abcuser

---

### Post by Clayton South on 2007-12-04
I am now experiencing the same problem....booting into safe mode doesnt seem to work either....it cant load xserver....please help.

-Thanks!

---

### Post by mike4ubuntu on 2007-12-06
I have the same problem now.  However, I also enabled the restricted nvidia driver, which forced a restart.  I suspect it's the restricted driver which could be incompatible to my ASRock mobo with integrated nvidia graphics.

What I plan to do tonight is boot with Live CD, and copy the /etc/X11/xorg.conf from live mount to installed mount.  Not sure what else to do at this point.

I already tried disabling the restricted driver in /etc/default/linux-restricted-modules-common and that didn't help.

---

