---
title: "SNMPD problem with defaultmonitors Warning: Unknown token: defaultMonitors."
date: 2014-10-22
forum: General Help
---

### Post by vavoem3 on 2014-10-22
Hi there.

i've got snmpd running and i can do a snmpwalk so it is really up and running however i get the following error message in /var/log/syslog upon snmpd startup

Warning: Unknown token: defaultMonitors.
Warning: Unknown token: linkUpDownNotifications.

I need this to actively monitor some processes and have them send a trap upon failure.

This error is similair to the following debian bug reported in may of this year. But there is no clear solution.

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=746399](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=746399)

Do any of you know a solution for this or 
Since ubuntu is really a fork of debian i was wandering whether or not i can install the latest  .deb package from debian where they say it must have been solved.

---

