---
title: "Stop HD booting in Read Only after failed fsck"
date: 2008-02-06
forum: General Help
---

### Post by Tatty on 2008-02-06
My laptop is relly badly messed up.  I think the hardware is fried, but before i can send it back to get fixed I need to rescue my /home.

Everytime it boots now it boots into fsck (because the last thing i did was a sudo mkdir /forcefsck") but the fsck always fails and demands i run it in readh only mode from a console.

When i do this, it fails at around 95% and then reboots, back into fsck.

I have tried various methods to get in, including booting from different live CDs, but none of them can mount my HD because it is an LVM partition.  If i try to install the software for LVM - sudo apt-get install lvm2 - then the computer usually crashes due to the severe hardware problems.

My next shot therefore is to try to prevent my hard disk from mounting in read-only mode after fsck fails.  Is there any way i can do this?
Or even to change it from read only mode to read-write mode?

---

### Post by kuja on 2008-02-06
Why not let it mount ro ..... at this point your only, only hope is to be able to copy everything off to another drive that you can before it dies altogether. I think I'd avoid using something like dd or partimage because that could probably copy the corruption along with ..... or die halfway in the middle. Anyhow ..... just try to cp everything over and hope for the best. Here's more or less what sort of fstab line I would use ..... if you can get that far:

/dev/blah /some/mountpoint ext3 defaults,ro 0 0

---

