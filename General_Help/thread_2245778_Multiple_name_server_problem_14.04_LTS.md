---
title: "Multiple name server problem 14.04 LTS"
date: 2014-09-26
forum: General Help
---

### Post by charles-meo on 2014-09-26
I'm trying to connect to two separate networks one by wire (internal corp) and one by wifi (internet). Corp network has in internal dns server for accessing resources I need to see which are not publicly exposed. The other one is for email etc.

For some reason, I can only resolve DNS using the first name server seen in /etc/resolv.conf. This was raised in a much earlier thread under ubuntu 10 and closed, but I've just hit this issue today with the latest version of ubuntu, and couldn't figure it out. So it seems to be still an issue.

How do I make ubuntu use all the nameservers in the list? And since resolve.conf now appears to be legacy (<snip> where's the win here?) what it is the kosher way to get this going. Connection manager seems to be making a mess of it so replies saying it all happens automagically will be binned. It doesn't.

What am I missing here?

Chuck

---

### Post by redrumrogue on 2014-09-26
Hi there - in your network connection settings you can set additional DNS servers.  Have you tried this already?

---

### Post by charles-meo on 2014-09-29
Yep, didn't help. What I ended up doing was adding some static host entries because I needed to get to work and the number of systems involved was small.

However my two general questions stand:
1. What is the approved way to add nameserver resources for multiple, disparate networks?
2. Does resolv.conf no longer work properly as a workaround? This IMO is a bug if so. It should do what is in the man page:
"If there  are  multiple  servers,  the resolver  library queries them in the order listed. " 
In other OS--even windoze god forbid--this seems to work as expected.

---

### Post by redrumrogue on 2014-09-29
I don't know what others would consider to be the "approved" way, and I'm not aware of one myself.  However, another suggestion I could give is that perhaps you might have some success installing bind9 (DNS Server) on your machine and setup a "caching server configuration" by following the instructions "Caching server configuration" on this web page [https://help.ubuntu.com/community/BIND9ServerHowto#Caching_Server_configuration](https://help.ubuntu.com/community/BIND9ServerHowto#Caching_Server_configuration)

After doing this you set your machines DNS server (in network options) to the bind9 DNS server (probably your localhost).

Here's more info on bind9 caching server config .. [https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-a-caching-or-forwarding-dns-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-a-caching-or-forwarding-dns-server-on-ubuntu-14-04)

I've had to setup bind9 on my home PC because for some reason my external no-ip.org address does not resolve when I try to access it from within my home LAN.  I setup bind9 with a no-ip.org zone ... worked a charm.

I'm not an expert on networking so others may have better suggestions!  No harm in trying bind9 caching server though ...

Hope this helps.

---

### Post by charles-meo on 2014-10-07
Best solution I've seen with the current state of affairs. It'd be far better if resolv.conf worked as documented tho...

Thanks!

---

### Post by redrumrogue on 2014-10-08
Have you tried my solution yet, and did it work?

You keep mentioning resolv.conf ... are you running ubuntu server or desktop?  If you're running desktop then why are you editing resolv.conf instead of going through the UI?  resolv.conf is not supposed to be edited by hand.  As far as I'm aware it gets edited by some scripts when you set the networking properties in the UI.

---

### Post by SeijiSensei on 2014-10-08
The resolver always uses the first server available in /etc/resolv.conf.  It only consults the other servers in the list if the first one is offline.  It most assuredly does not consult a secondary server if the first server cannot resolve a name.

Can't you resolve external addresses on the corporate server?  What if you use "host [www.google.com](www.google.com) ip.of.corp.server"?  Does it resolve?  If so, just use the corporate server for everything.  If you place it first in the list, then take the machine off the corporate network, the resolver will use the next server IP in resolv.conf.

---

