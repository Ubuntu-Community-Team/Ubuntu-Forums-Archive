---
title: "Making my computer &quot;invisible&quot; to the outside world"
date: 2006-10-30
forum: General Help
---

### Post by titancomputing on 2006-10-30
Okay, I know there are hundreds of Winblows XP tools that help make your computer "invisible" to the outside world on the internet. They claim to be able to not only hide your IP address, but also make it look like it's a completely different set of numbers. They claim they also seal up all the ports but the ones you specify, keep your passwords and drives encrypted, etc. Point being they basically turn your computer into a stealth machine. I was wondering how might one go about these effects with Ubuntu. I have a router and a cable modem, and I'd like very much to conceal my IP to all possible. Plus I'd love to have the ability to change what users see is my real IP. Sealing up ports I'm assuming can be done with a firewall, but things like blocking port scans and the like I don't know about. How can I make my computer the stealthiest little Ubuntu box on the block? Also, is there a port scanner available for Ubuntu? Just curious.. THanks in advance. :cool:

---

### Post by tronica on 2006-10-30
This is what i use,its a proxy. i have a tor server setup, and all my machines connect through it then to the net. very easy to use.

[http://tor.eff.org/](http://tor.eff.org/)

but of course you can just install it on your machine, instead of a dedicated server.

---

### Post by skymt on 2006-10-30
The only real way to conceal your IP is to use a proxy. Tor, as linked to in the previous post, is very secure, but also very slow. There are a lot of proxies out there, some free but slow and unreliable, some paid but fast and always available. It's your choice.

Also, for web surfing, you'll want Privoxy and NoScript. The former is a proxy that cleans various tracking methods from HTML (web bugs and the like). The latter is an extension for Firefox that disables Javascript, and lets you enable it for trusted sites only.

As far as port scanners go, the industry standard, nmap, is in the repositories. I think the Edgy has latest nmap, but Dapper is stuck with a very old 3.x version.

---

### Post by titancomputing on 2006-10-30
So without using a proxy to MAJORLY slow down my connection, there's no way to appear to be coming from a different IP than I really am? IP Masquerading maybe?

---

### Post by skymt on 2006-10-30
> **titancomputing said:**
> So without using a proxy to MAJORLY slow down my connection, there's no way to appear to be coming from a different IP than I really am? IP Masquerading maybe?

No. There is no way. IP Masquerading is Linux-ese for NAT, network address translation, which you're already doing (since you're behind a router). You're may be thinking about IP spoofing, which wouldn't be practical. The server you connect to needs your IP address, otherwise it can't know where to send the response.

---

### Post by NT4usB on 2006-10-30
How do you know you're not?
Go to grc.com and try the port probe on the shields up page. That'll give you an idea where you're at now.

---

### Post by ejket on 2006-10-30
Yes, grc.com is good ... I buttoned up my router using their advice, and everything has gone well in the years since.

---

