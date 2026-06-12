---
title: "RAM utilization question"
date: 2007-09-28
forum: General Help
---

### Post by denzilla on 2007-09-28
Does the standard i386 kernel fully utilize 1GB of RAM or to I need to swap to the proper kernel for my A64 3500+? What kernel should I use?

---

### Post by shae on 2007-09-28
Yes, you do not need to change your kernel unless you feel like messing with a custom kernel or experience problems.

---

### Post by denzilla on 2007-09-28
How much RAM can one have using the 386 kernel?

---

### Post by SeanTater on 2007-09-28
This is technically the answer:
[http://kerneltrap.org/node/2450](http://kerneltrap.org/node/2450)

What it boils down to:

4GB total. 1, 2, or 3 GB per process. (usually 3GB per process)

---

### Post by denzilla on 2007-09-28
That answers that. Thanks :)

---

