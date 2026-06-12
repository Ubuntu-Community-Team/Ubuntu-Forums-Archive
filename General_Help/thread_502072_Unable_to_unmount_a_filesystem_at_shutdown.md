---
title: "Unable to unmount a filesystem at shutdown"
date: 2007-07-16
forum: General Help
---

### Post by pvanberlo on 2007-07-16
Hi,

I'm facing an issue, which is not really causing any problems, but I would like to get this solved anyhow. I'm using EVMS on a debootstrap install of Ubuntu feisty. I have a separate /var partition, and on shutdown/reboot it shows that this partition cannot be unmounted because it's still busy/in use. I added some strategically placed lsof's to see if there are open files on /var, but there are none! I google'd around a bit, and found a reference to an old issue with Red Hat, where auditd was causing an issue with the mount count within the kernel. My install is not using auditd, doesn't even have this installed, but it appears that this is the same sort of issue, i.e. the mount count within the kernel is set to a value which causes /var to not be unmounted properly.

As stated at the beginning of this post, /var is mounted read-only after it claims it's still in use/busy, and everything is fine after that until the next shutdown/reboot.

This apparently started with the newer kernel version available for feisty. Is anyone experiencing the same issue? If so, any idea how to solve this?

Thank you.

-Paul

---

