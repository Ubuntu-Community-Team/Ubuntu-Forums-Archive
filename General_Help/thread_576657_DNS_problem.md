---
title: "DNS problem"
date: 2007-10-15
forum: General Help
---

### Post by prow on 2007-10-15
I've asked this question many times in the networking forum and no one seems to know what the problem is....

When i open up firefox and type in a web address say "www.ubuntuforums.org" and press enter or click go it gives me a "the connection was reset error. but when i press refresh it will then load the page. it does this for every page i visit.

it even does this when i use apt-get to install packages (fails the first time but if i try it again it works)

can someone tell me what i can check.

i know its not a router problem because all my other windows computers access the internet just fine.

---

### Post by holodad on 2007-10-15
It seems you have DNS problems...
DNS is quit easy and simple. If you have a DSL router, the DNS to use is the ip of the router. Ex:
If you pc is having the ip: 192.168.1.2 and the default gateway of your pc is 192.168.1.1, then most likely, the ip of the DNS will be 192.168.1.1
Yes, your router acts like a relay to the public DNS that your provider gives to you when you connect to the internet.
If you have problems, you can fix the dns on your computer. You can set two DNS on your computer. Set the primary DNS to the ip address of your router. Set the secondary DNS of your computer to the fallowing ip address: 194.2.0.20.
This DNS is a french public DNS that you can use for testing purpose.... The best solution is to use one of your provider DNS as a secondary DNS on your PC.
If your computer is in DHCP, see if you can enter a DNS on the web interface of you router. If you can't do that, the only solution will be to use static settings...



Cheers

---

### Post by prow on 2007-10-15
my dns on my ubuntu machine is exactly the same as the dns on my windows laptop so its not the dns settings in the network manager.
anyone else?

---

### Post by prow on 2007-10-16
bump

---

