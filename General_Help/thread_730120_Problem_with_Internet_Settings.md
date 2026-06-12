---
title: "Problem with Internet Settings"
date: 2008-03-20
forum: General Help
---

### Post by parrimin on 2008-03-20
Hi, 

I have just installed Ubuntu Gutsy, and it seems all is running, but internet...

I have installed ssh, so i could connect via putty from my windows computer. The Ubuntu PC is only to install apache php mysql, so i need internet to install them. I was trying to update from repositories, and i discovered i cant connect from ubuntu. 

I cant understand the problem, because the Ubuntu PC is accessible via putty, and it can access the router web administration too. If I ping to [www.google.com](www.google.com), there is response, and all seems to be ok. Can you imagine what could be the problem?

Windows PC get the ip through DHCP, like the Ubuntu PC. I tested changing the cable, and i tested the Windows cable (sure running) in the Ubuntu PC to connect to router, and there is no internet connection.

When I say there is no internet connection, i mean i cant connect to any page from firefox, and synaptic cant connect to repositories either, because if i ping any page, there is good response, and i can connect via ssh or ftp. Helpppp plezzzzzz

---

### Post by Het Irv on 2008-03-20
Do you have a firewall or proxy that could be giving you trouble?  You sound like you have tested everything, so I am not sure. Just make sure you have checked all of the simple stuff, it can really bite you sometimes.

---

### Post by dannyboy79 on 2008-03-20
it's a DNS issue from the sound of it BUT what's weird is that you're able to ping [www.gogle.com](www.gogle.com). Normally if it were a DNS issue you'd only be able to ping by IP addresses not FQDN (fully qualified domain names). Are you sure that the windows box and the ubuntu box don't have the same IP address? It may be that you have firefox setup to use a proxy server, don't know how you could do that accidentally though. Not sure what to suggest. What does this command return?

ifconfig

---

### Post by parrimin on 2008-03-20
> 
server:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:49:0C:BE:DA
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:49ff:fe0c:beda/64 Scope:Link
          UP DIFUSIÃN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:2026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2093 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000
          RX bytes:768419 (750.4 KB)  TX bytes:198247 (193.6 KB)
          Interrupt:17 Base address:0xc000

lo        Link encap:Bucle local
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



This is what ifconfig says. There is no proxy, firefox is not configured for proxy, and as all you i dont have no more ideas to test. 

Is not DNS problem, because [www.google.com](www.google.com), [www.hattrick.org](www.hattrick.org), and other pages are resolved ok while pinging, so,,,

---

### Post by parrimin on 2008-03-20
Ah, and is not only firefox, Synaptic, or apt-get install have problem to connect to repositories. Mmmm, not problem, they are not able to connect to repositories.

---

### Post by dannyboy79 on 2008-03-20
this is VERY strange to say the least. if you can ping [www.gogle.com](www.gogle.com), you should be able to view it thru firefox. what is the exact error for firefox and when you use synaptic.

or try this from the command line

sudo aptitude update

tell me what it says. I gotta go for now, but I subscribed to this thread so I'll be back later.

---

### Post by superprash2003 on 2008-03-21
sometimes due to bad DNS servers(like my isp) i am able to ping but not able to access via browser. .so try changing DNS servers to openDNS 208.67.222.222 and 208.67.220.220 that should solve it

---

### Post by parrimin on 2008-03-22
> **superprash2003 said:**
> sometimes due to bad DNS servers(like my isp) i am able to ping but not able to access via browser. .so try changing DNS servers to openDNS 208.67.222.222 and 208.67.220.220 that should solve it

Sorry for the delay in reply. I have no improvements yet. I don't think there is DNS problem, because my Windows PC and Ubuntu PC are connected to the same router with DHCP settings. Anyway, now im running your openDNS server addresses, and there is no change... Some more ideas plez?

Of course, with the Windows PC there is no problem on internet connection. I am writing in this forum through my Windows installation.

Ah! I thing there is no hardware problem either, because the Ubuntu PC is just formatted. Two days before it has had Windows installed, and there was no problem with internet. 

I only want to try to install a Mail Server and my Web Server in this Ubuntu machine, but of course, if there is no internet connections, not able to do anythin....

---

### Post by parrimin on 2008-03-22
> **dannyboy79 said:**
> this is VERY strange to say the least. if you can ping [www.gogle.com](www.gogle.com), you should be able to view it thru firefox. what is the exact error for firefox and when you use synaptic.

or try this from the command line

sudo aptitude update

tell me what it says. I gotta go for now, but I subscribed to this thread so I'll be back later.


ksoratec@ksoratec-server:~$ sudo apt-get update
[sudo] password for ksoratec:
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg
  No pude conectarme a archive.canonical.com:80 (1.0.0.0), expirÃ³ tiempo para conexiÃ³n
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg
  No pude conectarme a archive.ubuntu.com:80 (1.0.0.0), expirÃ³ tiempo para conexiÃ³n
0% [Conectando a archive.ubuntu.com (1.0.0.0)] [Conectando a archive.canonical.com (1.0.0.0)]


This is the response. The language is spanish. In summary, its saying its not able to connect to the server (normal if you think it can't connect to a web though web browser)

---

### Post by parrimin on 2008-03-22
Hey guys, i have solved!! It was all my fault. Someway, my ethernet card was not running properly. It was able to have LAN connections, but not WAN connections. Why? MMMM No idea. But i tried to change for an old PCI Ethernet card i have, and all is running Ok. Very thanks to all people that has answered!

---

### Post by parrimin on 2008-03-22
Hey, i was wrong, it hasnt been solved. Internet was runnign a while, but... doesnt now. While trying the openDNS ips, [www.google.com](www.google.com) was  ok, but not ubuntu repository ips, and i returned to my old DNS ips. All was going right, but only a few minutes. Now, i am as the first time. Sometimes the ips is resolved ok, sometimes not. But if ip is resolved, the page is not loaded from browser...

Whats happening, any idea?

---

### Post by parrimin on 2008-03-23
Some ideads plz. My temporal solution was to ping to ubuntu repositories, and replacing in sources.list the repositories by the ips. Is running, and i was able to update and install mysql php and apache, but i wish to fix it.

---

### Post by parrimin on 2008-03-23
Nobody have any more idea?

---

### Post by Het Irv on 2008-03-24
If you can get though with the IP's, but not the url, it is a DNS issue.  Have you tried resetting your modem and what not.

---

### Post by parrimin on 2008-03-26
Is not a DNS issue, because i can ping other machines...

---

### Post by Het Irv on 2008-03-26
Can you ping with IP's or Domain Names?
DNS has nothing to do with IP addresses, it converts Domain Names into IP's
DNS is also cached into your system (I don't know where), so one or two sites might be stored localy and therefor they would work.

---

### Post by bobthebob1234 on 2008-03-26
How many ethernet card do you have?

You can get to the cached DNS from  "system - administration - network" Then click on the hosts tab. There you are. You can also check the DNS is entered in the DNS tab!

---

