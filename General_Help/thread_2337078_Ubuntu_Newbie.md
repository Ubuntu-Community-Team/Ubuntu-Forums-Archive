---
title: "Ubuntu Newbie"
date: 2016-09-14
forum: General Help
---

### Post by tadrazen on 2016-09-14
What is the best application to be download after installing Ubuntu 16.04

Thanks

Drazen

---

### Post by howefield on 2016-09-14
Thread moved to the "*General Help*" forum.

Ask 20 different people and you'll likely have 20 different answers, only you can answer this question for yourself. If you are serious try asking something a bit more specific ?

---

### Post by Impavidus on 2016-09-14
Ubuntu comes with most of the stuff most people need installed automatically, the most notable exception being popular software with restrictive licenses. You may not need all of it and you may need other software, but it's up to you to decide what you need.

---

### Post by &amp;KyT$0P# on 2016-09-14
> **tadrazen said:**
> What is the best application to be download after installing Ubuntu 16.04
Synaptic package manager ;)

Install it by entering these commands in the Terminal
```
sudo apt-get install apt-xapian-index
sudo apt-get --no-install-recommends install synaptic
```

---

### Post by #&amp;thj^% on 2016-09-14
Just to make everyone aware of apt-xapian-index Bugs is why they do not include it 16.04
[https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/655831](https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/655831)
[http://osdir.com/ml/ubuntu-bugs/2016-09/msg07313.html](http://osdir.com/ml/ubuntu-bugs/2016-09/msg07313.html)
Not to mention some space it hogs up.
vasa1 has more information also on this.

---

### Post by &amp;KyT$0P# on 2016-09-14
I've always installed apt-xapian-index on Ubuntu since 14.04 and I've never had any issues, not even in VMs with limited resources... not that that necessarily means much though :mrgreen:

Anyway it's only needed if you want the quick filter feature of Synaptic, otherwise feel free to skip that step (run only the second command).

---

### Post by tadrazen on 2016-09-15
hi sir what is the use of this

---

### Post by ian-weisser on 2016-09-15
> **tadrazen said:**
> hi sir what is the use of this

Ask the package database for the software description. Open a Terminal. Try:
```
apt show apt-xapian-index
```

---

### Post by &amp;KyT$0P# on 2016-09-15
> **tadrazen said:**
> hi sir what is the use of this
Synaptic package manager will, among other things, make it easier for you to find the best application(s) for *your* intended use of Ubuntu 16.04.  Lots of software in the repositories, and installing from the repositories is safer way to get software in Ubuntu.

---

