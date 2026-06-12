---
title: "How to force full battery charge"
date: 2013-06-21
forum: General Help
---

### Post by Brian Sorensen on 2013-06-21
I have a laptop which is plugged in to the power outlet 90% of the time. It is a Lenovo X1 Carbon, so the battery cannot be replaced (easily at least). I have therefore changed the battery power management to what Lenovo recommends, that is, start charging below 75% and stop at 80%. This works like a charm and the battery is rarely used at all. However, since I sometimes use it unplugged as well (and I know when in advance) I would really like to be able to force the laptop to charge to 100% instead of 80%. Is there any way that I can override the general power management in these somewhat rare cases, without manually changing power management (in /etc/default/tlp)?

---

### Post by linrunner on 2013-06-21
Hi!

```
sudo tlp fullcharge
```
is what you're looking for. 

See the manual too: [http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html#commands](http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html#commands)

---

### Post by Brian Sorensen on 2013-06-23
Thanks!

That was exactly what I'm looking for.

---

