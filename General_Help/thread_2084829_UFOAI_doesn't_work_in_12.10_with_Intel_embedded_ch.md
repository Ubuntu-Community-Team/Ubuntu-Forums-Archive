---
title: "UFO:AI doesn't work in 12.10 with Intel embedded chipset"
date: 2012-11-16
forum: General Help
---

### Post by furtom on 2012-11-16
I've been doing some searching around and can't find a solution to this problem. It seems this [[COLOR="RoyalBlue"]problem[/COLOR]]("http://ufoai.org/forum/index.php?topic=7032") is common with the Q965 etc. embedded chipset.

The latest xserver-xorg-video-intel seems to break something. It was working in 12.04.

I checked the development repos, but this package is not updated.

Any advice would be appreciated.

Edit: Just to see what would happen, I tried forcing a roll back to xserver-xorg-video-intel to 2.2.17.0 (12.04 release). Unsurprisingly, this did not work. But that doesn't mean much since I did not roll back my entire xorg. :)

---

### Post by kostkon on 2012-11-16
You could try installing [libtxc-dxtn-s2tc0]("http://packages.ubuntu.com/quantal/libtxc-dxtn-s2tc0").

---

### Post by furtom on 2012-11-16
> **kostkon said:**
> You could try installing [libtxc-dxtn-s2tc0]("http://packages.ubuntu.com/quantal/libtxc-dxtn-s2tc0").

Hey, thanks for the suggestion. Unfortunately, this package is already installed.

---

