---
title: "My NTFS partition unmounts on restart/logout"
date: 2008-05-01
forum: General Help
---

### Post by KneeTie on 2008-05-01
my ntfs partition unmounts when i restart or log out and its a hassle since my wallpaper is there and my music to and everytime i restart/logout rhythmbox has to reasearch for my music and its quite annoying.

---

### Post by warp99 on 2008-05-01
> **KneeTie said:**
> my ntfs partition unmounts when i restart or log out and its a hassle since my wallpaper is there and my music to and everytime i restart/logout rhythmbox has to reasearch for my music and its quite annoying.

If your using a usb drive you need to add the mount command to your /etc/rc.local file so the drive is always mounted as root and not as the local user. The line you would add is something like this:

```
mount -t ntfs-3g /dev/<your_device_name> /media/<your_mount_point>
```

If your using an internal drive for your partition you need to add a line to your /etc/fstab file similar to this:

```
/dev/<your_device_name> /media/<your_mount_point> ntfs-3g  defaults,umask=0  0  0
```
then your partition will mount at boot time. Remember to backup your fstab file before you proceed.

---

