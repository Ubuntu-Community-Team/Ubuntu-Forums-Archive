---
title: "SNMP help please"
date: 2007-11-01
forum: General Help
---

### Post by batofd on 2007-11-01
Hey guys,

I'm just messing around with SNMP and Cacti.  I'm trying to monitor my network traffic and it's using the snmpnetstat command.  The following code is what I use to test:

```
snmpnetstat -v 2c -c public -P tcp myhost
```

It outputs nothing though.  No matter what I try, nothing.  I am root, I can see the "netstat" output, but not this however.  Has anyone came across this issue?  

Thanks for the help,

Matt

---

