---
title: "Locking the proxy"
date: 2007-12-24
forum: General Help
---

### Post by MarkCrossley on 2007-12-24
Does anyone know how to lock the proxy settings throughout ubuntu. The situation is that we are wanting to run an ubuntu awareness course at a secondary school, however before we can we have to demonstrate that pupils will not be able to access the internet, except through a designated proxy.

---

### Post by alan34 on 2007-12-24
You need  this. It is in the Synaptic Package Manager- search for squid . Takes some setting up but works well.

You will need fixed IP addresses for your network.

[http://www.squid-cache.org/](http://www.squid-cache.org/)

Good Luck

---

### Post by MarkCrossley on 2007-12-24
Looking at the website it looks like squid is caching software to run a web cache.

What I need is for each machine to be locked down to a specific proxy (eg 192.168.5.1for example) - ie a proxy server that is already set up.

Not having any experience of squid that might be what it does, but it doesn't look like it at first glance.

---

### Post by MarkCrossley on 2007-12-25
I know that it is possible to lock firefox's settings so that the proxy can't be changed in firefox...but presumably if another web browser was installed the proxy settings wouldn't automatically be transferred over.

---

### Post by alan34 on 2007-12-25
The set up is like this from the internet into the internal network

 Internet  - Router - Office Hub - Server/All other computers

(Crossover cat5 cable between router and office hub) - please google it - wired differently)

The Router needs setting up to only take http requests from the server, so no other
computers on the network can go out directly to the internet. This is what you really need
to set up for your goal but then you need a proxy server otherwise no Internet for any
other computers.

This means all requests for Internet pages from the other pcs on the network must
be directed to the server. Via in Firefox - Edit - Preferences - Advanced - Network - Proxy Settings

So say your server has the IP address 192.168.10.10 you would enter that in Firefox Proxy Settings 
on the other pcs and normally port 80 ( although this can be changed in squid  settings ).

Then you have to configure squid for your needs. I installed squid where I work and with this setup 
gives complete control of internet access to the system administrator. 
I think you will find that it is worth the effort but not a task for the fainthearted.

Good luck again

Normally Routers can save their configuration to a file via using a web browser to access
the setting make sure you save it before making any changes to the Router settings in case
things go wrong. I am not sure but I think you have to look in NAT settings on the Router.

---

