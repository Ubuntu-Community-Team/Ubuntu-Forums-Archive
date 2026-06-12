---
title: "/etc/fstab settings for USB drive"
date: 2022-03-18
forum: General Help
---

### Post by rsteinmetz70112 on 2022-03-18
I use USB drives for my backups they stay permanently connected to the computers. It works pretty well, the entire system is automated using crontabs to create remote and local backups for several computers on each drive.

I've used a number of different /etc/fstab entries without problems, the one think I know I need is UUDI mounting. Some are very basic others were copied from various places on the web at different times. There seem to be a lot of different approaches. I'd appreciate  your comments on the ones I've listed below, they all work for me, but I'll take any suggestions. 

```
UUID="2fd9d2e3-4fe1-4c33-aed4-5b5e6a47cda8" /backup ext4 defaults 0 1
UUID="dd9fb1f9-fcfd-482e-9c92-eb18a665c686" /backup ext4 defaults,nofail,x-systemd.device-timeout=30 0 1
UUID="9532efa4-e73b-40a8-97df-21495f3bc49c" /backup ext4 rw,noatime,errors=remount-ro 0 1
```

---

### Post by TheFu on 2022-03-18
The manpage for the fstab file explains all the options.
Field 6 - Non-OS, but locally connected disks should have 2 as the fsck priority number.

I wouldn't mount different UUIDs to the same target directory. Seems like a good way for things to end badly.
UUIDs are for computers.  Humans handle LABEL= better.  Just make certain that the LABEL for the file system is unique on that computer.

No need to specify "defaults", if there are other options too.  rw is the default.

I'm a fan of noatime for all storage and nofail for USB connected disks.

Actually, I don't mount USB devices through the fstab. I use **autofs**.

I think all the x-xxxxxx-yyyyyy options are abominations.

Since I use LVM, here's my mount for an internal disk:
```
/dev/vg-hadar/lv-backups  /Backups         ext4 nofail,noatime,errors=remount-ro  0 [COLOR="#FF0000"]2[/COLOR]
```

If it wasn't using LVM, I'd do something like this:
```
LABEL=RAID1-Array    /raid      ext4 noatime,errors=remount-ro  0 2
```
This is a RAID1 array, so I don't want to continue if there are failures.

Neither of these are USB connected. I don't have fstab entries for USB storage, but the autofs looks like this:
```
/misc/mybook    -nodev,nosuid,noatime,timeout=2,fstype=ext4     LABEL=MYBOOK
```
autofs doesn't mount storage until it is requested, then it automatically umounts it once no open files exist.

For pure data, not backups, might want nodev, noexec and nosuid options for added security.

---

### Post by rsteinmetz70112 on 2022-03-20
I am not mounting different UUIDs to the same mount point. The examples I gave were from different computers. I typically mount my backup media on /backup on all computers. For all of my internal drives I use LVM and mount by the name of the LV much like your example. 

For my USB devices I use uuid so it is unique to the specific drive. I don't typicality use labels, I feel like that could create problems if I somehow connect a drive to the wrong computer. The USB drives are typically reformatted with an ext4 file system for backup use, that allows me to mount them on other computers. For reason is one of my offices in a hurricane prone region and while we have never lost data directly due to a storm, we have suffered considerable down time. The removable backup allow me to take the back up with me when the office is evacuated. There are also off site backups which can be retrieved but having a physical copy makes me feel better.

I haven't used autofs in a long time I'll look into it. In your autofs example above where is that entry made is it /etc/auto.master? It seems a lot of the examples I'm seeing use a number of other files like auto.home or auto.removable. It also appears you could mount by UUID with UUID=xxxxxxxxxx as well.

---

### Post by HermanAB on 2022-03-22
Note that if you give a removable device a Volume Name, then it will always mount with that name.  So you don’t necessarily need to futz with fstab for removable media, just give each widget a unique volume name.

---

### Post by TheFu on 2022-03-22
> **HermanAB said:**
> Note that if you give a removable device a Volume Name, then it will always mount with that name.  So you don’t necessarily need to futz with fstab for removable media, just give each widget a unique volume name.

unique volume name == LABEL.

---

