---
title: "[SOLVED] Internet works in DesktopCD but not after install"
date: 2007-06-24
forum: General Help
---

### Post by ubuntu27 on 2007-06-24
I am reporting a problem that my friend has.

There is Internet connection when he uses the DesktopCD (LiveCD), but not after he did a Clean Install using the desktopCD. He used all the Hard Drive space for Ubuntu eradicating Windows. 

I am by no means a Linxu expert, I am tryng to help him by searching the forums for answers. Since I am still lost, here I am asking for help.


He uses Ethernet and has ADSL, he also use some router (Some like "router 2wire").


Here is his ifconfig output when using the LiveCD.

> ]eth0      Link encap:Ethernet  HWaddr 00:0F:FE:02:8A:D8  

          inet addr:189.167.117.71  Bcast:189.167.117.79  Mask:255.255.255.240

          inet6 addr: fe80::20f:feff:fe02:8ad8/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:21787 errors:0 dropped:0 overruns:0 frame:0

          TX packets:19974 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:8196187 (7.8 MiB)  TX bytes:4024140 (3.8 MiB)

          Interrupt:193 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:4 errors:0 dropped:0 overruns:0 frame:0

          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

Thank you in advance. :)

---

### Post by s_h_a_d_o_w_s on 2007-06-24
I'm not sure but tell your friend to run:

```
sudo pppoeconf
```

in the terminal

I hope that helps :D

---

### Post by ubuntu27 on 2007-06-24
My friend says that when his has Windows. Internet Works on both the LiveCD and the Hard Drive. But when he gets rid of Windows, Internet doesn't work in both LiveCD and the install.

> **s_h_a_d_o_w_s said:**
> I'm not sure but tell your friend to run:

```
sudo pppoeconf
```

in the terminal

I hope that helps :D

Thank you Shadows.
I just told him that now. We'll see if it works.

In the mean time, more info:

He says that after formating the Dar Drive, UBuntu doesn't detect the network card.

See
[This Image]("http://img359.imageshack.us/img359/6453/pantallazo3cr2.png") After reformating. There that part disappears.


Wonder if the LiveCD "borrows" the driver from Windows?

---

### Post by ubuntu27 on 2007-06-26
Problem SOlved!! 

The ubuntu that he was using was a old version (Dapper Drale). 
Looks like it was a bug in Dapper. Now that he installed Feisty, the problem is gone.
Now he has internet! :D

Thank you guys for helping me out.

---

