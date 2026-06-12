---
title: "isc-dhcp-server won't stop booting on startup, even after update-rc.d removal"
date: 2016-03-31
forum: General Help
---

### Post by vperaino on 2016-03-31
I set isc-dhcp-server up as a little experiment, and now I want to stop it from booting automatically. 

However, running **update-rc.d -f isc-dhcp-server remove** does NOT stop it from running at boot. 

I also checked /etc/init/isc-dhcp-server, which is a completely blank file. 

Sure enough, every time I reboot, **dhcpd** is always running as a process.

Any ideas? Also, I'm running 14.04.

---

