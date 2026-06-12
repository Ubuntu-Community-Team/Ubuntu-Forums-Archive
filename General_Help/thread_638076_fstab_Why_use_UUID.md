---
title: "fstab: Why use UUID?"
date: 2007-12-11
forum: General Help
---

### Post by chrismyers on 2007-12-11
Can somone please tell me why the swap partition in fstab is set out like this:

# /dev/sda5
UUID=cedf9a04-a260-48e1-aaeb-e742fa6185ef none            swap    sw              0       

Why is it not like this:

/dev/sda5 none            swap    sw              0       

I'm confused. After cloning a workstation I discovered that the swap partition was not working. I replaced the top example for the bottom to fix it.

I'm curious as to the benefits of using UUID. Can anyone tell me?

Many thanks.

---

### Post by mcduck on 2007-12-11
If the order in which the drives and partitions are recognized changes, their device names will also change. And if your fstab uses then the device names you'll have some major problems.

Many people have problems because their BIOS recognizes their drives in different order on every boot, and using UUID solves this.

Also, using UUID makes it possible to configure removable drives in fstab. Different drives plugged in at different times would have the same device name, while the UUID is unique for every drive/partition.

Last, but not least, the old way of naming PATA drives as /dev/hd** and SATA/SCSI discs as /dev/sd** is being phased out, and /dev/sd** names are now used fore both. (because the developers have found out that the SATA/SCSI driver actually handles PATA drives better than the PATA driver did). When fstab uses UUID's instead of device names the change in device names causes no problems.

THe only bad thing about UUID is that if you change the partitions, the UUID's change as well. but you can get UUID's for your partitions by running 'blkid' and then just edit the fstab to use the new UUIDs. At least we usually repartition our disks less frequently than we plug in different removable drives..

---

### Post by mdurham on 2007-12-11
> 
Many people have problems because their BIOS recognizes their drives in different order on every boot, and using UUID solves this
If this happens how can GRUB work properly? It can't can it?
Why not use LABLEs to identify drives? It's more convenient than using UUID.
Cheers, Mike

---

### Post by mcduck on 2007-12-11
> **mdurham said:**
> If this happens how can GRUB work properly? It can't can it?
Why not use LABLEs to identify drives? It's more convenient than using UUID.
Cheers, Mike
Ok, I'm not quite sure what part of the whole system is detecting drives in different order, but the fact is that it happens to some people, so we need a way to work around it. 

Why not use labels? because you'd actually have to give every disk a label before you could use it. Not very convenient when you think about it.. They all already have a UUID.

Also, with UUIDs it's less likely to end up with two same UUID's, while people could easily label their disks with same names like 'mydisk' or something.

---

