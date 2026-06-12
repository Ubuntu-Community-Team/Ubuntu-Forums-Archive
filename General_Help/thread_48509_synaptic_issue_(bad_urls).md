---
title: "synaptic issue (bad urls)"
date: 2005-07-12
forum: General Help
---

### Post by ephman on 2005-07-12
hey,

i'm trying to install a couple packages through synaptic and i get this bad message:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0_0.8.5-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0_0.8.5-2_i386.deb)
  MD5Sum mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libggi/libggi2_2.0.5-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libggi/libggi2_2.0.5-1ubuntu1_i386.deb)
  MD5Sum mismatch


any help would be nice thanks,
ephman

---

### Post by Knome_fan on 2005-07-12
[http://www.ubuntuforums.org/showthread.php?p=252212](http://www.ubuntuforums.org/showthread.php?p=252212)

---

### Post by ephman on 2005-07-12
now this is the error after i take out the ".us" from the sources.list  any help would be wonderful thanks,

eph



W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0_0.8.5-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0_0.8.5-2_i386.deb)
  MD5Sum mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libggi/libggi2_2.0.5-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libggi/libggi2_2.0.5-1ubuntu1_i386.deb)
  MD5Sum mismatch

---

### Post by ShaneR on 2005-07-12
After removing the .us, try reloading the lists in synaptic.  That should refresh everything. :)

---

### Post by ephman on 2005-07-12
tried that and my original problem happened BUT it seems that the sources.list doesn't show the ".us"  this is a strange problem (but aren't most linux issues?).  

thanks,
ephman

---

### Post by bgstratt on 2005-07-12
don't forget to sudo apt-get update after you save the sources.list

---

### Post by ephman on 2005-07-13
totally gave that a shot before.  nope, didn't work.  any other ideas???

---

### Post by Drunk247 on 2005-07-13
try this. open up synaptic,settings,repositories,highlight each repo and choose edit and change all us.archive to just archive.with just changing the sources.list didn't work for me either so i did it this way and it worked.good luck.PS don't forget to reload!!

---

### Post by ephman on 2005-07-13
ta da!!! that did the trick.  thanks so much.

ephman

---

