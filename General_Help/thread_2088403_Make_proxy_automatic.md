---
title: "Make proxy automatic?"
date: 2012-11-26
forum: General Help
---

### Post by lestertorres on 2012-11-26
Hi everyone,

I have setp up *SQUID3 PROXY* on my server with a *ISC-DHCP-SERVER* and it works great when I hook up a client to the server *eth1*.

The issue that I am having is that I am hooking up my server to a switch that will be for my company of 80-85 clients and I want to make the proxy turn on automatically because I have do it manually for the client I am using right now. 

Is there a way to do this?

Thanks for all the help in advance guys. If I figure it out I will let you all know how I got this to work. 

Party on! :guitar:

---

### Post by lestertorres on 2012-11-26
If I made the squid transparent would it make a difference?

---

### Post by lestertorres on 2012-11-29
So I have done some researching and found out that by making the proxy transparent it will give clients proxy automatically but cannot seem to quite figure out the correct setting. I added the word "transparent" to my squid.conf int the network option area to the port section...
*http_port 3128 transparent*
I also added 
[I]iptables -t nat -A POSTROUTING -s 192.168.2.0/24 &#8211;o eth0 -j MASQUERADE
[/I]
to the /etc/rc.local file and still nothing when testing a client to eth1. Any help would be highly appreciated. Thanks everyone.

---

### Post by btindie on 2012-11-29
You probably won't be able to use a transparent proxy with your current setup as it works at the network layer.

To find out how it works take a look at:
[http://en.wikipedia.org/wiki/Proxy_server#Transparent_proxy]("http://en.wikipedia.org/wiki/Proxy_server#Transparent_proxy")
[http://tldp.org/HOWTO/TransparentProxy-2.html]("http://tldp.org/HOWTO/TransparentProxy-2.html")

You would either need to use your Linux box as the gateway on your network to force all traffic through it, redirecting the required ports through SQUID, or have your current gateway/firewall configured to redirect all HTTP(S) traffic via your Linux box but allow your Linux box direct access to the internet.

---

