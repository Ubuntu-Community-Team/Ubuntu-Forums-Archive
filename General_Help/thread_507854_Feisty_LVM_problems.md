---
title: "Feisty LVM problems"
date: 2007-07-23
forum: General Help
---

### Post by AusIV4 on 2007-07-23
I've been using Dapper since it came out to run a MythTV system. I use RAID and LVM to combine several drives together and benefit from redundancy. Recently I've been trying to upgrade to feisty to take advantage of some new features, but I haven't been able to get my logical volumes to mount consistently.

Right after I installed raid and lvm, my devices were recognized and mountable, but after a couple of days I started getting the following error when I try to mount my LVM devices:

```

mount: wrong fs type, bad option, bad superblock on /dev/raid_lvm/jfs_home,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I don't understand why this would start happening randomly - I don't have the same problem under dapper, but I did under edgy, which is why I never switched.

Any ideas?

---

### Post by kuja on 2007-07-24
Can you post your /var/log/dmesg file?

---

### Post by AusIV4 on 2007-09-10
Should have posted this a long time ago, in case anyone else has the same problem.

The problem had nothing to do with LVM, it was a JFS issue. I just had to run jfs_fsck to repair it and it's been working fine ever since.

---

