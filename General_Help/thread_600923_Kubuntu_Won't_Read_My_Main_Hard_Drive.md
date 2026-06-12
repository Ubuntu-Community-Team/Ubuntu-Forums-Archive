---
title: "Kubuntu Won't Read My Main Hard Drive"
date: 2007-11-02
forum: General Help
---

### Post by MSchenker on 2007-11-02
Hello,
Until this afternoon, I had no problem accessing my main hard drive (the one known as C: in Windows).

Now, when I try to access it in Dolphin, I get this message:
*hal-storage-fixed-mount-all-options refused uid 100*

Can some please tell me what this is about?  How do I fix it?

Thanks,
Matt

---

### Post by taurus on 2007-11-02
Do you mount it with /etc/fstab?  Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
mount
```

---

### Post by MSchenker on 2007-11-02
Taurus,
I never knew how it was mounted.  Kubuntu just did it automatically.  Whenever I went into Dolphin, it showed my hard drive under the "Storage Media" entries.

I did the commands you suggested in a Konsole window, but I'm still getting the same errors.  I really hope you can help me solve this.

Here's the whole output:

[COLOR=RoyalBlue][sudo] password for matthew:

Disk /dev/sda: 80.0 GB, 80060424192 bytes
240 heads, 63 sectors/track, 10341 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1ffb1ffa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         556     4203328+  83  Linux
/dev/sda2   *         590       10340    73717560    7  HPFS/NTFS
/dev/sda3             557         589      249480    5  Extended
/dev/sda5             557         589      249448+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9728    78140128+   c  W95 FAT32 (LBA)
matthew@Main:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ec8a526a-1f3c-4cb5-93e6-47b033b754f8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=970235d4-b42b-46a3-9ac1-888fb9d7b833 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
matthew@Main:~$ mount
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
matthew@Main:~$

[/COLOR]

---

