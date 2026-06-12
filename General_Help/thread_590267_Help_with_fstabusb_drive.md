---
title: "Help with fstab/usb drive"
date: 2007-10-24
forum: General Help
---

### Post by herbster on 2007-10-24
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2a90aa4e-34b7-4078-b793-ef2e73d8987a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=f95565d9-b747-43f9-9cc3-d1630cf77eaa /home           ext3    defaults        0       2
# /dev/sdb3
UUID=310b7b87-0c52-4f4e-add7-1c30d9fed9ee /media/bobby    ext3    defaults        0       2
# /dev/sda4
UUID=dbf82137-d915-48cf-a729-95a34a67cdf4 /media/extra    ext3    defaults        0       2
# /dev/sdb1
UUID=9850f8ff-b9f4-4bbd-9e52-a6ea4a461a2b /media/feistyhome ext3    defaults        0       2
# /dev/sdb2
UUID=a3889ed1-1210-4cd5-8fc4-9309ba6039fc /media/feistyroot ext3    defaults        0       2
# /dev/sda2
UUID=f603a8f1-4d2a-4553-b935-55c53840a588 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdc1	/media/videobackup    ext3    defaults        0       2
/dev/sdc2	/media/newpicsbackup    ext3    defaults        0       2
/dev/sdc3	/media/systembackup    ext3    defaults        0       2
```

I have a 500gb WD drive in an enclosure connected via USB, and when I hit the on switch it doesn't automount, I have to sudo mount /dev/sdc1-3 for it to go and then I can use it just fine via the mount points in /media above.

I think by just copying the lines it's wrong, I mean the "2" at the end of each one I don't even know what that does, lol. I also think I should put user,noauto on each because I don't need it automounted at boot (in fact that's caused some probs). Can someone edit those lines properly for me???

---

### Post by logos34 on 2007-10-24
The '2' is fsck option--means it checks it in order after the root partition.  You can change it to 0 if you want.

system>preferences>removable drives and media>storage tab>check [B]mount removable drive when hot-plugged
[/B]

rw,noauto,user 

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by herbster on 2007-10-27
logos34,

Thanks! The problem was I took it upon myself to mount the external without even really letting it automount. I've deleted my set directories in /media and removed its lines from fstab, it now automounts just fine. Thanks!! :)

---

