---
title: "12 GB of RAM, do I still need swap space?"
date: 2014-06-05
forum: General Help
---

### Post by linuxhippy on 2014-06-05
I am a longtime linux user and have always gone with the rule of thumb that your swap space should be twice your memory.  Now, I heard that over 12 years ago when I first started using linux.  A lot has changed since then and now RAM has gotten a lot cheaper.  I just bought a Dell Inspiron 3000 that has 12 GB of RAM (that's stock my friend).  It also has a 1 TB drive with Win 8.1.  I shrank Win to 100 GB and then used gparted to give me 2 divisions of 50 GB each for Ubuntu installs and the rest of the drive remains unpartitioned at this point.  

So, I have plenty of RAM and plenty of drive space.  Should I make a 24 GB swap area?  My pc is hardly touching the 12 GB of memory it has now.

---

### Post by Toz on 2014-06-05
If you plan on hibernating, then you'll need one (suspend on the other hand, does not require a swap parition). Otherwise, with all the ram you have and the minimal ram consumption, you really don't need one. I stopped using a swap partition a little over a year ago and have not noticed any difference.

---

### Post by Tadaen_Sylvermane on 2014-06-05
I only keep a 2gb swap. I don't use hibernate and according to my occasional checks it's always 100% available. Not sure why I keep it to be honest.

---

### Post by QIII on 2014-06-05
Twice your RAM is a waste.

If you want to hibernate, you theoretically only need enough to capture your memory state:  i.e.: 12GB.

For good measure, 110% might not be a bad idea.

If you don't intend to hibernate, don't bother with a swap partition.  If you ever get even close to using that much RAM (unless you are using virtual machines, for example), something is wrong.

---

### Post by linuxhippy on 2014-06-06
I don't hibernate the pc, so I should be good to go-thanks!

---

