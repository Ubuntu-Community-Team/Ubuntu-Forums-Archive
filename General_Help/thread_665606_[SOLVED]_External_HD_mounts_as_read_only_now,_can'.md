---
title: "[SOLVED] External HD mounts as read only now, can't backup files anymore"
date: 2008-01-12
forum: General Help
---

### Post by lanruisen on 2008-01-12
I have a fat32 external HDD, I used to use to store files, now it says that it is read only, so I now have files that are stuck in the trash and can't be deleted. I tried to change the permissions, but this didn't work. I am wondering if the problem was installing emule  with wine on the removable HDD. Because now I can't use emule anymore, nor can I uninstall it through wine, and I can't reinstall it because the emule installer won't open with wine anymore. Any suggestions? I am using Ubuntu 7.10

---

### Post by taurus on 2008-01-12
How did you mount that fat32 partition?  Can you post the output of this command from a terminal?

```
mount
```

---

### Post by lanruisen on 2008-01-12
It's USB


```
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb5 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
```

---

### Post by taurus on 2008-01-12
Try

```
sudo umount /dev/sdb5
sudo mkdir /media/disk
sudo mount -t vfat /dev/sdb5 /media/disk -o umask=000
ls -la /media/disk
```

---

### Post by lanruisen on 2008-01-12
This is what I got.

```
ubuntu@ubuntu-laptop:~$ sudo umount /dev/sdb5
ubuntu@ubuntu-laptop:~$ sudo mkdir /media/disk
mkdir: cannot create directory `/media/disk': File exists
ubuntu@ubuntu-laptop:~$ sudo mount -t vfat /dev/sdb5 /media/disk -o umask=000
mount: mount point /media/disk does not exist
ubuntu@ubuntu-laptop:~$ ls -la /media/disk
```

---

### Post by lanruisen on 2008-01-12
I just plugged the drive back in, no change, still read only.

---

### Post by taurus on 2008-01-12
How about

```

sudo umount /dev/sdb5
sudo mkdir /media/sdb5
sudo mount -t vfat /dev/sdb5 /media/sdb5 -o umask=000
ls -la /media/sdb5

```

---

### Post by lanruisen on 2008-01-12
OK, that changed the names of the volume and now give me options to create files, but does not let me do so because it says I am not the owner of the volume. And I still can't empty the trash.  I do appreciate the help.

---

### Post by taurus on 2008-01-12
Just run nautilus with root privilege and you should be able to remove the trash on your USB drive.

```
gksudo nautilus
```

---

### Post by lanruisen on 2008-01-12
No, that didn't work. In fact now I have the disk mounted twice. One as "disk" which is my removable HDD, and as sdb5, which is an empty volume that can't be unmounted.


For some odd reason the drive let me write files for about 10mins and then it locked up again, but that was not using nautilus as root.  Maybe I should just reinstall.

---

### Post by taurus on 2008-01-12
Are you sharing that external harddrive with a windows machine?  If not, then why not format it as ext3 instead of vfat becasue ext3 is much better filesystem.

---

### Post by lanruisen on 2008-01-12
I use it with both windows and mac.

---

### Post by chrisccoulson on 2008-01-12
Filesystems being mounted as read-only are usually a symptom of errors on the filesystems. Being re-mounted usually happens automatically if there are errors, causing the behaviour you describe. It might be worth opening up a terminal, and monitoring the output of:
```
tail -f /var/log/messages
```
Do this before you plug in the drive, and monitor what happens when you plug it in and try to read/write data on the drive.

If there are errors, it's probably worth doing a dosfsck on the volume to see if it can be fixed. Make sure the device is unmounted before using dosfsck though.

I've seen this behaviour several times before on external FAT32 USB drives when they have been removed before all data has been written to the drive.

---

### Post by lanruisen on 2008-02-12
The problem was that the disk had some errors. I hooked it up to my Windoze box and ran the disk maintenence utility and that solved the problem. Now it mounts just fine.

Now I would like to know if there is a utility like that for Linux.

---

### Post by smoka on 2008-03-21
Yeah, I agree **lanruisen** - the quickest way I found to fix this was to connect it up to one of my WinXP machines and run chkdsk /f on the drive.

Plugged it back into my Ubuntu Machine (Gutsy Gibbon) and it mounted it correctly with read/write instead of just read only as it had been doing.

I'm wondering if anyone has a nice ***quick and simple*** solution for a fix without having to depend on a Windows box to fix this problem every time.

---

### Post by chrisccoulson on 2008-03-21
Yes, you can use dosfsck
```
man dosfsck
```

---

### Post by smoka on 2008-03-21
Ta for the info on dosfsck *chrisccoulson*, I'll have to try and remember to give that a try next time it happens, but I get a feeling that it won't work as the whole USB stick is mounted as read only, so I expect that it may find errors, but most likely will not be able to fix as it won't have the write permissions.

---

### Post by chrisccoulson on 2008-03-21
It doesn't matter whether the device mounted read-only or not, because you should never run dosfsck on a mounted volume, period. In fact, you shouldn't run any fsck on a mounted volume. **Always unmount first**, or you risk breaking your filesystem.

dosfsck works on the raw device (/dev/*whatever*) who's permissions are determined by udev. Those permissions are not related to whether the device is mounted read-write or read-only.

So, don't worry, dosfsck will work fine (just like fsck for all other filesystems). You have to specify either the -a or -r option if you want errors fixed though.

---

