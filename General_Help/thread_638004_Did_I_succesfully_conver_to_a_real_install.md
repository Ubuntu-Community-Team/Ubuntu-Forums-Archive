---
title: "Did I succesfully conver to a real install?"
date: 2007-12-11
forum: General Help
---

### Post by Valok on 2007-12-11
So I just went through the whole process listed in a sticky above guiding my through the steps to make ubuntu into a full install from WUBI.

My only question now is, how do I know that went through alright?  Is there a way I can tell that I'm working off my partitioned part of my HD right now and not the WUBI?

---

### Post by TorontoStorm on 2007-12-11
in a real ubuntu install, there shouldn't be a /host folder, and you can check if a partition was made by installing GParted and using that

---

### Post by Valok on 2007-12-11
What if the hard drive is named "host0".  Because that is the name of mine, but I don't have any /host folder

---

### Post by ago on 2007-12-12
cat /proc/mounts

Look what device is used to mount / 
If it's a root.disk file you are on wubi, if it's a disk device (/dev/sda1) you are on a dedicated partition

---

### Post by Valok on 2007-12-12
> **ago said:**
> cat /proc/mounts

Look what device is used to mount / 
If it's a root.disk file you are on wubi, if it's a disk device (/dev/sda1) you are on a dedicated partition

So I should type in the cat /proc/mounts into a termal and see what it returns right?

---

### Post by ago on 2007-12-12
> **Valok said:**
> So I should type in the cat /proc/mounts into a termal and see what it returns right?

Yep

---

### Post by Valok on 2007-12-12
Awesome thanks.

---

### Post by Valok on 2007-12-12
When I ran that command I didn't see any /mount in the information it returned.

```
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
/dev/disk/by-uuid/d855fea4-d075-4b35-84dd-6a61080b17a0 / ext3 rw,data=ordered 0 0
/dev/disk/by-uuid/d855fea4-d075-4b35-84dd-6a61080b17a0 /dev/.static/dev ext3 rw,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
usbfs /dev/bus/usb/.usbfs usbfs rw 0 0
udev /proc/bus/usb tmpfs rw 0 0
usbfs /proc/bus/usb/.usbfs usbfs rw 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/disk/by-uuid/F66C92BA6C927559 /media/host0 fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

```

---

### Post by Valok on 2007-12-12
I just DLed Gparted, so here is some information from that that might help.

Under the information tab it says the following about my ext3 partition.

Path: /dev/hda2
Status: Mounted on /

First Sector: 143380125
Last Sector:240107489
Total Sectors:96727365


Under the ntfs partition it says that it cannot find the mountpoint.


Also under Gparted I had the option to manage flags for each partition.  The ntfs partition had the "boot" flag enabled while the ext3 did not.  I changed it so that the boot option is on the ext3 partition now, but it didn't seem to make any difference when I rebooted.

---

### Post by ago on 2007-12-12
You are on a dedicated partition, the boot flag is only used by windows

---

### Post by Valok on 2007-12-12
Awesome!  Thanks again for the help in clarifying this for me.

---

