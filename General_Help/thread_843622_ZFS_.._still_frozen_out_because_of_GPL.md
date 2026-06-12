---
title: "ZFS .. still frozen out because of GPL?"
date: 2008-06-28
forum: General Help
---

### Post by dannyboy1121 on 2008-06-28
Just a quick post regarding the Linux position on ZFS. I understand that this is in OpenSolaris (understandably) but has also been given kernel level support in FreeBSD ... but the last I heard was that due to GPL restritions - Linux was restricted to the non kernel user space version ZFS FUSE.

Is this still the case? Does anyone know what the current state of affairs is with this?

Any info appreciated.

---

### Post by dannyboy1121 on 2008-06-29
Surely someone has a view on this? ZFS for Linux would be a massive boon.

---

### Post by kingtaurus on 2008-06-29
I doubt that it can just be due to the linux kernel being under the GPL (otherwise the binary drivers from ATI and NVidia wouldn't be allowed). I think the issue of GPL and MPL incompatibility could be avoided if they did the same thing as NVidia and ATI (essentially, claiming that ZFS is not a derived work, re-license the appropriate headers under both GPL and MPL and distribute a binary blob). 

According to [http://www.gnu.org/philosophy/license-list.html#MPL](http://www.gnu.org/philosophy/license-list.html#MPL) ,
> 
However, MPL 1.1 has a provision (section 13) that allows a program (or parts of it) to offer a choice of another license as well. If part of a program allows the GNU GPL as an alternate choice, or any other GPL-compatible license as an alternate choice, that part of the program has a GPL-compatible license.


So if CDDL (SUN license) was updated to reflect the revisions of MPL 1.1 it could be linked to GPL code (i.e. the kernel).

Note: IANAL (I am not a lawyer).

---

### Post by dannyboy1121 on 2008-07-01
Thanks KT... well let's hope we see some development on this going forward. It would be a shame for Linux to miss out on this opportunity and although FUSE is a noble effort it's unlikely to be used in anger.

---

### Post by soccerboy on 2008-07-01
yes that is still the case as far as I know but a linux version called btrfs is being worked on.

---

