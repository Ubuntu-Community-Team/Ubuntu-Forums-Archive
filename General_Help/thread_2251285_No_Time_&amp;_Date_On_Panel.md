---
title: "No Time &amp; Date On Panel"
date: 2014-11-03
forum: General Help
---

### Post by echotech2 on 2014-11-03
I upgraded on-line from 14.04.x to 14.10 (both using Unity).  When I re-booted the Time & Date weren't showing on the top panel. Network, Mail, Sound, etc. are showing and working.  Going to System Settings/Time & Date the first tab shows correct time zone and set time automatically from Internet.  On the clock tab everything is greyed out.  What am I missing?

---

### Post by philinux on 2014-11-03
Try this.

```
dconf reset -f /com/canonical/indicator/datetime/
```
Then..

```
setsid unity
```

---

### Post by echotech2 on 2014-11-03
Thanks, works just fine, but you didn't tell me the screen was going to jump all over the place with that second command, lol.

---

### Post by philinux on 2014-11-03
:p
Surprise that eh, yes it does bounce about lol.

---

