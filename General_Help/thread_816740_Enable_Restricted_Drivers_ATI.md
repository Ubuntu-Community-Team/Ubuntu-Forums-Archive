---
title: "Enable Restricted Drivers ATI"
date: 2008-06-03
forum: General Help
---

### Post by grogger13 on 2008-06-03
I have an ati x1400 with ubuntu 8.04 installed.  I was having problems with the graphics and i followed a tutorial that had me add some line to a text file possibly the xorg.conf( im not sure becuase i can't remember).  What it did was make sure the drivers from the restricted manager won't be in use even though there still enabled.  I want to reverse this but am not sure what i added, does any body sound like they know what tutorial this is or how to reverse it

---

### Post by Lord Xeb on 2008-06-03
go to synaptic and tpye in: restricted drivers manager

then open the manager and install the drivers for ATI

---

### Post by jocko on 2008-06-03
From what you describe, I think this is what you want:```
sudo gedit /etc/default/linux-restricted-modules-common
```Change it from:```
DISABLED_MODULES="fglrx"
```To:```
DISABLED_MODULES=""
```

---

### Post by grogger13 on 2008-06-03
Jocko thanks a lot, that's exactly what it was

---

