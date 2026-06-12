---
title: "wt?"
date: 2008-01-29
forum: General Help
---

### Post by midnex on 2008-01-29
i have internet on ppoe  the internet worket just fine but next day i can run Skype but updates browsing and ower i can't? plx help :D

---

### Post by jeffus_il on 2008-01-29
Check you DNS settings, Skype is using an IP address and the other stuff url's which need resolving.

---

### Post by midnex on 2008-01-29
> **jeffus_il said:**
> Check you DNS settings, Skype is using an IP address and the other stuff url's which need resolving.


but last day my internet worket just fine D:and on winXP 
but next day on linux dont work its just loading forever.....


Ban english :/

---

### Post by danwood76 on 2008-01-29
It does sound like a DNS issue.

try these 2 commands in terminal:
```

ping 66.102.9.147
ping www.google.com

```

they should both ping the same server and give you a good responce like below:
```

Pinging www.l.google.com [66.102.9.147] with 32 bytes of data:

Reply from 66.102.9.147: bytes=32 time=22ms TTL=238
Reply from 66.102.9.147: bytes=32 time=26ms TTL=238
Reply from 66.102.9.147: bytes=32 time=25ms TTL=238
Reply from 66.102.9.147: bytes=32 time=24ms TTL=238

Ping statistics for 66.102.9.147:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 22ms, Maximum = 26ms, Average = 24ms

```

if you get a responce from one (the actual IP address) and not the other you have a DNS issue.

regards,
Danny

---

### Post by midnex on 2008-01-29
i have this and its no stops

PING google.com (66.249.93.104) 56(84) bytes of data. 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=1 ttl=245 time=225 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=2 ttl=245 time=203 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=3 ttl=245 time=218 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=4 ttl=245 time=229 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=5 ttl=245 time=119 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=6 ttl=245 time=188 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=7 ttl=245 time=154 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=8 ttl=245 time=148 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=9 ttl=245 time=150 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=10 ttl=245 time=158 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=11 ttl=245 time=112 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=12 ttl=245 time=107 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=13 ttl=245 time=219 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=14 ttl=245 time=186 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=15 ttl=245 time=273 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=16 ttl=245 time=284 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=17 ttl=245 time=185 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=18 ttl=245 time=306 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=19 ttl=245 time=280 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=20 ttl=245 time=331 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=21 ttl=245 time=286 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=22 ttl=245 time=310 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=23 ttl=245 time=135 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=24 ttl=245 time=154 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=25 ttl=245 time=257 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=26 ttl=245 time=226 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=27 ttl=245 time=290 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=28 ttl=245 time=192 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=29 ttl=245 time=260 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=30 ttl=245 time=311 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=31 ttl=245 time=281 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=32 ttl=245 time=279 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=33 ttl=245 time=250 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=34 ttl=245 time=183 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=35 ttl=245 time=241 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=36 ttl=245 time=261 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=37 ttl=245 time=206 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=38 ttl=245 time=196 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=39 ttl=245 time=234 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=40 ttl=245 time=250 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=41 ttl=245 time=105 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=42 ttl=245 time=196 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=43 ttl=245 time=129 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=44 ttl=245 time=132 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=45 ttl=245 time=140 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=46 ttl=245 time=142 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=47 ttl=245 time=220 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=48 ttl=245 time=271 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=49 ttl=245 time=321 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=50 ttl=245 time=400 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=51 ttl=245 time=425 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=52 ttl=245 time=269 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=53 ttl=245 time=259 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=54 ttl=245 time=236 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=55 ttl=245 time=264 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=56 ttl=245 time=316 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=57 ttl=245 time=334 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=58 ttl=245 time=350 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=59 ttl=245 time=427 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=60 ttl=245 time=321 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=61 ttl=245 time=243 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=62 ttl=245 time=128 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=63 ttl=245 time=356 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=64 ttl=245 time=305 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=65 ttl=245 time=342 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=66 ttl=245 time=411 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=67 ttl=245 time=392 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=68 ttl=245 time=315 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=69 ttl=245 time=286 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=70 ttl=245 time=360 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=71 ttl=245 time=308 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=72 ttl=245 time=214 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=73 ttl=245 time=344 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=74 ttl=245 time=287 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=75 ttl=245 time=362 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=76 ttl=245 time=335 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=77 ttl=245 time=438 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=78 ttl=245 time=395 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=79 ttl=245 time=273 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=80 ttl=245 time=250 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=81 ttl=245 time=309 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=82 ttl=245 time=327 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=83 ttl=245 time=246 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=84 ttl=245 time=262 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=85 ttl=245 time=253 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=86 ttl=245 time=267 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=87 ttl=245 time=143 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=88 ttl=245 time=166 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=89 ttl=245 time=250 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=90 ttl=245 time=105 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=91 ttl=245 time=80.4 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=92 ttl=245 time=81.3 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=93 ttl=245 time=74.2 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=94 ttl=245 time=79.7 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=95 ttl=245 time=146 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=96 ttl=245 time=263 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=97 ttl=245 time=163 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=98 ttl=245 time=275 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=99 ttl=245 time=365 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=100 ttl=245 time=316 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=101 ttl=245 time=335 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=102 ttl=245 time=391 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=103 ttl=245 time=278 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=104 ttl=245 time=334 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=105 ttl=245 time=316 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=106 ttl=245 time=323 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=107 ttl=245 time=244 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=108 ttl=245 time=163 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=109 ttl=245 time=184 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=110 ttl=245 time=94.6 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=111 ttl=245 time=102 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=112 ttl=245 time=74.8 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=113 ttl=245 time=135 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=114 ttl=245 time=77.6 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=115 ttl=245 time=77.7 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=116 ttl=245 time=139 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=117 ttl=245 time=260 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=118 ttl=245 time=308 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=119 ttl=245 time=316 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=120 ttl=245 time=376 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=121 ttl=245 time=356 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=122 ttl=245 time=227 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=123 ttl=245 time=163 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=124 ttl=245 time=79.2 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=125 ttl=245 time=89.6 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=126 ttl=245 time=97.8 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=127 ttl=245 time=75.2 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=128 ttl=245 time=79.3 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=129 ttl=245 time=80.7 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=130 ttl=245 time=76.4 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=131 ttl=245 time=90.2 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=132 ttl=245 time=85.3 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=133 ttl=245 time=71.3 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=134 ttl=245 time=71.9 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=135 ttl=245 time=109 ms 
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=136 ttl=245 time=81.4 ms

