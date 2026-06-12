---
title: "Bittorrent not downloading - all ports open"
date: 2006-12-17
forum: General Help
---

### Post by wiggie on 2006-12-17
My torrent downlodas just don't work regardless of what client I use. I have opened the necessary ports with firestarter and on my router. I don't see how it still doesn`t work.

On my laptop which runs windows, I can download without any problems. I even tried using wine and running utorrent and it still doesn't work.

Perhaps you could give me some suggestions. I must mention that it worked fine before I did something with firestarter, where I couldn't even browse. So I suppose I accidentally closed all the ports and then had to reopen them manually. But I also opened the ones for torrent :confused: 

I'm running edgy.

Thanks in advance

---

### Post by TheWizzard on 2006-12-17
in your router, remove the entries for port-forwarding to your laptop.

---

### Post by wiggie on 2006-12-18
> **TheWizzard said:**
> in your router, remove the entries for port-forwarding to your laptop.

Could you give me an explanation of why I should do that or what you think the issue is? I could for example assign other ports to my linux machine.

---

### Post by BlahMan_of.Doom on 2006-12-18
Avoid using port 6880-6889, because those are generally attacked by ISPs.

---

### Post by wiggie on 2006-12-20
Yes, I know I've read a lot about the dos and don`ts of torrents so I did not choose those ports. I just think that when the torrents are being tracked, other ports than the ones designated are being requested and those are blocked. Hence no valid connection is possible.

---

### Post by TheWizzard on 2006-12-21
> **wiggie said:**
> Could you give me an explanation of why I should do that or what you think the issue is? I could for example assign other ports to my linux machine.

because the router cannot forward the same port to two computers.

---

### Post by dannyboy79 on 2006-12-21
> **TheWizzard said:**
> because the router cannot forward the same port to two computers.

 i was just going to post this when I read the first couple threads. i use bittornado and belong to a few register only torrent sites. i have added a block of 10 ports to be forwarded to each one of my machines within my router. then made sure that my firwalls were letting these ports thru. i get awesome speeds in both winbloz and ubuntu. i luv bittorrent!!! i love bittornado because I chose the exact ports I want it to use, and also randomize them so it's not always using the same ports. this way my isp hopefully won't catch on and close that port down.  so just make sure that you're forwarding ten different ports to each of your machines and your firewalls allow these ports and you should have no problem.

---

### Post by wiggie on 2007-01-19
Ok, well I tried many things, I tried many clients, some of which crashed but the problem remains. 

I decided to use ktorrent, it seems to be well configurable and easy to use and stable and fast.

So I forward port 54000 in my router and let it through my firewall.
The UDP tracker port is set to 54009 and I also checked `Use DHT to find additional peers' and I set it to 54001. All these ports are open in my firewall and forwarded by my router.

I then start a download and look at the output of firestarter and this is what I get:
> 
Time:Jan 19 17:42:57 Direction: Unknown In: Out:eth0 Port:1900 Source:192.168.178.26 Destination:239.255.255.250 Length:162 TOS:0x00 Protocol:UDP Service:SSDP
Time:Jan 19 17:42:58 Direction: Unknown In: Out:eth0 Port:6881 Source:192.168.178.26 Destination:68.61.173.232 Length:44 TOS:0x00 Protocol:TCP Service:BitTorrent
Time:Jan 19 17:42:58 Direction: Unknown In: Out:eth0 Port:6887 Source:192.168.178.26 Destination:65.78.25.100 Length:44 TOS:0x00 Protocol:TCP Service:BitTorrent
Time:Jan 19 17:42:58 Direction: Unknown In: Out:eth0 Port:6881 Source:192.168.178.26 Destination:72.181.177.154 Length:44 TOS:0x00 Protocol:TCP Service:BitTorrent
Time:Jan 19 17:42:58 Direction: Unknown In: Out:eth0 Port:9090 Source:192.168.178.26 Destination:75.18.204.28 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 19 17:42:58 Direction: Unknown In: Out:eth0 Port:46666 Source:192.168.178.26 Destination:203.155.1.252 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 19 17:43:01 Direction: Unknown In: Out:eth0 Port:6881 Source:192.168.178.26 Destination:68.61.173.232 Length:44 TOS:0x00 Protocol:TCP Service:BitTorrent
Time:Jan 19 17:43:01 Direction: Unknown In: Out:eth0 Port:6887 Source:192.168.178.26 Destination:65.78.25.100 Length:44 TOS:0x00 Protocol:TCP Service:BitTorrent
Time:Jan 19 17:43:01 Direction: Unknown In: Out:eth0 Port:6881 Source:192.168.178.26 Destination:72.181.177.154 Length:44 TOS:0x00 Protocol:TCP Service:BitTorrent
Time:Jan 19 17:43:01 Direction: Unknown In: Out:eth0 Port:9090 Source:192.168.178.26 Destination:75.18.204.28 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 19 17:43:01 Direction: Unknown In: Out:eth0 Port:46666 Source:192.168.178.26 Destination:203.155.1.252 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 19 17:43:04 Direction: Unknown In: Out:eth0 Port:9090 Source:192.168.178.26 Destination:75.178.188.104 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 19 17:43:04 Direction: Unknown In: Out:eth0 Port:8105 Source:192.168.178.26 Destination:80.229.28.7 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 19 17:43:04 Direction: Unknown In: Out:eth0 Port:49125 Source:192.168.178.26 Destination:71.114.211.2 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 19 17:43:04 Direction: Unknown In: Out:eth0 Port:48472 Source:192.168.178.26 Destination:80.213.126.185 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 19 17:43:04 Direction: Unknown In: Out:eth0 Port:60000 Source:192.168.178.26 Destination:193.110.62.120 Length:44 TOS:0x00 Protocol:TCP Service:Unknown


It is quite clear that none (well ok, the ones that are used aren`t displayed) of those ports that I forwarded are used, but instead the ones I didn't forward, like the typical 6881.

What am I not understanding here?

---

### Post by TheWizzard on 2007-01-19
do you have outbound policies in firestarter?

---

### Post by wiggie on 2007-01-20
Yup, 

outbound is restrictive by default and all the ports that I mentined before are allowed, both outbound and inbound. I even added the default bittorent ports from 6881-6889, but I guess that doesn't matter because my router won't have them open.

i will try with permissive by default set on. But I think that is a bad idea, since I cannot blacklist all the ports I don`t normally use.

The question still remains: Why are ports being used other than the ones I designated? Are they used by the torrent client or is there something else that chooses them randomly?

---

### Post by TheWizzard on 2007-01-21
> **wiggie said:**
> Yup, 

outbound is restrictive by default and all the ports that I mentined before are allowed, both outbound and inbound. I even added the default bittorent ports from 6881-6889, but I guess that doesn't matter because my router won't have them open.


bittorent doesn't work properly if you have outbound policies. 
open outbound policies in firestarter and make sure your router isn't blocking them.

---

