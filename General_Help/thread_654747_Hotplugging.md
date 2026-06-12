---
title: "Hotplugging"
date: 2007-12-31
forum: General Help
---

### Post by lowebb on 2007-12-31
Does anyone know how I could force a hotplugging of a device? I have a usb device which I regularly have to remove and reinsert to get it working. How could I do this without having to physically remove the device. Surely there is a remove and insert script command I could run to force this action to happen

---

### Post by earobinson on 2007-12-31
u can unmound and remount the device, use df to fund out what devices are mounted.

---

### Post by lowebb on 2008-01-01
In there lies the problem. This a dvb card which is mounted via udev, which has only 1 entry in the mtab file. It should mount my 2 dvb card to "/dev/dvb/adaptor0" & "/dev/dvb/adaptor1" but only mounts 1 on start-up. I cant seem to find a command to manually mount the other one

---

