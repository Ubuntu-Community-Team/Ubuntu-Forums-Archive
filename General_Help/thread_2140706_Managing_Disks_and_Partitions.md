---
title: "Managing Disks and Partitions"
date: 2013-04-30
forum: General Help
---

### Post by sebastiaopburnay on 2013-04-30
Hi,

I have an Ubuntu.12.04 64bit server VM which I have created with a single 60GB Virtual Disk:
```
root@myServer:~# df -h
Filesystem              Size  Used Avail Use% Mounted on
/dev/mapper/argus-root   58G  2.9G   52G   6% /
udev                    992M  4.0K  992M   1% /dev
tmpfs                   401M  340K  400M   1% /run
none                    5.0M     0  5.0M   0% /run/lock
none                   1001M     0 1001M   0% /run/shm
/dev/sda1               228M   25M  192M  12% /boot
```

I added this VM two disks:
[LIST=1]
[*]one for logs - 7GB, where I'd like to point /var/log/
[*]and other for the MySQL databases - 20GB, where I'd like to point /var/lib/mysql
[/LIST]

I have added those disks using the VMware Player's GUI and they are correctly associated with my ubuntu VM.

I just don't understand 
[LIST=1]
[*] why are the disks not listed with the df command,
[*] nor how to make them be recognized
[*] and more importantly, how will I map the mentioned parts of my actual FileSystem to these new disks
[/LIST]

Just for completion, I'm putting a VMWare Player's GUI screen as attachment to this post.

Thank you very much for your support

---

### Post by sebastiaopburnay on 2013-05-02
I began following some instructions and found those two drives were '/dev/sdb' and '/dev/sdc', both with:
```
root@argus:~# fsdisk -l
...
Disk identifier: 0x00000000
Disk /dev/sdc doesn't contain a valid partition table
...
```
For each drive I've done:
```
root@argus:~# mkfs.ext4 /dev/sdb
root@argus:~# chmod -R 777 <mounting point>
root@argus:~# mount /dev/sdb <mounting point>
```
And afterwords I've edited /etc/fstab and added an entry for each drive:
```
root@argus:~# cat /etc/fstab
# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/argus-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=0daeb714-1f37-46db-9ab2-a469cfb36e5d /boot           ext2    defaults        0       2
/dev/mapper/argus-swap_1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb        /var/lib/mysql  ext4    defaults        0       0
/dev/sdc        /var/log        ext4    defaults        0       0
```
After, I rebooted the system and I've sent a 700MB .iso to /var/log, and the respective entry in 'df -h' acused the extra ocupation rate from it (seems that it did the trick).

I'm just not understanding howcome the uoutput of fdisk -l:
```
...
Disk identifier: 0x00000000
Disk /dev/sdc doesn't contain a valid partition table
...
```
Why were these drives not given an identifier and why does the system complain about the validity of partition tables?

Thanks anyway.

Best regards,
sebastiaopburnay

---

### Post by prodigy_ on 2013-05-02
You don't mount block devices (e.g. /dev/sdc), you mount partitions (e.g. /dev/sdc1). You need to create partitions on your drives and and format those partitions to create file systems on them.

More info:
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

