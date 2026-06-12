---
title: "Software RAID1 not booting and out of sync"
date: 2007-01-14
forum: General Help
---

### Post by r3t0 on 2007-01-14
Hi

My setup is a sata software RAID (md) with two 320gb disks and edgy. the disks are identically partitioned including swap; single boot; grub installted to the mbr. Everything was working fine for about 3 weeks until some smaller updates two days ago (most were gnome-applet related, but I can't remember every package). Since then I can't boot my system anymore. after the BIOS POST the system stops booting with a blinking cursor. I guess it's grub.

Things I've already tried:

- I disconnected disk2 and was able to boot from disk1 alone. but the system on disk1 is about 3 weeks old (almost as old as the whole setup).
( I don't remember which disk was sda and which sdb so I'm talking about disk1 and disk2 here)

- If I disconnect disk1, disk2 doesn't boot (as expected). Grub seems to boot from disk2 by default (disk2 is on sata port 2 and disk1 is on sata port 1 both ports are bootable, I do have non-bootable sata ports on the board, though. but I don't know if that would help)

- I can boot a linux from a usb stick, but I cannot boot feisty from one of the sata dvd-drives. (the kernel panics)

Questions:
- as disk1 is bootable and disk2 has all the data: is there a way to boot from disk one and sync the md with mdadm? I'm very scared that a "wrong" sync of the raid would overwrite my data with the 3 weeks old data.

- should I try reinstall grub on disk2? is this a problem with software raid partitions?

any help is very much appreciated. thank you in advance.

reto

---

