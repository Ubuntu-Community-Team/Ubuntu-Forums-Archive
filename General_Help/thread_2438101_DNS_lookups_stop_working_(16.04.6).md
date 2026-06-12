---
title: "DNS lookups stop working (16.04.6)"
date: 2020-03-05
forum: General Help
---

### Post by scottws on 2020-03-05
I have a Ubuntu server (full desktop... don't ask) running 16.04.6 where DNS lookups stop working occasionally. Restarting the [FONT=Courier New]NetworkManager[/FONT] service resolves the issue.

I'm able to detect the issue when a system receiving logs from this system stops receiving them. I access the server via SSH* and find that the log shipper service on the system is in a failed state. Attempting to start it fails because it can't resolve the destination server's name. I [FONT=Courier New]dig [www.google.com](www.google.com)[/FONT] and it returns "[FONT=Courier New]connection timed out; no servers could be reached[/FONT]". I restart the NetworkManager service, and now DNS lookups work and I can start the log shipper service, resolving the issue (temporarily).

I have previously commented out [FONT=Courier New]dns=dnsmasq[/FONT] in [FONT=Courier New]/etc/NetworkManager/NetworkManager.conf[/FONT] ([https://askubuntu.com/questions/233222/how-can-i-disable-the-dns-that-network-manager-uses](https://askubuntu.com/questions/233222/how-can-i-disable-the-dns-that-network-manager-uses)) so that the system doesn't use dnsmasq as a local DNS proxy; however, I have this done on the other servers that perform the same role too and don't have this issue.

My question is: why is this happening or what are the recommended steps to figure out the cause?

* Empasizing the access is via SSH, meaning the system does in fact have network connectivity.

---

### Post by TheFu on 2020-03-06
Ping LAN and WAN addresses by IP the next time this happens.  Don't use DNS.  Do those both work?

Servers don't use network-manager and have static IPs.  You don't need/want it on a server. There are a few different methods (systemd/resolvconf) to manage the /etc/resolv.conf file or you can simply disable all the other fancy methods and manually edit it like we did for 30+ yrs before.  It's a freakin' text file with 2 or 3 lines.  Any competent admin can edit it correctly.

Depending on your admin skills, those are the 3 easy options.  Plus, you can purge network-manager* and nm-* from the system.

---

