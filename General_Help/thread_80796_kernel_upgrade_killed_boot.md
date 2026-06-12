---
title: "kernel upgrade killed boot"
date: 2005-10-23
forum: General Help
---

### Post by synrat on 2005-10-23
5.04 on AMD. root mounted from /dev/md0.
I upgraded to the latest kernel from the update sources today,
all files were installed. After the reboot, md0 is not mounted, so nothing
happens at all. I mounted one of the partitions manually booting from the cd, wanted to relink to the old kernel but it seems that the upgrade erased all the other kernels from /boot directory !!?? why would it do that ?? What do I do now ? Is there anything I can use to try installing the kernel from the original cd ? I didn't find dpkg binary there, there seems to be some apt-install thing which has no --help option and doesn't take file names as arguments.  This is very disturbing.

---

