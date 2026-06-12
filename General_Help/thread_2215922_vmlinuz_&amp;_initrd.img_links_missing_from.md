---
title: "vmlinuz &amp; initrd.img links missing from /"
date: 2014-04-09
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-04-09
The vmlinuz & initrd.img links that are supposed to be in / are missing in 2 of the 3 bootable systems I have installed (all 13.10 with openbox but otherwise tweaked differently). Adapting slightly an idea I think I found somewhere here on the forum (but can't find now, so maybe not) I've set up grub2 to show the main menu for just 1 second before defaulting to an entry that loads a second menu specified in /boot/grub/custom_menu.cfg. That lets me have a simplified menu that shows just one entry for each system that should point to the latest kernel on it and has an unambiguous title without losing easy access to the standard grub menu or mucking about with it too much. But it won't work to boot those 2 systems because it depends on those links.

I could recreate the links manually but then I assume they'd just continue to point to the same file and the whole point is that they are supposed to be changed each time a new kernal is installed to continue pointing to the latest. 

Could I be missing some program on those systems that is supposed to create (and delete and recreate as needed) those links? Or maybe there is a setting somewhere? Or maybe something is just plain broken and I need to reinstall it? Any thoughts on this would be appreciated.

---

### Post by coldcritter64 on 2014-04-09
> **Dreamer Fithp Apprentice said:**
> The vmlinuz & initrd.img links that are supposed to be in / are missing in 2 of the 3 bootable systems I have installed (all 13.10 with openbox but otherwise tweaked differently). Adapting slightly an idea I think I found somewhere here on the forum (but can't find now, so maybe not) I've set up grub2 to show the main menu for just 1 second before defaulting to an entry that loads a second menu specified in /boot/grub/custom_menu.cfg. That lets me have a simplified menu that shows just one entry for each system that should point to the latest kernel on it and has an unambiguous title without losing easy access to the standard grub menu or mucking about with it too much. But it won't work to boot those 2 systems because it depends on those links.

**I could recreate the links manually but then I assume they'd just continue to point to the same file** and the whole point is that they are supposed to be changed each time a new kernal is installed to continue pointing to the latest. 

Could I be missing some program on those systems that is supposed to create (and delete and recreate as needed) those links? Or maybe there is a setting somewhere? Or maybe something is just plain broken and I need to reinstall it? Any thoughts on this would be appreciated.

I have in the past with an Ubuntu install (12.04) just made links to the current kernel in use when they've been missing. On getting new kernels installed the link was automatically updated and always pointed to the latest kernel. I suspect that, with the links made and in place, the update process checked for them and updated them from then on. I have absolutely no idea why the links weren't there initially when the install was done. 

Keep an eye on where the links point to after the next kernel update. IIRC I used hardlinks not symlinks (not totally sure on that though, it was a while back.)

---

### Post by Dreamer Fithp Apprentice on 2014-04-10
Thanks, Coldcritter. That worked. I made sym links. I have upgraded the kernel on both of the affected systems since and the links are upgraded. Oddly enough, the ".old" backups got created pointing to the new kernel, not the old one. I'd give even money that normalizes with another cycle. But if not, I can't see that it is of any consequence.

---

