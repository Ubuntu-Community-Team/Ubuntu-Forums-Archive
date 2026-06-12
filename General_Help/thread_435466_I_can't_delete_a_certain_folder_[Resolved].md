---
title: "I can't delete a certain folder [Resolved]"
date: 2007-05-06
forum: General Help
---

### Post by Jimmeh on 2007-05-06
Hello all

I'm having trouble deleting a folder in my home directory. Usually it's quite straight forward, but this one won't delete.
The folder is called "<mount point>", and it got created automatically after I was trying to mount a hard disk that wasn't mounting. So when I issue the command "rm -r <\<mount\ point\>/" (i assume they are escape characters in there).. its says please see the rm help file. I can't seem to cd in to it either.
It says the root user has ownership, and Ive tried using sudo. I've also tried umount.

Any idea?

Thanks

James

---

### Post by aysiu on 2007-05-06
Are you sure it's not currently mounted? Is it an empty folder? Or is it displaying the contents of a drive?

Can you post the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
``` Just paste the commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here.

---

### Post by Jimmeh on 2007-05-06
I can browse to it in Konqueror, but nothing is in there.

sudo fdisk -l :
```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4099    32925186    7  HPFS/NTFS
/dev/sda2            4100        4227     1028160   82  Linux swap / Solaris
/dev/sda3            4228        4865     5124735   83  Linux

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7297    58613121    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        1023     8217243   54  OnTrackDM6

```

df -h :
```

Filesystem            Size Used Avail Use% Mounted on
/dev/sda3             4.9G  2.8G  1.8G  61% /
varrun                505M   96K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
procbususb            505M  128K  505M   1% /proc/bus/usb
udev                  505M  128K  505M   1% /dev
devshm                505M     0  505M   0% /dev/shm
lrm                   505M   33M  472M   7% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1              32G  8.4G   24G  27% /media/sda1
/dev/sdb1              56G   50G  6.8G  88% /media/sdb1
/dev/sdc1             233G  230G  3.2G  99% /media/sdc1

```

cat /etc/fstab :
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=24421c56-894b-499f-810f-cda9577f6e32 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda1
UUID=B28023CD802396BF /media/sda1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sdb1
UUID=D6F0146BF01453D9 /media/sdb1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sdc1
UUID=B4B8D9ABB8D96BFC /media/sdc1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda2
UUID=c0c92470-1c8f-46ad-a302-20b8868c4da0 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
<device> <mount\040point> auto users,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0

```

Seems to show up in the fstab file

---

### Post by aysiu on 2007-05-07
```
<device> <mount\040point> auto users,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0
``` Whoa. That's weird.

Press Alt-F2 and type ```
kdesu konqueror
``` Navigate to /etc and edit the fstab file and delete that last weird line. Then go to your home directory and delete <mount\40point>

---

### Post by Jimmeh on 2007-05-07
Thanks, that worked!
Appreciate it

---

