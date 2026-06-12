---
title: "asterisk"
date: 2005-03-27
forum: General Help
---

### Post by markacc on 2005-03-27
anyone know how to install asterisk on the ubuntu system, i am a non tech

---

### Post by bored2k on 2005-03-27
Enable universe repositories on your *hoary* [In synaptic > settings > repositories > add > select it].

and sudo apt-get install asterisk
[http://higgs.djpig.de/ubuntu/www/hoary/comm/asterisk](http://higgs.djpig.de/ubuntu/www/hoary/comm/asterisk)
[you don't have to get it from here, this just shows that it is available on Hoary's universe repositories] .

---

### Post by youngwax on 2005-04-11
ok, I have installed asterisk and zaptel.  I have run an actual phone system on another (suse) system.  I am having trouble configuring asterisk and zaptel on ubuntu.  why can't I find the wcfxo, wcfxs, zaptel .so's that I want to modprobe into the kernel so it will actually work?

---

### Post by youngwax on 2005-04-13
about installing asterisk: the package itself installs as it should with apt-get or synaptic.  By itself, it offers various sorts of voip.  After it is installed, there is a lot of configuring to do.  There is a manual at [www.digium.com/handbook-draft.pdf](www.digium.com/handbook-draft.pdf).  Digium makes cards that connect asterisk to the phone company, and Digium supports asterisk development.  They developed asterisk.

To use it with pots phones, you need more.  The software to use Digium cards (or other cards) is (should be) in the zaptel package (apt-get or synaptic)  I am stuck at that point, I can't get the cards to work...

---

