---
title: "Apache2 Files missing, where to get them from?"
date: 2005-05-20
forum: General Help
---

### Post by drx on 2005-05-20
Hello dear Ubunters,

as it seems i made a big mistake: While playing with my Apache2 configuration files i brought them to a state where nothing worked anymore. So i decided to remove the package "apache2" and "apache2-common"; but this left some config files in place, especially "apache2.conf". So i decided  to just wipe out the complete apache2 directory and reinstall.

As i did this now, Apache2 cannot find its file "apache2.conf" anymore -- it is not there and as it seems no default is restored when reinstalling. So i wonder where the initial apache2.conf came from and how to restore Apache2 in a way that it is like from out of the box.

Any help would be appreciated,
thanks 1024 times,
drx

---

### Post by shakin on 2005-05-20
Backup any data you have in /var/www and mark all apache2 packages for complete removal, then install them again from scratch.

---

### Post by Gandalf on 2005-05-20
you myst purge it so

sudo apt-get remove --purge apache2 apache-common
(install them if they are uninstalled before running the above command)

then install them again

---

### Post by drx on 2005-05-22
thanks!! that worked exactly!

---

### Post by Gandalf on 2005-05-22
[QUOTE=drx]thanks!! that worked exactly![/QUOTE]
 no problem

---

