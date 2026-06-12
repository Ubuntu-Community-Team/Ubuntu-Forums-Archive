---
title: "How do I put my WiFi card in monitor mode?"
date: 2007-05-23
forum: General Help
---

### Post by loathsome on 2007-05-23
.. topic ^

I've got an Intel 3495 Wireless card. Thanks!

---

### Post by seamless on 2007-05-23
If the driver supports it,
```
iwconfig eth0 mode Monitor
```
If you get errors then your card cannot be put into monitor mode due to driver constraints.

---

### Post by loathsome on 2007-05-23
I'll try later, thanks!

But what if it doesn't work, are there no other options? And how can I verify if it's monitor mode?

---

### Post by TheodoreWard on 2007-05-23
> **loathsome said:**
> I'll try later, thanks!

But what if it doesn't work, are there no other options? And how can I verify if it's monitor mode?

iwconfig by itself will tell you what mode the card is in. I'm not aware of any GUI programs that do the same thing. You might have to disable your network-manager icon to keep it from resetting your wireless settings.

---

