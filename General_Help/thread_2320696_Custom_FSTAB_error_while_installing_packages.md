---
title: "Custom FSTAB error while installing packages"
date: 2016-04-16
forum: General Help
---

### Post by amarildo2 on 2016-04-16
This is how my fstab looks now:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=bf588ee2-9a67-4ac6-9ee0-14e6ea4ef1fc /boot           ext4    defaults        0       2
/dev/mapper/ubuntu-home /home           ext4    defaults        0       2
/dev/mapper/ubuntu-tmp /tmp            ext4    defaults        0       2
/dev/mapper/ubuntu-var /var            ext4    defaults        0       2
/dev/mapper/ubuntu-swap none            swap    sw              0       0

```

I want to make fstab behave like it did in Arch Linux, but I'm getting a ton of dpkg errors while installing packages. The errors are about half-installed packages and permission denied on /var, even though I was installing packages as root.

This is how my fstab has been for the past months without problems on Arch:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=bf588ee2-9a67-4ac6-9ee0-14e6ea4ef1fc /boot           ext4    defaults        0       2
/dev/mapper/ubuntu-home /home           ext4    defaults        0       2
/dev/mapper/ubuntu-tmp /tmp            ext4    defaults,nodev,nosuid,noexec,relatime,data=ordered        0       2
/dev/mapper/ubuntu-var /var            ext4    rw,defaults,nodev,nosuid,noexec,relatime,data=ordered        0       2
/dev/mapper/ubuntu-swap none            swap    sw              0       0

tmpfs   /tmp            tmpfs   defaults,nodev,nosuid,noexec,dize=16G   0 0
tmpfs   /dev/shm        tmpfs   defaults,nodev,nosuid,noexec            0 0
tmpfs   /var/tmp        tmpfs   rw,defaults,nodev,nosuid,noexec         0 0

```

What editing do I need to make to it in order for dpkg to successfully install packages?

I can use the fstab above and try to install a package if you guys want to see the exact errors I'm facing. Just let me know.

[relevant]Specs:

Ubuntu 16.04, freshly installed from the mini.iso.

Cheers.

---

### Post by oldfred on 2016-04-17
I have never used separate partitions for any / (root) folders other than /home for a very short time.

You are not trying to share /boot or any of the other / partitions with your other system are you?
That would lead to many conflicts. Even sharing two different installs of Ubuntu can lead to issues.

---

### Post by deadflowr on 2016-04-17
> I can use the fstab above and try to install a package if you guys want to see the exact errors I'm facing. Just let me know.

Yes.
Do that.

The error you're getting can help a lot.

---

