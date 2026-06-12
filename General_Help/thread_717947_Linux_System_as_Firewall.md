---
title: "Linux System as Firewall?"
date: 2008-03-07
forum: General Help
---

### Post by ShinHadoken on 2008-03-07
I'm pretty sure that it's possible to set up a Linux box as a firewall. How do you do this? I would prefer to do it with Ubuntu, but if I can't, please tell me what distro I need. Thanks!

---

### Post by lswest on 2008-03-07
I do know for a fact there are some firewall linux systems, i have an article in one of my many magazines *glances at an overflowing 4 shelves of computer magazines* i'll get back to you with a name of the OS :P

*edit* i found an article (it seems to be the one i remember :P) about Astaro Firewall V.7, not sure if it's free or not though.  Seems to run on a unix kernel

*Last edit for today* after hunting through literally thousands of CDs i can't find the one pure-Linux firewall OS CD i know i have somewhere, but basically, yes, you can use a linux system as a firewall, it just requires a different configuration than that of a desktop system.

---

### Post by PeterJS on 2008-03-07
Ubuntu itself has everything* you need built in to it. All you need to run a linux based firewall is IPTables which is built in to the kernel itself. IPTables can handle both NAT and filtering. The trick is just getting IPTables configured, if you take the time to learn the monstrosity that is IPTables syntax you can do some ridiculously powerful things. A much more reasonable and real world approach would be to install Firestarter and use it to graphically configure IPTables.

*Software wise that is, a router with only one interface isn't very userful, but that's a hardware issue :)

---

### Post by Dennis on 2008-03-07
I use IPCOP:  [http://ipcop.org/](http://ipcop.org/) and have used Smoothwall:  [http://www.smoothwall.org/](http://www.smoothwall.org/)

---

### Post by pointone on 2008-03-07
[http://distrowatch.com/search.php?category=Firewall&origin=All&basedon=All&desktop=All&architecture=All&status=Active](http://distrowatch.com/search.php?category=Firewall&origin=All&basedon=All&desktop=All&architecture=All&status=Active)

---

### Post by bodhi.zazen on 2008-03-07
Depends on what you are wanting to do exactly.

If you are wanting to set up an old box as a router I advise two nic cards. You do not need much, all you would need to do is configure IP Tables and NAT.

Ubuntu, any distro really, can do this for you. My advice would be to do a minimal install and configure IP Tables.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

If, like us mere mortals, you do not know the lingo of ip tables, be prepared to read, read, read. You will likely find a distro specific to routing  you may like IP Cop or Smoothwall. They are lighter weight and have some helpful tools.

---

### Post by Mithrilhall on 2008-03-07
[http://distrowatch.com/dwres.php?resource=firewalls](http://distrowatch.com/dwres.php?resource=firewalls)

---

