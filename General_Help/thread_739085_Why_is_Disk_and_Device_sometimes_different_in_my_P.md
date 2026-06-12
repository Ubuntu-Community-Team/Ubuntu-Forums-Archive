---
title: "Why is Disk and Device sometimes different in my PSP?"
date: 2008-03-29
forum: General Help
---

### Post by Gerlads Mod on 2008-03-29
When I plug in my PSP, the Disk identifier is usually:
**/dev/sdb**
And the Device is usually:
**/dev/sdb1**

How come this sometimes changes and is there a way to get it to stay the same?

---

### Post by mcduck on 2008-03-29
/dev/sdb is the disk. /dev/sdb1 is the first partition on that disk.

The device names change depending on what order your devices are recognized. When detected, devices are given the first available device name. You can't force the device name to stay the same, but you can either use UUID or partition label instead of the device name, for example if you want to configure some special settings for the drive in /etc/fstab.

Actually if you look at fstab you should notice that the system drives are mounted using UUID's instead of device names. UUID is specific identifier given to the partition when it was made, so it works as a nice way to identify your partitions no matter what connector you use to plug them in or what order your system detects them.

You can list UUID's for all mounted partitions using the 'blkid'-command.

---

### Post by Gerlads Mod on 2008-03-29
I'm having trouble with my shell script.
The PSP will start at **/dev/sdb** and** /dev/sdb1** and sometimes when you have to unplug it, it will switch to** /dev/sdc** and** /dev/sdc1**, and then my script gets messed up.

And your also saying that I could tell if my PSP is plugged in by these UUIDS?

---

### Post by mcduck on 2008-03-30
> **Gerlads Mod said:**
> I'm having trouble with my shell script.
The PSP will start at **/dev/sdb** and** /dev/sdb1** and sometimes when you have to unplug it, it will switch to** /dev/sdc** and** /dev/sdc1**, and then my script gets messed up.

And your also saying that I could tell if my PSP is plugged in by these UUIDS?

I'm saying that by using the UUID instead of device name you are able to configure where your USB drive should mount using /etc/fstab. After that it should make no difference what device name i gets, it'll always mount to same place anyway.

---