---

### Post by jeffus_il on 2008-01-29
The name is resolved, can you now open google.com in your browser?
What do you suggest Danny?

---

### Post by midnex on 2008-01-29
yeah can but other sites not load

---

### Post by midnex on 2008-01-29
sosmone help D:

---

### Post by danwood76 on 2008-01-29
If you for example
```
ping www.bbc.co.uk
```
does that resolve and then are you able to access that through firefox?

btw to stop the pinging you press ctrl + c.

if it does resolve then I think the problem is with firefox resolving domain names.

how is your internet connection setup and connected to your PC?

regards,
Danny

---

### Post by midnex on 2008-01-29
> **danwood76 said:**
> If you for example
```
ping www.bbc.co.uk
```
does that resolve and then are you able to access that through firefox?

btw to stop the pinging you press ctrl + c.

if it does resolve then I think the problem is with firefox resolving domain names.

how is your internet connection setup and connected to your PC?

regards,
Danny

mh is not... i can do enything , just google and skype D:  :(

---

### Post by danwood76 on 2008-01-29
How is your computer connected to the internet?

---

### Post by midnex on 2008-01-30
> **danwood76 said:**
> How is your computer connected to the internet?

wyth modem in Ethernet conection ... i tested the live cd its not vorking to... [IMG]http://www.ipix.lt/out.php/i346646_Screenshot.png[/IMG]  maybe i need to set 1412 but there?

---

### Post by danwood76 on 2008-01-30
I doubt its an MMS/MTU issue, that would create a completely unusable internet.
What you have is a DNS issue.

So you are connected through a modem.
Can you elaborate on this, for example is it a DSL/ADSL connection, what speed your connection is.

regards,
Danny

---

### Post by midnex on 2008-01-30
ADSL modem spped 254kb (slow :P)

---

### Post by danwood76 on 2008-01-30
What modem do you have?

It could be an issue with the modem drivers.
I personally always use routers for ADSL/DSL as modems tend to be buggy, ive never used a USB modem with ubuntu on my ADSL back home unfortunatly.

regards,
Danny

---

### Post by midnex on 2008-01-30
my modem is not with USB :D [IMG]http://www.mercadolibre.com.ve/jm/img?s=MLV&f=7215777_4184.jpg&v=P[/IMG]model ZXDSL 8321AII (ZTE)

---

### Post by danwood76 on 2008-01-30
Ah right, sorry I should have read your post above :)
Well there shouldnt be any difference between running ubuntu and windows through that.

