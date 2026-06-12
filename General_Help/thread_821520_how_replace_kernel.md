---
title: "how replace kernel"
date: 2008-06-07
forum: General Help
---

### Post by adredz on 2008-06-07
hi, i just messed up apparmor. when i "modprobe apparmor" i got a "FATAL: Module apparmor no found" error. prior to this, i installed and removed selinux and installed back apparmor. i don't know how to fix this but i think it will be very easy if i will just replace the current kernel with a fresh one but the problem is i don't know how. i've been googling around but got nothing.. help pls...

---

### Post by y-lee on 2008-06-07
Hmmmm

Open synaptic package manager and do a search for linux-image. The kernels you have installed will be marked in green, right click the one you wish to reinstall and choose Mark for Reinstallation then click apply. You should probably reboot after that. Hope that helps :)

---

### Post by adredz on 2008-06-12
that didn't solve it. thanks anyway.. however i noticed that the error still exists though i made a fresh install. maybe apparmor modules are not loaded by default? can anyone confirm this please... if yes, then maybe it's ok to leave it as it is?

---

