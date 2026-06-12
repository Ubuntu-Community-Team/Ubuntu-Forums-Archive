---
title: "broken dependencies in edgy"
date: 2006-11-27
forum: General Help
---

### Post by muximus on 2006-11-27
libpng12-dev: Depends: libpng12-0 (= 1.2.8rel-5.1) but 1.2.8rel-5.1ubuntu0.1 is to be installed
E: Broken packages

i m using the official ubuntu repositories... ne help??

---

### Post by camilluk on 2006-11-27
> **muximus said:**
> libpng12-dev: Depends: libpng12-0 (= 1.2.8rel-5.1) but 1.2.8rel-5.1ubuntu0.1 is to be installed
E: Broken packages
i m using the official ubuntu repositories... ne help??
Try
```
sudo apt-get install --fix-missing libpng12-dev
```If that doesn't work you can try downloading and installing the files manually. You can get them [here]("http://packages.ubuntu.com/edgy/").

---

### Post by muximus on 2006-11-27
hey thanx

didnt know that the dev package was is security repos.. saw it on the link u provided
adding them to the sources.list solved it..

---

### Post by Randy R on 2006-12-04
Please help me. What exactly did you add to sources.list?

Thanks

---

### Post by drphilngood on 2006-12-04
> **Randy R said:**
> Please help me. What exactly did you add to sources.list?

Thanks

See here:

[Enabling Extra Repositories]("http://www.psychocats.net/ubuntu/sources")

---

