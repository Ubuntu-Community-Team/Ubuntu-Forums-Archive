---
title: "Mounting and UnMounting Drivers"
date: 2007-09-02
forum: General Help
---

### Post by gavinjb on 2007-09-02
Hi,

I am having a couple of issues with my external drive, not sure if anyone could give me some advice. 

1. I have just resized the fat partition, to make room for an ext3 partition, but now I can see the partition, but cant write the data as a standard user needs write permissions, I know I need to make some changes to fstab, but I am not sure what I need to do.

When I looking in Mtab it is setup as follows

```

/dev/sdb2 /media/disk ext3 rw,noexec,nosuid,nodev 0 0

```

2. When I try to unmount the fat patition, I get the following error "There is data that needs to b written to the device <devicename> before it can be removed. Please do not remove the media or disconnect the drive"

This error has occurred before I resized the partition with GParted, so I know it isn't a result of resizing the drive, I am looking at changing the drive from fat32 to ext3 in the long term but currently I have too much data to look at this (unless anyone knows of a tool that can do this without losing the data).

Thanks,



Gavin,

---

### Post by taurus on 2007-09-02
1.  Change the ownership of /media/disk from root to your login name.  Then, you can write to it whenever you want.  _Assuming_ your login name is **gavin** (replace it with the right one, okay), do

```
sudo chown -R **gavin**:**gavin** /media/disk
ls -la /media
```

2.  You need to unmount the drive with

```
sudo umount /dev/XXX
```
where XXX is the device the drive that you want to unmount.

---

### Post by gavinjb on 2007-09-03
Thanks,

As I wanted to rename what it appears as I created a folder in /media called VirtualBox and then used chown, I also added an entry to fstab

```

/dev/sdb2 /media/VirtualBox ext3 rw,noexec,nosuid,nodev 0 0

```

But all I get is :

```
Cannot mount volume.

You are not privileged to mount this volume.
```

I have checked and as you can see I seem to have permissions, do I need to change something in fstab as I would like to give permissions to anyone on this machine to be able to mount this partition (power it on) and write to it.

```

drwxr-xr-x  2 gavin gavin  4096 2007-09-02 16:48 VirtualBox

```

Thanks,


Gavin,

---

### Post by taurus on 2007-09-03
You have permissions to write to it but you still need to be root to mount it first.  Either reboot or run

```
sudo mount -a
df -h
```

---

### Post by gavinjb on 2007-09-03
thanks,

but this drive is an external drive that I only power on when I need to access it, I am looking for a way, that when it powers on it will auto mount (which worked before I tried to give it write permissions and mount it under VirtualBox)

Thanks,


Gavin,

---

