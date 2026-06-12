---
title: "Resume from hibernate fails"
date: 2014-04-29
forum: General Help
---

### Post by hojjat on 2014-04-29
I recently altered the logical volums on my disk, and also expanded the swap partition. It's UUID has changed since.

Now, I could hibernate, but when I resumed the machine, it just rebooted as if it was shut down. I found [https://wiki.ubuntu.com/DebuggingKernelHibernate](https://wiki.ubuntu.com/DebuggingKernelHibernate) but that didn't help fix the problem.

Here is how I fixed it (for future readers' benefit): I manually updated */etc/initramfs-tools/conf.d/resume* so it references the correct UUID; I got the UUID by running *blkid*. The I ran *sudo update-initramfs -u -k all* to update the ramdisks.

---

