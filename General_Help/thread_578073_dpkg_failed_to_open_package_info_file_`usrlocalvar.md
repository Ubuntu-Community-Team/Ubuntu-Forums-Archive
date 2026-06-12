---
title: "dpkg: failed to open package info file `/usr/local/var/dpkg/status' for reading: No s"
date: 2007-10-16
forum: General Help
---

### Post by I.You on 2007-10-16
Hi there

I installed dpkg from source code (because of no packaging tools like apt) to embedded linux.
and ran 

# dpkg -i xxx.deb

I got the following error:

dpkg: failed to open package info file `/usr/local/var/dpkg/status' for reading: No such file or directory

What is wrong?


/usr/local/var/dpkg # ls
alternatives  lock          parts
info          methods       updates


CPU : ARM9
Distro : N/A

---

