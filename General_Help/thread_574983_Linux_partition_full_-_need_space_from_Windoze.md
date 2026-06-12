---
title: "Linux partition full - need space from Windoze"
date: 2007-10-13
forum: General Help
---

### Post by davehkent on 2007-10-13
I have ubuntu 7.04 dual-booting on an old pc running windoze 98. The partition for ubuntu is now 98% full, so I would like to allocate the space used by windoze to the ubuntu partition i.e remove windoze 98 completely. 

I've loaded Gparted from Synaptic, but read on another post that I can't use this whilst running ubuntu - is this true? Will I have to use my ubuntu live cd or the Gparted cd? And once the program is running, what do I actually need to do - reduce the windoze partition to zero size and increase the ubuntu partition accordingly? Step-by-step instructions would be appreciated. 

Also, with windoze removed, will this stop the pc from booting up - is there anything else that needs to be changed? Sorry about all the questions, but I really do not want to muck this up. 
Regards 
davehkent

---

### Post by Pumalite on 2007-10-13
You need th stand alone program:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Boot from it and resize your partition.

---

### Post by bodhi.zazen on 2007-10-13
> **davehkent said:**
> I have ubuntu 7.04 dual-booting on an old pc running windoze 98. The partition for ubuntu is now 98% full, so I would like to allocate the space used by windoze to the ubuntu partition i.e remove windoze 98 completely. 

I've loaded Gparted from Synaptic, but read on another post that I can't use this whilst running ubuntu - is this true? Will I have to use my ubuntu live cd or the Gparted cd? And once the program is running, what do I actually need to do - reduce the windoze partition to zero size and increase the ubuntu partition accordingly? Step-by-step instructions would be appreciated. 

Also, with windoze removed, will this stop the pc from booting up - is there anything else that needs to be changed? Sorry about all the questions, but I really do not want to muck this up. 
Regards 
davehkent

You can not resize a mounted partition, so since you want to resize root, /, you need to work from a live CD.

You need an updated version of gparted to do this operation, either the version on 7.10 , gutsy , or the  gparted live CD.

Follow the links / advice Pumalite gave you.

---

