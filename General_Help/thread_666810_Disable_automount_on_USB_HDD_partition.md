---
title: "Disable automount on USB HDD partition"
date: 2008-01-13
forum: General Help
---

### Post by Snip on 2008-01-13
I've got this external HDD which has two partitions: a small ntfs one, and a large ext3 one. I don't need the ntfs partition when in ubuntu, so I figured I'd disable automounting:

# Added this to fstab
UUID=582D426B09416ED3                       none            ntfs    defaults,user,noauto        0   0

Now when I plugin the device, it only mounts the ext3 partition. However, it also gives me an error message saying I'm not privileged to mount the volume (the ntfs one). Is there another way of disabling automount without getting this error every time?

Thanks in advance

---

### Post by logos34 on 2008-01-13
> # Added this to fstab
[COLOR="Red"]#[/COLOR] UUID=582D426B09416ED3 none ntfs defaults,user,noauto 0 0

..

---

### Post by Snip on 2008-01-14
But I added that line with the **noauto** so it won't automount. If that line isn't there, it automatically mounts the partition and I don't want that. I guess UDEV tries to mount it anyway, but can't because I told it not to in fstab, and then gives me the error?

---

### Post by vanadium on 2008-01-14
The problem is that the "automount" mechanism for USB drives and /etc/fstab are two different mechanisms that you probably should not mix. In other words, removable drives should not be included in /etc/fstab.

That said, I am not sure whether you will be able to selectively disable automount. Automount for removable devices is disabled through "System - Preferences - Removable drives and media", but that will disable mounting of all partitions.

Perhaps you can effectuate something by right-clicking the partition in "Places - Computer" but I am not sure as I never use this. Probably you should just let that ntfs partition mount as well.

---

