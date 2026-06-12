---
title: "installing new apps through adept (ogle)"
date: 2005-11-02
forum: General Help
---

### Post by tamskp on 2005-11-02
I'd like to install ogle so I can watch dvds, but on the ogle site it tells me to use apt-get - surely this bypasses the adept package manager?  If I install it this way will it still show up in the Kmenu, not just through a shell?

Any hints on how to get adept to find new apps?  Should I download the source file and unpack it to a specific location on the hard drive?

---

### Post by TomG on 2005-11-02
I installed it like this (names may slightly vary as I translate) :
K menu -> System -> Package Manager (add applications)
Searck for *ogle* and you should see several entries.
Choose what you want (i took oKle as on KDE). 
Once done I got a *DVD Player* in my *Multimedia* menu...
Works fine for me ! ;) 

Tom

---

### Post by aysiu on 2005-11-02
Adept is just a graphical front-end for apt-get. They essentially do the same thing.

---

### Post by tamskp on 2005-11-02
I've tried that...the problem seems to be that the package manager won't access the repositories.  It waits for ages for a response, then the only packages available are the ones in the installation package, and I've uncommented the repositories in sources.list, and added new ones that I found on the net.  Still it doesn't seem to be able to access them.  What other things can I check to find out why it won't access the net?

I have also tried the apt-get command in a shell, but the same thing happens.

---

