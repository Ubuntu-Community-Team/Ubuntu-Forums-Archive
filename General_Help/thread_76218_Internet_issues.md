---
title: "Internet issues"
date: 2005-10-14
forum: General Help
---

### Post by nelposto on 2005-10-14
Hey people,

So I just last night decided to give this whole linux thing a go, grabbed live (it should be LIVE! but I think that's been done before) and booted up. Had to use a parameter for my laptop because it wouldn't display properly but in the end it was all sorted.

Soooo came into it, lovely and slick, after being lost for about 5 minutes I found where I could enable my ethernet and wireless business, but after I did that I still had issues.

Using DHCP, it grabbed the settings ok by itself, but I at first couldn't browse anywhere in firefox, connect thru gaim, irc, download apps etc. But I could browse to my router 192.168.... etc. 

So then using network tools I manage to ping any domain.com, and with the ip address that it puts out from that, I can browse to it. 

So I was on the IRC channel and a helpful chap reccommended me changing an option in firefox network.dns.disableIPV6 to true. So now firefox works fine.

My DNS server (router) is in /etc/resolv.conf.

Any ideas on how to get the rest of my connectivity happening?

Thanks


...oh and also while I'm here... Ubuntu won't recognise my laptop's subwoofer so tunes sound a little weak atm.. any way around this as well?

---

### Post by manicka on 2005-10-14
I'd try just configuring things manually to see if it makes a difference.

---

### Post by nelposto on 2005-10-14
.. no luck.... :(

---

### Post by nelposto on 2005-10-14
bumped for the fellas up the front

---

### Post by manicka on 2005-10-14
Has DHCP set up your dns server correctly. The reason I ask is that my router always provides itself as the dns server address and it need to be my providers dns server address, hence I have to enter it manually.

---

### Post by nelposto on 2005-10-14
That was it, thanks!

I didn't fully understand those settings but now that I see what the values were supposed to be it's clear that the router was putting itself as the DNS.

Thanks again.

---

### Post by manicka on 2005-10-15
okay, glad things worked out :)

Enjoy your Ubuntu and welcome to Linux

---

