---
title: "Extremely slow network connection to and from 6.06 server"
date: 2007-05-24
forum: General Help
---

### Post by Wesslan on 2007-05-24
I've had a 6.06 server with FTP, Samba, mail server, Subversion etc running w/o problems for about a year.
Last week my network connection speed to and from the server dropped dramatically! The "speed" are down to 5-10 kb/s... :(
I tested my home network (replaced cables, ports, rebooted switch etc) and all my other computers work just fine. I also replaced the network card without luck. Still the same crappy speed.
All server software are also running correctly.

Does anyone have an idea of how to solve this?

Regards,
Peter

---

### Post by Wesslan on 2007-05-25
If it helps anyone, "ifconfig -a" shows
```

eth0      Link encap:Ethernet  HWaddr 00:0C:6E:70:25:7A
          inet addr:192.168.210.110  Bcast:192.168.210.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe70:257a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:199960 errors:0 dropped:0 overruns:0 frame:2809
          TX packets:184090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:34085394 (32.5 MiB)  TX bytes:30791310 (29.3 MiB)
          Interrupt:209

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11015920 (10.5 MiB)  TX bytes:11015920 (10.5 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by Wesslan on 2007-05-29
For future reference it **was** a hardware error. All the diagnostics told me it wasn't but since I replaced the card everything runs like a charm! :)

---

### Post by liberalist on 2007-05-29
> **Wesslan said:**
> For future reference it **was** a hardware error. All the diagnostics told me it wasn't but since I replaced the card everything runs like a charm! :)

I am glad to hear it. Let us know if you have any other questions.

---

