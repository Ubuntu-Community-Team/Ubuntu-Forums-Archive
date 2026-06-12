---
title: "Won't upgrade from 18.04.4LTS to 20.04"
date: 2020-07-09
forum: General Help
---

### Post by justen_m on 2020-07-09
When I tried to update an ancient system, I got a message saying I couldn't. So is 18 the last version that supports my 12-year-old 32-bit system? I kind of figured. This was via do-release-uprgrade -d. 

"Sorry, no more upgrades for this system

There will not be any further Ubuntu releases for this system's
'i386' architecture."

Never heard about this. Probably head in the sand. Guess I will look into other distros for this. LXLE?

---

### Post by pqwoerituytrueiwoq on 2020-07-09
you should sill be able to upgrade, just cause there is no official install disk image doers not mean 32bit is completely dead, you sure you cpu does not support 64 bit?
you could force the upgrade
**** this is NOT the recommended upgrade method, be sure to have a backup just in case**
```

sed -i 's/bionic/focal/' /etc/apt/sources.list
sudo apt-get update && sudo apt-get dist-upgrade

```
if you see something alarming and do not install the new packages you can go back like this
```

sed -i 's/focal/bionic/' /etc/apt/sources.list
sudo apt-get update

```

---

### Post by kc1di on 2020-07-09
18 was the last version for 32 bit systems so no upgrade is available to 19.x or 20.x 
however 32 bit libs are still updated for the time being. 
But the OS as a whole ended 32 bit OS with version 19.x
[Here's a list of distros]("https://itsfoss.com/32-bit-os-list/") still supporting 32bit systems
since your used to debian type systems i would try MX first good luck.

---

