---
title: "The difference between sources,list flags"
date: 2004-11-06
forum: General Help
---

### Post by tvlad on 2004-11-06
What is the difference between restricted, main, and multiverse, i mean i know it's in the packages, but how and in what way, universe from what i gather also holds non free packages as well.

---

### Post by az on 2004-11-06
Read gnu.org and the Free Software Foundation.  Specifically, the principles of free software.

Main contains only free software.

Restricted contains software that does not quite meet the standards of free software (sourcecode with restriced licences, firmware and so forth.

Multiverse is stuff that is probably not really legal to distribute in some contries (mp3 encoding patents...)

Universe is everything in the debian Sid archive that can compile on a Warty base.

When you think of it, if software is not 100percent  free, it will one day become either extinct, proprietary or eventually become free.

---

### Post by tvlad on 2004-11-07
Thanks, so if i add the universe flag, basically it encompases all the rest and there wouldn't be a need to add the rest as well.

---

### Post by tvlad on 2004-11-07
Is there any practical difference between 

       deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe
and
        deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) universe

Because if universe has ALL the packages, than why should i also add the other repositories, if i don't plan to filter from what repository to choose the packages.

---

### Post by WW on 2004-11-07
The universe component does *not* contain anything that is in main.  The packages in the various components do not overlap.  (For the math geeks, they are "disjoint sets".)

---

### Post by jdong on 2004-11-07
Each repository is a section, much like folders on a hard drive. They don't overlap.

---

