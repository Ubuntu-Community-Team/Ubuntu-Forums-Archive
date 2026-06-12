---
title: "yet another wireless question"
date: 2008-03-11
forum: General Help
---

### Post by maninalift on 2008-03-11
I posted this in Kubuntu forum but as I don't think it is KDE-specific and here is busier I am reposting it here:

Here we go

To start off kwifimanager turns off my wireless card and it won't turn on again until I reboot. That is a seperate issue I think but ask me for more information on that if you think it is important.

I also intalled wifi-radar but that only seems to d the same as "iwlist scan" and doesn't allow me to pick one of the networks and connect to it.

OK so from the command line or (or rather Konsole):

```

$ sudo iwconfig eth1 essid XXXXXXXX
```

Seems to connect me...   sort-of.

Here is what I get when I enter iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Aston-General-Access"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:0F:E7:75:70
          Bit Rate:18 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/100  Signal level=-85 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:287   Missed beacon:0

```

So I do have an access point and am displaying a connection speed of about 15Mb/s. However no applications seem to be able to connect. Is it just that I have a signal/noise ratio of only 10. My ethernet connection works fine. I'll try in a different location later? *edit* - no the problem is NOT the signal strenth.

entering ifconfig gives the following
```

eth0      Link encap:Ethernet  HWaddr 00:1D:60:B8:CC:CB
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xc400

eth1      Link encap:Ethernet  HWaddr 00:19:D2:A0:7C:00
          inet6 addr: fe80::219:d2ff:fea0:7c00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:5 dropped:302 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1172 (1.1 KB)  TX bytes:464 (464.0 b)
          Interrupt:17 Base address:0x6000 Memory:fbeff000-fbefffff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5104 (4.9 KB)  TX bytes:5104 (4.9 KB)
```

Should I be concerned that my wireless card "eth1" is listed as "Link encap:Ethernet"  ?

---

### Post by maninalift on 2008-03-11
*bump* sorry I'm just impatient. *edit* shouldn't have done that now I won't be on the unanswered questions list.

---

### Post by maninalift on 2008-03-18
*bump* again. Sorry.

Any help out there? Any response would be useful, am I just being dumb or is this an odd problem or do I need to post more info?

---

