---
title: "Emergency"
date: 2007-09-11
forum: General Help
---

### Post by the_sorrow on 2007-09-11
Today I formated my windows partition today, and when it was finished I wasn't allowed to enter ububtu again, but the linux partition is still there.

What can I do??

Thnx

The Sorrow

---

### Post by isahak on 2007-09-11
Buddy
It looks like you installed the boot loader on MBR. So, when you formated windows drive you deleted boot loader also. Try to install a boot loader (like grub), and modify that. Then it should work.

---

### Post by the_sorrow on 2007-09-11
How Can I istall a but loader?? Where do I get?

---

### Post by merlinus on 2007-09-11
Use supergrub to reinstall grub:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Info on its use here:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#situtions_where_sgd_is_useful](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#situtions_where_sgd_is_useful)

---

### Post by az on 2007-09-11
You simply need to reinstall grub.  You can use the live cd for that.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by tgalati4 on 2007-09-11
>sudo grub-install /dev/hda1

Modify the device partition to match your configuration.

---

### Post by the_sorrow on 2007-09-11
Thnx guys

---

