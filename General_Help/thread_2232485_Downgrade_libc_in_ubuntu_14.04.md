---
title: "Downgrade libc in ubuntu 14.04"
date: 2014-07-02
forum: General Help
---

### Post by vincent18 on 2014-07-02
Hi, I've just installed ubuntu 14.04 and want to compile some C++ project in that system.
But there is some conflict functions between 3pp library and libc6-dev 2.19.

I've used 12.04 before, in that system, the libc verison is libc6-dev 2.14, and it's perfect for that project.

Does anybody know how can I downgrade the libc version to 2.14? Thank you in advance!

---

### Post by ian-weisser on 2014-07-02
You use dpkg to downgrade. It's well-explained in the dpkg man page.

A perhaps safer option is to create a chroot or container for your project running the lower version of libc6. That way, the unanticipated consequences of the downgrade will be contained.

---

### Post by vincent18 on 2014-07-02
Hi Ian-weisser,

Thank you very much for your information.
For dpkg, where can I find the deb package of old version libc-dev?
For the container solution, is that possible to explain it a bit more? I'm very interested at it.

---

### Post by ian-weisser on 2014-07-02
You can download the 12.04 version of libc6-dev from packages.ubuntu.com.
It's dpkg, not apt-get. You download the package manually.

A very good explanation of LXC, one well-developed container system for Ubuntu is at [https://help.ubuntu.com/community/LXC](https://help.ubuntu.com/community/LXC)

---

