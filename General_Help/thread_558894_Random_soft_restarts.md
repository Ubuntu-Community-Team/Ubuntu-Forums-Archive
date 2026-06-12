---
title: "Random soft restarts"
date: 2007-09-24
forum: General Help
---

### Post by AmonSacha on 2007-09-24
My computer has been restarting randomly since last night, I have checked the logs and there is nothing indicating what may have caused it. Here is a small section of when it happened from /var/log/messages:

Sep 24 11:20:03 toshiba dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Sep 24 11:20:03 toshiba dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Sep 24 11:20:03 toshiba dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Sep 24 11:21:05 toshiba syslogd 1.4.1#20ubuntu4: restart.
Sep 24 11:34:26 toshiba -- MARK --
Sep 24 11:46:48 toshiba syslogd 1.4.1#20ubuntu4: restart.
Sep 24 11:46:48 toshiba kernel: Inspecting /boot/System.map-2.6.20-16-generic
Sep 24 11:46:49 toshiba kernel: Loaded 24980 symbols from /boot/System.map-2.6.20-16-generic.
Sep 24 11:46:49 toshiba kernel: Symbols match kernel version 2.6.20.
Sep 24 11:46:49 toshiba kernel: No module symbols loaded - kernel modules not enabled. 

If anyone can help, that would be wonderful,

I have a laptop running Ubuntu 7.02 Fiesty with kernel 2.6.20-16-generic, the only thing that I did the night before was run `sudo update-alternatives --config java' sometime last night

---

### Post by AmonSacha on 2007-09-24
It's been corrected, it was actually a house electricity issue

---

