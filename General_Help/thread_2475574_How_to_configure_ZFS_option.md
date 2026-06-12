---
title: "How to configure ZFS option"
date: 2022-06-01
forum: General Help
---

### Post by david509 on 2022-06-01
Hi

How do you configure ZFS on Ubuntu to use the debug flag on **non**-ECC memory after installing Ubuntu? 

If you know, please walk me through the steps.

Cheers. :)

---

### Post by #&amp;thj^% on 2022-06-01
Most of the ZFS kernel module parameters are accessible in the SysFS /sys/module/zfs/parameters directory. Current value can be observed by
```

cat /sys/module/zfs/parameters/PARAMETER
```
To observe the list of parameters along with a short synopsis of each parameter, use the modinfo command:
```

modinfo zfs
```
 It is suggested that adding the flag options **zfs zfs_flags=0x10 to the "/etc/modprobe.d/zfs.conf"** file may help mitigate the risk of using non-ECC RAM, at the cost of some performance loss

If your system boots from ZFS, this file will not be available until after ZFS is started since it’s stored on a ZFS volume, so you will need to update the initial RAM file system to pick up the changes before the root ZFS volume is mounted.
```

update-initramfs -u
```

If you are on an EFI system, you will also need to update the kernel list in the EFI boot menu so the updated initial RAM file system is used.
```

pve-efiboot-tool refresh

```

---

### Post by david509 on 2022-06-01
Thank you for your reply.

I don't have the zfs.conf file for some reason????? I am using Ubuntu 20.04 (not 22.04 just yet).

---

### Post by #&amp;thj^% on 2022-06-01
What shows here first:
```
modinfo zfs
```
BTW That file has to be created by you.

---

