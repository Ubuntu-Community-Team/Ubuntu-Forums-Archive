---
title: "stupid question: what happen when I compile"
date: 2005-10-11
forum: General Help
---

### Post by towsonu2003 on 2005-10-11
I am a newbie and SCARED of debian... My question is; 
after getting the kernel headers, what happens if I compile a package myself from source with make and make install instead of using a debian/ubuntu package? I know it won't be updated automatically, but are there issues with compiling other than that (introcuding bugs, or causing instability or vulnerabilities etc)??

---

### Post by Pablo_Escobar on 2005-10-11
Apt-get "checkinstall".
and then : 
1. ./configure 
2. make 
3. sudo checkinstall 
any program You want.

It'll make a deb file and it'll install it. If it's broken you can always remove it from Synaptic.

---

### Post by mlomker on 2005-10-11
Pablo makes a good suggestion.  Checkinstall doesn't work with every package but it's a nice tool.  My only advice with packages that you've done *make install* on is to keep the source directory.  That way if you decide to remove it some day you can *make uninstall*.

---

### Post by towsonu2003 on 2005-10-11
nice
thanks so much!

---

