---
title: "snmptrapd.conf logging option syntax"
date: 2021-01-19
forum: General Help
---

### Post by tc2020 on 2021-01-19
Hello All,

I am running Ubuntu Server 20.04 LTS and installed snmptrapd ($sudo apt install snmptrapd). I would like to set snmptrapd so that it logs all traps to a file. 

The following is what I have in /etc/snmp/snmptrapd.conf:

authCommunity log,execute,net public
logOption -Lf /home/ubuntu/templog
disableAuthorization yes

The /etc/default/snmptrapd file contains one line (default after installation):
TRAPDOPTS='-LSwd -p /run/snmptrapd.pid'

When I do $ sudo /etc/init.d/snmptrapd start, the syslog says 'Unknown token: logOption'. It also shows the same message when I replace it with TRAPDOPTS = '-Lf /home/ubuntu/templog'. The status of snmptrapd is 'Active' even with this message, however, it does not receive any traps.

If I do $ sudo /etc/init.d/snmptrapd stop and then $ sudo snmptrapd -Lf /home/ubuntu/templog2, traps get logged Ok.

What seems to be the problem?. What are the differences between the two ways to start snmptrapd?. Any help would be greatly appreciated. Thank you.

tc2020

---

