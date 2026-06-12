---
title: "mounting hard disks"
date: 2008-04-07
forum: General Help
---

### Post by f16 on 2008-04-07
I installed Ubuntu  7.10 removing my sata hard disk to make grub installed in second hard disk.Then, plugged in it again. But when I logged into Ubuntu I didn't see my sata hard disk
how can I mount it without reinstalling Ubuntu.

---

### Post by f16 on 2008-04-07
My sata hard disk contains two partitions one of them is for windows

---

### Post by vanadium on 2008-04-07
The Ubuntu installation program did not see your unplugged drive obviously. You therefore will need to mount it yourself by including the appropriate entry in the file /etc/fstab.

I suspect some problems for you, though. If your system normally boots from the removed drive into Windows, I presume that you won't be able to boot Ubuntu once that drive is inserted again. Alternatively, if the removed drive normally boots last, you won't be able to boot Windows, unless you manually edit the grub menu. In fact, I advise you to reinstall Ubuntu, leaving both drives in place this time. This way, it will all be configured correctly. You might even be able to specify from within the Ubuntu install program where grub should be installed.

---

