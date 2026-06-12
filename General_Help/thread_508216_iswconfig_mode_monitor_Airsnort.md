---
title: "iswconfig mode monitor Airsnort"
date: 2007-07-23
forum: General Help
---

### Post by newbiefromwindows on 2007-07-23
When I try and use airsnort it tells me that "You must place your card into monitor mode manually. " When I try and do that here is what happens

: iwconfig eth1 mode monitor

Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Operation not permitted.

Anybody have any ideas how to fix this?

---

### Post by sr20ve on 2007-07-24
Try prefixing that command with sudo.

---

