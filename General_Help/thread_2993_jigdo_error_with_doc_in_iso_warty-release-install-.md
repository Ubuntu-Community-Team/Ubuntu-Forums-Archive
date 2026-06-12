---
title: "jigdo error with /doc/ in iso warty-release-install-i386"
date: 2004-11-02
forum: General Help
---

### Post by N0ne on 2004-11-02
--11:57:14--  [http://archive.ubuntulinux.org/ubuntu/dists/warty/main/daily-installer-i386/20040801ubuntu19.0.20041018/doc/manual/en/ch06s02.html](http://archive.ubuntulinux.org/ubuntu/dists/warty/main/daily-installer-i386/20040801ubuntu19.0.20041018/doc/manual/en/ch06s02.html)
           => `warty-release-install-i386.iso.tmpdir/archive.ubuntulinux.org/ubuntu/dists/warty/main/daily-installer-i386/20040801ubuntu19.0.20041018/doc/manual/en/ch06s02.html'
Connecting to archive.ubuntulinux.org[82.211.81.138]:80... connected.
HTTP request sent, awaiting response... 404 Not Found
11:57:14 ERROR 404: Not Found.

I use the warty-release-install-i386.jigdo and warty-release-install-i386.template from United Kingdom (primary).

And it's better to use the "live" release ? iam a bit confuse about that on.  :confused: 

Thanks all.

---

### Post by N0ne on 2004-11-03
My solution ...

Jigdo file warty-release-install-i386.jigdo
/dists/warty/main/** daily-installer-i386 /20040801ubuntu18.0.20041018**/doc/manual/en/apas01.html
/dists/warty/main/** daily-installer-i386 /20040801ubuntu19.0.20041018**/doc/manual/en/apas01.html
/dists/warty/main/** daily-installer-i386 /20040801ubuntu20.0.20041018**/doc/manual/en/apas01.html

Real server path.
/dists/warty/main/** installer-i386 /20040801ubuntu20**/doc/manual/en/

I do a ...
cat warty-release-install-i386.jigdo | sed 's/daily-installer-i386/installer-i386/g' | sed 's/20040801ubuntu[12][90].0.2004101[89]/20040801ubuntu20/g' > warty-release-install-i386.jigdo-MOD

And complete my download with this mod files.
md5sum was clean.

---

