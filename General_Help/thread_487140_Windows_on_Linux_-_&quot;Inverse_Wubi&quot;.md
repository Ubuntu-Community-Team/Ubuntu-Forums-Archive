---
title: "Windows on Linux - &quot;Inverse Wubi&quot;"
date: 2007-06-28
forum: General Help
---

### Post by brodo on 2007-06-28
Hi there,
I discovered Wubi today and I love the idea. I think it would be great to have sort of an 'inverse Wubi'. This would be a Windows installation on a virtual disk in a Linux filesystem. Sadly int don't even know if this is possible. One would need a virtual bootable NTFS partition and i never heard of such a thing.
If it is possibele i would love to know how...

---

### Post by ago on 2007-06-28
If you have a fairly new processor, the new kernel supports built-in virtualization that is extremely fast (KVM). Therefore the best option is to have Windows in VM within Linux. Even better if you add seamless virtualization on top: [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

That works well for everything except games/3D apps.

---

### Post by brodo on 2007-06-29
Sadly, the onely thing I use Windows for is gaming... :-(

---

### Post by tuxcantfly on 2007-06-30
Well you could always shrink your ubuntu partition, install Windows, then reinstall grub if you want a windows install... Resizing ext3 partitions is quite safe and well-tested, so there's likely little risk in it... Also, some games will run fine in Wine or Cedega (check the appdb to see)...

---

### Post by phenest on 2007-09-23
Is there no other way? Wubi claims to install Ubuntu as a "Real" installation and not a virtual one, running from a file and not a partition.

There is Lubi - which can run Linux in Ubuntu without visualisation.

But nothing for Windows?

---

