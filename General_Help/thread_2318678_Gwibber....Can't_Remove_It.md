---
title: "Gwibber....Can't Remove It"
date: 2016-03-28
forum: General Help
---

### Post by Del_80 on 2016-03-28
O.k......On this netbook there is a program called Gwibber.......it says that is a ''social networking site'' and ''supports Facebook, Twitter, and Flickr etc. etc.    I have tried removing it, via the Ubuntu Software Centre, but it refuses to budge......are there some programs that you just can't remove ?........Del

---

### Post by vasa1 on 2016-03-28
> **Del_80 said:**
> O.k......On this netbook there is a program called Gwibber.......it says that is a ''social networking site'' and ''supports Facebook, Twitter, and Flickr etc. etc.    I have tried removing it, via the Ubuntu Software Centre, but it refuses to budge......are there some programs that you just can't remove ?........Del
Could you be more explicit than "it refuses to budge"? And which distro are you using? What is its version? 
```
$ apt-cache show gwibber
Package: gwibber
Priority: optional
Section: universe/misc
Installed-Size: 45
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: all
Version: 3.7.0bzr13.04.05-0ubuntu1
Depends: friends-app
Filename: pool/universe/g/gwibber/gwibber_3.7.0bzr13.04.05-0ubuntu1_all.deb
Size: 2452
MD5sum: 01d749889aa1d646f8f22a02ba4db40e
SHA1: c34b58a6a282138983cbe1990d67df691f370ec9
SHA256: 39e87572b3ba302d6c77ce70985313f440931dfbefd00d0137970fe8a5c70140
Description: transitional dummy package
Description-md5: 1f317b04f78374dba7d1e14def0b7f80
Homepage: https://launchpad.net/gwibber
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

$ 
```

Seems to be "something" about it. I'm on Lubuntu, no gwibber. Installing it pulls in too many other files (157). I'd rather be antisocial ;)

Edit: it seems to be related to *friends-app*? Do you see that on your system? Can you get rid of *that* without removing a lot of other software?

---

### Post by Del_80 on 2016-03-28
It's o.k......it has uninstalled on the second attempt, and no harm done.......quite agree about the ''anti social'' bit........thanks.....Del.

---

