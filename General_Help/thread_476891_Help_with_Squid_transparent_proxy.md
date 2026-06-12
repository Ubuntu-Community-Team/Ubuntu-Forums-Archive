---
title: "Help with Squid transparent proxy"
date: 2007-06-17
forum: General Help
---

### Post by kr0w on 2007-06-17
Hi there!

I'm trying to set a transparent proxy with Squid 2.6. The proxy seems to work perfect, as it does what it should if I configure it in a web client (Opera in my case): so the squid.conf is fine.
But if I remove the Opera proxy configuration and I set the iptables rules to forward the 80 port requests to the squid's 3128 listening port, it stops working.
The gateway is a router which (theorycally) is forwarding the port 80 requests to the proxy server's port 80, but here's where the problem seems to be.

Here's an ugly draw of what it should do:

[[IMG]http://img266.imageshack.us/img266/5844/proxywb3.png[/IMG]](http://imageshack.us)
When I intend to access a website, my gateway (router) should redirect my request to the proxy server (listening on port 3128 ) so it get 'proxied', and then go to the internet.

There must be some simple thing that I'm missing, but dunno what... :S

---

### Post by kr0w on 2007-06-18
anyone? :S

---

### Post by awreneau on 2007-08-20
I'm doing almost the same thing, only thing different in my case is that I'm using a cable modem and a Linksys firewall/router.

They key for me here is transparency.  If I configure the browser on the client it works, if I remove the proxy setting no one can get anywhere.


The linksys router is also a wireless access point.  I dont advertise my SSID but I'm sure a savvy person could find me.  I'd like to force all wireless traffic into the proxy as well.  


Sure hope somebody answers this post.

---

