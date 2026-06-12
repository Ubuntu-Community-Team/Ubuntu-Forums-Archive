---
title: "Huwaei MT882 modem config for BSNL broadband"
date: 2007-10-02
forum: General Help
---

### Post by ReyCazador on 2007-10-02
Hello, I am currently using a Huwaei MT882 modem for BSNL broadband in India can someone tell me how to configure this modem to work Ubuntu 7.04 using a USB conection.

---

### Post by ksbalaji on 2008-01-11
You may open a terminal and enter 'sudo pppoeconf' which will take care of the entire job. It is supposed to do so.  I also use MT882 in Chennai. I have Ubuntu gutsy installed.  If you do not have pppoeconf installed, please install and try. 
But sorry to say this:  I am not able to configure MT882 using pppoeconf! I dont know why. May be I bave meddeled with pppoe too much. I found your post while trying to find a solution. Goodluck.
If you find a complete solution, Pl inform me.

---

### Post by AliROCK on 2008-03-10
i can not install this modem how can install it ubuntu is very poor for drivers?

---

### Post by prashantryp on 2008-03-22
I am having the problem to run sudo pppoeconf it returns error

Sorry, I scanned 1 interface, but the Access
Concentrator of your provider did not respond. Please
check your network and modem cables. Another reason
for the scan failure may also be another running pppoe
process which controls the modem.

i was unable to connect to internet and received the message


ifconfig -a

eth0 Link encap:Ethernet HWaddr xx.xx.xx.xx.xx.xx
inet addr:192.168.1.2 Bcast xxx.xxx.xxx.xxx Mask:255.255.255.0
inet6 addr: Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:623 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:269 errors:0 dropped:0 overruns:0 frame:0
TX packets:269 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:26935 (26.3 KB) TX bytes:26935 (26.3 KB)

I like to make a WAN miniport pppoe connection LIKE IN WINDOWS so i can put user id and password to connect to my internet. I dont want autodial by modme's pppoe.

I have seen my modem in ubuntu gutsy 7.10 device manager whith specification so i think it's installed.

Is it due to IPV6 because in windows it's woking with IPV4

even i am unable to ping my modem by entering fixed ip setting in netwrok configuration.

---

