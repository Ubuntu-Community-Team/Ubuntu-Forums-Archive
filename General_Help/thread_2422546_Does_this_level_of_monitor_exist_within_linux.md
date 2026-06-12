---
title: "Does this level of monitor exist within linux"
date: 2019-07-09
forum: General Help
---

### Post by ubotbuddy on 2019-07-09
I automate a lot of my routine jobs and that helps my productivity but there is one tool/app I cannot find and maybe it does not exist.

I want an app whereby I can monitor all of my system.  It does not have to be fancy but it would be awesome to be able to see the Hard-drive utilization (Total Size & Used), RAM utilization (Total & Used), Network (Still active, Total Packets sent & received), DHCP for monitor overall network usage by clients, System upgrade notifications and any other critical area that I am forgetting.

In my searching I found Station and Rambox and these are great from a client perspective but are there good tools for monitoring a whole network?

Any ideas?

Buddy

---

### Post by HermanAB on 2019-07-09
SNMP Zabbix?

---

### Post by ubotbuddy on 2019-07-09
Awesome!  Thanks for sharing.  That gets me on track.

Buddy

---

### Post by rbmorse on 2019-07-09
Also gkrellm.  There are a number of plugins available that extend it beyond it's default capabilities.

---

### Post by TheFu on 2019-07-09
> **HermanAB said:**
> SNMP Zabbix?

There are many similar F/LOSS tools - nagios is the main player. There are about 10 forks.  opennms is another original. Cacti is another.  
Depending on how fancy you want, there are monit, munin, sysusage and others like that.

Huge enterprises would use commercial products and have deployment teams come in for weeks.  Some might use OpenNMS - there is a support/deployment company around that tool, but it is 100% F/LOSS. Just depends on what you need.  If you deploy mostly Linux stacks, you'll find nagios used most places with the forks of nagios being used from time to time. Often, those forks have prettier graphics or an easier deployment.
If you have a spare Raspberry Pi, there is NEMS.  Load it up, point it at your network and start watching.  [https://nemslinux.com/](https://nemslinux.com/)

---

