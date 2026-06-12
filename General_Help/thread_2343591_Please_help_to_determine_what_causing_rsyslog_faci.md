---
title: "Please help to determine what causing rsyslog facility switching"
date: 2016-11-17
forum: General Help
---

### Post by vt420 on 2016-11-17
Hi,

Please advise what maybe causing log facility defined in the settings of the FreeRADIUS as local1 to switch to security/authorization.

Pertinent configuration changes from defaults, as far as I can tell, are:

in  /etc/freeradius/radiusd.conf:

user =root
group =root

log {
  destination = syslog
  syslog_facility = local1
  auth = yes
}

in  /etc/rsyslog.conf:

$PrivDropToUser adm
$PrivDropToGroup adm

local1.*        /var/log/fradius.log
*.*     @10.2.2.1

-------------------------------------------------------------

As far as I can tell, restarting FreeRADIUS service resets the logging to proper facility.
But if the server is left alone, after a while local1 switches to security/authorization.

Thank you in advance and let me know if I can provide any additional information.

---

