---
title: "Problems launching applications from cluster accounts"
date: 2007-06-11
forum: General Help
---

### Post by m.milway on 2007-06-11
I am bulding up some Feisty (7.04) boxes on Dell Optiplex 745 hardware to use on our existing Linux cluster. I can log on happily using cluster or local accounts. I can access the home directories on the network. I have some startup scripts that run from /common. Running editors and compilers from the command line works OK. From that point of view I believe that I have correctly joined our cluster (but i am open to correction on this).

However, when I start some applications from the Applications menu, it takes several minutes for them to start up. Others start up immediately.

The following applications start slowly:
Applications-->Internet-->Firefox web browser
Applications-->Office-->Kile
Applications-->Programming-->KDevelop C/C++

The following applications start quickly:
Applications-->Accessories-->Calculator
Applications-->Accessories-->terminal
Applications-->Games-->Solitaire
Applications-->Office-->OpenOffice

All these applications start up quickly if I log in with a local account.

Firefox came pre-installed. I installed Kile and KDevelop after I joined the cluster.

There appears to be an issue to do with launching applications using cluster accounts. Are the any system variables or entries in files like /etc/hosts that need to be set up?

Regards,
Michael Milway
University of Wollongong.

---

### Post by dini on 2007-06-15
Hi !

(Sry I'm French ;) )
	
Maybe I can help you, I am currently studying the various solutions of cluster available on Ubuntu, and set up a cluster to load balancing applications like OpenOffice Firefox ..

 I have to ask to you which is the solution of cluster which you use?

---

