---
title: "Installed Conglomerate but can't remove it..."
date: 2007-03-16
forum: General Help
---

### Post by sthompson on 2007-03-16
Hello all,

I installed conglomerate in Edgy and can't uninstall. I get the error message that says, "E: conglomerate: subprocess pre-removal script returned error exit status 1". And then an error message says, "sudo apt-get install -f" to fix it.

I've tried to remove it via synaptic and from the command line using..

sudo apt-get remove conglomerate
sudo aptitude --remove conglomerate etc etc..

Nothing works!

Does anyone know how I can remove it?


Thanks,

Steve

---

### Post by zvacet on 2007-03-17
```
sudo aptitude --purge 
```
Or you can do it manualy.It means that you have to look in usr/bin,etc,etc/init.d,home(including hidden folders).Every file you find delete.

---

