---
title: "Another: Encrypted Swap not mounting"
date: 2014-08-21
forum: General Help
---

### Post by djpemberton on 2014-08-21
I am using Ubuntu 14.04. I am having an encrypted swap problem similar to others. However, I don't seem to have some of the same fstab entries as others. 

Here is my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=ff3d661a-1480-424f-9a15-2463b097d006 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```


blkid returns

```
/dev/sda1: UUID="ff3d661a-1480-424f-9a15-2463b097d006" TYPE="ext2" 
/dev/sda5: UUID="d65d5b03-8f4c-4432-8802-876fdce62b57" TYPE="crypto_LUKS" 
/dev/mapper/sda5_crypt: UUID="swgQHm-B4GE-orMs-kUWv-1rMO-Fn0R-68t98A" TYPE="LVM2_member" 
/dev/mapper/ubuntu--vg-root: UUID="7939d23f-5146-49bb-b548-4b0b1022defc" TYPE="ext4"
```


swapon -s returns nothing

In Ubuntu's Disks utility, swap is shown under "Other Devices" as "4.2 GB Block Device, /dev/ubuntu-vg/swap_1".


sudo swapon -a returns

```
swapon: /dev/mapper/ubuntu--vg-swap_1: read swap header failed: Invalid argument
swapon: /dev/mapper/cryptswap1: stat failed: No such file or directory
```

Does any of this mean anything to anyone else?

---

### Post by djpemberton on 2014-08-23
Anyone?

---

### Post by malkiervt on 2014-12-28
Did you ever figure this out? I'm having the exact same problem....

---

### Post by djpemberton on 2015-01-02
No. Unfortunately not. There should be a warning about this during install. I would have handled encryption differently had I known of this problem. I am now looking at having to do a fresh install. Hassle.

---

### Post by djpemberton on 2015-01-02
I am curious as to whether this happens only if you encrypt /home, or if it also happens if you choose for the whole disc to be encrypted. Anyone know?

---

### Post by worden-lee on 2015-10-22
I have this exact problem. Would welcome any helpful info.

---

