---
title: "kernel log daemon hangs"
date: 2008-07-07
forum: General Help
---

### Post by optimus on 2008-07-07
Hello

Whenever I boot my pc it hangs at "starting kernel log daemon".  Gdm won't start with this message: " WARNING: gdm_config_parse: Authdir /var/
lib/gdm does not exist. Aborting.".
and also Avahi-daemon gives a failed message back.

Any advice

/var/log/messages:
Jul  7 00:00:48 OptimusPrime kernel: [52876.069050] nautilus[5938]: segfault at 3e000020 eip b76d12d6 esp bff72a10 error 4
Jul  7 00:00:54 OptimusPrime kernel: [52882.212954] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul  7 00:00:56 OptimusPrime exiting on signal 15
Jul  7 09:40:44 OptimusPrime syslogd 1.5.0#1ubuntu1: restart.
Jul  7 09:40:44 OptimusPrime syslog: Kernel log daemon terminating.
Jul  7 09:42:07 OptimusPrime exiting on signal 15
Jul  7 09:43:15 OptimusPrime syslogd 1.5.0#1ubuntu1: restart.
Jul  7 09:43:15 OptimusPrime syslog: Kernel log daemon terminating.
Jul  7 09:46:37 OptimusPrime gnome-power-manager: (patrick) This program cannot start until you start the dbus system service. It is <b>strongly recommended</b> you reboot your computer after starting this service.
Jul  7 09:48:16 OptimusPrime dhcdbd: Started up.
Jul  7 10:03:14 OptimusPrime -- MARK --
Jul  7 10:07:18 OptimusPrime exiting on signal 15
Jul  7 10:08:29 OptimusPrime syslogd 1.5.0#1ubuntu1: restart.
Jul  7 10:08:29 OptimusPrime syslog: Kernel log daemon terminating.
Jul  7 10:13:30 OptimusPrime dhcdbd: Started up.
Jul  7 10:19:04 OptimusPrime dhcdbd: Started

---

### Post by jmac0101 on 2009-04-08
I changed the permissions on my var directory and it caused this hang for me. I think this was due to logging. I could only get it to stop by having the permission set to rwx to all.

---

### Post by jmac0101 on 2009-04-08
Actually I changed it from rwx all, to rwx owner and read and exe to group and world.

---

