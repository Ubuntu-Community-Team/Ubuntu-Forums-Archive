---
title: "Firefox crash taking sound with it"
date: 2007-04-08
forum: General Help
---

### Post by DiJEH on 2007-04-08
Could anyone tell me how I unblock the soundcard after firefox crashs and locks it up please?

Thank you.

---

### Post by jpeddicord on 2007-04-09
Try running this, either in the Alt+F2 window or in a terminal:
> killall esd
That command should reset all sound apps and free up the card.

Jacob

---

