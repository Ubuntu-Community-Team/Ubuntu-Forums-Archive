---
title: "gutsy + rt73 + serialmonkey"
date: 2007-10-19
forum: General Help
---

### Post by sefs on 2007-10-19
BEAKING NEWS!!!!!

I am having a problem with my wireless since upgrading to gutsy.

The serial monkey drivers I use compile just fine.

The problem is when I stick my USB wireless into the usb port the computer freezes and the caps lock and scroll lock lights on the keyboard blinks.

If I reboot it sticks in the graphical boot screen and the same above lights just blink.

What should I do.

Thanks.

---

### Post by defconoii on 2007-10-24
i can confirm this issue as well, it seems the wpa portion of the serialmonkey driver crashes the system, i have regressed back to wep and use strict mac control's, i would suggest for you to do the same because the problem does not seem to be fixed and nobody seems to be working on it yet...

---

