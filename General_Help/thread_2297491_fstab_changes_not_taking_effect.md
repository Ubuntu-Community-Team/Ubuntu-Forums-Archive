---
title: "fstab changes not taking effect"
date: 2015-10-04
forum: General Help
---

### Post by continuity2 on 2015-10-04
I'm running xubuntu 15.04 in virtualbox and I need to enable the option user_xattr for my file system. I believe I have correctly followed instructions to add this option to /etc/fstab however the option is not taking effect.

here is my modified fstab:

```

jamie@jamie-VirtualBox:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=523fdccb-b3f4-44de-814b-73e642c7116f / ext4 errors=remount-ro,user_xattr 0 1
# swap was on /dev/sda5 during installation
UUID=19763b8b-6f16-4060-9520-0a4268532940 none            swap    sw              0       0

```

I have tried remounting:

```
sudo mount / -o remount
```

I have tried rebooting, but still:

```
jamie@jamie-VirtualBox:~$ mount | grep -i sda
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
```

What do I have to do to get user_xattr working for sda1?

---

### Post by TheFu on 2015-10-04
[https://unix.stackexchange.com/questions/136171/acl-is-not-enabled-but-its-working](https://unix.stackexchange.com/questions/136171/acl-is-not-enabled-but-its-working) says that xattr is enabled by default for ext4 for a long time now.  Try to use some. Do they work?

I checked a few systems here. All were enabled for ext4 file systems.

---

### Post by continuity2 on 2015-10-04
You're right, it is working, I was using this to test:

```

touch ~/.xattr_test && setfattr -n 'user.testAttr' -v  'attribute value' ~/.xattr_test &> /dev/null; getfattr  ~/.xattr_test 2>&1 | grep -q user.testAttr && echo 'It  works!' || echo 'No workie!'; rm ~/.xattr_test &> /dev/null
```

But that was hiding the fact that I didn't have attr installed.  So problem solved.

---

