---
title: "lircd on edgy"
date: 2007-02-01
forum: General Help
---

### Post by jammln on 2007-02-01
Hi All,

Having a few problems with lirc on edgy. All has installed fine (and I've stopped the inputlircd daemon), but I'm having problems keeping lircd alive.


```
# sudo lircd -d /dev/input/event3 -n
lircd-0.8.0[7407]: lircd(userspace) ready

#irw
lircd-0.8.0[7407]: accepted new client on /dev/lircd
lircd-0.8.0[7407]: could not get hardware features
lircd-0.8.0[7407]: this device driver does not support the new LIRC interface
lircd-0.8.0[7407]: major number of /dev/input/event3 is 13
lircd-0.8.0[7407]: LIRC major number is 61
lircd-0.8.0[7407]: check if /dev/input/event3 is a LIRC device
lircd-0.8.0[7407]: caught signal


```


it doesn't matter which device I listen to it always dies when starting irw. Any suggestions?

Also, does anyone know why, even after killing all ir daemons X still picks up remote signals for things like volume, power etc? Is there someway to stop this as it's interfering with other apps that I'm trying to control?

Thanks for you help

---

### Post by joshidax on 2007-02-09
Hi !
the reason why you still get signals without a ir daemon running is the new kernel support in edgy for some ir receivers on DVB cards I guess.
Check out [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)
and see the part : Managed I2C Devices
I got the same with a Nexus-S in my system.

To solve the first problem just follow the howto.

---

