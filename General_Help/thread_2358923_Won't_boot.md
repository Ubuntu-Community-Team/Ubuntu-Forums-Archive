---
title: "Won't boot"
date: 2017-04-18
forum: General Help
---

### Post by janicefamily on 2017-04-18
So first off I've been messing with Linux awhile but when problems arise... I'm a noob.

OK I built a TV backend/ zfs file server about 8 months ago. All was good till the other day my power went out. Now it won't boot it says something about "ata7.00 status drdy" it sounds like it is a bad hdd? But I'm not really sure witch one, but it won't boot so does that mean it's my ssd that the mythbuntu is on on, or could it be one of the other drives that are in zfs?

Also after I went into the bios to take a look at the settings, now it just gets stuck on loading operating system when booting.

Thanks in advance

---

### Post by oldfred on 2017-04-18
If you had power failure that often creates file corruption. And then you cannot mount drives with fstab. If in your zfs partitions you may be able to temporarily comment those out to boot.

If boot or root is ext4 you can run fsck. But for zfs you have to use whatever tools they have for file checking.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Not familiar with other file systems and what tools/commands are used.

---

### Post by janicefamily on 2017-04-19
So do I need to do this in a terminal when using the live cd, or do I use the cd to do some sort of recovery type of thing?

---

### Post by oldfred on 2017-04-19
#From liveDVD/Flash so everything is unmounted,swap off if necessary

Depends on what repairs/recovery you want to do. If file repair does not work, then other repairs or recovery may be necessary. Or checking if drive is ok in Disks.

---

