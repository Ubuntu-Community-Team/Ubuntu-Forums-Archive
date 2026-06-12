---
title: "Problem with ZFS because of missmatching zfsutils-linux and builtin zfs kernel module"
date: 2021-10-13
forum: General Help
---

### Post by Mark_Petersen on 2021-10-13
I am having the problem on any Ubuntu 20.04 flavor.

That the UserSpace of zfs and kernel module doesnt match.
And this prevents me from doing zfs Send/Recieve.

----

the zfs version and kernel module is

```
zfs-0.8.3-1ubuntu12.12
zfs-kmod-2.0.2-1ubuntu5.1

```
As can be seen the kernel module and zfs userspace doesnt match.

[https://github.com/jimsalterjrs/sanoid/issues/665](https://github.com/jimsalterjrs/sanoid/issues/665)

This leads to failed zfs send/recieve.

----

When looking at zfs-dkms the  version of kernel module would match the zfsutils-linux package.

```
apt search zfs-dkms


zfs-dkms/focal-updates,focal-updates 0.8.3-1ubuntu12.12 all
  OpenZFS filesystem kernel modules for Linux
```

----

The problem is when i run install it. It wont built it for the kernel.
Possibly because the kernel allready has it built in.

```
apt install --reinstall zfs-dkms

Building for 5.11.0-37-generic
Building initial module for 5.11.0-37-generic
Error!  The /var/lib/dkms/zfs/0.8.3/5.11.0-37-generic/x86_64/dkms.conf for module zfs includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
Skipped.

```

----

Now my question is.

How do i force zfs-dkms to be the kernel module i wish to use?
For now and any futher kernel updates.

----

Ty for reading and best regards
Darkyere

---

