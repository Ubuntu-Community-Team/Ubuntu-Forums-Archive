---
title: "How do I change IP on linux?"
date: 2016-02-03
forum: General Help
---

### Post by chj191 on 2016-02-03
Hi how do I change the static ip on linux?

---

### Post by Habitual on 2016-02-03
Ask your ISP.

Where exactly to change it? I don't know, sorry.
Do you have a router?

---

### Post by chj191 on 2016-02-03
No I have an all in one modem.
Pretty sure it includes router.
Anyway. With Windows I'm able to change the IP from the IPV6 window.
The first line I think was the real IP, the second line was my new ip (same ip with different ending number).

---

### Post by Habitual on 2016-02-03
reboot the modem?

---

### Post by chj191 on 2016-02-03
What is that gonna do?
It's still the same IP when I reboot the modem.

---

### Post by Habitual on 2016-02-03
[http://ubuntuforums.org/showthread.php?t=2312300&p=13433649#post13433649](http://ubuntuforums.org/showthread.php?t=2312300&p=13433649#post13433649)

---

### Post by QIII on 2016-02-03
It might be helpful to know if you are trying to change the IP of the internet facing side of you AIO or the IPs of the machines on your home LAN.

Patience is a virtue.

---

### Post by Dennis N on 2016-02-03
Your modem acquires an IP address (public IP address) assigned by you service provider that is used by your computer on the internet. To see what it is:

[https://www.iplocation.net/find-ip-address](https://www.iplocation.net/find-ip-address)

Your router provides an IP address usable on your local area network. If it is set up as static, you can change it.

use ifconfig to see this IP address.

Ways to change it depend on your system; sometimes in the router setup, or possibly in the network manager.

---

### Post by chj191 on 2016-02-03
Thanks Dennis. Finally a real answer.

I can't see anything regarding static IP in the ifconfig output though.
> eth0      Link encap:Ethernet  HWaddr bc:ae:c5:69:58:60            inet addr:10.0.0.106  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::beae:c5ff:fe69:5860/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10427553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8693506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9841856923 (9.8 GB)  TX bytes:5943940821 (5.9 GB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5149474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5149474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:304552231 (304.5 MB)  TX bytes:304552231 (304.5 MB)



Can you help me set it up?

---

### Post by QIII on 2016-02-03
Again:  Are you trying to change the internet facing side or the IPs of the machines on your LAN?

---

### Post by chj191 on 2016-02-03
The 3 last digits. And I believe that's referred to as static IP.

---

### Post by QIII on 2016-02-03
Again: On the internet side of your modem/router or the machines on your home network?

---

### Post by chj191 on 2016-02-03
I've never done it from the modem.
In Windows (like I said), I used to go to the modem profile and then IPV6 and do it from there.

---

### Post by QIII on 2016-02-03
Do what?  Change your modem's IP or your computer's IP?

---

### Post by lisati on 2016-02-03
You have been asked several times: are you trying to change a public IP address or one on your local network?

Before replying, I suggest you read this: [https://en.wikipedia.org/wiki/IP_address](https://en.wikipedia.org/wiki/IP_address)

---

### Post by Dennis N on 2016-02-03
This old post is the way I used to set a static IP (wired connection) from the Network Manager dialog:

[http://ubuntuforums.org/showthread.php?t=1905186&p=11593844#post11593844](http://ubuntuforums.org/showthread.php?t=1905186&p=11593844#post11593844)

I hope it still works. 

Instead, I have been setting static IP in the router ever since I acquired a router capable of doing that. It is simpler. But you work with what you have.

---

### Post by QIII on 2016-02-04
Thread closed.

---

