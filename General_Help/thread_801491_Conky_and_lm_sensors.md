---
title: "Conky and lm_sensors"
date: 2008-05-20
forum: General Help
---

### Post by Gauvenator on 2008-05-20
Is there a way to get Conky to display readings from specific sensors?  Specifically, I would like to display info from this type of sensor:

```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +42.0°C  (crit = +85.0°C) 
```
(folding atm, that's why temps so high)

---

### Post by jjgomera on 2008-05-20
maybe any sensor conky varible it was fine, you can prove ${i2c temp} or ${acpitemp}
but if it dont work you can use some like:

${execi 20 sensors |grep "Core 0" | cut -d" " -f3}

---

### Post by Gauvenator on 2008-05-20
will that use a lot of processor tho?  I remember something about commands eating up resources with conky.

---

### Post by jjgomera on 2008-05-21
yeah, execi is the command eating up more resources in conky, but depend your computer that are more resources

but that is the **last option**, first you may prove the conky variables, you can prove ${i2c temp}

---

