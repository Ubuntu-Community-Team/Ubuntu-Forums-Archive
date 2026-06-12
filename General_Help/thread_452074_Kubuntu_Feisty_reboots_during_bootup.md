---
title: "Kubuntu Feisty reboots during bootup"
date: 2007-05-22
forum: General Help
---

### Post by Ashex on 2007-05-22
This has been an ongoing issue for me for a couple weeks. Kubuntu will randomly reboot during startup, it's generally a hit-and-miss. Occasionally it will just hang and I haven't really been able to isolate the issue yet.

From syslog, I pulled this from the latest occurance:

```

May 22 20:15:55 Phorin avahi-daemon[5085]: Registering new address record for fe80::250:56ff:fec0:1 on vmnet1.*.
May 22 20:15:55 Phorin avahi-daemon[5085]: Registering new address record for fe80::250:56ff:fec0:8 on vmnet8.*.
May 22 20:16:04 Phorin kernel: [   55.684000] vmnet1: no IPv6 routers present
May 22 20:16:04 Phorin kernel: [   55.724000] vmnet8: no IPv6 routers present
May 22 20:16:07 Phorin kdm_greet[5787]: Internal error: memory corruption detected
May 22 20:16:24 Phorin hcid[5491]: Default passkey agent (:1.12, /org/bluez/passkey_agent_6012) registered
May 22 20:16:42 Phorin gconfd (ahmed-6143): starting (version 2.18.0.1), pid 6143 user 'ahmed'
May 22 20:16:42 Phorin gconfd (ahmed-6143): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 22 20:16:42 Phorin gconfd (ahmed-6143): Resolved address "xml:readwrite:/home/ahmed/.gconf" to a writable configuration source at position 1
May 22 20:16:42 Phorin gconfd (ahmed-6143): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 22 20:16:42 Phorin gconfd (ahmed-6143): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 22 20:16:42 Phorin gconfd (ahmed-6143): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 22 20:18:52 Phorin syslogd 1.4.1#20ubuntu4: restart.

```

I also grabbed the events from kern.log at the same time:

```

May 22 20:15:43 Phorin kernel: [   33.688000] /dev/vmnet: open called by PID 5674 (vmnet-natd)
May 22 20:15:43 Phorin kernel: [   33.688000] /dev/vmnet: hub 8 does not exist, allocating memory.
May 22 20:15:43 Phorin kernel: [   33.688000] /dev/vmnet: port on hub 8 successfully opened
May 22 20:15:46 Phorin kernel: [   36.852000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 6:00.0] forgot to specify physical device; fix it!
May 22 20:15:46 Phorin kernel: [   36.856000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 6:00.0] forgot to specify physical device; fix it!
May 22 20:15:46 Phorin kernel: [   36.856000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 6:00.0] forgot to specify physical device; fix it!
May 22 20:15:52 Phorin kernel: [   43.512000] eth0: no IPv6 routers present
May 22 20:15:53 Phorin kernel: [   44.796000] /dev/vmnet: open called by PID 5792 (vmnet-netifup)
May 22 20:15:53 Phorin kernel: [   44.796000] /dev/vmnet: hub 1 does not exist, allocating memory.
May 22 20:15:53 Phorin kernel: [   44.796000] /dev/vmnet: port on hub 1 successfully opened
May 22 20:15:53 Phorin kernel: [   44.800000] /dev/vmnet: open called by PID 5793 (vmnet-netifup)
May 22 20:15:53 Phorin kernel: [   44.800000] /dev/vmnet: port on hub 8 successfully opened
May 22 20:15:53 Phorin kernel: [   44.864000] /dev/vmnet: open called by PID 5809 (vmnet-dhcpd)
May 22 20:15:53 Phorin kernel: [   44.864000] /dev/vmnet: port on hub 8 successfully opened
May 22 20:15:53 Phorin kernel: [   44.864000] /dev/vmnet: open called by PID 5815 (vmnet-dhcpd)
May 22 20:15:53 Phorin kernel: [   44.864000] /dev/vmnet: port on hub 1 successfully opened
May 22 20:16:04 Phorin kernel: [   55.684000] vmnet1: no IPv6 routers present
May 22 20:16:04 Phorin kernel: [   55.724000] vmnet8: no IPv6 routers present
May 22 20:18:52 Phorin kernel: Inspecting /boot/System.map-2.6.20-15-generic

```

Anyone know what would cause it to restart randomly on startup or where to look?

---

