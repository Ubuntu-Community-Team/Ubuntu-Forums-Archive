---
title: "dnsmasq as tftp server"
date: 2018-01-18
forum: General Help
---

### Post by atux on 2018-01-18
i am running a small ubuntu server that has some services on it. with dnsmasq i have the dhcp.
i would like to setup a tftp server in the same system and i thought of dnsmasq, since it is already present in the system.
i uncommented the lines
```
enable-tftp
tftp-root=/var/lib/tftp
```
and i created the /var/lib/tftp

the use of this service is to offer the software to some devices to upgrade their software. Most of the devices have as anonymous user the username. where is in the dnsmasq the username passwd, to set it up?

---

