---
title: "upgrade problems"
date: 2006-10-26
forum: General Help
---

### Post by koulanji on 2006-10-26
My internet connection is fine, however, when I try to upgrade from 6.06 - 6.10 I get this error, which also tells me that this problem is due to my network connection. Any ideas anyone? That would be greatly appreciated.

Failed to fetch [http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz](http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz](http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

---

### Post by ayoli on 2006-10-26
i suppose xgl.compiz.info repos was for compiz, but as i can see it's still the dapper one in your sources.list. you may want to try another one for edgy
```
deb http://www.beerorkid.com/compiz edgy main-edgy
```

---

### Post by koulanji on 2006-10-26
how do i get rid of the other repos?

---

### Post by ayoli on 2006-10-26
edit your sources.list, and comment the repos lines you don't need anymore with a # at the beginning of line.
or graphical way: in synaptics menu categories > repositories tab 'third party' uncheck the repositories you don't want (here you can also add repos with add button at bottom).

---

