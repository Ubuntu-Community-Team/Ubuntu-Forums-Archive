---
title: "Missing kernel scripts?"
date: 2007-10-12
forum: General Help
---

### Post by the.drizzle on 2007-10-12
Hi there!  I am very new to Xubuntu--this is day one with 7.04--and it seems to be working fine.  Sort of.

I need to get the winmodem on this box up and running, as it is the only way it will be able to connect to the internet.  It should be possible, as scanModem says its a conexant HSF modem that is supported by the open-source driver at

[http://www.surak.eti.br/linux/ubuntu/deb/conexant/](http://www.surak.eti.br/linux/ubuntu/deb/conexant/)

so that's all good.  The problem is, though, when I go to make the module, I get a heap of errors I don't understand, such as 

/bin/sh: scripts/genksyms/genksyms: not found

I see the source files are there, but I cannot build them.  In fact, if I even try to run make menuconfig at /usr/src/linux, all I get is a heap of errors!  Sorry, I can't post them here, as the computer that is having trouble is the one that still cannot connect to the internet!

Like I say, this is day one with Xubuntu, and I am really confused...  I'm assuming that somehow I'm supposed to use apt-get or something like that to put on the missing files (sorry, I am only familiar with Gentoo and am lost with Debian based distros) so that make can actually find the stuff it needs?  If that's all it is, what is name of the package I'm supposed to get?

Many thanks in advance, and sorry if this was a "dumb" question--I'm just stumped!

---

