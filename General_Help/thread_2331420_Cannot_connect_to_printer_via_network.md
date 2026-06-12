---
title: "Cannot connect to printer via network"
date: 2016-07-22
forum: General Help
---

### Post by charitosha on 2016-07-22
I've got a hp color laserjet pro mfp m277dw printer in the office and i'm the only person with a linux laptop :cool: 
(I still have 12.04 lts version)
However I am afraid that hp doesn't hAave drivers for linux. I tried to do what this article says [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
but with no luck.
From the printer i was able to get the ipv4 address, host name, hardware address.
I think the only useful info that i can give is the following:
```
haris@Mini-210:~$ sudo nmap -sS 169.254.53.44
[sudo] password for haris: 

Starting Nmap 5.21 ( http://nmap.org ) at 2016-07-22 09:20 MSK
Nmap scan report for 169.254.53.44
Host is up (0.0055s latency).
Not shown: 993 closed ports
PORT     STATE SERVICE
80/tcp   open  http
443/tcp  open  https
515/tcp  open  printer
631/tcp  open  ipp
8080/tcp open  http-proxy
8291/tcp open  unknown
9100/tcp open  jetdirect

Nmap done: 1 IP address (1 host up) scanned in 1.79 seconds
```

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

```


Any help would be much appreciated

---

### Post by speartip on 2016-07-22
HP has probably the best supported linux software.
Have you got the packages hplip & printer-driver-hpcups installed?
Looking at this page it seems to have been well supported upto Ubuntu 10.04, but 12.04 should work.
[http://store.hp.com/UKStore/Merch/Product.aspx?id=B3Q11A&opt=B19&sel=PRN](http://store.hp.com/UKStore/Merch/Product.aspx?id=B3Q11A&opt=B19&sel=PRN)

---

### Post by charitosha on 2016-07-25
I have hplip packages and printer driver hpcups.
However no matter what i get the printer is not connected notification.
I dont know what to do....
at printing set up, did found some drivers but with no luck. Can somebody help me to start troubleshooting?

---

