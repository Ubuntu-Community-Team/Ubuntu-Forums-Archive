---
title: "wget help"
date: 2008-04-27
forum: General Help
---

### Post by fouadk on 2008-04-27
hi everyone....

im trying to download ubuntu 64 bit but i have a slow connection....but my server have a decent connection....

im connecting to my server via ssh and then i run the command 

```
wget http://ubuntu.etherkiller.de/hardy/ubuntu-8.04-desktop-amd64.iso
```

and i get the following output....

```
--16:55:55--  http://ubuntu.etherkiller.de/hardy/ubuntu-8.04-desktop-amd64.iso
           => `ubuntu-8.04-desktop-amd64.iso'
Resolving ubuntu.etherkiller.de... 85.233.58.40, 2001:4c50:89:1::10
Connecting to ubuntu.etherkiller.de|85.233.58.40|:80... failed: Connection refused.
Connecting to ubuntu.etherkiller.de|2001:4c50:89:1::10|:80... failed: Address family not supported by protocol.
```

any address i try i get a similar output...why ???

please help...

thanks in advance...

---

### Post by rubicon on 2008-04-27
Okay, here's uncrypted (;)) message:

Connection to 85.233.58.40 (this is IPv4 IP-address) was refused either by the host, or by firewall/proxy/router of your server's LAN. 
Connection to 2001:4c50:89:1::10 (this is IPv6 IP-address) was refused by *your* server. Either its kernel doesn't support IPv6 or its NIC is not capable of transmitting IPv6 packets.

Look, I tried this command and the server didn't respond on port 80 in reasonable time. Most likely it is too busy to process your request so it rejects it.

---

