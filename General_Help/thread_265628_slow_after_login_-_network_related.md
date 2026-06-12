---
title: "slow after login - network related"
date: 2006-09-26
forum: General Help
---

### Post by shanepardue on 2006-09-26
after i type my username and password, the computer goes brown and hangs there for about 3 minutes. after that, the computer runs fine other than the first time i open system>networking. the problem first started when i created a location in the networking application. i've since deleted all the locations, but the problem still exists. the internet works perfectly fine after it takes forever to load up.

please help!

---

### Post by chrisccoulson on 2006-09-26
> **shanepardue said:**
> after i type my username and password, the computer goes brown and hangs there for about 3 minutes. after that, the computer runs fine other than the first time i open system>networking. the problem first started when i created a location in the networking application. i've since deleted all the locations, but the problem still exists. the internet works perfectly fine after it takes forever to load up.

please help!

This might be a red herring, but both times I've had a problem similar to this, it was due to my local loopback interface not being started automatically for whatever reason.

Can you drop out to text mode with CTRL+ALT+F1 and run ifconfig to see if your loopback interface (lo) is listed.

---

### Post by shanepardue on 2006-09-26
i think that's the problem. here's the entire output from ifconfig. how would i remedy the situation?

```
wlan0     Link encap:Ethernet  HWaddr 00:30:BD:4E:16:02
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:bdff:fe4e:1602/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14285 errors:0 dropped:358 overruns:0 frame:0
          TX packets:12626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5960400 (5.6 MiB)  TX bytes:2440696 (2.3 MiB)
          Interrupt:11 Memory:e096e000-e096e100
```

---

### Post by chrisccoulson on 2006-09-26
I've had this happen to me twice now, and both times were due to different problems. The first time was due to a problem with my /etc/network/interfaces file. Does your file contain these lines:
```
auto lo
iface lo inet loopback
```

If not, then I believe it should do.

The second time this happened to me was after I had restored my entire root filesystem from a tar archive I had created. Because I had archived the contents of some virtual filesystems (/var/run and /var/lock), these filesystems could not then be mounted afterward I had restored the system, which caused me problems. However, unless you have recently restored your system from a backup, I doubt this would be the issue. 

I would look at the first suggestion though.

---

### Post by shanepardue on 2006-09-26
> **chrisccoulson said:**
> I've had this happen to me twice now, and both times were due to different problems. The first time was due to a problem with my /etc/network/interfaces file. Does your file contain these lines:
```
auto lo
iface lo inet loopback
```

If not, then I believe it should do.

The second time this happened to me was after I had restored my entire root filesystem from a tar archive I had created. Because I had archived the contents of some virtual filesystems (/var/run and /var/lock), these filesystems could not then be mounted afterward I had restored the system, which caused me problems. However, unless you have recently restored your system from a backup, I doubt this would be the issue. 

I would look at the first suggestion though.
that was it!! for some reason i was missing "auto lo" in there. that's strange, but thanks for the fix!!!

---

### Post by chrisccoulson on 2006-09-27
No probs:)

---

### Post by teumima on 2006-09-28
nice one! worked!

---

