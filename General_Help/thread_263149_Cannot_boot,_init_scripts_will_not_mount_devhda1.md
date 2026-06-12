---
title: "Cannot boot, init scripts will not mount /dev/hda1"
date: 2006-09-22
forum: General Help
---

### Post by BoredByPolitics on 2006-09-22
Hi

For the last couple of days I've been having a problem trying to get Ubuntu to boot.  I've had it installed for a few weeks with no problems.  There was a kernel update about a week ago, but rebooting after that didn't show any problems.

On booting the process gets as far as /scripts/local, which appears to fail to mount /dev/hda1 as /root.  I've run fsck on it (via the installation CD), and it checks out OK.  I can mount it from the busybox command line using:

```
mount -text3 /dev/hda1 /root
```

Unfortunately I've not found the secret to getting the init scripts to carry on from this point.

I think the problem may have something to do with fstype.  If I run the command:

```
fstype /dev/hda1
```

I get the output

```
FSTYPE=minix
FSSIZE=280
```

Which is a little odd, as it's definitely an ext3 partition.

The next thing I'm going to try is to amend /scripts/local so it defaults to mounting the partition as ext3, instead of using fstype to determine the type.

Does anyone have any advice, or has someone run into this issue before? :confused: 

Thanks

Pete

---

### Post by BoredByPolitics on 2006-09-24
OK, eventually I discovered that if I mount /dev/hda1 manually, and then exit, the bootup continues.  Still not sure why this has happened in the first place though...

:confused:

---

