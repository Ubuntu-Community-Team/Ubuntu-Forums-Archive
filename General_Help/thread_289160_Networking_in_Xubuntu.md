---
title: "Networking in Xubuntu"
date: 2006-10-30
forum: General Help
---

### Post by spaceghoti on 2006-10-30
I'm not sure if the problem is persistent networking in Xubuntu or if it's just IRC connections, but I'm finding it impossible to maintain a consistent connection to my preferred IRC server (irc.esper.net).  I didn't have this problem with the KDE desktop, it has only started since I opened XFCE.  I originally started with XChat and switched to Konversation to see if that would be any different, and the results were the same:  the system would lag out over the course of several minutes and eventually force me to reconnect.

I'm not sure where to find the GUI controls for networking in Xubuntu, but I get the following response from ifconfig (identity altered to protect the innocent):

```
eth0  Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.xx.xx  Bcast:192.168.xx.255  Mask:255.255.255.0
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1625440 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1957462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:662774066 (632.0 MiB)  TX bytes:1653989207 (1.5 GiB)
          Base address:0x8400 Memory:c0220000-c0240000
```

If anyone has any ideas why I keep timing out of IRC in XFCE but not in KDE, I would appreciate it.

---

