---
title: "snmptraps  does not translate OID’s"
date: 2013-01-16
forum: General Help
---

### Post by la_bigmac on 2013-01-16
Hello,

I am configuring an SNMP listener, I have it 95% done..

I have downloaded the mibs, and setup the listener on udp 162. This works and my syslog is filling up nicely. 

But in my syslog, snmpd is not translating the OID to a human readable format. 

If I manually run 
snmptranslate iso.3.6.1.4.1.1991.1.1.4.13.9 
FOUNDRY-SN-SW-L4-SWITCH-GROUP-MIB::snL4TrapVirtualServerPort

I get the right response so it must be able to use the MIB's so what have I missed from my snmp config for it to not translate before adding it to syslog?

Hope someone can help. 

M.

---

### Post by la_bigmac on 2013-01-25
Solved it. 

all to do with the export option!

Some other helpful hints and tips on getting traps to work I placed in a blog.

[http://insertscream.blogspot.co.uk/2013/01/snmptraps.html](http://insertscream.blogspot.co.uk/2013/01/snmptraps.html)

---

