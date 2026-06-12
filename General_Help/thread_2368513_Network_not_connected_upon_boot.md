---
title: "Network not connected upon boot"
date: 2017-08-11
forum: General Help
---

### Post by lsutiger on 2017-08-11
When I reboot, the network is not connected. In order to connect I have to click on the network connection icon in the notification area and click on my network adapter(enp2s5). What is listed in systemctl is a different name for the network (enp2s0)
How can I fix this on boot?

From sudo systemctl status networking
```
networking.service - Raise network interfaces
   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor preset: enabled)
  Drop-In: /run/systemd/generator/networking.service.d
           &#9492;&#9472;50-insserv.conf-$network.conf
   Active: failed (Result: exit-code) since Thu 2017-08-10 15:41:56 CDT; 23h ago
     Docs: man:interfaces(5)
 Main PID: 1010 (code=exited, status=1/FAILURE)

Aug 10 15:41:55 brian-test systemd[1]: Starting Raise network interfaces...
Aug 10 15:41:56 brian-test ifup[1010]: Cannot find device "enp2s0"
Aug 10 15:41:56 brian-test ifup[1010]: Failed to bring up enp2s0.
Aug 10 15:41:56 brian-test systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILUR
Aug 10 15:41:56 brian-test systemd[1]: Failed to start Raise network interfaces.
Aug 10 15:41:56 brian-test systemd[1]: networking.service: Unit entered failed state.
Aug 10 15:41:56 brian-test systemd[1]: networking.service: Failed with result 'exit-code'.

```

---

### Post by lsutiger on 2017-08-11
For whatever reason, the interface in /etc/network/interfaces was incorrect.

---

