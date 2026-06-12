---
title: "Error on bootup"
date: 2007-05-21
forum: General Help
---

### Post by dpar on 2007-05-21
Hi; I'm getting an error on bootup, but everything seems to load ok.
Anyone have any ideas??

I've tried to attach a screenshot. Hopefully it will work....lol

Edit:- Here is some stuff in the message log that may or maynot be helpfull.

May 21 07:05:40 dave-desktop kernel: [   69.808469] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 3:00.0] forgot to specify physical device; fix it!
May 21 07:05:40 dave-desktop kernel: [   69.813425] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 3:00.0] forgot to specify physical device; fix it!
May 21 07:05:40 dave-desktop kernel: [   69.818382] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 3:00.0] forgot to specify physical device; fix it!
May 21 07:05:40 dave-desktop kernel: [   70.039545] ppdev: user-space parallel port driver
May 21 07:05:41 dave-desktop hpiod: 1.7.3 accepting connections at 2208... 
May 21 07:05:41 dave-desktop kernel: [   71.498414] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
May 21 07:05:41 dave-desktop kernel: [   71.498423] apm: overridden by ACPI.
May 21 07:05:43 dave-desktop kernel: [   73.583539] Bluetooth: Core ver 2.11
May 21 07:05:43 dave-desktop kernel: [   73.583643] NET: Registered protocol family 31
May 21 07:05:43 dave-desktop kernel: [   73.583647] Bluetooth: HCI device and connection manager initialized
May 21 07:05:43 dave-desktop kernel: [   73.583655] Bluetooth: HCI socket layer initialized
May 21 07:05:43 dave-desktop kernel: [   73.691505] Bluetooth: L2CAP ver 2.8
May 21 07:05:43 dave-desktop kernel: [   73.691512] Bluetooth: L2CAP socket layer initialized
May 21 07:05:43 dave-desktop kernel: [   73.713068] Bluetooth: RFCOMM socket layer initialized
May 21 07:05:43 dave-desktop kernel: [   73.713094] Bluetooth: RFCOMM TTY layer initialized
May 21 07:05:43 dave-desktop kernel: [   73.713098] Bluetooth: RFCOMM ver 1.8
May 21 07:05:44 dave-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
May 21 07:05:44 dave-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
May 21 07:05:44 dave-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
May 21 07:05:44 dave-desktop gconfd (dave-5565): starting (version 2.18.0.1), pid 5565 user 'dave'
May 21 07:05:44 dave-desktop gconfd (dave-5565): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 21 07:05:44 dave-desktop gconfd (dave-5565): Resolved address "xml:readwrite:/home/dave/.gconf" to a writable configuration source at position 1
May 21 07:05:44 dave-desktop gconfd (dave-5565): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 21 07:05:44 dave-desktop gconfd (dave-5565): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 21 07:05:44 dave-desktop gconfd (dave-5565): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 21 07:05:48 dave-desktop gconfd (dave-5565): Resolved address "xml:readwrite:/home/dave/.gconf" to a writable configuration source at position 0
May 21 07:25:28 dave-desktop -- MARK --
May 21 07:26:50 dave-desktop gconfd (root-6449): starting (version 2.18.0.1), pid 6449 user 'root'
May 21 07:26:50 dave-desktop gconfd (root-6449): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 21 07:26:50 dave-desktop gconfd (root-6449): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May 21 07:26:50 dave-desktop gconfd (root-6449): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 21 07:26:50 dave-desktop gconfd (root-6449): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 21 07:26:50 dave-desktop gconfd (root-6449): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 21 07:27:20 dave-desktop gconfd (root-6449): GConf server is not in use, shutting down.
May 21 07:27:20 dave-desktop gconfd (root-6449): Exiting

---

### Post by dpar on 2007-05-21
Bumpity Bump!! Anyone have any ideas???

---

### Post by vtel57 on 2007-05-21
It's a known bug, Dave. No biggie. It won't cause any problems for you. Read more about it [HERE](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/110173).

Luck! :)

---

### Post by dpar on 2007-05-21
Thanks vtel57. I tryed the mv .gconf .gconf_TEMP thing from another post again and it worked this time.....????? Go figure, huh? So I'm good to go now, I guess.

Thanks again......Dave

---

### Post by vtel57 on 2007-05-21
You're welcome. 

Have FUN! :)

---

