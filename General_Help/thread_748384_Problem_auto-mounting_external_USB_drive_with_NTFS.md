---
title: "Problem auto-mounting external USB drive with NTFS partition"
date: 2008-04-07
forum: General Help
---

### Post by adityagadre on 2008-04-07
I have an external USB drive (Western Digital, 160GB) which has a single primary partition, formatted as NTFS. The partition was formatted on a Windows XP machine and later was cleanly unmounted from it before connecting to my Ubuntu machine. I am running Ubuntu 7.10 Desktop.

If I log into GNOME, the partition (/dev/sda1) is auto-mounted and I can access it for reading and writing without any problems. However, I need to have it auto-mounted without GNOME, on a command line. I added following line to my /etc/fstab - 

/dev/sda1    /media/Backup    ntfs    defaults    0    0

(I have tried several variations of the above line, using ntfs-3g, adding user to mount options.)

During the boot process when /etc/fstab is processed, I get the following message - 
"failed to access /dev/sda1: no such device or dirctory" and the partition does not get mounted. 

Then if I log into non-GUI command line environment. I can mount the above mentioned partition with super-user privileges using the command "sudo mount /dev/sda1". 

The mount command displays following output - 

/dev/sda1 on /media/Backup type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

It seems as if the partition/usb drive is not recognized by the time /etc/fstab is processed; however it is in due time is correctly recognized. I am not sure how to fix this. I would appreciate any help. Thanks.

---

### Post by vanadium on 2008-04-07
It surely looks as if the usb drives are not yet recognized at the time fstab is loaded. This makes some sense if you think of it because an USB drive isn't supposed to be always available.

You could work around this by putting the mount command in /etc/rc.local This is sort of an "autoexec.bat" of Linux. This initialisation script is executed the very last.

---

### Post by warp99 on 2008-04-07
Use the ntfs-3g drivers to mount the drive in your fstab:

```
<your partition> /media/<mount point> ntfs-3g defaults,locale=en_US.utf8 0 0
```

That should auto-mount the drive. Read the 'man fstab' pages for more information on different settings.

Edit:

Of course make sure you have the ntfs-3g package installed. Also about your question, just issue a 'sudo mount -a command' after you boot to you prompt and all drives not mounted will be mounted per your fstab.

---

### Post by vanadium on 2008-04-08
The point is that the external drive seems not yet recognized, and using ntfs or ntfs-3g won't change that.

---

### Post by adityagadre on 2008-04-08
Vanadium and warp99, thanks for your posts. I have put the mount command in rc.local and it is working great. I was wondering why /etc/fstab is processed until all hardware detection is completed.

---

