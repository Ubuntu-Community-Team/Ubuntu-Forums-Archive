---
title: "Firewall aMule problem"
date: 2006-11-06
forum: General Help
---

### Post by kikazaru on 2006-11-06
I just installed ubuntu 6.10, and am trying to get amule working. 

I managed to connect, search and upload files, but couldn't download them and get a low ID. I checked the amule docs and there's a page where you can check your ports are open. It tells me the port is being blocked:
[B]
Error: TCP port 4662 is unavailable. Make sure your firewall or router is allowing/forwarding this TCP service port and your ED2K client is running (i.e. aMule, eMule).[/B]

I didn't manually block the port, and I didn't activate the firewall. I ran system->administration->firestarter, and unblocked all the ports the amule uses, including 4662 but I still get the error. 

Is there another firewall I need to configure?
Did anyone else have the same problem?
Any suggestions?

I had it working on the same system under debian linux so I know there should be no problem with my hardware etc.

---

### Post by sebastfr on 2006-11-06
> **kikazaru said:**
> I just installed ubuntu 6.10, and am trying to get amule working. 

I managed to connect, search and upload files, but couldn't download them and get a low ID. I checked the amule docs and there's a page where you can check your ports are open. It tells me the port is being blocked:
[B]
Error: TCP port 4662 is unavailable. Make sure your firewall or router is allowing/forwarding this TCP service port and your ED2K client is running (i.e. aMule, eMule).[/B]

I didn't manually block the port, and I didn't activate the firewall. I ran system->administration->firestarter, and unblocked all the ports the amule uses, including 4662 but I still get the error. 

Is there another firewall I need to configure?
Did anyone else have the same problem?
Any suggestions?

I had it working on the same system under debian linux so I know there should be no problem with my hardware etc.

Do you connect to Internet via a router or is your adsl modem connected to your machine?

If you are behind a router, then you need to setup Port Forwarding on the router so that people from outside (internet) can connect to the port 4662 of your machine....

let us know

Seb

---

### Post by kikazaru on 2006-11-06
Thanks for the super fast reply Seb.

I am using YahooBB, which is one of the major providers here in Japan.
They gave me an ADSL modem. I can only connect one computer to it (computer to modem to phone socket), although you can attach an "IP phone" to it and use that simultaneously. 

I didn't set up any port forwarding when I had amule running under Debian... although I remember it was problematic setting it up for some reason.

---

### Post by taurus on 2006-11-06
I bet your ADSL modem has a building firewall!  Why don't you call your ISP and ask them if there is a build in firewall on that thing and if there is, how to access it.  You need to open whatever ports you want if you want incoming traffic.

---

### Post by kikazaru on 2006-11-07
Thanks for the suggestion. I managed to get to the settings of my modem/router. I put 172.16.255.254 into a web browser and I got the setup page.

There's a section called "port forwarding", but I'm not sure what I need to fill in. I get

WAN side port (RPort) : 
Protocol : TCP/UDP
Forwarding target port number (LPort) :
Forwarding target IP address :

I guess I should forward port 4662 to 4662 with the TCP protocol, but what IP address should I put in...?

---

### Post by bignickel on 2006-11-07
I think you should forward at least one TCP port, and you might get better results if you also forward a UDP port.  Check [this site]("http://www.amule.org/wiki/index.php/Firewall") and look at how they do it on one of the generic routers.

As for your IP, I think it's much easier if you use static IP (and not DHCP).  If you do that, then just type ifconfig on your ubuntu machine to see your IP, and put that into the firewall.

---

### Post by sebastfr on 2006-11-07
> **kikazaru said:**
> Thanks for the suggestion. I managed to get to the settings of my modem/router. I put 172.16.255.254 into a web browser and I got the setup page.

There's a section called "port forwarding", but I'm not sure what I need to fill in. I get

WAN side port (RPort) : 
Protocol : TCP/UDP
Forwarding target port number (LPort) :
Forwarding target IP address :

I guess I should forward port 4662 to 4662 with the TCP protocol, but what IP address should I put in...?

You need two entries, one for tcp, and one for udp:

WAN side port: 4662
Protocol: TCP for entry #1, UDP for entry #2
Forwarding target port number: 4662
Forwarding target IP address: the IP of your machine running aMule

that should do :)

seb

EDIT: I agree with bignickel (we must have replied at pretty much the same time he he) about DHCP -> keep static IP on that machine or tell your DHCP server to always lease the same IP to that machine (the machine running aMule that is)

---

### Post by kikazaru on 2006-11-07
Wow, most excellently fast replies. 

Thanks indeed. 

I will try and set things up as your suggest.

...and bingo! It's working... yeehaw. Thanks again for your help Seb and Bignickel!

---

