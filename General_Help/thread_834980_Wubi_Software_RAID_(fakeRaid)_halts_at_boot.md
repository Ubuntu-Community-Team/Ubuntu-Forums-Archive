---
title: "Wubi Software RAID (fakeRaid) halts at boot"
date: 2008-06-20
forum: General Help
---

### Post by paralax on 2008-06-20
I have vista installed on top of an Intel software raid. Vista just autodiscovered the RAID and showed it to me as a single disk.

The install of ubuntu using wubi seemed to work perfectly until I tried to boot. The DOS grub booted fine, but for any of the 4 boot choices I get kicked to a BusyBox prompt showing (initramfs). 

Enabling debugging seems that when trying to read my sda1 it just fails and doesn't proceed.

Since wubi is ontop of windows, shouldn't it just see a single disk like vista does?

As a side note, I tried to install from the liveCD and hosed my install pretty badly. I installed dmraid, but then the installer tried to partition my free space, and then failed, regarless of which fs I chose for the free space. So I'm currently stuck without Ubuntu until I either abandon my software raid, or someone comes to my rescue here.

---

### Post by ago on 2008-06-20
Fakeraids are not supported at the moment. They will be supported in the next release in October and earlier on in pre-releases.

---

