---
title: "Something wrong with mdadm RAID1 when removing one member"
date: 2016-01-10
forum: General Help
---

### Post by Saulius_B on 2016-01-10
Hi,

Perhaps I am doing something wrong with the software RAID that I am trying to create. Would appreciate if someone would point out the issue.

Assembled a PC from old parts + added 2 x new 3TB HGST NAS disks. Installed Ubuntu on a old separate disk.

Created partitions on 3TB disks, sdb1 and sdc1 using Gparted. Did not format. Started with sector 2048 and also left 2GB unallocated space as per some recommendations.

Then 
mdadm --create /dev/md0 --level=mirror --devices=2 /dev/sdb1 /dev/sdc1

Waited 5 hours to sync.

Then
mkfs.ext4 /dev/md0

Also, added ARRAY line to /etc/mdadm/mdadm.conf

(copied from output of mdadm --detail --scan)

Then ran
update-initramfs -u (is that maandatory for non-system disk RAID?)

Rebooted to test. Mounted/dev/md0 manually to /storage (didn't want to ad to fstab just yet). All good. Downloaded few large files directly to /storage

Then thought to test. Powered off, disconnected one mirror member. Power on.

Cannot mount  /dev/md0. GUI Disks utility shows that 3TB Array device has no blocks present (could be innacurate wording). The disk which is still connected (/dev/sdb1) is shown as member of the raid.

When I run
mdadm --detail /dev/md0

I see that now array is recognized as RAID0 instead of RAID1, there's no mention about failed disks. Also, there are two letters A, i.e. AA stating that both members are active instead of one being represented by "." as missing. When I run the same command when both disks are connected, I see RAID1 as type.

I tried to do the same on a VM, I even took Fedora. Config was identical, except update-initramfs command. Got the same issue - if I disconnect one of the drives, RAID is non functional and I see RAID0 as type.

If I try to purposely fail one of members with mdadm -f, I get functional RAID1 with details showing array to be degraded. If in a such situation I physically remove the disk which I marked as failed, the array fails, like it would have some unique (superblock?) information.

What am I doing wrong? Your help is greatly appreciated!

BR,
Saulius

P.S. I might have made a typo in some command while creating this thread from memory, all actual commands where entered while using reference guides.

---

### Post by SeijiSensei on 2016-01-10
I don't know what "level=mirror" means.  I use "level=1" for RAID1.

I also set the partition type for the array members to "fd" using fdisk.  I suspect you can do that with gparted as well, but I've never tried.

---

### Post by Saulius_B on 2016-01-11
Hi SeijiSensei,

Thank you for response!

I think level=mirror and level=1 are interchangeable ([https://raid.wiki.kernel.org/index.php/RAID_setup](https://raid.wiki.kernel.org/index.php/RAID_setup)). At least, when I create RAID using this command and check it afterwards, it is displayed as RAID1, so perhaps all should be ok here.

Regarding partition type - I actually don't set any type, but after I create RAID and check - I see "Linux RAID" as type. I cannot use fdisk for drives larger than 2TB. Should that be sufficient?

Thanks again.

Actually, I just checked my VM on which I have purposely installed Fedora instead of Ubuntu. I have 2GB virtual disks there, just so that RAID syncing would be very quick, so fdisk works on that machine. I had partition type 83 (Linux). Maybe that IS my problem. Will check and post an update.

SeijiSensei,

you have pointed out the issue correctly!!! Thank you!

At least the Fedora VM RAID1 now works fine with just one member disk. I still don't understand, why there are so many RAID guides on the net which don't mention anything about partition type being so important....

Thanks again!

Saulius

---

### Post by Saulius_B on 2016-01-11
Ok, since this is resolved for me, for anyone who also struggles with RAID and partition types, I will post some guidance.

On another physical Ubuntu machine which had 2 x 3TB drives I had GPT instead of MBR (>2TB limit). So, I couldn't use fdisk. So there I have used gdisk to set partition type (parted can also be used):

 gdisk /dev/sdb

then typed "t" and typed "fd00" and "w" to write changes.

Repeated procedure for other disk.

The partition type for MBR (<2TB) has to be "fd" or 0xFD!!! For GUID, it is whole different story with partition types/names, as it is a long GUID string. Program like gdisk just uses 4 letter human-friendly mapping which is derived from old partition type names. You may read more here by the creator of gdisk: [https://bbs.archlinux.org/viewtopic.php?id=157993](https://bbs.archlinux.org/viewtopic.php?id=157993), post #5.

My main failure was to use Gparted to partition disks for RAID. Even though I didn't set partition type using Gparted, after I have created RAID with mdadm, I checked that Gparted displayed partition type as "Linux raid", which lead me to believe all was ok, but it was not! Take this as a warning and use gdisk or parted to partitition large disks and set partition types.


Off topic - is there a way I could change the name of this topic to "mdadm RAID issues with large 3TB (>2TB) disks"?

---

### Post by SeijiSensei on 2016-01-11
I'm pretty sure vBulletin gives the OP the power to change the thread title, but it appears to be disabled here at UF.  I'm afraid you'll need to ask a moderator.  Click the Report button on your initial positing and request the title change.

---

