---
title: "cpu temp"
date: 2007-01-21
forum: General Help
---

### Post by atlfalcons866 on 2007-01-21
is there a program like speedfan from windows xp to let me see the temperature of my processor

---

### Post by teaker1s on 2007-01-21
lmsensors

---

### Post by atlfalcons866 on 2007-01-21
where can i get that?

---

### Post by shane634 on 2007-01-21
It is in the repos use Synaptic ( System--> Administration-->Synaptic ). You may also wish to get Gkrellem from Applications-->Add/Remove it works well with lmsensors.

---

### Post by atlfalcons866 on 2007-01-21
is it called gdesklets data?

---

### Post by atlfalcons866 on 2007-01-21
i ment this picture

---

### Post by shane634 on 2007-01-21
Nope open Synaptic like above and click search then put in lm-sensors. Mark it for installation by right clicking it. Then get Gkrellem as stated above to put it on the desktop in a very cool fashion.

---

### Post by atlfalcons866 on 2007-01-21
i have them installed how do i run it?

---

### Post by shane634 on 2007-01-21
Get Gkrellm as suggested. Then run from a terminal 

```
sudo sensors-detect
```

  Then reboot and reopen Gkrellm and set it to show all the temps, voltages, and fan speeds ya want.

---

### Post by dexter on 2007-01-21
> **atlfalcons866 said:**
> i have them installed how do i run it?

type sensors in a terminal window

---

