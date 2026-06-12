---
title: "Kernel panic after updating to linux kernel 3.8.0-32"
date: 2013-11-07
forum: General Help
---

### Post by aaronmmorrison on 2013-11-07
I'm getting the following errors after upgrading to the newest kernel:
  ```
VFS: Cannot open root device "UUID=1f09d896-51ad-47b8-8e62-c289906e527a" in unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:

```  and
  ```
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

```  It allows me to boot if I change ```
root=/dev/sdc2


```  I've tried re-installing the kernel as well running

  ```
sudo update-initramfs -u -k all

```  and
  ```
sudo update-grub2

```  I've confirmed it's the correct UUID in the fstab etc.
  ```
# / was on /dev/sdc2 during installation UUID=1f09d896-51ad-47b8-8e62-c289906e527a /               ext4    errors=remount-ro 0       1

```  I'm also able to boot from previous versions.  Google has pretty much  run out of results for me to try now.  Help me ubuntuforums, you're my only  hope.

---

