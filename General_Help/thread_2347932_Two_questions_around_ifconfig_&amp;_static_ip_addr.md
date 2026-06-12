---
title: "Two questions around ifconfig &amp; static ip addresses"
date: 2016-12-30
forum: General Help
---

### Post by blackagave2 on 2016-12-30
I have a network set up at home that is giving me back different responses
for ifconfig for each computer(having just read that during a proofread I
realized...duh). There are currently 3 computers, will be four eventually,
in total on the network that I would like to be able to access a few from
stable static ip addresses.

The mac is wireless.
the HTPC is wired.
BigBox sits behind a Asus RT-n16 running dd-wrt and is set up to be a
client bridge.

Now I know per
[https://www.swiftstack.com/docs/install/configure_networking.html](https://www.swiftstack.com/docs/install/configure_networking.html) I'm
supposed to edit /etc/network/interfaces.

however, I'm getting really confused with the ifconfig outputs.

eth0 on the htpc:

```
eth0      Link encap:Ethernet  HWaddr 4d68:44f3:8f3:2969:a5a8:10ff:5e:d03d
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 4d68:44f3:8f3:2969:a5a8:10ff:5e:d03d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76072836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31133640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:97038587365 (97.0 GB)  TX bytes:8395717189 (8.3 GB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:602966 errors:0 dropped:0 overruns:0 frame:0
          TX packets:602966 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:57609169 (57.6 MB)  TX bytes:57609169 (57.6 MB)

```

lo0, gif0, stf0, en0, en1, en2, p2p0, awdl0, bridge0 on the mac:

```
lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
    options=3<RXCSUM,TXCSUM>
    inet6 ::1 prefixlen 128
    inet 127.0.0.1 netmask 0xff000000
    inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1
    nd6 options=1<PERFORMNUD>
gif0: flags=8010<POINTOPOINT,MULTICAST> mtu 1280
stf0: flags=0<> mtu 1280
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
    ether 4d68:44f3:8f3:2969:a5a8:10ff:5e:d03d
    inet6 4d68:44f3:8f3:2969:a5a8:10ff:5e:d03d prefixlen 64 scopeid 0x4
    inet 192.168.1.9 netmask 0xffffff00 broadcast 192.168.1.255
    nd6 options=1<PERFORMNUD>
    media: autoselect
    status: active
en1: flags=963<UP,BROADCAST,SMART,RUNNING,PROMISC,SIMPLEX> mtu 1500
    options=60<TSO4,TSO6>
    ether 4a:00:07:76:e7:e0
    media: autoselect <full-duplex>
    status: inactive
en2: flags=963<UP,BROADCAST,SMART,RUNNING,PROMISC,SIMPLEX> mtu 1500
    options=60<TSO4,TSO6>
    ether 4a:00:07:76:e7:e1
    media: autoselect <full-duplex>
    status: inactive
p2p0: flags=8843<UP,BROADCAST,RUNNING,SIMPLEX,MULTICAST> mtu 2304
    ether 06:b3:01:c9:1d:53
    media: autoselect
    status: inactive
awdl0: flags=8943<UP,BROADCAST,RUNNING,PROMISC,SIMPLEX,MULTICAST> mtu 1484
    ether 211d:58c7:9682:937a:366e:494f:41a2:da18
    inet6 211d:58c7:9682:937a:366e:494f:41a2:da18 prefixlen 64 scopeid 0x8
    nd6 options=1<PERFORMNUD>
    media: autoselect
    status: active
bridge0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
    options=63<RXCSUM,TXCSUM,TSO4,TSO6>
    ether c6:b3:01:9c:82:00
    Configuration:
        id 0:0:0:0:0:0 priority 0 hellotime 0 fwddelay 0
        maxage 0 holdcnt 0 proto stp maxaddr 100 timeout 1200
        root id 0:0:0:0:0:0 priority 0 ifcost 0 port 0
        ipfilter disabled flags 0x2
    member: en1 flags=3<LEARNING,DISCOVER>
            ifmaxaddr 0 port 5 priority 0 path cost 0
    member: en2 flags=3<LEARNING,DISCOVER>
            ifmaxaddr 0 port 6 priority 0 path cost 0
    nd6 options=1<PERFORMNUD>
    media: <unknown type>
    status: inactive

```


lo, p4p1 on the BigBox:

```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:21151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6169882 (6.1 MB)  TX bytes:6169882 (6.1 MB)

p4p1      Link encap:Ethernet  HWaddr 10:bf:48:82:d4:69
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 211d:58c7:9682:937a:366e:494f:41a2:da18/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:419334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:270066 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:173155572 (173.1 MB)  TX bytes:36165221 (36.1 MB)
```

What do all those mean?
Do I create the static ip addresses as noted above in the link but just
where the current entry is but "should be" eth0?

---

### Post by wildmanne39 on 2016-12-30
Thread closed as a duplicate, I suspect this is due to a forum glitch. Your other thread is here:
[https://ubuntuforums.org/showthread.php?t=2347927](https://ubuntuforums.org/showthread.php?t=2347927)

---

