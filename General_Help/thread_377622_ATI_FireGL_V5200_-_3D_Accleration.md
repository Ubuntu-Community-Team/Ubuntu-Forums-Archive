---
title: "ATI FireGL V5200 - 3D Accleration"
date: 2007-03-06
forum: General Help
---

### Post by Voltaic Shock on 2007-03-06
I have been trying to get Beryl to work but I can't figure out how to enable 3D Accleration on my ATI Mobility FireGL V5200 (Laptop - nw8440).  I have installed the drivers from ATI (not sure if I should have done that.)

My xorg.conf has two devices section, but when I take one out I can't get into any DE and have to replace it with my backup.

Any suggestions on what to do?

Voltaic Shock

---

### Post by mcduck on 2007-03-06
It should work after running these two commands:

```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
```

---

### Post by Voltaic Shock on 2007-03-06
> **mcduck said:**
> It should work after running these two commands:

```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
```

Should I uninstall what I downloaded from the ATI site first?

I also looked in Synaptic manager and I already have the orog-driver-fglrx installed.  Did installing the one from ATI overwrite this one?

I have ran the "sudo aticonfig --initial"

Voltaic Shock

---

### Post by TonyLechner on 2008-01-29
I also seem to be having trouble with this, if anyone happens to have any insight...

---

