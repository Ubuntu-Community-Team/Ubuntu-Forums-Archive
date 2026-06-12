---
title: "simon listens [ i need help]"
date: 2013-02-19
forum: General Help
---

### Post by spiders on 2013-02-19
Hi All

I am trying to install a program called simon listens... So

I use the following commands:

```

sudo add-apt-repository ppa:grasch-simon-listens/simon 

```Which brings up heaps of stuff but importantly at the bottom

```

W: Failed to fetch http://ppa.launchpad.net/grasch-simon-listens/simon/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/grasch-simon-listens/simon/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/grasch-simon-listens/simon/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found



```
And just on the off chance :)

```

$ sudo apt-get install simon
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: Unable to locate package simon


```Any help would be appreciated

Spiders

---

### Post by Yellow Pasque on 2013-02-19
It means the PPA doesn't have any software for your version of Ubuntu, quantal/12.10

---

