---
title: "Ubuntu does not recognize my 4g modem"
date: 2013-01-14
forum: General Help
---

### Post by poolhustler on 2013-01-14
Hi, I'm having problems installing my new 4g modem. 

The model is: ZTE  mf880 

The older usb-modem(3g) I have gets recognized by Ubuntu without problem but when I stick my new modem in it does not show anywhere. I've tried to fix this with the "Edit connection-window" but It doesn't help.

Any suggestions?

---

### Post by sanderj on 2013-01-14
The usual questions for unrecognized USB devices:

Which Ubuntu version?
What is the 'lsusb' ID of the 4G modem? Did you google that ID?
When you plugin the 4G modem, what's the output of 'dmesg'? Warning: this can be lot of lines (possibly more than one page)

---

### Post by poolhustler on 2013-01-15
I have the 12.04 version.  I followed this thread:

[http://ubuntuforums.org/showthread.php?t=1969322](http://ubuntuforums.org/showthread.php?t=1969322)  (alefish's advice, top-post on page 2) 

and now the modem gets detected when I start the computer but I have to enter the pin-code for the sim-card every time. Also the "edit-connection-window does not pop up automatically and when I try to edit a connection manually there is no plan APN for Mobile Broadband. 

The indicator changes colour a short while after I've entered the pin-code so it seems to detect the 4g-net?

Ubuntu seems to detect the modem but I cant connect to the internet.

---

### Post by poolhustler on 2013-01-15
Now I've managed to not have to enter the pin-code every time I put the modem in the computer. But I still cant connect to the internet. 

I open the network-manager, click the Mobile Broadband tab and there I can see my modem. It says: ZTE LTE Technologies MSM.  Then I press the continue-button and choose country. Then I press the continue-button again and choose the provider for my broadband. Then I press continue and I'm asked to select my plan. My plan witch is Mobile Broadband is not an option for some reason(my 3g mobile broadband gets to choose the  right option) so I press "My plan is not listed" and write APN-plan manually ,MobileBroadband.

Then I apply. Then a new window with several tabs pops up with several fields/forms to fill. 
This shows on the Mobile Broadband-tab:  Basic
                                                                                   Number : *99#
                                                                                   Username:   blank
                                                                                   Password:    blank
                                                                                   Advanced
                                                                                   APN:  MobileBroadband
                                                                                   Network ID:  blank
                                                                                   Type:  Any
                                                                                   PIN:   blank

I have tried to enter the same pin-code in the field/form but it did not work. Still cant connect with internet.

If there is anybody that have had the same problem and have manage to solve it I would be thankful for the solution.

Does Linux have an OS that is compatible with 4g mobile broadbands?

---

### Post by poolhustler on 2013-01-15
I managed to solve it.   Aperently it was not aloud to have to connections installed so I removed my old one and then installed the new one and it worked. 

It is ridiculously slow though!

---

### Post by sanderj on 2013-01-15
> **poolhustler said:**
> I managed to solve it.   Aperently it was not aloud to have to connections installed so I removed my old one and then installed the new one and it worked. 

It is ridiculously slow though!

What's the output of ifconfig

And what does "ping www.google.com" give you?

Post the output here.

---

### Post by poolhustler on 2013-01-15
output of ifconfig

```
eth0      Link encap:Ethernet  HWaddr c8:0a:a9:42:cc:4c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3964 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3964 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:522934 (522.9 KB)  TX bytes:522934 (522.9 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:95.209.7.9  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:915323 errors:0 dropped:0 overruns:0 frame:0
          TX packets:720613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:869949009 (869.9 MB)  TX bytes:208551960 (208.5 MB)


```output of ping [www.google.com]("http://www.google.com")

```
PING www.google.com (173.194.71.104) 56(84) bytes of data.
64 bytes from lb-in-f104.1e100.net (173.194.71.104): icmp_req=1 ttl=51 time=69.7 ms
64 bytes from lb-in-f104.1e100.net (173.194.71.104): icmp_req=2 ttl=51 time=75.7 ms
64 bytes from lb-in-f104.1e100.net (173.194.71.104): icmp_req=3 ttl=51 time=65.6 ms
64 bytes from lb-in-f104.1e100.net (173.194.71.104): icmp_req=4 ttl=51 time=222 ms
64 bytes from lb-in-f104.1e100.net (173.194.71.104): icmp_req=5 ttl=51 time=116 ms
64 bytes from lb-in-f104.1e100.net (173.194.71.104): icmp_req=6 ttl=51 time=70.4 ms
64 bytes from lb-in-f104.1e100.net (173.194.71.104): icmp_req=7 ttl=51 time=91.5 ms
64 bytes from lb-in-f104.1e100.net (173.194.71.104): icmp_req=8 ttl=51 time=147 ms
64 bytes from lb-in-f104.1e100.net (173.194.71.104): icmp_req=9 ttl=51 time=75.3 ms
64 bytes from lb-in-f104.1e100.net (173.194.71.104): icmp_req=10 ttl=51 time=88.9 ms
64 bytes from lb-in-f104.1e100.net (173.194.71.104): icmp_req=11 ttl=51 time=133 ms
64 bytes from lb-in-f104.1e100.net (173.194.71.104): icmp_req=12 ttl=51 time=85.2 ms
64 bytes from lb-in-f104.1e100.net (173.194.71.104): icmp_req=13 ttl=51 time=292 ms
64 bytes from lb-in-f104.1e100.net (173.194.71.104): icmp_req=14 ttl=51 time=92.2 ms
64 bytes from lb-in-f104.1e100.net (173.194.71.104): icmp_req=15 ttl=51 time=160 ms
^C
--- www.google.com ping statistics ---
15 packets transmitted, 15 received, 0% packet loss, time 14018ms
rtt min/avg/max/mdev = 65.639/119.214/292.896/62.555 ms

```Not sure how much data you need.  It seemed to never end.

---

### Post by sanderj on 2013-01-16
That doesn't look too bad.

What speed does [http://speedtest.net/](http://speedtest.net/) report to you?

---

### Post by poolhustler on 2013-01-16
Today the test gave me between 0.40  - 1.00Mbps and during the night it gave me as much as 10Mbps so I guess it depends on how much internet-traffic there is.

---

### Post by rrich1974 on 2013-01-16
the ping is big for a 4g network. it seems that you are quite far from the BTS.

---

### Post by sanderj on 2013-01-16
> **poolhustler said:**
> Today the test gave me between 0.40  - 1.00Mbps and during the night it gave me as much as 10Mbps so I guess it depends on how much internet-traffic there is.

Ouch. Which country, which provider?

BTW: it might be you're not on a 4G service / cell, but 3G.

---

### Post by poolhustler on 2013-01-16
> Ouch. Which country, which provider?

BTW: it might be you're not on a 4G service / cell, but 3G. 

Sweden and the provider is called 3. 

Just now I got the result 5.55Mbps. Maybe speed is not the problem but the reception is. Well I guess I have to deal with my provider on this issue.

---

