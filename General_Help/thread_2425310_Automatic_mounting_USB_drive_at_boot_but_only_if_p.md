---
title: "Automatic mounting USB drive at boot but only if present"
date: 2019-08-23
forum: General Help
---

### Post by Briga on 2019-08-23
Hi, I wonder if any one can help me solving this issue since I cannot get it to work. 

All the previous posts solutions (in this forum and elsewhere) failed or use fstab options that are deprecated or don't work as they should in Ubuntu. 

I have an external drive (USB) with several folders that should be mounted at boot under different folders in my home. 

Right now it works as it should with those lines in fstab

```
UUID=5f9a7748-634f-4382-9a0b-7dd6d266225c	/mnt/exthdd	ext4	noauto,nofail,x-gvfs-hide	0	0
#and their binds
/mnt/exthdd/Music	/home/user/Music	none	bind,x-gvfs-hide	0	0
/mnt/exthdd/My\040Photos	/home/user/Pictures/My\040Photos	none	bind,x-gvfs-hide	0	0
```

There are more folders all with a bind mount. 

Problem is if the drive is not connected that stops the system to boot. 
Whenever I tried different solutions (including mounting them outside fstab with a script, using also symbolic links) or it didn't work or they had to be mounted manually or it still blocked booting when drive was missing. 

What is the proper way of doing this?

Thanks

---

### Post by TheFu on 2019-08-23
autofs

---

### Post by Briga on 2019-08-27
Thanks for the answer. I was looking for a static mount but I'll look into it, especially if you can disable the automatic unmount for inactivity. 

Briga

---

### Post by HermanAB on 2019-08-27
Howdy,

Removable devices are mounted by the desktop system, in this case Gnome under /media/username/volumelabel.

If you give the HDD a Volume Label using the disk utility, e.g. MYHDD, then it will always mount the same way when you plug it in and then you can make links to it, that will still work the next time.

If the disk doesn't have a volume label, then it will be mounted with a random name and then your links will only work once.

---

### Post by TheFu on 2019-08-27
> **Briga said:**
> Thanks for the answer. I was looking for a static mount but I'll look into it, especially if you can disable the automatic unmount for inactivity. 

Briga

This is a static mount, just becomes available when requested.  Rather than mounting it under your HOME, which can cause some issues, perhaps mounting somewhere else, then having symbolic links from your HOME to those locations would be acceptable?  That would remove the bind-mount stuff and probably simplify your backups, since backups are usually performed at the partition or LV.

If you want a static mount, then the fstab is the way to make that happen.  I only use the fstab for esata and sata connected devices.  NFS and USB devices go through autofs because those connections aren't permanent.

---

### Post by Briga on 2020-05-03
In the end the solution that worked for me was to have this line in the /etc/fstab

UUID=5f9a7748-634f-4382-9a0b-7dd66539725c	/mnt/exthdd	ext4	nofail,x-systemd.device-timeout=5,x-gvfs-hide	0	0

and then use symlinks rather than mounts with bind.

---

