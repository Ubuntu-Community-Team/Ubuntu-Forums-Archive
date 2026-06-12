---
title: "nut-scanner issues"
date: 2023-01-19
forum: General Help
---

### Post by zkab on 2023-01-19
I have Ubuntu 22.10 workstation connected to APC UPS (SmartUPS 750) via LAN/SNMP.
Trying to setup NUT server and have installed following NUT modules.

```
ii  nut            2.7.4-14ubuntu2 all          network UPS tools - metapackage
un  nut-cgi        <none>          <none>       (no description available)
ii  nut-client     2.7.4-14ubuntu2 amd64        network UPS tools - clients
ii  nut-ipmi       2.7.4-14ubuntu2 amd64        network UPS tools - IPMI driver
un  nut-monitor    <none>          <none>       (no description available)
ii  nut-server     2.7.4-14ubuntu2 amd64        network UPS tools - core system
ii  nut-snmp       2.7.4-14ubuntu2 amd64        network UPS tools - SNMP driver
ii  nut-xml        2.7.4-14ubuntu2 amd64        network UPS tools - XML/HTTP driver
```
When I run 'sudo nut-scanner -S -s 192.168.1.0 -e 192.168.1.255' I get following:

Neon library not found. XML search disabled.
Scanning SNMP bus.

Then I ran ''sudo nut-scanner -D -S -s 192.168.1.0 -e 192.168.1.255' and got following:
> Neon library not found. XML search disabled.
Scanning USB bus.
Scanning SNMP bus.
Scanning NUT bus (old connect method).
Scanning IPMI bus.
Init SSL without certificate database
nut_ipmi_ctx_open_outofband: connection timeout

How can this be fixed?
Howto install 'Neon library'?

---

### Post by MAFoElffen on 2023-01-19
Does anything from this thread help: [https://ubuntuforums.org/showthread.php?t=2479812](https://ubuntuforums.org/showthread.php?t=2479812)

---

