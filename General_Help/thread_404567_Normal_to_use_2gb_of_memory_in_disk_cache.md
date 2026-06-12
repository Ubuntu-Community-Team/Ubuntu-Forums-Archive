---
title: "Normal to use 2gb of memory in disk cache?"
date: 2007-04-08
forum: General Help
---

### Post by Mau on 2007-04-08
Is it normal for KDE/Linux/Kubuntu to use 2GB of memory for disk cache and disk buffer?

I have 3GB of memory and 75% of it is being used for disk cache.  I assume once I launch something that requires lots of RAM, the disk cache will shrink?

---

### Post by heimo on 2007-04-08
Yes, that's normal behaviour. Most of the free memory will be used to boost disk access, and it'll be freed for applications as soon as necessary. For example, I have 1GB of memory, about half is in use for applications and system, about 50MB is totally unallocated and over 40% is being used for disk cache.

---

