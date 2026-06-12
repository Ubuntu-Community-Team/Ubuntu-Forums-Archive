---
title: "partitons just randomly changed mount points"
date: 2007-02-03
forum: General Help
---

### Post by Polygon on 2007-02-03
For some reason, (i think it might of been cause i installed kubuntu-desktop) my partitions are screwed up, and they changed mount points on me

here is a picture showing what i mean:

[[IMG]http://img502.imageshack.us/img502/6622/partitionchangeaw1.th.png[/IMG]](http://img502.imageshack.us/my.php?image=partitionchangeaw1.png)

i had 4 partitons, / , /boot , /home and /swap

but for some reason, /boot went over to the partition that had /home, and /dev/.static/dev got added to the partition that contained "/"

so.. how do i change this? i dont think changing the /etc/fstab would work because if this is correct, the the data somehow changed partitions as well? I dont know, im so confused :confused:

---

### Post by taurus on 2007-02-03
Are you using UUID in /etc/fstab?

---

### Post by Polygon on 2007-02-03
yeah, it has the UUID's listed. The only one i added manually was for my /home, because the installer did not give it one and i had to enter it manually for fsck to stop yelling at me

here is my /etc/fstab just in case anyone needs it:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hde2
UUID=ec884cb1-c508-4490-a861-784f6aec1b89 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hde1
UUID=c0675fc3-aca1-4dee-bd78-81012e478edf  /boot           ext3    defaults        0       2
# /dev/hde4
UUID=c0675fc3-aca1-4dee-bd78-81012e478edf /home           ext3    defaults        0       2
# /dev/hdf2
UUID=C09C1CF69C1CE924 /media/Programs ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdf3
UUID=1704-146C  /media/WinData  vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdf5
UUID=6C446449446417DA /media/Windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hde3
UUID=b38141e7-ce76-423b-886f-66f98a2cfd82 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


---

### Post by taurus on 2007-02-03
Why don't you replace the UUID with the actual device, /dev/XXXX, for your partitions in /etc/fstab.  Reboot and see if everything mounts where they're supposed to be.

---

### Post by Polygon on 2007-02-03
I did just what you told me, i uncommented the "/dev/hdXX" and deleted the UUID's in the /etc/fstab, and my computer still booted up (yay) and now it appears that /boot is appearing on the correct partition. It still says that one of the partitons has the mount point of / and /dev/.static/dev, but i dont care about that

but its weird that after having that there for a while, that /boot would suddenly appear to have changed partitons? Do i need to report this as a bug? i made a backup of the older fstab file

---

