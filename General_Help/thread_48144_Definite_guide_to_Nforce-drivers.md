---
title: "Definite guide to Nforce-drivers?"
date: 2005-07-11
forum: General Help
---

### Post by Morimando on 2005-07-11
Is there a definite HowTo for installing the Nvidia-Nforce drivers?
I got as far as installing them and inserting the modules in /etc/modules.
Now i need to find out where to change the 
```
alias sound-slot-0 nvsound // alias snd-card-0 nvsound
``` and the ```
alias eth0 nvnet 
```
as well as removing the amixer from autostart, since it beeps like crazy (coz missing the intel8x0 module)... 
anyone know how to do it correctly? would be really nice.

---

### Post by fourhead on 2005-11-04
I'd like to know the same. nvnet works fine for me, but how can I make it load automatically at boot? I've put it into /etc/modules, and it loads at boot, but eth0 still uses the old forcedeth driver.


Tom

---

