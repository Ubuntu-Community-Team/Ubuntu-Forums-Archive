---
title: "Festy disconnects LAN without warning"
date: 2007-05-31
forum: General Help
---

### Post by elpampero on 2007-05-31
I'm working and suddenly the LAN connection is lost without warning.
The worst part, it does not reconnect at all.

Here's my syslog:

[HTML]May 31 17:16:27 dd1 kernel: [130414.253663] eth0: link down
May 31 17:16:27 dd1 NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid. 
May 31 17:16:27 dd1 NetworkManager: <information>^IDeactivating device eth0. 
May 31 17:16:27 dd1 kernel: [130414.280073] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
May 31 17:16:27 dd1 dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 20625
May 31 17:16:27 dd1 dhclient: killed old client process, removed PID file
May 31 17:16:27 dd1 dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
May 31 17:16:27 dd1 avahi-daemon[4845]: Withdrawing address record for 192.168.1.200 on eth0.[/HTML]

I've reinstalled network-manager-gnome but still happens.

anyone can help me? Thanks

---

