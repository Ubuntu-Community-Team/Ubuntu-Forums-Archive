---
title: "change order of init tasks: from where  ntpdate runned"
date: 2012-12-01
forum: General Help
---

### Post by icegood on 2012-12-01
have from my syslog:

> Dec  1 03:38:04 ubuntu ntpdate[1108]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Dec  1 03:38:04 ubuntu ntpdate[1108]: no servers can be used, exiting
Dec  1 03:38:04 ubuntu ntpdate[1157]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Dec  1 03:38:04 ubuntu ntpdate[1157]: no servers can be used, exiting
============================
========
Dec  1 03:38:08 ubuntu dhclient: Internet Systems Consortium DHCP Client 4.2.4
Dec  1 03:38:08 ubuntu dhclient: Copyright 2004-2012 Internet Systems Consortium.
Dec  1 03:38:08 ubuntu dhclient: All rights reserved.
Dec  1 03:38:08 ubuntu dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Dec  1 03:38:08 ubuntu dhclient: 
Dec  1 03:38:08 ubuntu dhclient: Listening on LPF/wlan0/1c:4b:d6:d5:81:ec
Dec  1 03:38:08 ubuntu dhclient: Sending on   LPF/wlan0/1c:4b:d6:d5:81:ec
Dec  1 03:38:08 ubuntu dhclient: Sending on   Socket/fallback
Dec  1 03:38:08 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Dec  1 03:38:11 ubuntu dbus[939]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Dec  1 03:38:11 ubuntu dbus[939]: [system] Successfully activated service 'org.freedesktop.UDisks'
Dec  1 03:38:11 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Dec  1 03:38:11 ubuntu dhclient: DHCPREQUEST of 192.168.73.177 on wlan0 to 255.255.255.255 port 67
Dec  1 03:38:11 ubuntu dhclient: DHCPOFFER of 192.168.73.177 from 192.168.73.1
Dec  1 03:38:11 ubuntu dhclient: DHCPACK of 192.168.73.177 from 192.168.73.1
Dec  1 03:38:11 ubuntu dbus[939]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Dec  1 03:38:11 ubuntu dbus[939]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Dec  1 03:38:12 ubuntu dbus[939]: [system] Activating service name='org.kde.powerdevil.backlighthelper' (using servicehelper)
Dec  1 03:38:12 ubuntu org.kde.powerdevil.backlighthelper: QDBusConnection: system D-Bus connection created before QCoreApplication. Application may misbehave.
Dec  1 03:38:12 ubuntu dbus[939]: [system] Successfully activated service 'org.kde.powerdevil.backlighthelper'
Dec  1 03:38:13 ubuntu dhclient: bound to 192.168.73.177 -- renewal in 37181 seconds.
so, my dhclient runned later than ntpdate. 
dhclient called from my owm network-manager script from init.d on runlevel 2
with priority S20.
But from where runned ntpdate - i cannot get. Could you help me to spot?
Tried
grep -nRE ntpdate . in init.d - just nothing

---

