---
title: "Ubuntu on a beowulf cluster?"
date: 2007-11-13
forum: General Help
---

### Post by HPCE_Larry on 2007-11-13
I'm curious if Ubuntu will work on a computing cluster, and if not, what would be the recommended distro? I know redhat works, but I don't think its free. The cluster will have anywhere from 50 to 100 cpu's.

---

### Post by PaganHippie on 2007-11-13
It should work, and the particular distro shouldn't matter.  (I assume you're asking about K/X/Ubuntu here.)  Since most of the systems in the cluster wouldn't even need desktops, 'Server Install' should suffice.

There's information [here]("http://www.informatik.uni-koeln.de/fai/fai-guide/ch-beowulf.html") on setting up a Beowulf cluster using Debian which should apply pretty closely, if not exactly, to Ubuntu.

All this comes with the *caveat* that I have not tried it myself, so I can't speak to its relative ease or difficulty.  Good luck and *bon appetit*.

---

### Post by HPCE_Larry on 2007-11-13
Thanks that is deffinitally helpful. By distros I was actually referring to other linux distros (ie redhat, centos, etc). Anyone know if any of these is better/easier or not?

---

### Post by PaganHippie on 2007-11-14
As far as I know the particular distro shouldn't matter, so long as you've installed exactly and only what you need to run the cluster.  Anything extraneous probably wouldn't prevent things from working, but they might slow things down a bit.

The only HOWTOs for Beowulf that I've seen online refer to either RedHat ([Fedora]("http://fedoraproject.org/") is very close and completely free; have you looked into it?) or Debian (which has many relatives including Ubuntu).  If you really want to optimise for performance, you might look into [Slackware]("http://www.slackware.com/"), [Gentoo]("http://www.gentoo.org/"), or [LFS]("http://www.linuxfromscratch.org/") (Linux From Scratch).  I'm sure any of them could be made to work in Beowulf clusters, but Gentoo and LFS are a bit too hairshirt for my taste.  I like distros with installers that pick up my hardware without grief (which is why I'm a huge Ubuntu fan).

---

### Post by hikaricore on 2007-11-14
Imagine an overused slashdot comment here!

lol

---

### Post by PaganHippie on 2007-11-14
ouch!

---

### Post by mahousaru on 2007-11-14
The most important thing about clustering isn't really the kit (well not in the beginning), but it is the problem you want to solve and how you will break it down.  For example some problems are better solved with fast HPC clusters whilst others like the SETI project are better solved by getting as many nodes as possible and the speed of the links don't matter.  

But in regards to clustering in general why not try out some of the ready made solutions like Rocks Cluster or Knoppix Cluster?  With Rocks you can just add nodes to the cluster and it can automatically install the OS via PXE.  With Knoppix you guessed it you can run the nodes off memory via PXE.

[http://www.rocksclusters.org/wordpress/](http://www.rocksclusters.org/wordpress/)

[http://clusterknoppix.sw.be/](http://clusterknoppix.sw.be/)

Whatever you decide on if you come across some sites defending the Microsoft Cluster solution you best get ready for a huge dose of MS fan boy reality...

---

