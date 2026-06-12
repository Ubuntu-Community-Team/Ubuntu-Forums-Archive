---
title: "Ubuntu 13.10 Keyboard reverts to U.S. on reboot"
date: 2013-11-09
forum: General Help
---

### Post by siabost on 2013-11-09
Hi,

On doing a fresh install of Ubuntu 13.10 64bit on my Sony laptop I find that the keyboard reverts to US from my chosen UK option every time I reboot.
As a (rather unsatisfactory) workaround I've installed two UK keyboard layouts and switch between the two via the System Tray Switcher icon immediately on boot up.

How do I fix this permanently? - I can't offer this version of Ubuntu to non-techies until this bug is sorted.

I also get the warnings below as Ubuntu is booting up - I don't know if this is relevant to my keyboard issue, though.

Any help appreciated. Thanks.

[ATTACH=CONFIG]247712[/ATTACH]

---

### Post by efflandt on 2013-11-09
See what is in /etc/default/keyboard and if **XKBLAYOUT="us"**, change that to **"gb"** (use sudo prefix for your terminal editor or gksu gedit), and read the file listed in the first line.

"man xkeyboard-config" shows the codes for keyboard model and layout.

I only have 13.10 on a new laptop, but I saw similar warnings too, so that is likely unrelated.

---

### Post by siabost on 2013-11-10
Thanks efflandt, but I think events have overtaken us ... for the better!

A software update notification happened to come in last which I installed and this morning the keyboard issue seems to be fixed.
XKBLAYOUT appears to be correct & the boot screen error messages have also vanished - although, as you say, that could've been a different bug.

Many thanks :)

---

