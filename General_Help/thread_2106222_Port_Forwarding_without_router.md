---
title: "Port Forwarding without router"
date: 2013-01-18
forum: General Help
---

### Post by lucky509 on 2013-01-18
Any one plz help me out how to port forward without router in ubuntu 11.04.

---

### Post by steeldriver on 2013-01-18
Hello and welcome

Can you explain a bit more about exactly what you are trying to do? 'Forwarding' usually means from one side of a router to the other side (WAN to LAN)

---

### Post by jimmytbane on 2013-01-18
It is impossible to connect to the internet without a router. Therefore if you have no router. And no internet. How did you make this post. If what you mean is how to port forward without access to the router controlls, maybe for increasing speed of f2p or p2p downloading? Or maybe to make a server for a video game said action is likely impossible. If you don't have access to the password to the router. Maybe because you are a young child or the router owner doesn't trust you. You will need to convince the owner to give you access. If its simply that you can't understand how to use the router. [http://portforward.com/](http://portforward.com/) will help you.

---

### Post by mcduck on 2013-01-18
> **jimmytbane said:**
> It is impossible to connect to the internet without a router. Therefore if you have no router. And no internet. How did you make this post. If what you mean is how to port forward without access to the router controlls, maybe for increasing speed of f2p or p2p downloading? Or maybe to make a server for a video game said action is likely impossible. If you don't have access to the password to the router. Maybe because you are a young child or the router owner doesn't trust you. You will need to convince the owner to give you access. If its simply that you can't understand how to use the router. [http://portforward.com/](http://portforward.com/) will help you.
A router is definitely not needed for connecting to the Internet, even though broadband and cable *modems* made for consumer use often include built-in router and switch functions. A router is just a simple device for separating two networks from each other and managing traffic between them.

---

### Post by efflandt on 2013-01-18
Port forwarding without a router would seem to imply that your computer has a public IP address and that you are trying to use Linux to masquerade a private LAN and forward certain ports in to private IP addresses.  You can web search how to use iptables to masquerade a private LAN.

But you need to provide more details about your network and what you are trying to forward from where to where to get a helpful answer.  Otherwise we may be wasting out time explaining something totally unrelated to what you are trying to do.

---

### Post by lucky509 on 2013-01-19
> **efflandt said:**
> Port forwarding without a router would seem to imply that your computer has a public IP address and that you are trying to use Linux to masquerade a private LAN and forward certain ports in to private IP addresses.  You can web search how to use iptables to masquerade a private LAN.

But you need to provide more details about your network and what you are trying to forward from where to where to get a helpful answer.  Otherwise we may be wasting out time explaining something totally unrelated to what you are trying to do.


We have 2Mbps Vpn connection(total=4locaions) from from our H.O location  to our VPN sites.From H.O location  Only internet Bandwidth sharing to our Vpn sites 4 locations.Now what i want do in 4 locations we have cc cameras .In H.O location installed ubuntu and configured both public Ips and Local lan series in Ubuntu.Now how can i port forward without router in each location.How can i port forward in ubuntu .Can plz explain me the steps for port forwarding.

---

### Post by lucky509 on 2013-01-19
> **steeldriver said:**
> Hello and welcome

Can you explain a bit more about exactly what you are trying to do? 'Forwarding' usually means from one side of a router to the other side (WAN to LAN)

We have 2Mbps Vpn connection(total=4locaions) from from our H.O location   to our VPN sites.From H.O location  Only internet Bandwidth sharing to  our Vpn sites 4 locations.Now what i want do in 4 locations we have cc  cameras .In H.O location installed ubuntu and configured both public Ips  and Local lan series in Ubuntu.Now how can i port forward without  router in each location.How can i port forward in ubuntu .Can plz  explain me the steps for port forwarding.

---

### Post by dradius on 2013-01-19
> **lucky509 said:**
> We have 2Mbps Vpn connection(total=4locaions) from from our H.O location   to our VPN sites.From H.O location  Only internet Bandwidth sharing to  our Vpn sites 4 locations.Now what i want do in 4 locations we have cc  cameras .In H.O location installed ubuntu and configured both public Ips  and Local lan series in Ubuntu.Now how can i port forward without  router in each location.How can i port forward in ubuntu .Can plz  explain me the steps for port forwarding.

I don't think its port forwarding that you need, especially if there are no routers involved.  Depending on how your cameras are set up I would assume they have some sort of client software that talks to your "master" server at the home office?

---

### Post by chadk5utc on 2013-01-20
Lucky
 from what Im gathering your trying to view the CC cameras remotely? Is this correct? If so How do you access them locally? with a web browser? or some other way? Are they networked??

---

