---
title: "Snmptt daemon mode"
date: 2013-12-09
forum: General Help
---

### Post by amiragall74 on 2013-12-09
Hello, 

I've Ubuntu server 12.04 installed and snmptt running on standalone mode full working. At the beggining all was rigth but the problem started when the traps received grow. The cpu's use up to 70% and more. I've been reading that it is caused by snmptt is called every time snmtrpad receives a trap and reads all the config files & mibs. I would try to config snmptt on daemon mode but I don't found what are the changes on config files. 

Is enough change snmtt.ini  (mode = daemon) and modify snmptrapd.conf ( traphandle default /usr/sbin/snmptthandler)??

Thankyou

aTon.

---

