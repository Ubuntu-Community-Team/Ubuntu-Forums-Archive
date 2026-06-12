---
title: "I think I broke my kernel, how can I restore it?"
date: 2007-05-28
forum: General Help
---

### Post by Halsnalle on 2007-05-28
Trying to get wifi working on my MacBook Pro running Feisty I think I have screwed up the kernel (my attempt to insert madwifi into the kernel ([http://ubuntuforums.org/showpost.php?p=2731662&postcount=26](http://ubuntuforums.org/showpost.php?p=2731662&postcount=26)) failed), and now my Ubuntu install won't start.

I get to the logo with the progress bar. It loads ca ten percent, and then stalls. Should I do a complete reinstall? Although I have no important data on the partition, I'd of course prefer restoring to reinstalling.

---

### Post by MoLE on 2007-06-03
Can you get into recovery mode via the grub boot menu?  You may need to press Esc when grub is loading at boot time to see it.

If so, try sudo aptitude reinstall linux-image-{version}-generic, to refresh your kernel install.  Or you may find it easier to install a different kernel, boot into that and remove the old one, before reinstalling it.

---

