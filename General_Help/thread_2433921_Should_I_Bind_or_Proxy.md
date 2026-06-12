---
title: "Should I Bind or Proxy?"
date: 2019-12-27
forum: General Help
---

### Post by monsonj on 2019-12-27
I am developing a server stack. I am hosting a website, a cloud server, a friendica server, a mastodon server, and a couple of game servers with web based remote consoles.

All these are web based interfaces. I am using a single domain to communicate with these services, but I will also be hosting a multiple domain web server. 
All of this is connected to a single router with a single IP address provided by my ISP.
Mail is not included as it is going to be on a completely separate IP address from my ISP.

Here is my example 
[www.example.com](www.example.com) would be routed to 192.168.0.100
friendica.example.com would be routed to 192.168.0.101
mastodon.example.com would be routed to 192.168.102
cloud.example.com would be routed to 192.168.0.103
game1.example.com would be routed to 192.168.0.104
and finally
[www.example2.com](www.example2.com) would be routed to 192.168.0.100

*** each of the above internal IP addresses are connected to a separate physical machine. *******

My initial thought was to build a bind9 server on 192.168.0.106 and have it listen for all incoming web traffic and redirect accordingly. However i have been unable to find a resource that explains how to do this. Then I came up with building a proxy server to handle this, however I am still unclear on how proxy servers work. I thought before I went down another rabbit hole and spend hours tying to pull my hair out, I would ask if I was on the correct path with either of these methods, or is there a simpler way to do this?

---

### Post by TheFu on 2019-12-28
DNS won't help with internal IPs.

You need to use a **reverse-proxy**.  That is very different from a proxy, which is normally used by end-users to access a filtered internet.
ha-proxy, nginx, apache pound and a few others can perform the task of a reverse-proxy.  I've used pound and currently use nginx.

I doubt you need separate machines for each of those servers.  Since they are all internet facing, the risk factors for each is basically the same, so only the server load and stack for each specific service should be considered.  For example, I run all php web-apps inside a single VM with 1GB of RAM and 1 vCPU.  On of those is a voice/video conference server for family use and easily handles 4 concurrent people.  I be freindica would easily run on a small raspberry pi v2 box, but suspect game1 would need more CPU and RAM.  "cloud", if that is nextcloud/owncloud, I run that on my shared php VM.

Might consider using Linux Containers for those.  They are much lighter than full VMs.

Might also consider some network security design considerations.  Please don't put any non-internet-facing servers on the same subnet.  No desktops, no wifi, no IoT or phones or printers or tablets or desktops on that same subnet.  Setup firewall rules between any subnets as needed to allow access in, but not out.  Please.

---

### Post by SeijiSensei on 2019-12-28
Using Apache you need multiple <VirtualHost> declarations with a ProxyPass statement in each. See [https://confluence.atlassian.com/conf59/using-apache-with-virtual-hosts-and-mod_proxy-792499654.html](https://confluence.atlassian.com/conf59/using-apache-with-virtual-hosts-and-mod_proxy-792499654.html) for an example.

---

### Post by monsonj on 2019-12-28
There will only be these machines on this network. It is a static IP provided by my ISP, and has no other purpose than to service these servers.
I have a second static IP for my mail and mail gateway servers.
I have a separate dynamic IP address for everything else. I am using 3 separate routers, one for each WAN IP so there is no crossover or worry about subnets.
The static IPs were dirt cheap at $9.99/ month on my business account.
The reason for all these machines being separate is that;
 1) I have the equipment. (6 R710 and 4 R310) so I want to spread load across the machines. 
2) I plan on making this a business with Web hosting, Email hosting, and Cloud services, so I want the business portion to be separate from the "hobby" portion.

Thank you for your recommendations I will be looking into revers-proxy and try to wrap my head around it.

---

