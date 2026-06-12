---
title: "can you mount FFS?"
date: 2006-11-29
forum: General Help
---

### Post by pau on 2006-11-29
Hi,

I know that you can mount FFS disks (with OpenBSD on them) with

mount -t ufs -o ufstype=44bsd /dev/blabla /openbsd

But for that you have to configure support into the kernel enabling CONFIG_UFS_FS & CONFIG_UFS_FS_WRITE and compile a new kernel, at least in the old times... Is this enabled by default in Ubuntu?

thanks,

Pau

---

### Post by JoesGrindingTeeth on 2006-11-29
Hi,

I dont have UFS volume on this machine at present but IIRC in the past I've just done a modprobe ufs and I could succesfully mount FreeBSD partitions in the past, recompilation of the kernel is not necessary.

---

