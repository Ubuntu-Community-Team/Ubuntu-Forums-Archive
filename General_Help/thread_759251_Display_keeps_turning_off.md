---
title: "Display keeps turning off"
date: 2008-04-18
forum: General Help
---

### Post by hashi856 on 2008-04-18
My monitor keeps turning off, even though I set the display to never go to sleep. Yes I have it off in both screen saver and power managment

---

### Post by ramjet_1953 on 2008-04-19
Have you checked the power saving features in your BIOS?

Regards,
Roger :cool:

---

### Post by pointone on 2008-04-19
It might also be built into the monitor.

Alternatively, try: 

```
setterm -blank 0 -powersave off -powerdown 0
```

---

### Post by hashi856 on 2008-04-19
> **pointone said:**
> It might also be built into the monitor.

Alternatively, try: 

```
setterm -blank 0 -powersave off -powerdown 0
```

Tried it and got this message

stephen@stephen-desktop:~$ setterm -blank 0 -powersave off -powerdown 0
cannot (un)set powersave mode
[14;0]stephen@stephen-desktop:~$

---

### Post by pointone on 2008-04-19
Try using sudo.

---

