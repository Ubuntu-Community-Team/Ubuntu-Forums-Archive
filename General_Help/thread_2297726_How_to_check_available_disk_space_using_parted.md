---
title: "How to check available disk space using parted?"
date: 2015-10-06
forum: General Help
---

### Post by i12 on 2015-10-06
Making new partition using parted: "...     mkpart primary 0  <amount>" I must enter partition size. How to know exactly available value? And what mean 0 after primary?

---

### Post by dino99 on 2015-10-06
use "print" to first list the partitions; then you will know the 'start' & 'end' & the 'free' space
[http://www.thegeekstuff.com/2011/09/parted-command-examples/](http://www.thegeekstuff.com/2011/09/parted-command-examples/)

---

