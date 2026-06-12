---
title: "busybox initramfs - read-only file system error"
date: 2018-12-17
forum: General Help
---

### Post by amjad4 on 2018-12-17
From some time, I have been getting the busybox initramfs prompt while trying to boot. Opening in recovery mode and executing fsck on the root partition results in the subsequent boot succeeding, but after using the system for some time (just a few minutes) the file system becomes read-only again and the cycle repeats. I'd really appreciate some help getting it up and running again.

The device is an Acer TravelMate 246M 313T laptop. It's a dual-boot system with Windows 10, but I haven't used W10 in some time and that seems to be having some issues as well (not sure if they are related).

Results of some commands to help in identifying the issue:

df -h:
```

Filesystem      Size  Used Avail Use% Mounted on
udev            938M     0  938M   0% /dev
tmpfs           192M   11M  181M   6% /run
/dev/sda6        87G   41G   43G  49% /
tmpfs           958M  3.2M  955M   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           958M     0  958M   0% /sys/fs/cgroup
/dev/sda4       141G   95G   46G  68% /media/amjad/ACER
/dev/sda2        96M   42M   55M  44% /boot/efi
/dev/sda5       233G  167G   66G  72% /media/amjad/ACER040DATA
tmpfs           192M   52K  192M   1% /run/user/1000

```

sudo smartctl -a /dev/sda6:
[https://paste.ubuntu.com/p/YNQGYd75c9/]("https://www.google.com/url?q=https%3A%2F%2Fpaste.ubuntu.com%2Fp%2FYNQGYd75c9%2F&sa=D&sntz=1&usg=AFQjCNFh_K2PEQPyPSjaQfhAoTPRcaaWag")

dmesg:
[https://paste.ubuntu.com/p/dfyKNcY2Z8/]("https://www.google.com/url?q=https%3A%2F%2Fpaste.ubuntu.com%2Fp%2FdfyKNcY2Z8%2F&sa=D&sntz=1&usg=AFQjCNG8HyuZ9GCUiTWEenuQFp0CAS3xYg")

Please help.

---

### Post by Impavidus on 2018-12-17
Maybe it's just a loose connector, but this definitely sounds like a broken hard drive. Whenever a read/write error occurs, the filesystem is remounted read-only.

---

