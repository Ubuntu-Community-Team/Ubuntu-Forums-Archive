---
title: "How to get permissions on mounting a USB pen drive"
date: 2013-09-16
forum: General Help
---

### Post by navraj_singh on 2013-09-16
Hi everyone I have recorded some videos from Digital PVR on a USB drive. 

The pen drive is accessible in Ubuntu however some folders that contain the videos and data do not give full permissions.

Is there any way to reset the entire permissions on this USB drive.


Thanks

---

### Post by jamesisin on 2013-09-16
Which files system do you have that drive formatted?  (FAT32, NTFS, Ext3, &c)

---

### Post by navraj_singh on 2013-09-16
The PVR uses linux and is formatting the drive in linux compatible file system. The drive is not accessible in windows.

---

### Post by Dennis N on 2013-09-16
> **navraj_singh said:**
> 
Is there any way to reset the entire permissions on this USB drive.
Thanks

I have this one in my Linux toolbox. You must decide for yourself if it is appropriate:   
It changes the permissions on ALL subdirectories of the current working directory to whatever you specify (here using 755):

```
find ./ -type d -exec chmod -c 755 {} \;
```

So if you use this command in the root of the USB, it should be done. 
This does nothing to regular files. I have it in a small bash script for convenience.

---

### Post by navraj_singh on 2013-09-16
thanks will try this

---

