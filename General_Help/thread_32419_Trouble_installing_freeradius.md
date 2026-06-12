---
title: "Trouble installing freeradius"
date: 2005-05-07
forum: General Help
---

### Post by makimonaco1 on 2005-05-07
I am totally new with LINUX. My Company installs WINDOWS based RADIUS servers and I am trying to re-orient them towards LINUX.

I have installed Ubuntu  Warty Warthog 4.10 on my Celeron 2.4 system and everything seemed to go okl: I can go on the net, edit files...

I downloaded a RADIUS package called freeradius from [www.freeradius.org](www.freeradius.org) into my /home/maxo directory. Following the install instructions from that directory I enter the command line:

[COLOR=Navy]maxo@ubuntu:~/freeradius-1.0.2 $[/COLOR] [COLOR=Red]./configure[/COLOR]

and get the following result:

[COLOR=Red]loading cache ./config.cache
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH[/COLOR]

Can you help me?

Thanks.

---

### Post by reckless2k2 on 2005-08-13
If you didn't find the answer or someone tell you, open synaptic and install the kernel-source, headers, and GCC. That should give you enough to get going with the install. 

I was new to linux some time ago and wasn't lucky enough to have forums this good. Sorry a response took so long. 

Good luck.

---

### Post by thilupas on 2007-05-15
open the terminal and type:
sudo apt-get install build-essential


good lucky!!

---

