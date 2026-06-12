---
title: "vfat drive became read-only"
date: 2006-07-16
forum: General Help
---

### Post by PsychoCemia on 2006-07-16
Ok...I've looked through just about every thread in every forum I've tried, and I'm still stuck on how to fix this. I have an external drive (250gb) that I've partitioned to vfat, and have had a rocky trip with it ever since I've started. I've been able to mount it using the following /etc/fstab settings: (you'll see that the external drive is /dev/sda5)

```

proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/Windows  ntfs    ro,defaults,user,gid=1000,umask=0222 0       0
/dev/sda5       /media/MEDIA    vfat    rw,users,shortname=mixed,codepage=850,exec,auto,uid=1004,gid=1000,umask=0000 0 0

```

Well, it worked fine as it stands for several days, but one night while I was asleep, the power cut out in the house for a second (while a transfer was going on). Ever since, every time I mount the drive, it turns out to be read-only, even though I see rwx permissions for all users in the properties tab. 

dmesg gives me the following pertinent info whenever I mount the drive:
```

[17182216.700000] FAT: Filesystem panic (dev sda5)
[17182216.700000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[17182216.700000]     File system has been set read-only

```

This leads me to believe that the drive is being mounted correctly as rw, but because of some writing error, ubuntu has taken it upon itself to freak out and close it down for writing further.

Thanks in advance for your help.

---

### Post by PsychoCemia on 2006-07-16
ok...well...I looked around a bit more, and saw a couple tricks others have tried, most notably those of unmounting and remounting, rebooting repeatedly, and clearing the /etc/fstab entry and remounting...and none of these have worked.

If anyone has any ideas, PLEASE help... 
Thanks.

---

### Post by ky0sh0 on 2008-05-17
in your /etc/fstab add options :

fmask=0000,dmask=0000

a lil bit late but what the heck it'll saves somebody else's arss :D

---

