---
title: "lost net connetion during apt-get upgrade"
date: 2005-10-11
forum: General Help
---

### Post by Waylan on 2005-10-11
Last night I ran apt-get update followed by apt-get upgrade. Apt-get upgrade started downloading 60 packages. At package 61, I lost my net connection. If I try rerunning, it just starts to redownload all those packages. What do I need to do to avoid this? Thanks.

---

### Post by mlomker on 2005-10-11
> If I try rerunning, it just starts to redownload all those packages. What do I need to do to avoid this? Thanks.

Are you sure it isn't starting where it left off?  That's what typically happens.  I've lost my connection a number of times.  Packages are temporarily stored in /var/cache/apt/archives and apt will check there before downloading them again.

---

