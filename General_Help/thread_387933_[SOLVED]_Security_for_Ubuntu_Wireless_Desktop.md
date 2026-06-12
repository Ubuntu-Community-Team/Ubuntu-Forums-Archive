---
title: "[SOLVED] Security for Ubuntu Wireless Desktop"
date: 2007-03-18
forum: General Help
---

### Post by JawsThemeSwimming428 on 2007-03-18
I am currently running Ubuntu 6.06LTS (Dapper Drake). I am somewhat a Linux new-comer, I have only been using Ubuntu for about 8 months. I want to find a good firewall and some type of AntiVirus program to ensure a clean and secure system and I am not sure what to go with. I am using FireStarter right now but I don't feel it is a good defense. I was looking into Bastille but it seems difficult to configure. Anyone have any reccommendations? Thanks!

---

### Post by simonn on 2007-03-19
--- whoops double post --

---

### Post by simonn on 2007-03-19
> **JawsThemeSwimming428 said:**
>  I am using FireStarter right now but I don't feel it is a good defense.

Why not? It is a front end to iptables which is pretty good.

---

### Post by mcduck on 2007-03-19
Iptables is as good as firewall can be, and Firestarter is a great tol for configuring it. If you want more hardcore iptables configuration than Firestarter can do you could try this Arno's Iptables Firewall. It's the best one I've ever seen (altough not as easy to setup & configure as Firestarter is): [http://rocky.eld.leidenuniv.nl/]("http://rocky.eld.leidenuniv.nl/").

What comes to antivirus, there's no need for such thing. There's no viruses to scan for, all linux antivirus programs are made to scan for Windows viruses, and are meant to be used on mail servers and such.  (not that you would actually need a firewall either, unless you install some servers on your machine. In default Ubuntu setup there is no programs listening to any port..)

---

