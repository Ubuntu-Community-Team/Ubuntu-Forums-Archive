---
title: "thunderbird2"
date: 2007-08-23
forum: General Help
---

### Post by n.aggel on 2007-08-23
hi, i am searching in synaptic for thunderbird2 and i can't find it..... how can i iinstall thunderbird2 without using automatix?

---

### Post by rainwalker on 2007-08-23
It's called "mozilla-thunderbird" in Synaptic, try searching for that

---

### Post by por100pre1 on 2007-08-23
Use [Ubuntuzilla.py]("http://ubuntuzilla.wiki.sourceforge.net/") to install Thunderbird 2. You won't go wrong with it. :)

---

### Post by n.aggel on 2007-08-23
> **rainwalker said:**
> It's called "mozilla-thunderbird" in Synaptic, try searching for that
this is what i already have installed, but it is version 1.5....and i want to install 2...

---

### Post by n.aggel on 2007-08-23
> **por100pre1 said:**
> Use [Ubuntuzilla.py]("http://ubuntuzilla.wiki.sourceforge.net/") to install Thunderbird 2. You won't go wrong with it. :)
i used your advise and downloaded the script from sourcforge... Everything is working smooth...

Some questions though:

why i can't do the  update from synaptic?
why the script downloaded automatix{at least it downloaded something from automatix}?

PS:: if anyone want to update thunderbird, he must type::

ubuntuzilla.py -p thunderbird

---

### Post by nanotube on 2007-08-23
> **n.aggel said:**
> i used your advise and downloaded the script from sourcforge... Everything is working smooth...

Some questions though:

why i can't do the  update from synaptic?
why the script downloaded automatix{at least it downloaded something from automatix}?

PS:: if anyone want to update thunderbird, he must type::

ubuntuzilla.py -p thunderbird

re: synaptic: because they don't do major upgrades once a release of ubuntu has been made, so feisty is stuck with tb 1.5.

re: download: the script does not download anything from automatix. it downloads the mozilla releases straight from releases.mozilla.org.

---

### Post by davidjmayo on 2007-08-23
DELETE
Nanotube replied already

---

### Post by n.aggel on 2007-08-23
> re: synaptic: because they don't do major upgrades once a release of ubuntu has been made, so feisty is stuck with tb 1.5.

my mistake then...I thaught that synaptic was updated automatically....each it fetched the sources...

---

### Post by nanotube on 2007-08-23
> **n.aggel said:**
> my mistake then...I thaught that synaptic was updated automatically....each it fetched the sources...

well, minor security updates do get pushed through to synaptic during the life of an ubuntu version. so, e.g., you'd get upgrades from 1.5.0.11, to 1.5.0.12. but they don't push out major upgrades, from 1.5.x to 2.0.x. 

so you're right, synaptic does update the package lists automatically, and they do put out some security updates. it's just that major software upgrades are generally not included.

so if you're looking just to be running software with the latest security patches, synaptic is just fine.

hope that clarifies things. :)

---

