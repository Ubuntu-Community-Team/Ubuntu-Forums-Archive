---
title: "Ubuntu not added to windows boot manager"
date: 2007-07-17
forum: General Help
---

### Post by jdeisenberg on 2007-07-17
I did the Wubi install using a local copy of the alternate iso (in the same folder as the wubi installer).

When I rebooted, I just went straight into Windows XP; there was no boot manager menu shown to give me a choice. Here's output from MbrFix; the extended partition was from a former install of Linux.

```
C:\Temp>mbrfix /drive 0 listpartitions
# Boot Size (MB) Type
1 Yes     24999    7  NTFS or HPFS
2           635  130  Prime
3         13625   15  WIN95: Extended partition, LBA-mapped
4             0    0  None
```

Any suggestions?

---

### Post by jdeisenberg on 2007-07-18
My bad! (as the young people say nowadays)

I didn't use the correct fixmbr program; restoring it from the Windows XP install CD did the trick.  I am testing it on a P3, 866 MHz, and it runs OK. This is a *great* package.

---

