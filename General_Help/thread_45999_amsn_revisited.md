---
title: "amsn revisited"
date: 2005-07-02
forum: General Help
---

### Post by Sipper on 2005-07-02
Hi Guys

I'm trying to install amsn. I downloaded the .deb file for ubuntu and when running dpkg -i *.deb I get the following error message.

__Cut
 amsn depends on imlib1; however:
  Package imlib1 is not installed.
 amsn depends on sox; however:
  Package sox is not installed.
 amsn depends on libpng10-0; however:
  Package libpng10-0 is not installed.
 amsn depends on docker; however:
  Package docker is not installed.
 amsn depends on tcltls; however:
  Package tcltls is not installed.
dpkg: error processing amsn (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amsn
__

However if I try and apt-get any of the above they all fail dependancies on each other.

Can someone help me out here please.

Thanks

Sipper

---

### Post by Sipper on 2005-07-02
Aaaarghhh

I just ran sudo apt-get -f install and everything was done for me.


Sipper

---

### Post by djgenesis on 2006-04-12
Just in case.. If anyone else gets a similar error, open synaptic and look for amsn. 
It will install everything for you automatically :D

---

