---
title: "update killed Hoary boot"
date: 2005-10-05
forum: General Help
---

### Post by MrCheese on 2005-10-05
> I let the update tool have it's way last night but shut down rather than rebooted. Turning on tonight I get the message "EBDA is too big; kernel setup stack overlaps LILO second stage".
I really dont want to have to reinstall - any ideas how to fix this?:confused:

fixed it - booted install cd in rescue mode (type "rescue" at lilo prompt), mount all partitions, run "grub-install /dev/hda" (my system is on a laptop, single hdd) replace with the correct device!

OK, grub isn't pretty but at least it does the job and doesn't barf when the kernel gets updated.

---

