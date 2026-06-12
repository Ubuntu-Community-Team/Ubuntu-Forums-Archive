---
title: "Softlink / Symlink help"
date: 2013-10-01
forum: General Help
---

### Post by ac1d2 on 2013-10-01
Recently installed the newest AMD drivers, installation went fine. However when trying to load amdcccle or amdconfig I get the following error:

amdcccle: error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS32


So I'm not sure of how, or what to link. I know the command is ln -s 
just not sure of what to put in after that :(

---

### Post by drmrgd on 2013-10-01
Are you sure that you need to create a link here?  The error suggests you have the wrong libraries for your architecture (i.e. you have 32-bit libraries but are on a 64-bit system).  You might double check that you have matching drivers / libraries for your architecture first as that might solve this problem.

---

