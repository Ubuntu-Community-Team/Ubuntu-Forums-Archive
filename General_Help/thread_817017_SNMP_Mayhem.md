---
title: "SNMP Mayhem"
date: 2008-06-03
forum: General Help
---

### Post by markbusu on 2008-06-03
Hi guys,

Ive been trying to get SNMP working on my 1st Ubuntu Server for the past few days... and its driving me crazy!

What i did:

[http://www.debuntu.org/how-to-monitor-your-servers-with-snmp-and-cacti](http://www.debuntu.org/how-to-monitor-your-servers-with-snmp-and-cacti)

Now, if I run an SNMP WALK... i get the following output

```
SNMPv2-MIB::sysDescr.0 = STRING: Linux ubt00.markbusuttil.com 2.6.24-16-server #                                                                             1 SMP Thu Apr 10 13:58:00 UTC 2008 i686
SNMPv2-MIB::sysObjectID.0 = OID: NET-SNMP-MIB::netSnmpAgentOIDs.10
DISMAN-EVENT-MIB::sysUpTimeInstance = Timeticks: (629300) 1:44:53.00
SNMPv2-MIB::sysContact.0 = STRING: Root <root@localhost> (configure /etc/snmp/sn                                                                             mpd.local.conf)
SNMPv2-MIB::sysName.0 = STRING: ubt00.markbusuttil.com
SNMPv2-MIB::sysLocation.0 = STRING: Unknown (configure /etc/snmp/snmpd.local.con                                                                             f)
SNMPv2-MIB::sysORLastChange.0 = Timeticks: (17) 0:00:00.17
SNMPv2-MIB::sysORID.1 = OID: SNMP-FRAMEWORK-MIB::snmpFrameworkMIBCompliance
SNMPv2-MIB::sysORID.2 = OID: SNMP-MPD-MIB::snmpMPDCompliance
SNMPv2-MIB::sysORID.3 = OID: SNMP-USER-BASED-SM-MIB::usmMIBCompliance
SNMPv2-MIB::sysORID.4 = OID: SNMPv2-MIB::snmpMIB
SNMPv2-MIB::sysORID.5 = OID: TCP-MIB::tcpMIB
SNMPv2-MIB::sysORID.6 = OID: IP-MIB::ip
SNMPv2-MIB::sysORID.7 = OID: UDP-MIB::udpMIB
SNMPv2-MIB::sysORID.8 = OID: SNMP-VIEW-BASED-ACM-MIB::vacmBasicGroup
SNMPv2-MIB::sysORDescr.1 = STRING: The SNMP Management Architecture MIB.
SNMPv2-MIB::sysORDescr.2 = STRING: The MIB for Message Processing and Dispatchin                                                                             g.
SNMPv2-MIB::sysORDescr.3 = STRING: The management information definitions for th                                                                             e SNMP User-based Security Model.
SNMPv2-MIB::sysORDescr.4 = STRING: The MIB module for SNMPv2 entities
SNMPv2-MIB::sysORDescr.5 = STRING: The MIB module for managing TCP implementatio                                                                             ns
SNMPv2-MIB::sysORDescr.6 = STRING: The MIB module for managing IP and ICMP imple                                                                             mentations
SNMPv2-MIB::sysORDescr.7 = STRING: The MIB module for managing UDP implementatio                                                                             ns
SNMPv2-MIB::sysORDescr.8 = STRING: View-based Access Control Model for SNMP.
SNMPv2-MIB::sysORUpTime.1 = Timeticks: (17) 0:00:00.17
SNMPv2-MIB::sysORUpTime.2 = Timeticks: (17) 0:00:00.17
SNMPv2-MIB::sysORUpTime.3 = Timeticks: (17) 0:00:00.17
SNMPv2-MIB::sysORUpTime.4 = Timeticks: (17) 0:00:00.17
SNMPv2-MIB::sysORUpTime.5 = Timeticks: (17) 0:00:00.17
SNMPv2-MIB::sysORUpTime.6 = Timeticks: (17) 0:00:00.17
SNMPv2-MIB::sysORUpTime.7 = Timeticks: (17) 0:00:00.17
SNMPv2-MIB::sysORUpTime.8 = Timeticks: (17) 0:00:00.17
End of MIB
root@ubt00:/etc/courier# snmpwalk -v 1 -c public localhost
SNMPv2-MIB::sysDescr.0 = STRING: Linux ubt00.markbusuttil.com 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686
SNMPv2-MIB::sysObjectID.0 = OID: NET-SNMP-MIB::netSnmpAgentOIDs.10
DISMAN-EVENT-MIB::sysUpTimeInstance = Timeticks: (629872) 1:44:58.72
SNMPv2-MIB::sysContact.0 = STRING: Root <root@localhost> (configure /etc/snmp/snmpd.local.conf)
SNMPv2-MIB::sysName.0 = STRING: ubt00.markbusuttil.com
SNMPv2-MIB::sysLocation.0 = STRING: Unknown (configure /etc/snmp/snmpd.local.conf)
SNMPv2-MIB::sysORLastChange.0 = Timeticks: (17) 0:00:00.17
SNMPv2-MIB::sysORID.1 = OID: SNMP-FRAMEWORK-MIB::snmpFrameworkMIBCompliance
SNMPv2-MIB::sysORID.2 = OID: SNMP-MPD-MIB::snmpMPDCompliance
SNMPv2-MIB::sysORID.3 = OID: SNMP-USER-BASED-SM-MIB::usmMIBCompliance
SNMPv2-MIB::sysORID.4 = OID: SNMPv2-MIB::snmpMIB
SNMPv2-MIB::sysORID.5 = OID: TCP-MIB::tcpMIB
SNMPv2-MIB::sysORID.6 = OID: IP-MIB::ip
SNMPv2-MIB::sysORID.7 = OID: UDP-MIB::udpMIB
SNMPv2-MIB::sysORID.8 = OID: SNMP-VIEW-BASED-ACM-MIB::vacmBasicGroup
SNMPv2-MIB::sysORDescr.1 = STRING: The SNMP Management Architecture MIB.
SNMPv2-MIB::sysORDescr.2 = STRING: The MIB for Message Processing and Dispatching.
SNMPv2-MIB::sysORDescr.3 = STRING: The management information definitions for the SNMP User-based Security Model.
SNMPv2-MIB::sysORDescr.4 = STRING: The MIB module for SNMPv2 entities
SNMPv2-MIB::sysORDescr.5 = STRING: The MIB module for managing TCP implementations
SNMPv2-MIB::sysORDescr.6 = STRING: The MIB module for managing IP and ICMP implementations
SNMPv2-MIB::sysORDescr.7 = STRING: The MIB module for managing UDP implementations
SNMPv2-MIB::sysORDescr.8 = STRING: View-based Access Control Model for SNMP.
SNMPv2-MIB::sysORUpTime.1 = Timeticks: (17) 0:00:00.17
SNMPv2-MIB::sysORUpTime.2 = Timeticks: (17) 0:00:00.17
SNMPv2-MIB::sysORUpTime.3 = Timeticks: (17) 0:00:00.17
SNMPv2-MIB::sysORUpTime.4 = Timeticks: (17) 0:00:00.17
SNMPv2-MIB::sysORUpTime.5 = Timeticks: (17) 0:00:00.17
SNMPv2-MIB::sysORUpTime.6 = Timeticks: (17) 0:00:00.17
SNMPv2-MIB::sysORUpTime.7 = Timeticks: (17) 0:00:00.17
SNMPv2-MIB::sysORUpTime.8 = Timeticks: (17) 0:00:00.17
End of MIB
```

This is the information you get by default using Ubuntu... other variants give me a whole lot of more information such as Interface I/O etc...

Now.. i had this problem once and not aware what i had done to fix the issue... I also went ahead and configured the following:

[http://www.debianhelp.co.uk/snmp.htm](http://www.debianhelp.co.uk/snmp.htm)

However... still same results... Anyone that has managed this and remembers... A helping hand is appreciated!

Thanks!

Mark!

---

### Post by markbusu on 2008-06-03
bump

---

### Post by actodor on 2009-01-26
A little late, but maybe others are still encountering this issue...

The solution lies in correctly configuring snmpd.conf. You have the following lines:

#       sec.name  source          community
com2sec paranoid  default         public
#com2sec readonly  default         public
...

#               sec.model  sec.name
group MyROSystem v1        paranoid
group MyROSystem v2c       paranoid
group MyROSystem usm       paranoid
group MyROGroup v1         readonly
group MyROGroup v2c        readonly
group MyROGroup usm        readonly

...
#                context sec.model sec.level match  read   write  notif
access MyROSystem ""     any       noauth    exact  system none   none
access MyROGroup ""      any       noauth    exact  all    none   none

In short, you have, by default, only com2sec 'paranoid' for the 'public' community enabled. This applies to the MyROSystem group for v1/v2c/usm security model. The access for this association is 'read' for the 'system' MIB only.

Now, to get you access to other info through snmp, the shortest way is to change 'system' into 'all':

#                context sec.model sec.level match  read   write  notif
access MyROSystem ""     any       noauth    exact  **all**    none   none

and restart the snmpd daemon (/etc/init.d/snmpd restart).

This is not recommended though, I think one should first get a thorough understanding of how snmpd.conf works and create new rules from scratch.

Hope this helps.
Cheers!

---

