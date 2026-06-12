---
title: "Swap Location"
date: 2007-01-02
forum: General Help
---

### Post by eviltang on 2007-01-02
Hello all.  Thank you for taking the time to check out my post.

Here is my issue.  I have 4 Primary Partitions. None of which are my swap. I have 2GB of RAM, but I would still like to enable a swap "area".

I was wondering of it is possible to create the swap file on the / (root) partition (a la windows pagefile.sys).  

Any information is appreciated.

Respectfully,

Eviltang

---

### Post by bodhi.zazen on 2007-01-02
Should be no problem.

I would make a 1 Gb swap.  See here:

[http://www.ubuntuforums.org/showpost.php?&p=1926707&postcount=6](http://www.ubuntuforums.org/showpost.php?&p=1926707&postcount=6)

---

### Post by eviltang on 2007-01-02
> **bodhi.zazen said:**
> Should be no problem.

I would make a 1 Gb swap.  See here:

[http://www.ubuntuforums.org/showpost.php?&p=1926707&postcount=6](http://www.ubuntuforums.org/showpost.php?&p=1926707&postcount=6)

Bodhi.zazen,

Thank you very very much.  That is exactly what I was looking for.

Much Respect,

Eviltang

---

### Post by SoggyCornflake on 2007-01-02
> **eviltang said:**
> I was wondering of it is possible to create the swap file on the / (root) partition (a la windows pagefile.sys).  


I've never tried to use a swapfile.  Linux orginally was designed around a swap partition, and most distros make a swap partition.  If you truly can't create a swap partition, you might try this link to some intructions from Redhat:

[**Redhat instructions **]("http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html")

I'm not sure if it works with Ubuntu with "stock" kernel.  If the Kernel needs to be compiled to use a swap file,  you're probably a lot better off just adding a swap partition.

---

### Post by eviltang on 2007-01-02
> **SoggyCornflake said:**
> I've never tried to use a swapfile.  Linux orginally was designed around a swap partition, and most distros make a swap partition.  If you truly can't create a swap partition, you might try this link to some intructions from Redhat:

[**Redhat instructions **]("http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html")

I'm not sure if it works with Ubuntu with "stock" kernel.  If the Kernel needs to be compiled to use a swap file,  you're probably a lot better off just adding a swap partition.

Thank you.  I am testing the swap area as a file.  If I have any issues, I will post back here.

---

