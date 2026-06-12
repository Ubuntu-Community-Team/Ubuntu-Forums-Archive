---
title: "install directory"
date: 2008-04-07
forum: General Help
---

### Post by gaurdianAQ on 2008-04-07
how can I change the default install directory when installing software on ubuntu because when my computer was set up a dual boot was set up with a storage drive accessible from both windows and ubuntu and I want to know how to install software to the storage drive instead of the main drive I will check my book but if it doesnt cover it then I will come back here lol

---

### Post by nick_h on 2008-04-07
> how can I change the default install directory when installing software on ubuntu
You can't.  Software you install from the repositories installs files where they need to be.

Most software is installed below the /usr directory.  You can choose to mount a partition on /usr and in this way most of your software would then be in a different partition to your root filesystem.

---

### Post by bodhi.zazen on 2008-04-07
with chroot

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

---

### Post by gaurdianAQ on 2008-04-09
great now I messed my comp again lol :cry:

---

