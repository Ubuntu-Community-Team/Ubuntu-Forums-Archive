---
title: "Should I worry about the &quot;HD Wear &amp; Tear&quot; thing?"
date: 2007-10-26
forum: General Help
---

### Post by DR583V3 on 2007-10-26
I've read that laptop mode is disabled by default and I haven't heard my laptop's HD make any abnormal noises and after installing Gusty, my laptop is cooler.

I'd like to sleep comfortably at night.

---

### Post by swisscow on 2007-10-26
What is this laptop mode?

---

### Post by arkara on 2007-10-29
i don't know if you should worry but to fix this give

```
sudo hdparm -B 255 /dev/sda
```

and you should be fine. but battery life on your laptop will be reduced

---

### Post by Cochise on 2007-10-29
does this affect desktop pc&#347; as well or just laptop?

---

