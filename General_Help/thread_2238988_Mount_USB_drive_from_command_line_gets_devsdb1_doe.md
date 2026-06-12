---
title: "Mount USB drive from command line gets /dev/sdb1 does not exist error"
date: 2014-08-11
forum: General Help
---

### Post by roadrawts on 2014-08-11
Need help with mount of USB drive in Ubuntu 14.04 LTS from command line. USB drive mounts when automatically to /dev/sdb1 when I plug it in.  But when I try and mount from the command line or in a shell script I get /dev/sdb1 special device does not exist.

When it mounts automatically it shows up as:

/dev/sdb1 on /media/USB DISK type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)

The shell script is:
sudo mount -t vfat /dev/sdb1 /media/USB\ DISK

Thanks

---

### Post by roadrawts on 2014-08-11
Changed the name of the device from USB\ DISK to just USB to eliminate the space in the name.

The shell script line is :
sudo mount -t vfat /dev/sdb1 /media/myID/USB -o uid=1000,gid=1000,utf8=1,dmask=027,fmask=137

now getting "Permission Denied" with permissions set ot drxwr -xr-x on myID as owner and group.

---

### Post by roadrawts on 2014-08-12
Got rid of the permission issue and now back to /dev/sdb1 does not exist.  Can't seem to figure this out.

---

### Post by steeldriver on 2014-08-12
The /dev/sd[a-z][0-9] block device numbering isn't guaranteed to be persistent - you can check what current device the system recognizes using

```

sudo parted -l

```

or
```

sudo fdisk -l

```

(note that fdisk doesn't cope well with GPT disks or LVM/RAID devices though). If you are going to automate the mounting via /etc/fstab you will likely find it is more reliable to use either a partition label or UUID instead of relying on the /dev/sd[a-z][0-9] block device numbering - you can find the UUID using

```

sudo blkid -c /dev/null

```

---

