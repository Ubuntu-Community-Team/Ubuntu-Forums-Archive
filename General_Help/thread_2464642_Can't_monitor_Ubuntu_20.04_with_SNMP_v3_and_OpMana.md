---
title: "Can't monitor Ubuntu 20.04 with SNMP v3 and OpManager"
date: 2021-07-07
forum: General Help
---

### Post by araczek2 on 2021-07-07
HI,
I am trying to set up an SNMP v3 configuration on an Ubuntu server and monitor this server via SNMP. I have loaded SNMP on the Ubuntu server, created a user, allowed the 
ports 161 & 162 through ufw, performed a netstat and saw the listening ports. I used Paeslar SNMP tester and tested the configuration and I can retrieve the Uptime. Yet when I use 
ManageEngine OpManager to test the same SNMP credential the test fails, essentially telling me the server may not be running, SNMP may not be running, the credentials may be wrong.
Banging my head against the wall trying to resolve this. 

Any idea's?

...ar

---

### Post by araczek2 on 2021-07-13
Finally found out what the issue was. Ubuntu out of the box only allows local SNMP queries, from 127.0.0.1. You need to go to /etc/snmp/snmpd.conf and modify the lines that have a value
of agentAddress. Comment out the line only allowing 127.0.0.1 and uncomment the line allowing queries from all interfaces. Restart snmpd anf you shoud be good to go!

...ar

---

