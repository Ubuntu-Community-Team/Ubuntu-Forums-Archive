---
title: "Program menus come up empty"
date: 2012-10-26
forum: General Help
---

### Post by Fraoch on 2012-10-26
Occasionally my program menus will not display.  Instead I get a little "stub" but no menu.  See the screenshot.

It's being really persistent today, LibreOffice will display the menus fine when I have an empty document but as soon as I start modifying the document I lose my menus.

I've seen it in more applications than just LibreOffice, I believe it's related to Unity integrated menus.

Ubuntu 12.10 64-bit.

Any ideas?  Thanks!

---

### Post by dino99 on 2012-10-26
hm that issue has been fixed a few weeks back, but seems reappeared:

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1064962](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1064962)
[https://bugs.launchpad.net/ubuntu/quantal/+source/libreoffice/+bug/1044657](https://bugs.launchpad.net/ubuntu/quantal/+source/libreoffice/+bug/1044657)
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1069345](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1069345)

So thats not only with unity, and seems related to the latest global-menu changes.

---

### Post by Fraoch on 2012-10-30
Thanks, the first bug looks closest to what I'm experiencing.  I see a fix is in testing, hope it makes it to production because LibreOffice is more or less unusable in its present state.

Lately I've had it generate menus as expected but clicking on a menu item does nothing.

---

### Post by kanikilu on 2012-10-30
I just upgraded (12.04 -> 12.10) yesterday, and I noticed the same thing with LibreWriter within minutes of the reboot. Hope it gets fixed soon - none of the workarounds work for me. Thankfully I still have MS Office in my VM :-/

---

