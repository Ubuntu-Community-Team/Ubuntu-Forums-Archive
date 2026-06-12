---
title: "create debs"
date: 2007-06-07
forum: General Help
---

### Post by luckyd on 2007-06-07
I have read several places that checkinstall is a crude tool. So what is the proper way to make .debs after running the ./configure command on a source directory?

---

### Post by testube_babies on 2007-06-07
Making "proper" .debs is incredibly time consuming and difficult.  I'd stick with checkinstall, even if it doesn't correctly deal with dependencies.

If you're truly interested, the Ubuntu Packaging Guide shows the proper guidelilnes:
[https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html)

---

### Post by ramjet_1953 on 2007-06-08
checkinstall is the go if you just want to make a deb package to install on your PC.

As the previous poster said, it is a very long process to make a package for general distribution.

Regards,
Roger :cool:

---

