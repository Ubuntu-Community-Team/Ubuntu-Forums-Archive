---
title: "installing cedega has dependency conflicts"
date: 2006-12-01
forum: General Help
---

### Post by rbprogrammer on 2006-12-01
i just got cedega, but one of the dependency packages is [xlibs].  but that is not in the repositories because that package was replaced by [xkb-data] or something like that..... 

so i went to [http://packages.debian.org/stable/libs/xlibs](http://packages.debian.org/stable/libs/xlibs) and downloaded [xlibs]. but i cannot install it because [xkb-data] conflicts with it.  how do i install the necessary packages to install cedega without messing up my system.  because i know i cannot uninstall [xkb-data] because it also removes the KDE desktop as well as other necessary packages......

---

### Post by rbprogrammer on 2006-12-02
just in case anyone else had this problem, i solved it.....

i went to [http://www.chorse.org/archive/2006/05/01/cedega-and-ubuntu-dapper/](http://www.chorse.org/archive/2006/05/01/cedega-and-ubuntu-dapper/) and downloaded the [http://www.chorse.org/junkroom/xlibs-dummy/xlibs_6.8.2-77_all.deb](http://www.chorse.org/junkroom/xlibs-dummy/xlibs_6.8.2-77_all.deb) which is just an [xlibs] dummy package.

---

