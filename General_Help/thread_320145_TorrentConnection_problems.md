---
title: "Torrent/Connection problems"
date: 2006-12-16
forum: General Help
---

### Post by boris yeltsin on 2006-12-16
I use Azureus to download my torrents, but I used to use ktorrent, and I had the same problem with both. After a certain time my Internet (and my downloads) disconnect and I can't do anything so I am forced to shut down Azureus and change my Static IP to another IP (or restart) in order to get everything going again. 

Is this a problem with a setting or something? I don't have any problems with utorrent when running Windows, it's just Ubuntu (edgy eft) that gives me the problems.

Help would be appreciated. :-?

---

### Post by stoeptegel on 2006-12-17
I would try a few things

1. Lower the max number of connections, if it would not work then 2
2. Disable DHT, if it would not work then 3
3. Wireless? Try wired.

---

### Post by stoeptegel on 2006-12-18
Also, if you happen to be located in a local network with a static ip address assignment: Be sure to check if you have not configure the same IP as someone else already has, because it will trash the network FAST.

---

### Post by IceFire on 2006-12-22
Same problem here. I'm on a xubuntu 6.10 and a old laptop. Everything else works normally, but after 1-5 mins of using any bittorrent client, connection dies and **any** traffic will not go anywhere.

---

### Post by IceFire on 2006-12-23
Some more info on the problem. Im new to linux so i dont know how to troubleshoot network problems, but i found out this:
```
eth0      Link encap:Ethernet  HWaddr xxx  
          inet addr:xxx  Bcast:xxx  Mask:255.255.224.0
          inet6 addr: xxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34510 errors:0 dropped:0 overruns:418 frame:0
          TX packets:26397 errors:7 dropped:0 overruns:1 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:35914282 (34.2 MiB)  TX bytes:3036828 (2.8 MiB)
          Interrupt:11 Base address:0xa000 
```

Normally there's no overruns (i dont really know what it means), but when i start a torrent, overruns start building up rapidly and connection dies. Maybe someone could explain is this a problem or suggest a how to find out what's wrong with the connection.

---

### Post by boris yeltsin on 2006-12-24
Well, it hasn't happened for a day, I set all my computers to static IP adresses and it hasn't occured since, so i figure that the desktop was attempting to connect to the same IP, however if it ocurrs again then that is probably not the problem. I'll get back to you if it happens again and we can figure this out, but it seems that solved my problem.

---

