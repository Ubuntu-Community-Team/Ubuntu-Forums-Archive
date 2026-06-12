---
title: "How can I implement RAID1 on existing LVM/LUKS installation? 15.10"
date: 2016-01-23
forum: General Help
---

### Post by aaaa6 on 2016-01-23
My current set up is a fresh Ubuntu 15.10 install using the guided LVM/LUKS set-up. It is install on a 500 GB SSD and I have a second 500 GB which I want to use to mirror the first.

The layout is:

```

/dev/sda1 - /boot/efi
/dev/sda2 - /boot
/dev/sda3 - crypt-luks

/dev/sdb1 - /boot/efi
/dev/sdb2 - /boot
/dev/sdb3 - linux-raid

```

```
cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb3[1]
      467944448 blocks super 1.2 [2/1] [_U]
      bitmap: 4/4 pages [16KB], 65536KB chunk
```

All the guides I come across are implementing RAID1 either without LUKS on an existing install or with LUKS during the installation process.

When I edit GRUB to change root to md0 and it boots up, Ubuntu does not carry over any files from the home folder. When I take out sda and put sdb in its place, GRUB rescue appears and is unable to boot.

Is there something I am missing or not doing?

---

