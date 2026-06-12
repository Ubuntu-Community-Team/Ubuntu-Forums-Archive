---
title: "Microsoft reserved partition problem (Gparted)"
date: 2019-03-10
forum: General Help
---

### Post by KieranFitzgerald on 2019-03-10
I was planning to do some moving and resizing of some of my partitions.   One of the partitions on sda is a Microsoft reserved partition with an unknown file system.  Gparted marks this with a warning.  Windows works fine but I can't move this partition limiting other moves etc.  Screenshot attached.   Can this be fixed?

---

### Post by jeremy31 on 2019-03-10
You may want to see if it can be moved in Windows.  If that partition is deleted, windows doesn't boot

---

### Post by KieranFitzgerald on 2019-03-10
I can't even see the partition in windows!
PS this thread should be marked Ubuntu instead of lubuntu (can it be changed?)

---

### Post by oldfred on 2019-03-10
Gparted marks the Microsoft Reserved, since it is unformatted. This really should be fixed in gparted as it has a valid GUID and it is required to be unformatted.
The bios_grub partition is the same, gparted flags as an error since unformatted and it has a valid GUID.

Have you tried live installed & its gparted or a gparted live ISO?
You should mounted partitions and you cannot work on mounted partitions.

---

### Post by CatKiller on 2019-03-10
[https://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](https://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

> Microsoft expects an MSR to be present on every GPT disk... The MSR partition is not visible within the Microsoft Windows Disk Management control utility, but it is listed (as "Reserved") with the Microsoft Diskpart command line utility.

It's a Microsoft-only weirdness, which you may be able to recreate somewhere else on the disc from within Windows.

As an aside, having /usr as a separate partition is a bit odd.

---

### Post by KieranFitzgerald on 2019-03-10
Same issue with Gparted fom a live session.  Should I report it as a bug?

Partitions were set up when I first got my SSD, it was a suggestion re optimisation.  /var (high traffic) is on the hard disk.

---

### Post by KieranFitzgerald on 2019-03-12
Reported issue to Gnome.

---

