---
title: "WUBI and rootkits?"
date: 2007-10-04
forum: General Help
---

### Post by nooby on 2007-10-04
I looked through serveral threads and failed to find an answer for WUBI. 

I'm a noob so bear with me. When one do a WUBI install of ubuntu Gutsy around November. 

Will such an install also be vulnerable to rootkits? 

linuxworld.com warn about rootkits on linux servers. 
They had asked the owners of the servers if they knew they was used as control centers for bots doing attacs on the net. the owners had no idea such was happening. 

Does that mean that programs like check root kit doesn't detect them? 

That the bad guys have more advanced code already? 

As a noob one could get scared for less. If even advanced users fail to see these how are we able to know about them? 

So my simple question. Is a virtual machine like wubi isntall protecting me from rootkits? 

Are there any other way to not get them? 

Linuxworld had a text about it recently. I try to find link to it. Back soon

[http://www.linuxworld.com/news/2007/100407-ebay-phishers-linux.html?fsrc=rss-linux-news]("http://www.linuxworld.com/news/2007/100407-ebay-phishers-linux.html?fsrc=rss-linux-news")
> "The vast majority of the threats we saw were rootkitted Linux boxes, which was rather startling. We expected Microsoft boxes," he said.

Rootkit software covers the tracks of the attackers and can be extremely difficult to detect. According to Cullinane, none of the Linux operators whose machines had been compromised were even aware they'd been infected.

---

### Post by ago on 2007-10-04
> **nooby said:**
> 
Will such an install also be vulnerable to rootkits? 


Wubi security model is identical to standard Ubuntu. Wubi will be as secure as Ubuntu.

> 
Does that mean that programs like check root kit doesn't detect them? 

I am by no means an expert, but for what I understand it depends on the rootkit, kernel rootkits are very difficult to detect. Kernel rootkits are not a Linux-only thing, quite the opposite...

> 
As a noob one could get scared for less. If even advanced users fail to see these how are we able to know about them? 

Standard Ubuntu settings should be more than good enough (all ports are closed, viruses are unheard of and automatic updates fix most outstanding issues fairly rapidly and not least packages are signed). Even more so if you use a firewall router. This does not make you invulnerable, but it makes your machine substantially more secure than 99% of computers out there. That means you can still be targeted individually (and if that happen you would stand little chance), but there are millions of far easier prays...  

> 
So my simple question. Is a virtual machine like wubi isntall protecting me from rootkits? 

Wubi is not a virtual machine. It is a standard dual boot installation. If you want to improve security you can run a caged linux (vm or other) for browsing and similar activities. There are plenty of articles on how to improve security.

> Are there any other way to not get them?
Hmm a rootkit is not like virus. A rootkit is used AFTER  a machine has been cracked to cover the tracks so that the machine can be used without the owner sospecting anything. Viruses are one way to crack a machine (not so much in the linux world). There are other means as well, but without open ports it would be substantially more difficult.

My guess is that many machines are simply cracked by brute force attacks, many "advanced" users have ssh or other such tools with weak passwords... In fact in a recent honeypot study all of the unix machines that were cracked, were cracked by brute force. This paradoxically makes "advanced" users somewhat more exposed than regular users, since regular users are unlikely to have ssh or open ports to worry about.

---

### Post by nooby on 2007-10-04
Thanks!

---

