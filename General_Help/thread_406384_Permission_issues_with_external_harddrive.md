---
title: "Permission issues with external harddrive"
date: 2007-04-10
forum: General Help
---

### Post by dbansal on 2007-04-10
Hello,

So I finally got my external harddrive to detect. However, it is on an NTFS filesystem and I am having permissions issues with it. I checked some suggestions on the forums (unmounting > editing fstab > remounting). The only problem is that my fstab does not list my external harddrive. I can access the harddrive just fine. Any suggestions?

Here are the commands that i have entered:
[I]
lodge@lodge-server:/$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         319     2562336   82  Linux swap / Solaris
/dev/hda2             320         956     5116702+  83  Linux
/dev/hda3             957        7297    50934082+  83  Linux

[COLOR="Red"]Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes[/COLOR]

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]/dev/sda1   *           1       30515   245111706    7  HPFS/NTFS[/COLOR][/I]

[I]lodge@lodge-server:/$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=a190aa94-46a4-4676-9ede-f374b1f8d3aa /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=7f22e723-779e-4cfc-ba53-f83864c0e851 /files/hda3     ext3    defaults        0       2
# /dev/hda1
UUID=d5779f1c-b0ce-470c-9bc5-6e95c0a81a97 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
[/I]

[I]lodge@lodge-server:/$ cat /etc/mtab
/dev/hda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-11-generic/volatile tmpfs rw 0 0
/dev/hda3 /files/hda3 ext3 rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
[COLOR="Red"]/dev/sda1 /media/New\040Volume ntfs rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0[/COLOR]


[/I]

---

### Post by dbansal on 2007-04-10
bump

---

