---
title: "&lt;B&gt;UBUNTU 8 working very slow without an internet connection&lt;/B&gt;"
date: 2008-06-29
forum: General Help
---

### Post by hc1501 on 2008-06-29
Hey,

My PC config are

AMD 4000+ X2
ASUS M2n MX SE
160 Sata
512 DDR2 Ram


I have installed UBUNTU 8 for the past 2 weeks. initially it worked perfectly. But as soon as I configured my broadband and started using it, it became very slow whenever I'm not connected to it. If I start UBUNTU without connecting to the internet then it starts in about 10 minutes and that too with most the applications not opening like Synaptic, Administration, etc. As soon as I start the broadband it gears up its speed. I have dual boot with WIN XP. Please help me out....


Here is a copy of my /etc/hosts




127.0.0.1 harshit-deski.aaaa
127.0.1.1 harshit-deski.aaaa

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by ar0n on 2008-07-02
I think its because of the resolver trying to resolve localhost.

Add this to your hosts file: 

127.0.0.1 localhost.localdomain localhost

---

