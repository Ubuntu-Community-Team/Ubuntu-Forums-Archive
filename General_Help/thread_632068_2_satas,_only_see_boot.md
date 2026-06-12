---
title: "2 satas, only see boot"
date: 2007-12-05
forum: General Help
---

### Post by helbuns on 2007-12-05
i have 2 hard drives, 1 500gb with 2 partitions one which is boot, and another harddrive 120gb that has 2 partitons one of which is boot, both ubuntu. i have data i wanna extra from 120gb, i normall use the 500, both run fine when only one is connected.. but when both are hooked up, they are SATA if that matters, when they are both hooked up which ever one is plugged into the "primary" (i guess) data cable is boot, i see alot of post people putting up mouth, fstab -l and.. something else i don't remember. oh and i can't see it in g-parted either.

helbuns@helbuns-desktop:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda4 on /storage type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=helbuns)



helbuns@helbuns-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00072abe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *       35704       60044   195519082+  83  Linux
/dev/sda3           60045       60801     6080602+   5  Extended
/dev/sda4              20       35703   286631730   83  Linux
/dev/sda5           60045       60801     6080571   82  Linux swap / Solaris

Partition table entries are not in disk order
helbuns@helbuns-desktop:~$ 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4 /storage ext3 defaults 0 0
# /dev/sda2
UUID=f972c389-7da6-4995-bb01-0991450db7d0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d15bfe37-eb3a-4113-a509-0647c83371cd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


now again... i don't know what anything means.. but i would like to "mount" my second drive.. or whatever.. steal the data and then wipe her out allll over again. also can i only wipe a drive with g-parted if it's not the boot drive? i mean i have to unmount it and then play with it? so if i wanted to resize my boot i would mount it under another drive then? i know 2 hard questions sorry. but thank you for helping.

- Helbuns :)

---

### Post by barney_1 on 2007-12-07
This is an interesting problem you have.

The first thing I would do is check your bios settings.  You should not have RAID enabled since you are trying to use the two drives separately.  If that turns out to be the problem, you should be able to disable it, connect both drives and try again.

You posted the output of:
```
sudo fdisk -l
```

And we see this listed:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00072abe

Device Boot Start End Blocks Id System
/dev/sda2 * 35704 60044 195519082+ 83 Linux
/dev/sda3 60045 60801 6080602+ 5 Extended
/dev/sda4 20 35703 286631730 83 Linux
/dev/sda5 60045 60801 6080571 82 Linux swap / Solaris

Partition table entries are not in disk order
```

This shows us one drive located at /dev/sda with a size of 500.1gb.  We should also see your other drive and it should be listed as /dev/sdb but it is not.  Did you have both drives connected when you ran this command.  If so this also makes me think there is a problem with your bios setup.

If you bios is fine, I would suggest hooking up both hard drives but boot to a liveCD.  Then run the command:
```
sudo fdisk -l
```
and post the output here.

---

