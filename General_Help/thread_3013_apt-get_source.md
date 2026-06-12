---
title: "apt-get source ?"
date: 2004-11-02
forum: General Help
---

### Post by marguz on 2004-11-02
Hi,
I'm trying to compile an app and when I do a "sudo apt-get  --compile source foo-bar"
I get "dpkg-checkbuilddeps: Unmet build dependencies: libfoobar-dev" and there are about 30 of there unmet dependencies. Is there a way to tell apt-get to fetch the *.dev files? Right now all I can do in type on at a time.

Mark

---

### Post by jdong on 2004-11-02
apt-get build-dep <pkg-you-want-to-build>

---

### Post by marguz on 2004-11-02
[QUOTE=jdong]apt-get build-dep <pkg-you-want-to-build>[/QUOTE]
 got it

Thanks

---

