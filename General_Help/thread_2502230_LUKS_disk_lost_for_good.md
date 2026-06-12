---
title: "LUKS disk lost for good?"
date: 2024-11-06
forum: General Help
---

### Post by leodp on 2024-11-06
Hi,
I got into issues yesterday evening when upgrading to Ubunti 24.10, and my superficial knowledge of UEFI+RAID0+LUKS made things worse.
Long story short:
I had /dev/sda & /dev/sdb as SDDs in RAID0, with LUKS-encrypted home partition, plus a non encrypted boot and a root partitions.
I HAD /dev/sdb HDD as standalone storage drive, also LUKS encrypted.

Trying to reformat the RAID0 SDDs I followed this guideline:

[https://gist.github.com/umpirsky/6ee1f870e759815333c8](https://gist.github.com/umpirsky/6ee1f870e759815333c8)

as as you could have correctly guessed by now...
I forgot to change some sdb into sdc somewhere along the sgdisk, mdadm, ubiquity, mount command chain, leading to a rewrite of the HDD partition table, losing the LUKS.

I tried to recover the LUKS header with hexdump & all that, but it seems to be lost, or at least I have not been able to recover the LUKS, following the reasoning of various very reliable posts & websites in the "Internet".
No success, some sleep lost, but at least I was distracted from the USA election results.

Before I wipe everything & create a simpler setup that I can manage: is there anything I can do to see if data can be recovered?

Thanks to anybody which will throw its 5c.

Leo

---

### Post by TheFu on 2024-11-06
If you use LUKS, you need excellent backups.
If you use RAID0, you need excellent backups.
Using either of those means you should have excellent backups for when something bad happens.

So, since you would know this, just wipe and start over.

BTW, always create a partition table and at least1 partition for any storage device use. Many tools won't work if we write directly to the whole disk device without have a partition table and at least 1 partition.  You already knew this.

So, with the backups, you should have YOUR system on 24.04 in less than 45 minutes again.

You might want to rethink using RAID0.  If anything bad happens, all data on both disks is lost.

---

### Post by leodp on 2024-11-06
Yes, yes.
I have a 99% backup, some photos are missing, my bad.
RAID0 was for doubling RW speed during image editing, so I was ready to pay the price of an extra risk.
Thanks.

---

### Post by TheFu on 2024-11-06
If this thread is SOLVED, please use the Thread Tools button to mark it that way. Save some other people time.

---

