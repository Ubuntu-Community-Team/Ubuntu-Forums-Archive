---
title: "Woops - Deleted module"
date: 2013-03-04
forum: General Help
---

### Post by KieranFitzgerald on 2013-03-04
Ubuntu 12.10 64 bit

I am trying to get a parallel port working on my system and while "fiddling" around I deleted the file

parport_pc.ko in kernel/drivers/parport

How can I restore it?
Thanks

---

### Post by Impavidus on 2013-03-04
It's provided by the package linux-image-<some version>. Reinstalling that package should bring the file back.

---

### Post by KieranFitzgerald on 2013-03-04
Thanks I've downloaded linux-image-3.5.0-25.39_amd64.deb
Any precautions before doing this?

---

### Post by dino99 on 2013-03-04
you should reinstall from synaptic, its way easier

sudo apt-get install synaptic
sudo synaptic

then reinstall the package

---

### Post by ManamiVixen on 2013-03-04
NO!!!! Don't install downloaded packages. Instead run  --  sudo apt-get install --reinstall linux-image-<some version>  --  Just find the version of the package you have currently installed on your computer.

---

### Post by iponeverything on 2013-03-04
the package is probably still sitting in /var/cache/apt/archives/

---

### Post by KieranFitzgerald on 2013-03-05
The synaptic route worked!
Thanks

---

