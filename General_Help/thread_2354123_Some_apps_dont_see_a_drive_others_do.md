---
title: "Some apps dont see a drive others do"
date: 2017-02-28
forum: General Help
---

### Post by helium2 on 2017-02-28
I have Ubuntiu on one drive and data on a NTFS Data drive as I dual boot win10 from a third drive. When I boot Ubuntu the Linux drive showed the Data drive unmounted so I have to click on it in the File manger to mount it and all apps can then access the Data drive. I set the "auto mount" off feature and ticked the "mount at boot option" in Disks so it would be mounted at boot which it does now. Now when I boot, Libre Office sees the drive ok but Thunderbird does not nor does Darktable. I have to then unmount and remount the drive for Thunderbird to see it. How may I fix this so all apps see the drive at boot without me having to mount it manually? My knowledge of Linux is only a few days old.

---

### Post by TheFu on 2017-02-28
gvfs mounts aren't "real" mounts.  Use the fstab instead.  [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

[https://unix.stackexchange.com/questions/169571/what-is-the-difference-between-mounting-in-fstab-and-by-mounting-in-file-manager](https://unix.stackexchange.com/questions/169571/what-is-the-difference-between-mounting-in-fstab-and-by-mounting-in-file-manager) has an explanation for why some apps don't see the gvfs storage.

Also, don't allow Windows to "fast-boot" or leave file systems open or no other OS will be able to access the disk(s).

---

