---
title: "Flaky wireless configuration???"
date: 2007-08-02
forum: General Help
---

### Post by cisforcojo on 2007-08-02
I've been having really flaky wireless service (it had been perfect before).

Sometimes my wireless just simply will not work, I'll check the network settings and sometimes my 'Wired connection' will be on again. This is only sometimes. While my wireless is being flaky, sometimes it will work and be really fast but only for a short time before it's off again. Is my computer somehow switching between LAN and wireless? I SOMETIMES use LAN and know that if I have both selected under System->Admin->Network then my internet will be unreliable (as it is now).

Any ideas?

---

### Post by HermanAB on 2007-08-02
Read up on iwconfig:
$ man iwconfig

If your signal strength is bad then WiFi will be unreliable.  If you and all your neighbours are using the same channels, then it will also cause problems.  Sometimes however, the WiFi module in your PC simply won't work properly with your access point and you have to change the one or the other.

Cheers,

Herman

---

