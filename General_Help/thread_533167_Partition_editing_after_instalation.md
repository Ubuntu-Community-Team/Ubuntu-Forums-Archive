---
title: "Partition editing after instalation"
date: 2007-08-23
forum: General Help
---

### Post by malfist on 2007-08-23
I just installed ubuntu and I tried to set up a '/' and a '/home' partition but it didn't seem to work. What I've got right now is a 18GB partition with everything on it and a blank ext3 partition that's >100GB. How can I merge the two?

Malfist

---

### Post by merlinus on 2007-08-23
Use gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

You may want to split that big partition up into smaller ones.  If so, best to create an extended partition, and then logical ones within that so you do not risk overstepping the limit of four primaries.

Info here on creating a separate /home after install:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

-merlin

---

### Post by stinger30au on 2007-08-23
you can also install gparted under applications and the install program options.just select the button that says "show all" and search on gparted

---

### Post by malfist on 2007-08-23
you can't edit active partitions. I'll get the gparted live CD

---

### Post by merlinus on 2007-08-23
Problem with using gparted installed versus live version is that you will have to unmount partitions before sizing/moving, and cannot do that with the ubuntu partition since it is being used.

Also, the live cd is a later version, with more features and capabilities than the one in the ubuntu repos or on its install cds.

-merlin

---

### Post by bodhi.zazen on 2007-08-23
FYI : Gutsy has the updated version of gparted :

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gparted&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gparted&searchon=name&subword=1&version=all&release=all)

---

