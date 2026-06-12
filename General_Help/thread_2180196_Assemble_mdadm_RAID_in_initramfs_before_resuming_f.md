---
title: "Assemble mdadm RAID in initramfs before resuming from hibernate"
date: 2013-10-11
forum: General Help
---

### Post by hemebond on 2013-10-11
My root (/) partition is on an SSD. Hibernation works fine with the current swap partition on the SSD drive.

I'd like to use a swap file (/home/swapfile) on my mdadm RAID1 device (mounted as /home).

The issue appears to be that the hibernation file is checked before mdadm has assembled the RAID, so resume fails every time.

```
Oct 12 15:53:42 excession kernel: [    1.924108] PM: Checking hibernation image partition UUID=970cbac3-b09d-48aa-bc1a-55cdf15b7614
...
Oct 12 15:53:42 excession kernel: [    2.094152] PM: Hibernation image not present or could not be loaded.
...
Oct 12 15:53:42 excession kernel: [    2.169527] md: bind<sdc>
Oct 12 15:53:42 excession kernel: [    2.198371] firewire_ohci: Added fw-ohci device 0000:07:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
Oct 12 15:53:42 excession kernel: [    2.199545] md: bind<sdd>
Oct 12 15:53:42 excession kernel: [    2.200939] md: raid1 personality registered for level 1
```

I have already had a go at getting initramfs to assemble the RAID, but it hasn't made a difference (yes, I have run update-initramfs -u each time).

```
~$ cat /etc/initramfs-tools/modules
md
raid1
ext4

$ cat /etc/initramfs-tools/scripts/init-premount/mdadm 
mdadm --assemble --scan
```

Is it possible at all to assemble the RAID in time for resuming (or thawing) from hibernate?

---

### Post by hemebond on 2013-10-19
I've tried to hibernate to a swap file sitting on an Ext4 partition on another disk and was unable to restore from it; just kept saying there was no hibernation file. Hibernating and restoring from a swap partition on the same disk works fine.

---

