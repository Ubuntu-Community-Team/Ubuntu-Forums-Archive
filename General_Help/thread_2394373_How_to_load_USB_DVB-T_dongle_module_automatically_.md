---
title: "How to load USB DVB-T dongle module automatically at boot."
date: 2018-06-15
forum: General Help
---

### Post by debderivs on 2018-06-15
Hey guys,

The module/driver of my 2 USB DVB-T dongles doesn´t always load at boot even having tried two
solutions I found on the net, but it loads with no problem if I re-plug them physically.

I copied the module, "dvb-usb-af9015.fw", to the folder /lib/firmware, and then added a line with 
its name to these 2 files:

To "/etc/modules"

And to "/etc/rc.local" adding "modprobe dvb-usb-af9015.fw".

What else could I try to make this module load automatically at boot without having to re-plug
the dongles?

Distro is Xubuntu, installed on Live USB with persistence.

Thanks in advance.

Regards.

---

