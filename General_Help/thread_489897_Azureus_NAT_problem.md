---
title: "Azureus NAT problem"
date: 2007-07-01
forum: General Help
---

### Post by sirab on 2007-07-01
My NAT is stuck on white.

When I try to download a torrent it says


> Connection error(ConnectionException:Connection Refused)

I did go to terminal and try this out

>  iptables -I INPUT -p tcp --dport <65534> -j ACCEPT

but I get

>  syntax error near unexpected token `65534'

so please help

---

### Post by Praill on 2007-07-01
This would be handled by your router. Your routers WAN IP might be 204.23.34.124. This is your address once the signal leaves your router. However internally your router distributes "internal ips" so that more than one computer can use the same connection. Your internal IP may be something like 192.168.1.2.

Azureus can be set up to make transfers on a particular unique port and then the router can be setup to forward all requests on that port to a particular computer within your house (or office). So you need to set this up inside the router. 

The best way to do it is to enable a rather common feature called upnp (or up2p cant really remember) in newer routers. This makes the router a "smart" port forwarder that will handle everything for you. You'll also have to enable this somewhere in the azureus settings.

The general fool proof and older way to do this is to manually set up port forwarding in your router to forward all traffic on the particular port azureus is using to your computers IP.

And the frowned upon, unsafe, but functional way is to put your particular computer in your routers DMZ so that it bypasses the NAT and firewall.


I hope this isnt too technical of an explination but I find the best way to solve a problem is to fully understand it. Good luck.

---

### Post by sirab on 2007-07-01
It wasn't too technical.

Now I just need to know how to do all that lol

Thank you though now I understand my problem better =]

---

### Post by sirab on 2007-07-02
Ok now I connected my computer to a wired network and when i try to download I get 4 error messages
> 
UPnP: Mapping 'Incoming Peer Data Port (UDP/65534)' has been reverved by 'some.number.im.not.stupid.enough.to.post' - please select a different port

> UPnP: Mapping 'UDP Tracker Client Port (UDP/65534)' has been revered by 'some.number.im.not.stupid.enough.to.post' - please select a different port
> 
UPnP: Mapping 'Incoming Peer Data Port (TCP/65534)' has been reverved by 'some.number.im.not.stupid.enough.to.post' - please select a different port
> 
UPnP: Mapping 'Distributed DB (UDP/65534)' has been reverved by 'some.number.im.not.stupid.enough.to.post' - please select a different port

I did change the port but when I do I get the exact same message with the new port number.

---

### Post by d_xtremw on 2007-07-02
lol i jus posted a thread about this same thing.. more or less. anyways praill i too have that problem. only it says my NAT is okay but my DHT is firewalled. can you offer an explanation for that. 

ps. your explanation was kinda technical :$. i understood most of it but there were still sum things i didnt quite get and dont know how to do. can you tell us how to go into the router and do this?? i think i already know my external IP address if thats helpful in anyway

---

### Post by sirab on 2007-07-02
My DHT is all fine and dandy its green my NAT just doesnt even turn a color it stays blank.

---

### Post by Praill on 2007-07-02
> Ok now I connected my computer to a wired network and when i try to download I get 4 error messages
Quote:
UPnP: Mapping 'Incoming Peer Data Port (UDP/65534)' has been reverved by 'some.number.im.not.stupid.enough.to.post' - please select a different port
Quote:
UPnP: Mapping 'UDP Tracker Client Port (UDP/65534)' has been revered by 'some.number.im.not.stupid.enough.to.post' - please select a different port
Quote:
UPnP: Mapping 'Incoming Peer Data Port (TCP/65534)' has been reverved by 'some.number.im.not.stupid.enough.to.post' - please select a different port
Quote:
UPnP: Mapping 'Distributed DB (UDP/65534)' has been reverved by 'some.number.im.not.stupid.enough.to.post' - please select a different port
I did change the port but when I do I get the exact same message with the new port number.

UPnP has already set up port forwarding for a different internal ip (probably for the one you leased when you connected wirelessly). It can't set it up for two. You could go into the router, find the port forwarding section and clear it, or power cycle the router (may and may not clear it).

> NAT is okay but my DHT is firewalled.
If DHT is being firewalled then there is no port forwarding set up for packets using the UDP protocol. You need to set up seperate port forwarding rules for TCP and UDP packets. UPnP-enabled routers along with a UPnP-enabled client should usually do this for you though.

---

### Post by d_xtremw on 2007-07-02
> **Praill said:**
> 

If DHT is being firewalled then there is no port forwarding set up for packets using the UDP protocol. You need to set up seperate port forwarding rules for TCP and UDP packets. UPnP-enabled routers along with a UPnP-enabled client should usually do this for you though.


how can i tell if my router/ client has already done this (which i guess it hasnt). and how can i do this myself?

---

### Post by Praill on 2007-07-02
> **d_xtremw said:**
> how can i tell if my router/ client has already done this (which i guess it hasnt). and how can i do this myself?
I could never provide specific instructions as they vary with different hardware. Most likely your router is set up to use UPnP port forwarding. It is probably just a matter of enabling UPnP within azureus. If that doesnt fix in then google a solution for port forwarding with your particular router.

---

### Post by d_xtremw on 2007-07-02
aight well what i've done so far:

went into my router information and assigned a specific range of ports to transfer upnp infortmation to a specific ip address(my laptop) . but for sum reason azureus still shows that my DHP is firwaalled

---

### Post by Malik on 2007-10-16
i dont have a router and my thing stays on yellow how do i fix?

---

