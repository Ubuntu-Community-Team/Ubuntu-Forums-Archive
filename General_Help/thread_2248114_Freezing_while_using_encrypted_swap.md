---
title: "Freezing while using encrypted swap"
date: 2014-10-12
forum: General Help
---

### Post by noisecapella on 2014-10-12
I'm using Ubuntu 14.04 on a Samsung Series 9 which has a 128G SSD. I have 4G of memory in my laptop and 12G of swap space. The swap partition is located in an LVM volume under an encrypted partition using LUKS.

Generally this works but when memory is scarce my laptop will freeze completely, maybe for 30 seconds or more at a time. No mouse movement or anything. Is this normal? I wish performance would degrade more gracefully

I noticed that /dev/mapper/cryptswap1 points to /dev/dm-3, which is different from the swap LVM which is /dev/dm-2 from the dmsetup output below. Maybe this is significant?

Thanks for your help!

dmsetup ls:
```

sda5_crypt	(252:0)
ubuntu--vg-swap_1	(252:2)
cryptswap1	(252:3)
ubuntu--vg-root	(252:1)

```

fstab:
```
/dev/mapper/cryptswap1 none swap sw 0 0
```

lvdisplay:
```

  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                6Lkavz-MdCb-ky8n-M6Fo-h1by-Pz2R-KkZgiR
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2013-08-30 23:21:29 -0400
  LV Status              available
  # open                 1
  LV Size                100.00 GiB
  Current LE             25600
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                WUzNnR-J80N-Vp89-q10x-e1r3-9u0d-B3YZa3
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2013-08-30 23:21:30 -0400
  LV Status              available
  # open                 1
  LV Size                12.00 GiB
  Current LE             3072
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
   

```

---

### Post by tgalati4 on 2014-10-12
Does

```
free
```

show that swap is in use when RAM is full?

Is there a reason that swap is not a separate partition?  Is there an advantage to having swap encrypted?

I'm thinking there is a subtle conflict with the SSD controller and a large, encrypted swap file.  Anything in /var/log?  Usually, you will get lots of errors in syslog when paging fails.

Performance does degrade with swap.  Sometimes painfully.  How it degrades depends on your processes.  If your SSD controller is getting slammed with page requests, then that might be a bottleneck since SSD reads are pretty fast.

Are you running virtual machines that eat up your RAM?

---

