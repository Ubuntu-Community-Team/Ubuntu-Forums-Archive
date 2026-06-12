---
title: "md5sum fail to match after burning"
date: 2008-05-01
forum: General Help
---

### Post by satimis on 2008-05-01
Hi folks,


Ubuntu 7.10 desktop amd64


Ran following commands to burn a DVD

- create ISO image```

$ mkisofs -r -o tar.iso -joliet-long -D tar/*.tar.bz2

```


- check ISO```

$ cfv -C -t md5 -f tar.md5 tar.iso 

```


- blank DVD```

$ dvd+rw-format -force /dev/dvd

```


- burn ISO image```

$ growisofs -dvd-compat -Z /dev/dvd=tar.iso

```


- check DVD```

$ cfv -C t md5 -f burnedtar.md5 /dev/dvd

```


Compared the harsh of tar.md5 and burnedtar.md5 and found not identical.


However mounting the DVD on another PC (Ubuntu 7.04 server amd64) and decompressing *.tar.bz2, all directories and files were found.  I could not figure out what was the cause.  Any advice?


TIA


B.R.
satimis

---

