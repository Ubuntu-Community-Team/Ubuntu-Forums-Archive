---
title: "Nagios monitoring cisco and dell"
date: 2012-12-04
forum: General Help
---

### Post by IvanMP on 2012-12-04
Hi all,

i have installed nagios and nagios plugins on Ubuntu Server like instructions according to the quick start guid on nagios page. I have one Cisco router and dell switch and i like to configure to show me a interface status like up or down or UpTime of the interface but all i get some errors like:

> External command error: MIB search path: /root/.snmp/mibs:/usr/share/mibs/site:/usr/share/snmp/mibs:/usr/share/mibs/iana:/usr/share/mibs/ietf:/usr/share/mibs/netsnmp
Cannot find module (SNMPv2-SMI): At line 0 in (none)
ifOperStatus.1: Unknown Object Identifier (Sub-id not found: (top) -> ifOperStatus)

So i suppose i have to install the mib files on my nagios server so he should know or i doing something wrong, because i try everything like punting the MIB or by default ... 

define service{
use    generic-service
host_name     CiscoRouter
check_command   check_snmp!-C ExampleCisco -o ifOperStatus.1 -r 1 -m RFC1213-MIB
}

i also try o change check command with mib
check_snmp!-C ExampleCisco -o .1.3.6.1.2.1.2.2.1.8 
but nothing ... 

so i hope i can get help here ... tnx in advance

---

