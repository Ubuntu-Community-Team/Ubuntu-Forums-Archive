---
title: "Increase /boot partiion"
date: 2016-11-10
forum: General Help
---

### Post by linus_leung on 2016-11-10
I selected LVM and disk encryption for install Ubuntu 14.04. Therefore, the size of the /boot partition only 256M by default. How can I increase the boot partition?

---

### Post by ian-weisser on 2016-11-10
Use LVM tools to shrink the LVM. Do NOT use parted/gparted to change an LVM partition. 
Then use parted/gparted to grow /boot. Do NOT use LVM tools to change a non-LVM partition.

It's generally simpler to merely enable unattended-upgrades, which will automatically and regularly remove the older kernels that fill /boot.

---

### Post by linus_leung on 2016-11-10
Dear Ian-weisser,

  Thank you so much for your reply! 

  It may be too difficult for the general users to regularly remove older kernels in /boot. That is why I want to help them grow /boot.

  How can I use LVM tools to shrink file system? Could you give me some links?

---

### Post by ian-weisser on 2016-11-10
> **linus_leung said:**
> It may be too difficult for the general users to regularly remove older kernels in /boot. That is why I want to help them grow /boot.
Unskilled users don't need to remove older kernels, nor to repartition /boot.
They simply need to enable the already-installed unattended-upgrades (14.04 and earlier), or upgrade to 16.04 (where the problem is fixed).

I do not use LVM, so will let another community member help you re-partition LVM.

---

