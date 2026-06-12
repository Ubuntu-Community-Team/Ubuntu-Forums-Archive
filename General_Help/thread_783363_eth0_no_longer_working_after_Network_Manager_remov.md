---
title: "eth0 no longer working after Network Manager removal... (yes I configured it)"
date: 2008-05-05
forum: General Help
---

### Post by bcardarella on 2008-05-05
Using Ubuntu 8.04....
I'm having some issues and would appreciate some help.

I removed Network Manager for several reasons but now I'm having an issue with eth0. I've configured it in /etc/network/interfaces  as:

```

auto eth0
iface eth0 inet dhcp

```

but when I restart the network it can not find my DHCP server:

```
administrator@kbanks-laptop:/var/run$ sudo /etc/init.d/networking start
 * Configuring network interfaces...
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:90:f5:6c:2d:3f
Sending on   LPF/eth0/00:90:f5:6c:2d:3f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

In /var/log/messages it just says that the link is up, then it times out, brings it up, times out... this is from the DHCPDISCOVER I assume.

Anyway, I tried reinstalling the Network Manager package but that didn't solve anything.

Both the server and the connection are fine. I ran the 8.04 LiveCD and everything works with no problems. So this is a configuration issue.

Any and all help would be greatly appreciated!

---

### Post by stream303 on 2008-05-06
I don't need NM either on my wired non-roaming box, so I disabled it rather than deleted it:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5)

I was playing around with this a while back, so I just reinstalled NM, and then disabled it, and had no problem, other than having to go back into the network prefs and enable the connection for dhcp.

I think that disabling, rather than removing NM, might be the better way to go since I read that certain things depend on it being installed.  Forgot where though...

---

