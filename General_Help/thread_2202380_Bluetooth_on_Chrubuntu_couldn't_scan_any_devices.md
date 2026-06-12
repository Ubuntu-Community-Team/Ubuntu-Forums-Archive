---
title: "Bluetooth on Chrubuntu couldn't scan any devices"
date: 2014-01-28
forum: General Help
---

### Post by jacky4 on 2014-01-28
I am using HP 14 Chromebook with xfce4 13.10 Chrubuntu and I couldn't scan any devices at all whenever I opened my bluetooth manager and pressed the scan button. I have been trying to find solutions online, but I couldn't find one that works. I have tried using hcitool scan on the terminal, but it didn't scan any devices at all. 

This is what I have when I type in lsusb:

> root@chrubuntu:/home/user# lsusbBus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0bda:0177 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 12d1:1570 Huawei Technologies Co., Ltd. 
Bus 002 Device 003: ID 0cf3:311e Atheros Communications, Inc. 
Bus 002 Device 002: ID 0bda:5776 Realtek Semiconductor Corp. 


and this is what I have when I type in ifconfig:
> root@chrubuntu:/home/user# ifconfiglo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:569208 (569.2 KB)  TX bytes:569208 (569.2 KB)


usb0      Link encap:Ethernet  HWaddr 02:2c:80:13:92:63  
          inet6 addr: fe80::2c:80ff:fe13:9263/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:268113 (268.1 KB)


wlan0     Link encap:Ethernet  HWaddr 80:56:f2:bb:67:f7  
          inet addr:10.53.30.4  Bcast:10.53.255.255  Mask:255.255.0.0
          inet6 addr: fe80::8256:f2ff:febb:67f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:104102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48609 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57352587 (57.3 MB)  TX bytes:6956586 (6.9 MB)


If you need more information, I will try my best to provide more, so that we can solve this easily. :)

Thanks!

---

### Post by maggaknet on 2014-08-24
same problem here, xubuntu 14.04 on HP Chromebook 14 with ChrUbuntu. Bluetooth adapter is recognized but no devices can be found.

lsusb -v fails with this:

Bus 002 Device 003: ID 0cf3:311e Atheros Communications, Inc. 
lsusb: gconv.c:74: __gconv: Assertion `outbuf != ((void *)0) && *outbuf != ((void *)0)' failed.

---

