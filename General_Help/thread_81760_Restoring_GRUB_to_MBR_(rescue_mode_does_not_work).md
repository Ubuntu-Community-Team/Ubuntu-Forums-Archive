---
title: "Restoring GRUB to MBR (rescue mode does not work)"
date: 2005-10-25
forum: General Help
---

### Post by timelord726 on 2005-10-25
Hi everyone,

What's the best way to restore GRUB to the master boot record after a Windows installation?  I attempted to use the install CD to access my root partition and do it that way, and it worked once but running **grub-install /dev/hda** failed and when I restarted it now gives me an error mounting root partition every time.

Thanks in advance for any recommendations.

---

### Post by SilentCacophony on 2005-10-25
Hi. There is another way without having to do the grub-install command explicitly outlined here:

[http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652)

It basically uses the installer to do it for you by making it skip the actual installation. Note the 'DO NOT FORMAT THEM' warning carefully, though.

---

### Post by timelord726 on 2005-10-26
Oh no!  My partition table no longer shows up in the Ubuntu installer!  :eek:

---

