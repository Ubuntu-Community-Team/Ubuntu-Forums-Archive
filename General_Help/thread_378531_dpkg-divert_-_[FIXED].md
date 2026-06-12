---
title: "dpkg-divert - [FIXED]"
date: 2007-03-07
forum: General Help
---

### Post by amphet on 2007-03-07
I'm getting this error everytime I try to install anything using apt-get or aptitude

dpkg-divert: cannot open diversions: No such file or directory

any ideas?

---

### Post by amphet on 2007-03-07
I fixed it by using

sudo touch /var/lib/dpkg/diversions

---

