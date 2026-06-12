---
title: "HTC Kaiser not recognised"
date: 2008-06-13
forum: General Help
---

### Post by livefastdiefun87 on 2008-06-13
I know I probably posted in the wrong area so I will apologise straight off the bat, but can anyone help me. I am after mounting my HTC Kaiser in 8.04 what prompt is needed in the terminal to mount this device

Any help greatly appriciated

---

### Post by Arlanthir on 2008-06-13
I don't think you can mount HTC devices without WM5torage, but I might be wrong. My HTC Touch only manages to disconnect my network connection without said program :P

WM5torage works wonders, though =)

---

### Post by SaintDanBert on 2010-01-11
> **Arlanthir said:**
> I don't think you can mount HTC devices without WM5torage, but I might be wrong. My HTC Touch only manages to disconnect my network connection without said program :P

WM5torage works wonders, though =)

There are several issues about phone recognition:
[list]
[*]USB cable conx results in linux--phone visibility
[*](optional)BlueTooth conx results in linux--phone visibility
[*]visibility presents phone storage as read-write linux media storage
[*]visibility enables read-write sync of on-phone applications with linux desktop applications (contacts, calendar, events, reminders, etc)
[*]visibility enables phone to offer broadband internet "modem" services
[/list]

When I connect my phone, "stuff happens" and I get a desktop pop-up saying there is a connection but I cannot use it. At that time, /var/log/messages shows:
```

Jan 11 09:36:13 mumbles kernel: [ 1495.356282] usb 1-4.3: new full speed USB device using ehci_hcd and address 5
Jan 11 09:36:13 mumbles kernel: [ 1495.455069] usb 1-4.3: configuration #1 chosen from 1 choice
Jan 11 09:36:13 mumbles kernel: [ 1495.517930] usbcore: registered new interface driver cdc_ether
Jan 11 09:36:13 mumbles kernel: [ 1495.630234] eth1: register 'rndis_host' at usb-0000:00:1a.7-4.3, RNDIS device, 80:00:60:0f:e8:00
Jan 11 09:36:13 mumbles kernel: [ 1495.630287] usbcore: registered new interface driver rndis_host
Jan 11 09:36:13 mumbles kernel: [ 1495.642925] usbcore: registered new interface driver rndis_wlan
Jan 11 09:36:13 mumbles kernel: [ 1495.677149] udev: renamed network interface eth1 to eth2

```

And my network interfaces report:
```

eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1     
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:f8200000-f8220000

eth2      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet addr:XXX.XXX.XXX.XXX  Bcast:XXX.XXX.XXX.XXX  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:29 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2686 (2.6 KB)  TX bytes:14232 (14.2 KB)

pan0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet addr:XXX.XXX.XXX.XXX  Bcast:XXX.XXX.XXX.XXX  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14857489 (14.8 MB)  TX bytes:1495377 (1.4 MB)

```

---

### Post by Sudarson4 on 2012-10-04
I have the same problem, but even as root i can't execute the command /var/log/messages, and how do i see the network interfaces report?

---

