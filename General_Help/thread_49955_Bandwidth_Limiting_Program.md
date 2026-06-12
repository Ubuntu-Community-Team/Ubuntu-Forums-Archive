---
title: "Bandwidth Limiting Program?"
date: 2005-07-18
forum: General Help
---

### Post by Phixion on 2005-07-18
Hello, can anyone tell me of a bandwidth limiter for Linux? I used to use NetLimiter but I need an alternative.

Thanks for everything

---

### Post by amohanty on 2005-07-18
If you are only concerned about web access, look at squid and the concept of delay pools, or for some other solutions:

[http://sourceforge.net/projects/cbqinit/](http://sourceforge.net/projects/cbqinit/)
[http://sourceforge.net/projects/htbinit/](http://sourceforge.net/projects/htbinit/)
shaper0 for linux
for the bsds there is something called ALTQ

I would suggest setting up a cheap OpenBSD box (my P3 500/15GB HDD and CRT cost only about 80.00 USD) as a firewall and use ALTQ or ipf/dummynet? to throttle bandwidth.


HTH
AM

---

### Post by Phixion on 2005-07-18
[QUOTE=amohanty]If you are only concerned about web access, look at squid and the concept of delay pools, or for some other solutions:

[http://sourceforge.net/projects/cbqinit/](http://sourceforge.net/projects/cbqinit/)
[http://sourceforge.net/projects/htbinit/](http://sourceforge.net/projects/htbinit/)
shaper0 for linux
for the bsds there is something called ALTQ

I would suggest setting up a cheap OpenBSD box (my P3 500/15GB HDD and CRT cost only about 80.00 USD) as a firewall and use ALTQ or ipf/dummynet? to throttle bandwidth.


HTH
AM[/QUOTE]

Thanks, I'm looking for something to cap my download / upload speed so I don't lag my brother out on our LAN, I'm connected to a Linksys Router.

Is there anyway I can get something that'll work for me with apt-get?

I'm relatvely new to Linux and I'd rather install things the easy way.

Cheers

---

### Post by amohanty on 2005-07-18
Sorry! I am not aware of any thing in the repos. One easy way to manage source built apps is via 'checkinstall'

Install that via synaptic. 

Then for any source.tar.gz
>> tar xzf source.tar.gz
>> cd source...
>> ./configure --prefix=/usr/local 
This will put all your files under /usr/local for easy manual removal if you need to, checkinstall helps in that you can use dpkg for that (dpkg kinda like apt-get but for debian packages on local systems)
>> make
>> checkinstall
for x86_64 kernels may have to do >> checkinstall -A amd64

This will create a .deb package for you and install it. To remove the app just do:
>> dpkg -r source

HTH
AM

---

### Post by Phixion on 2005-07-18
[QUOTE=amohanty]Sorry! I am not aware of any thing in the repos. One easy way to manage source built apps is via 'checkinstall'

Install that via synaptic. 

Then for any source.tar.gz
>> tar xzf source.tar.gz
>> cd source...
>> ./configure --prefix=/usr/local 
This will put all your files under /usr/local for easy manual removal if you need to, checkinstall helps in that you can use dpkg for that (dpkg kinda like apt-get but for debian packages on local systems)
>> make
>> checkinstall
for x86_64 kernels may have to do >> checkinstall -A amd64

This will create a .deb package for you and install it. To remove the app just do:
>> dpkg -r source

HTH
AM[/QUOTE]

Thanks for everything, I'll give it a go :)

---

