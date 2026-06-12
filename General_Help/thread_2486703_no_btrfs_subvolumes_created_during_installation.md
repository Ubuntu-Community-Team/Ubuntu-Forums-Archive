---
title: "no btrfs subvolumes created during installation"
date: 2023-05-08
forum: General Help
---

### Post by nhasian on 2023-05-08
I did a fresh install of Ubuntu 23.04 (amd64) and chose the btrfs filesystem option. It created an a 1 Gig efi boot partition mounted at /boot, and the rest of the disk was allocated to the root filesystem using btrfs. 

/etc/fstab shows:

```
# / was on /dev/nvme0n1p2 during curtin installation
/dev/disk/by-uuid/1234b7e4-c230-4521-9b7f-ecef842091d6 / btrfs defaults 0 1
# /boot/efi was on /dev/nvme0n1p1 during curtin installation
/dev/disk/by-uuid/B7E9-1234 /boot/efi vfat defaults 0 1
```

```
sudo btrfs subvolume list /
```
shows nothing.

However, I installed Kubuntu 23.04 on another computer and the Kubuntu installer did create @ and @home subvolumes.

I understand that Ubuntu 23.04 has a new graphical installer. I don't think it created the @ and @home subvolumes. How can I correct this?

---

