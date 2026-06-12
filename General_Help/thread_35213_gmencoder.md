---
title: "gmencoder"
date: 2005-05-18
forum: General Help
---

### Post by silent82 on 2005-05-18
hello,

I've tried to install gmencoder, but I have some probelms.

I've downloaded **gmencoder** debian package form ***[http://gmencoder.sourceforge.net/](http://gmencoder.sourceforge.net/)*** and the first problem was the dependency... I downloaded and installed all dipendecy libs trough apt-get. The only library not found in the ubuntu archives was **liblinc1** so I downloaded **liblinc1_0.1.21-1_i386.deb** form the ***[http://packages.debian.org/](http://packages.debian.org/) site.*** 

The only problem is that the **liblinc1** is in conflict with **liborbit2** . If I ***dpkg -i --force-all liblinc1_0.1.21-1_i386.deb*** all seems to work fine, but every time I ***apt-get install something*** it tells me about the conflict.

Anyone knows how to fix the conflict?

Tanks!

---

### Post by a_hanley on 2007-08-09
I found a useful link that does not seem to have the dependency problems

[http://download.ubuntu.pl/_Breezy_Badger/gmencoder/](http://download.ubuntu.pl/_Breezy_Badger/gmencoder/)

Hope this helps :-)

---