### Post by lucky509 on 2013-01-20
> **chadk5utc said:**
> Lucky
 from what Im gathering your trying to view the CC cameras remotely? Is this correct? If so How do you access them locally? with a web browser? or some other way? Are they networked??

yes they are networked with web browser we are lookin localy.For remote monitoring ourpose only i am asking port forwarding

---

### Post by chadk5utc on 2013-01-20
Ok if you do not have routers then youll likely have to pass what ever ports you need through your firewall/server or device that connects all of your locations, without knowing much about your network setup it makes it very hard to give many suggestions. you did mention VPN and that you have 4 total locations, So my guess is that you will likely have to forward these through the VPN server if this is how your locations communicate.

---

### Post by lucky509 on 2013-01-20
> **chadk5utc said:**
> Ok if you do not have routers then youll likely have to pass what ever ports you need through your firewall/server or device that connects all of your locations, without knowing much about your network setup it makes it very hard to give many suggestions. you did mention VPN and that you have 4 total locations, So my guess is that you will likely have to forward these through the VPN server if this is how your locations communicate.

there is no Vpn server in our network.From H.O to 4 locations from ISp leased line connection taken  1Mbps to each location. Internet bandwidth sharing from H.O to 4 sites through this 1Mbps leased line sites.Separate internet bandwidht not taken for 4 sites.So all 4 sites are connected in lan.

---

### Post by chadk5utc on 2013-01-20
> **lucky509 said:**
> there is no Vpn server in our network.From H.O to 4 locations from ISp leased line connection taken  1Mbps to each location. Internet bandwidth sharing from H.O to 4 sites through this 1Mbps leased line sites.Separate internet bandwidht not taken for 4 sites.So all 4 sites are connected in lan.

Ok then Im lost. If you have dedicated lines to all locations from HO what is it your trying to do but are unable to? I dont see any need for port forwarding??

---

### Post by lucky509 on 2013-01-20
> **chadk5utc said:**
> Ok then Im lost. If you have dedicated lines to all locations from HO what is it your trying to do but are unable to? I dont see any need for port forwarding??
in lan we can access viewing cameras of all locations in Wan i want to view cameras remotely for that i want confiure port forwarding without router

---

### Post by chadk5utc on 2013-01-20
> **lucky509 said:**
> in lan we can access viewing cameras of all locations in Wan i want to view cameras remotely for that i want confiure port forwarding without router

OK I understand that. Now the question is do any of the locations have internet access? And how is that access provided? there has to be some device that connects the "LAN" to the outside world? Which in most but not all cases is a server, router or firewall?

---

### Post by lucky509 on 2013-01-20
> **chadk5utc said:**
> OK I understand that. Now the question is do any of the locations have internet access? And how is that access provided? there has to be some device that connects the "LAN" to the outside world? Which in most but not all cases is a server, router or firewall?

For all sites internet bandwidth sharing  from H.o location only.in H.O location isp own router there but they not give access for us.to port forwarding anything.Thats way H.O location installed ubuntu with public ip configuration

---

### Post by steeldriver on 2013-01-20
I'm still not sure I understand what you're trying to do but it sounds like you need to *tunnel* the camera stream via a protocol that your ISP supports - e.g. over SSH

---

### Post by lucky509 on 2013-01-20
[QUOTE=steeldriver;12464589]I'm still not sure I understand what you're trying to do but it sounds like you need to *tunnel* the camera stream via a protocol that your ISP supports - e.g. over SSH[/QUOT

just i want to view cameras remotely in wan network.without port forwarding in router.Is their any way to port forwarding instead of router in ubuntu 11.04

---

### Post by Cheesemill on 2013-01-20
> **lucky509 said:**
> in H.O location isp own router there but they not give access for us.to port forwarding anything

In that case what you want to do isn't possible, changes have to be made to the settings on the router.

You will need to talk with your ISP to come up with a suitable solution.

---

### Post by dradius on 2013-01-20
> **Cheesemill said:**
> In that case what you want to do isn't possible, changes have to be made to the settings on the router.

You will need to talk with your ISP to come up with a suitable solution.

Maybe, maybe not.

Lucky- have you tried to access the cameras the same way you would on the "LAN" but from a remote machine?

---

### Post by lucky509 on 2013-01-21
> **dradius said:**
> Maybe, maybe not.

Lucky- have you tried to access the cameras the same way you would on the "LAN" but from a remote machine?
  In Lan from remote machine its accessing no problem i want to access from Wan network

---

### Post by HermanAB on 2013-01-21
You could do a reverse tunnel with netcat, socat, ncat or ssh, if you have a machine somewhere that is reachable by the two sides of the problem.

---

### Post by dradius on 2013-01-21
> **lucky509 said:**
> In Lan from remote machine its accessing no problem i want to access from Wan network

What happens when trying across WAN?

---

