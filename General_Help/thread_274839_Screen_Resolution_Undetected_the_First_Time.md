---
title: "Screen Resolution Undetected the First Time"
date: 2006-10-10
forum: General Help
---

### Post by aysiu on 2006-10-10
Here's something weird.

Ubuntu is pretty damn good at detecting my hardware. Sound works just fine. Internet works just fine. Even my eight-in-one media card reader works just fine.

When I installed Dapper (months ago) and when I installed Edgy (just last night), Ubuntu did not pick up my monitor's native screen resolution (it gives me 800x600 instead of 1280x1024).

That's not weird, right? Ubuntu can't pick up *everything* after all.

The weird part is that if I do a ```
sudo dpkg-reconfigure xserver-xorg
``` Ubuntu will *then* autodetect my monitor's appropriate VertRefresh and HorizSync values and then add them to /etc/X11/xorg.conf, giving me the proper screen resolution.

This happened for both Dapper and Edgy, and it confuses me. I understand if Ubuntu plain doesn't recognize my monitor, but if it recognizes it after a *sudo dpkg-reconfigure xserver-xorg*, why wouldn't it recognize it before?

Any ideas? Is this a bug I should report?

---

### Post by aysiu on 2006-10-15
Bump

---

