---
title: "Snmp Problem"
date: 2008-05-18
forum: General Help
---

### Post by d11 on 2008-05-18
HI. i have a ubuntu 7.10 server runing some aplications and i want to monitor snmp whit a windows 2003 server runing solarwinds orion, but the problem is that i cant configure snmp in ubuntu server i tried whit the snmp guide for debian but it dosentwork.

when solarwind tried to connect to ubuntu whit snmp its impossible.

---

### Post by d11 on 2008-05-21
i had to edit /etc/default/snmp

and change this line 

SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 127.0.0.1' 

to this

SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 0.0.0.0'

now solarwinds found my ubuntu server.

---

