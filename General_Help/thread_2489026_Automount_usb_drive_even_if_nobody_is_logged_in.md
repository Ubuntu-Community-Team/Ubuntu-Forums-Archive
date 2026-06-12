---
title: "Automount usb drive even if nobody is logged in"
date: 2023-07-15
forum: General Help
---

### Post by fawzib-rojas on 2023-07-15
I want to be able to access the usb drives when connected through SSH (nobody connected to desktop) and I dont want to use fstab, automount only. 

First I thought with an udev rule, mount in a different location (like /mnt/usb/the_drive). I created a rule for that:

```

# get the label if present, otherwise assign one based on device/partitionENV{ID_FS_LABEL}!="", ENV{dir_name}="%E{ID_FS_LABEL}"
ENV{ID_FS_LABEL}=="", ENV{dir_name}="usbhd-%k"


##########################
# CONNECTED
##########################


ACTION=="add", SUBSYSTEMS=="usb", SUBSYSTEM=="block", ENV{ID_FS_USAGE}=="filesystem", RUN+="/bin/systemd-mount --no-block --discover --options=umask=0000 --collect $devnode '/mnt/usb/%E{dir_name}'"


##########################
# DISCONNECTED
##########################


ACTION=="remove", SUBSYSTEMS=="usb", SUBSYSTEM=="block", ENV{ID_FS_USAGE}=="filesystem", RUN+="/bin/systemd-mount --umount --no-block --discover --options=umask=0000 --collect $devnode '/mnt/usb/%E{dir_name}'", RUN+="/bin/rmdir '/mnt/usb/%E{dir_name}'"


```

It works but as soon as someone logs in in the desktop it mounts to /media/user/the_drive and kills the udev mount.

Tried making it shared, using the examples from udisk site:

```
# UDISKS_FILESYSTEM_SHARED
# ==1: mount filesystem to a shared directory (/media/VolumeName)
# ==0: mount filesystem to a private directory (/run/media/$USER/VolumeName)
# See udisks(8)
ENV{ID_FS_USAGE}=="filesystem|other|crypto", ENV{UDISKS_FILESYSTEM_SHARED}="1"

```

I thought since it is shared (not linked to a user) it would always be available. Nope only works when someone logs to the desktop. 
So what I need is to either be able to mount twice, mount to my given location (/mnt/usb/the_drive) when connected and let the desktop connect to its default location when someone logs in or have udisks2 always create a shared mount point as soon as the drive is connected regardless of the user logging in.

Is this possible?

---

### Post by ajgreeny on 2023-07-15
Why do you not want to use fstab?

That could mount it to the folder of your choice irrespective of any user logging in after mounting the USB drive.

---

### Post by fawzib-rojas on 2023-07-15
> **ajgreeny said:**
> Why do you not want to use fstab?

That could mount it to the folder of your choice irrespective of any user logging in after mounting the USB drive.

The disks (multiple) can be removed/changed/added at any time.

---

### Post by #&amp;thj^% on 2023-07-15
> **fawzib-rojas said:**
> I want to be able to access the usb drives when connected through SSH (nobody connected to desktop) and I dont want to use fstab, automount only. 


This is an older post but looks like it will work currently: [https://superuser.com/questions/717861/use-local-usb-when-connected-via-ssh](https://superuser.com/questions/717861/use-local-usb-when-connected-via-ssh)

---

