---
title: "snmpwalk on hrSWRun only show snmp process"
date: 2017-06-09
forum: General Help
---

### Post by PsyKoptiK on 2017-06-09
Hi all,

I'm using Ubuntu 16.04 LTS and I try to get Linux processes through SNMP by walking hrSWRun OID but I only have this result :

```
snmpwalk -u user -A pass1 -a SHA -X pass2 -x AES -l authPriv myserver hrSWRun
HOST-RESOURCES-MIB::hrSWRunIndex.1131 = INTEGER: 1131
HOST-RESOURCES-MIB::hrSWRunName.1131 = STRING: "snmpd"
HOST-RESOURCES-MIB::hrSWRunID.1131 = OID: SNMPv2-SMI::zeroDotZero
HOST-RESOURCES-MIB::hrSWRunPath.1131 = STRING: "/usr/sbin/snmpd"
HOST-RESOURCES-MIB::hrSWRunParameters.1131 = STRING: "-LS 4 d -Lf /dev/null -u snmp -g snmp -I -smux mteTrigger mteTriggerConf -p /var/run/snmpd.pid"
HOST-RESOURCES-MIB::hrSWRunType.1131 = INTEGER: application(4)
HOST-RESOURCES-MIB::hrSWRunStatus.1131 = INTEGER: running(1)
```

Instead of printing every processes launched on my server, I only get the snmpd process.
I did not have this behavior with Ubuntu 14.04 LTS because I could parse every processes running on my server so... what did change in Ubuntu 16.04? And how can I do that now?

Any ideas?
Thanks.

---

### Post by PsyKoptiK on 2017-06-12
Does someone have any solution to propose?
Thanks.

---

