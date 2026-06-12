---
title: "how to remove added keys?"
date: 2007-09-26
forum: General Help
---

### Post by maduranga on 2007-09-26
hello... i have followed a tutorial and added following keys, but now want to remove them.

wget [http://flomertens.keo.in/ubuntu/givre_key.asc](http://flomertens.keo.in/ubuntu/givre_key.asc) -O- | sudo apt-key add -
wget [http://mirror.ubuntulinux.nl/1135D466.gpg](http://mirror.ubuntulinux.nl/1135D466.gpg) -O- | sudo apt-key add -

 the problem is i can't recognize them in the synaptic>repositories>Authentication.

and please can someone tell me what keys are added in a default ubuntu installation? 


---thanks----

---

### Post by rsambuca on 2007-09-26
Post a screenshot of your keys.

---

### Post by maduranga on 2007-09-26
thanks for helping. the a screenshot is attached. :)

---

### Post by /etc/init.d/ on 2007-09-26
The only keys that ship with Ubuntu are the two Automatic Signing Keys.

The Quinn Storm and lupine keys you have are for the Compiz 3D effects, if you're using those then it would probably be best to keep those keys.

---

### Post by maduranga on 2007-09-26
thanks, i just installed ubuntu and now i have automatix and envy installed and configured. other than that, all things should be still in as the defaults, i think.

---

