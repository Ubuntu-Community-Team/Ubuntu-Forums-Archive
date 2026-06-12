---
title: "mpich: broken mpiCC after install"
date: 2005-09-27
forum: General Help
---

### Post by martux on 2005-09-27
Hi there,

package mpich installs
/usr/bin/mpiCC -> /etc/alternatives/mpiCC
which links to
/etc/alternatives/mpiCC -> /usr/bin/mpiCC.mpich
which in turn goes to
/usr/bin/mpiCC.mpich -> ../lib/mpich/bin/mpiCC
and as the grand final the directory only contains
/usr/lib/mpich/bin/mpicc or mpicxx  but certainly no mpiCC :confused:.

Is the package broken? I'd really like to get mpiCC (which is basically a convenience wrapper for gcc). Any ideas anyone?

---

