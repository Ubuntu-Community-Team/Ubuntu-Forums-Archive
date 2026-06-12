---
title: "[SOLVED] Is Bittorrent secure?"
date: 2007-12-30
forum: General Help
---

### Post by t0p on 2007-12-30
I've just recently started using Bittorrent, and out of curiosity ran **netstat** while the client was running.  Here's part of the output:
```
t0p@x-box:~$ netstat -a
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:6881                  *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      1 172.23.101.244:48806    c-24-10-239-105.h:36709 SYN_SENT   
tcp        0      0 172.23.101.244:46826    74-129-123-213.dh:36757 ESTABLISHED
tcp        1      0 172.23.101.244:50004    a195.22.198-166.dep:www CLOSE_WAIT 
tcp        0      1 172.23.101.244:36128    S0106001310d374d7:59192 SYN_SENT   
tcp        0     48 172.23.101.244:40830    CPE000d613489ed-C:54586 ESTABLISHED
tcp        0      1 172.23.101.244:58150    089-101-240238.nt:26082 SYN_SENT   
tcp        0      1 172.23.101.244:59406    adsl-75-47-69-155.:6771 SYN_SENT   
tcp        0   9789 172.23.101.244:37097    60.53.193.223:27970     ESTABLISHED
tcp        0      0 172.23.101.244:46660    adsl-75-47-69-135.:6771 ESTABLISHED
tcp        0      1 172.23.101.244:57054    c-67-183-201-111.:60069 SYN_SENT   
tcp        0      1 172.23.101.244:35984    pool-71-126-190-6:49679 SYN_SENT   
tcp        0      0 172.23.101.244:48793    85.93.188.213:44078     ESTABLISHED
tcp        1      0 172.23.101.244:48028    a195.22.198-145.dep:www CLOSE_WAIT 
tcp        0      1 172.23.101.244:33449    future-is.orange.c:6881 SYN_SENT   
tcp        0      0 172.23.101.244:34327    213.219.137.110.a:39379 ESTABLISHED
udp        0      0 *:32768                 *:*                                
udp        0      0 *:mdns                  *:*     


```

So... what the hell's all *that* about?!  I don't understand why the torrent I'm downloading would make that many connections.  Bittorrent isn't reporting that much up/downloading activity.  What's going on?

Are there any steps I should take specifically to harden Bittorrent?

---

### Post by CatKiller on 2007-12-30
> **t0p said:**
> I don't understand why the torrent I'm downloading would make that many connections.  Bittorrent isn't reporting that much up/downloading activity.  What's going on?

That's what BitTorrent does: it's more-or-less the point of using BitTorrent. All of those connections with SYN_SENT aren't actually downloading anything yet - you're just getting synchronised - so those connections wouldn't show up as activity in your BitTorrent client.

---

### Post by LaRoza on 2007-12-30
It is safe and secure.

---

### Post by Liolikas on 2007-12-30
It is closed source so you can not be shure what it does. You can use network sniffer like **wireshark** if you want to gaher more info about program actions online.
  
Ktorrent, azureus or rtorrent is much more secure.

---

### Post by LaRoza on 2007-12-30
> **Liolikas said:**
> It is closed source so you can not be shure what it does. You can use network sniffer like **wireshark** if you want to gaher more info about program actions online.
  
Ktorrent, azureus or rtorrent is much more secure.

Add Deluge to the list of clients for Linux. Have no idea if any are better than the others, but it is popular it seems.

---

