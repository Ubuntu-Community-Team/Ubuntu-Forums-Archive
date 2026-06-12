---
title: "setiathome wont install"
date: 2006-10-21
forum: General Help
---

### Post by Monk22 on 2006-10-21
i was installing some stuff with the synaptics package manager one file was setiathome.  all i get is this loop over and over

> monk@Masamune:~$ sudo dpkg --configure -a
Setting up setiathome (3.08-4) ...
setiathome-3.08.i686-pc-linux-gnu.tar not found in /tmp.
--18:51:14--  [ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar](ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar)
           => `/tmp/fileXNwQya'
Resolving alien.ssl.berkeley.edu... 128.32.18.176
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21...


how do i make it stop trying to install this package?

---

### Post by randomnumber on 2006-10-22
sudo apt-get remove setiathome
i think

if not try, in gui
System -> Administration -> Synaptic Package Manager
  search for setiathome
  mark for removal
  apply changes

---

### Post by Monk22 on 2006-10-22
thanks the "remove setiathome" command worked, that was the problem when i went into synaptic package manager it told me that i needed to run dpkg whatever -a and then closed thanks for the help

Josh

---