I do find it very strange that you can get [www.google.com](www.google.com) but no other sites.

Has your internet ever worked with ubuntu?
I think there may be some compatibility issue with your modem and linux.

Looking at the modem specs it does have a firewall and port forwarding.
Can you log into the modem with firefox?
it might possibly be [http://192.168.1.1](http://192.168.1.1) although I cant be 100% sure as sometimes the IP address chnages.

can you post the result of:
```
ifconfig
```
in the treminal please.

regards,
Danny

---

### Post by midnex on 2008-01-30
how tu enter to  modem? :D

---

### Post by danwood76 on 2008-01-30
you have to go to it in firefox.

so [http://modems_IP_address](http://modems_IP_address)

regards,
Danny

---

### Post by midnex on 2008-01-30
ok i have my ifconfig 

eth0      Link encap:Ethernet  HWaddr 00:13:D3:9A:16:CD  
          inet6 addr: fe80::213:d3ff:fe9a:16cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:139 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16169 (15.7 KB)  TX bytes:4951 (4.8 KB)
          Interrupt:21 Base address:0xdead 

eth0:avah Link encap:Ethernet  HWaddr 00:13:D3:9A:16:CD  
          inet addr:169.254.7.225  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1800 (1.7 KB)  TX bytes:1800 (1.7 KB)

2.i cant go to 192.168.1.1

---

### Post by jeffus_il on 2008-01-30
avahi is giving you and address out of your lan 169.254.7.225, with this address you are not on the same local network as your router 192.168.1.1, this happens when there is a problem that dhcp does not give you an address from your router, manually edit your interfaces file
```
sudo nano /etc/network/interfaces
``` and hard code a static address for example  192.168.1.10
Everything will then work.
Get an example of the interfaces file by typing ```
man interfaces
```

something like this:
```
              iface eth0 inet static
                   address 192.168.1.10
                   netmask 255.255.255.0
 

```

afterwards restart the network using ```
sudo /etc/init.d/networking restart
```

---

### Post by danwood76 on 2008-01-30
Well your modem isnt configured properly.

If you go System -> Administration -> Network
then select the wired network (eth0) and click properties.

Then making sure 'Enable this connection' is ticked modify the settings as follows.

First Try:
```

Configuration: Automatic Configuration (DHCP)
Other fields blank

```
and click ok then close and wait for around 2 mins and get the output of ifconfig.
then change the network settings again to:
```

Configuration: Static IP Address
IP Address: 192.168.1.2
Subnet Mask: 255.255.255.0
Gateway Address: 192.168.1.1

```
and try and access the router @ [http://192.168.1.1](http://192.168.1.1)
post your results.

regards,
Danny

-- edit --

Follow jeffus_il's post, he beat me to it and his explaination is better.

---

### Post by midnex on 2008-01-30
ok i enetered to my modem but its like pasvord protected what to do now the sites not loading again ....i dont wana back to WIN xp

---

### Post by danwood76 on 2008-01-30
so you can access your modem now, good.
And you still dont have access to any other sites?

can you give us the output of ifconfig again?
also do you get a good response from
```
ping 64.233.183.104
```
now?

regards,
Danny

---

### Post by midnex on 2008-01-30
i get 

PING 64.233.183.104 (64.233.183.104) 56(84) bytes of data.
64 bytes from 64.233.183.104: icmp_seq=1 ttl=245 time=132 ms
64 bytes from 64.233.183.104: icmp_seq=2 ttl=245 time=89.4 ms
64 bytes from 64.233.183.104: icmp_seq=3 ttl=245 time=76.5 ms
64 bytes from 64.233.183.104: icmp_seq=4 ttl=245 time=79.0 ms
64 bytes from 64.233.183.104: icmp_seq=5 ttl=245 time=69.7 ms
64 bytes from 64.233.183.104: icmp_seq=6 ttl=245 time=68.1 ms
64 bytes from 64.233.183.104: icmp_seq=7 ttl=245 time=80.3 ms
64 bytes from 64.233.183.104: icmp_seq=8 ttl=245 time=96.8 ms
64 bytes from 64.233.183.104: icmp_seq=9 ttl=245 time=89.3 ms
64 bytes from 64.233.183.104: icmp_seq=10 ttl=245 time=77.2 ms
64 bytes from 64.233.183.104: icmp_seq=11 ttl=245 time=90.8 ms
64 bytes from 64.233.183.104: icmp_seq=12 ttl=245 time=114 ms
64 bytes from 64.233.183.104: icmp_seq=13 ttl=245 time=107 ms
64 bytes from 64.233.183.104: icmp_seq=14 ttl=245 time=84.9 ms

--- 64.233.183.104 ping statistics ---
14 packets transmitted, 14 received, 0% packet loss, time 13003ms
rtt min/avg/max/mdev = 68.141/89.867/132.912/17.512 ms

and my ifconfig

eth0      Link encap:Ethernet  HWaddr 00:13:D3:9A:16:CD  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fe9a:16cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1823 errors:126 dropped:0 overruns:0 frame:126
          TX packets:1796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:444995 (434.5 KB)  TX bytes:266485 (260.2 KB)
          Interrupt:21 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16016 (15.6 KB)  TX bytes:16016 (15.6 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:78.56.207.119  P-t-P:213.190.60.229  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1525 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1725 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:379978 (371.0 KB)  TX bytes:220815 (215.6 KB)


What to do now :P its stell dont loads sites

---

### Post by danwood76 on 2008-01-30
This shows that you are connected to the internet.
I think you still have a DNS issue.

What is listed under DNS in System -> Administration -> Network ?

regards,
Danny

---

### Post by midnex on 2008-01-31
> **danwood76 said:**
> This shows that you are connected to the internet.
I think you still have a DNS issue.

What is listed under DNS in System -> Administration -> Network ?

regards,
Danny

IP Address: 192.168.1.2
Subnet Mask: 255.255.255.0
Gateway Address: 192.168.1.1

---

### Post by danwood76 on 2008-01-31
> **midnex said:**
> IP Address: 192.168.1.2
Subnet Mask: 255.255.255.0
Gateway Address: 192.168.1.1

Your DNS servers page should look like the page in this attatchment, although the IP address will be different.

If its blank click add and add the IP address 192.168.1.1

regards,
Danny

---

### Post by danwood76 on 2008-01-31
Also I was wondering what happens when you go to this address in firefox: [http://91.189.94.186](http://91.189.94.186) it should load these forums up if you do have a DNS issue.
You would then be at least able to access the forums from ubuntu.

regards,
Danny

---

### Post by midnex on 2008-01-31
dont load again .......

---

### Post by midnex on 2008-01-31
> **danwood76 said:**
> Your DNS servers page should look like the page in this attatchment, although the IP address will be different.

If its blank click add and add the IP address 192.168.1.1

regards,
Danny

YES I Have adreses :[

---

### Post by midnex on 2008-01-31
so any cat help me :confused::confused::confused::confused::confused::(

---

### Post by danwood76 on 2008-01-31
You could try changing the DNS IP address to a public one like:
204.97.212.10

can you ping a set of addresses?

like:
ubuntuforums.org
[www.google.com](www.google.com)
[www.kernel.org](www.kernel.org)

with good results?

Because if it resolves those addresses then maybe its a problem with the way you have firefox configured or some other unknown variable.
It could be something to do with your login credentials on your ADSL or anything.

otherwise im stumpted!

sorry I cant help,
Danny

---

