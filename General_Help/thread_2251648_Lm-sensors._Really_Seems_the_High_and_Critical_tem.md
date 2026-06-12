---
title: "Lm-sensors. Really? Seems the High and Critical temps are way high."
date: 2014-11-05
forum: General Help
---

### Post by mikodo on 2014-11-05
Like the title. Am I wrong?  I have an intel processor. Thanks.

```
mikodo@mikodo-GV465AA-ABA-a6245n:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +43.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +43.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +37.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +37.0°C  (high = +84.0°C, crit = +100.0°C)

f8000-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.36 V  
3VSB:         +3.36 V  
Vbat:         +3.23 V  
fan1:        1532 RPM
fan2:         983 RPM
fan3:           0 RPM  ALARM
fan4:           0 RPM
temp1:        +40.0°C  (high = +70.0°C, hyst = +60.0°C)
temp2:        +28.0°C  (high = +100.0°C, hyst = +85.0°C)
temp3:        +25.0°C  (high = +100.0°C, hyst = +85.0°C)


```

---

### Post by QIII on 2014-11-05
High = damage if it goes on.

Crit = get some popcorn and watch the pretty blue smoke.

---

### Post by sammiev on 2014-11-05
Much the same as mine. I unlocked my Bios and lowered my temps by 5c on fan startup and full speed. They do not seem to run any less or longer than they have.

---

### Post by sammiev on 2014-11-05
> **QIII said:**
> High = damage if it goes on.

Crit = get some popcorn and watch the pretty blue smoke.

Your too funny... :lolflag:

---

### Post by mikodo on 2014-11-05
> **sammiev said:**
> Much the same as mine. I unlocked my Bios and lowered my temps by 5c on fan startup and full speed. They do not seem to run any less or longer than they have.
Thanks.

Maybe I'll do the same. Can't hurt and sometime, it may help.

---

### Post by mikodo on 2014-11-05
> **QIII said:**
> High = damage if it goes on.

Crit = get some popcorn and watch the pretty blue smoke.
Thanks.

I may be wrong here, but it seems I read once, you stated that for an Intel CPU, 70C, was *damage* time.

If, I am wrong/or misquoted you, I apologize .

I just think, they should be a little lower numbers, for the "unsuspecting".

---

### Post by Impavidus on 2014-11-05
I once downloaded the pdf documentation for my i5 processor from Intel. They say it's supposed to be fine up to 105ºC. IIRC it should protect itself by reducing voltage and frequency when hitting 100ºC. I've never let it get hotter than 72ºC. So the 84ºC could be realistic. Still, there is the risk of burning if you touch the box...

---

### Post by mikodo on 2014-11-05
> **Impavidus said:**
> I once downloaded the pdf documentation for my i5 processor from Intel. They say it's supposed to be fine up to 105ºC. IIRC it should protect itself by reducing voltage and frequency when hitting 100ºC. I've never let it get hotter than 72ºC. So the 84ºC could be realistic. Still, there is the risk of burning if you touch the box...
Thanks.

---

### Post by QIII on 2014-11-05
> **mikodo said:**
> Thanks.

I may be wrong here, but it seems I read once, you stated that for an Intel CPU, 70C, was *damage* time.

If, I am wrong/or misquoted you, I apologize .

I just think, they should be a little lower numbers, for the "unsuspecting".

No misquote.  With current on-die graphics they run hotter and are designed for the heat.

---

### Post by sammiev on 2014-11-05
> **Impavidus said:**
> I once downloaded the pdf documentation for my i5 processor from Intel. They say it's supposed to be fine up to 105ºC. IIRC it should protect itself by reducing voltage and frequency when hitting 100ºC. I've never let it get hotter than 72ºC. So the 84ºC could be realistic. Still, there is the risk of burning if you touch the box...

+1 I noticed on mine it may jump quickly to 69c and after the fan increases in speed it drops to the high 40s in seconds but seems to stay about 50 to 55c at most times. Under very low loads it will stay at about 49c with no fan running.

---

