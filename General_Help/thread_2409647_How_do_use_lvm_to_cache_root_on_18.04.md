---
title: "How do use lvm to cache /root on 18.04?"
date: 2019-01-04
forum: General Help
---

### Post by cabryan on 2019-01-04
How do I cache /root using lvmcache on 18.04?  I can use lvm to cache /root on 16.04 but when I use the same process on 18.04 and reboot, all I get is the Grub2 screen and prompt.

---

### Post by cabryan on 2019-01-16
Here is what worked for me:

1. I used the alternate ISO to install so I could manually set partition the drives and set up LVM.
2. On my hard drive, I created a partition for EFI and another partition formated to Ext4 mounted to /boot.
3. I created my volume group and logical volumes for /root and /swap on the remaining space on my hard drive.
4. I expanded my volume group to include my SSD, then set up logical volumes for the cache data and cache meta data.
5. After completing the install & rebooting, I followed the steps from Jethro's blog ([http://scyu.logdown.com/posts/519001-ubuntu-lvmcache-setup](http://scyu.logdown.com/posts/519001-ubuntu-lvmcache-setup)).  I skipped directly to the lvconvert steps since the logical volumes had already been created on the SSD.  I also removed "--cachepolicy mg".
6. I also followed Johannes Bauer advice adding "copy_exec /usr/sbin/cache_check" to /usr/share/initramfs-tools/hooks/lvm2 and making lvm2 executable.
7. Then I updated initramfs (update-initramfs -u -k all) then updated (apt-get update) and upgraded (apt-get full-upgrade).

I may have done more that I needed to, but I've followed these steps to set up three machines running 18.04 with SSD caching through lvmcache.

---

