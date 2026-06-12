---
title: "Freevo python2.4 package dependency problem"
date: 2005-04-18
forum: General Help
---

### Post by tinkaj on 2005-04-18
I tried to install Freevo by adding
deb [http://freevo.sourceforge.net/debian](http://freevo.sourceforge.net/debian) unstable main
to my sources.list

but when I ran
apt-get install freevo
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed.
...

The following packages have unmet dependencies:
freevo: Depends: python (< 2.4) but 2.4-0ubuntu6 is to be installed
E: Broken packages

Freevo doesnt work with python2.4 it needs 2.3 . Is there anyway to tell apt to use python2.3 instead?
I have 2.3 and 2.4 installed.
 
Or do I have to download the packages directly from [http://freevo.sourceforge.net/debian/dists/unstable/main/binary-i386/](http://freevo.sourceforge.net/debian/dists/unstable/main/binary-i386/)
and do something with dpkg?
 ](*,)

---

### Post by TravisNewman on 2005-04-18
if you search for python in synaptic, you can install 2.3, however this may or may not work for you. Depending on how the package is built. If that doesn't work, you'd have to uninstall 2.4 and then install 2.3, but that may be more trouble than it's worth.

---

### Post by n3X_VI on 2005-06-23
are there any news about the freevo install problem? 

maybe any workaround?

greets, n3X

---

