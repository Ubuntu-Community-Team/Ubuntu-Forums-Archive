---
title: "need help  to install  on correct partition"
date: 2008-05-26
forum: General Help
---

### Post by klemencic on 2008-05-26
I have 3 HDD on installed in my system, 1 is used for Windows, 1 partitioned as /home and the other as /root
I have installed Flightgear using Synaptic but it installed most if not all of its files into /root but I want all of my programs installed onto the drive /home
Can someone please explain how this is done

---

### Post by pointone on 2008-05-26
It isn't done--that's not how the [Linux Filesystem Hierarchy]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/") is designed. Programs are installed into /usr, normally.

Also, please try not to confuse ("/root": root's home directory) with ("/": the root directory).

If you want to install into /home, you will need to either compile from source, or manually extract packages and copy files into place.

---

### Post by klemencic on 2008-05-27
OK thanks for that
It seems I might have partioned my drive wrong them.  I remember reading somewhere where you can partition the drive and if anything happens and you need to reformat, you can just reformat the one partition containing Ubuntu and you can keep all of your other installed programs - or was that just /home

---

### Post by zvacet on 2008-05-27
You didn´t partition wrong.If you need to reformat you can save all your packages with [APTonCD.]("http://aptoncd.sourceforge.net/") I post you link just to read it and see what APTonCD is.You can install it from synaptic.

---

