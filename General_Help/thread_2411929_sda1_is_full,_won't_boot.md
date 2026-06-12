---
title: "sda1 is full, won't boot"
date: 2019-02-05
forum: General Help
---

### Post by webmanoffesto on 2019-02-05
I'm running on a live disk now. My laptop won't boot. I think that's because sda1 is full. 
How do I get access to sda1 while using a live disk and how do I clean up junk so it will boot again.

```

$ sudo fdisk -l 

Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0002d4c2

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048   40962047   40960000  19.5G 83 Linux
/dev/sda2         40962048 1887989759 1847027712 880.7G 83 Linux
/dev/sda3       1887989760 1953523711   65533952  31.3G 82 Linux swap / Solaris

~$ sudo blkid
/dev/sdb1: LABEL="MULTISYSTEM" UUID="7F5D-E59C" TYPE="vfat" PARTUUID="686a6515-01"
/dev/sda1: UUID="d1dc2540-fc44-47dc-a749-88e08be90b00" TYPE="ext4" PARTUUID="0002d4c2-01"
/dev/sda2: UUID="670d08f8-498c-4ac5-ad0b-eddf64dc8534" TYPE="ext4" PARTUUID="0002d4c2-02"
/dev/sda3: UUID="f2c26c25-ac0d-46c7-af3a-21fafebb01ff" TYPE="swap" PARTUUID="0002d4c2-03"
/dev/sdb2: LABEL="Tom" UUID="eb47bc29-aa23-4b83-a52e-543930de014c" TYPE="ext4" PARTUUID="686a6515-02"

$ sudo lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1   8:1    0  19.5G  0 part /mnt
&#9500;&#9472;sda2   8:2    0 880.7G  0 part 
&#9492;&#9472;sda3   8:3    0  31.3G  0 part [SWAP]
sdb      8:16   1  29.8G  0 disk 
&#9500;&#9472;sdb1   8:17   1  28.8G  0 part /isodevice
&#9492;&#9472;sdb2   8:18   1  1023M  0 part /media/ubuntu/Tom
sr0     11:0    1  1024M  0 rom  

```

---

### Post by oldfred on 2019-02-05
Linux normally reserves 5%, so users have a chance to houseclean or rearrange before it really is full.
You must not have noticed warnings?

You may have to chroot into system, if you you cannot boot.

Post this also, after mounting all partitions:
df -h

I use 25 or 30GB for / (root) and only use about 8 or 10GB. But I have all data in data partition including some hidden larger folders like Firefox & Thunderbird profiles.

Looks like old type BIOS install on MBR partitioned drive.
If UEFI, LVM or newer NVMe drive mounts would be different.

Once chrooted, you then can run housecleaning commands.
       drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
[http://en.wikipedia.org/wiki/Chroot](http://en.wikipedia.org/wiki/Chroot) 
    
Start with these, sudo not required inside a chroot:
       sudo apt-get update
sudo apt-get upgrade
apt-get autoremove
sudo apt-get autoclean
sudo apt-get dist-upgrade 
    
       # empty trash
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz 
    
Older links, but still valid for most housekeeping issues:
       RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

 Caution deborphan will delete anything you manually installed. See comment: 
 Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

---

### Post by webmanoffesto on 2019-02-05
> **oldfred said:**
> 
Post this also, after mounting all partitions:
df -h


The output of "df -h" is confusing because, sda must be the large SSD in my laptop which has three partitions:

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048   40962047   40960000  19.5G 83 Linux
/dev/sda2         40962048 1887989759 1847027712 880.7G 83 Linux
/dev/sda3       1887989760 1953523711   65533952  31.3G 82 Linux swap / Solari..

```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        20G   19G     0 100% /mnt
/dev/sdb1        29G   18G   12G  61% /isodevice
/dev/sdb2       991M  1.3M  923M   1% /media/ubuntu/Tom
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  1.8M  1.6G   1% /run
/dev/loop0      1.9G  1.9G     0 100% /cdrom
/dev/loop1      1.8G  1.8G     0 100% /rofs
/cow            7.8G  3.2G  4.7G  41% /
tmpfs           7.8G   32M  7.8G   1% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
tmpfs           7.8G   17M  7.8G   1% /tmp
tmpfs           1.6G   68K  1.6G   1% /run/user/999
/dev/loop2       87M   87M     0 100% /snap/core/4917
/dev/loop3       35M   35M     0 100% /snap/gtk-common-themes/319
/dev/loop4      141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/loop5      2.4M  2.4M     0 100% /snap/gnome-calculator/180
/dev/loop6       13M   13M     0 100% /snap/gnome-characters/103
/dev/loop7       15M   15M     0 100% /snap/gnome-logs/37
/dev/loop8      3.8M  3.8M     0 100% /snap/gnome-system-monitor/51

```

---

### Post by oldfred on 2019-02-05
It looks like you did not mount the second Linux partition on sda, so it is not shown in output.

But sda1 is then the partition you need to chroot into & houseclean.

---

### Post by webmanoffesto on 2019-02-06
> **oldfred said:**
> It looks like you did not mount the second Linux partition on sda, so it is not shown in output.
But sda1 is then the partition you need to chroot into & houseclean.
How do I do that?

------------

I seem to have access to sda1. What do I do now?
```

$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~/bin$ cd /mnt
ubuntu@ubuntu:/mnt$ ls
bin   cdrom  etc   initrd.img      lib    lib64       media  opt   root  sbin  srv  tmp  var      vmlinuz.old
boot  dev    home  initrd.img.old  lib32  lost+found  mnt    proc  run   snap  sys  usr  vmlinuz

```

```

$ lsblk -af |grep -sv loop 
NAME   FSTYPE   LABEL                    UUID                                 MOUNTPOINT
sda                                                                           
&#9500;&#9472;sda1 ext4                              d1dc2540-fc44-47dc-a749-88e08be90b00 /mnt
&#9500;&#9472;sda2 ext4                              670d08f8-498c-4ac5-ad0b-eddf64dc8534 
&#9492;&#9472;sda3 swap                              f2c26c25-ac0d-46c7-af3a-21fafebb01ff [SWAP]
sdb                                                                           
&#9500;&#9472;sdb1 vfat     MULTISYSTEM              7F5D-E59C                            /isodevice
&#9492;&#9472;sdb2 ext4     Tom                      eb47bc29-aa23-4b83-a52e-543930de014c 
sr0 

```

I have write permission there too
```

/mnt$ sudo mkdir testing
/mnt$ ls
bin   cdrom  etc   initrd.img      lib    lib64       media  opt   root  sbin  srv  testing  usr  vmlinuz
boot  dev    home  initrd.img.old  lib32  lost+found  mnt    proc  run   snap  sys  tmp      var  vmlinuz.old
/mnt$ cd testing
/mnt/testing$ sudo nano testing.txt
/mnt/testing$ sudo mv testing.txt testing.v02.txt
/mnt/testing$ ls
testing.v02.txt

```

I have a VM in "mnt/usr/share/virtualbox"
I guess I could delete that and then just rebuild it later. Is that a good idea?

Maybe I could delete something here
```

/mnt$ sudo find -type f -exec du -Sh {} + | sort -rh | head -n 5
1.4G    ./usr/share/games/0ad/mods/public/public.zip
908M    ./var/lib/snapd/snaps/0ad_47.snap
906M    ./var/lib/snapd/snaps/0ad_50.snap
904M    ./var/lib/snapd/snaps/0ad_61.snap
411M    ./var/lib/snapd/snaps/wine-platform_74.snap

```

I deleted
./usr/share/games/0ad/mods/public/public.zip

and then was able to boot up my system.
I got the "filling up" error message again, so I ran the below, those snaps took up a lot of space.
```

#!/bin/bash
# Removes old revisions of snaps
# CLOSE ALL SNAPS BEFORE RUNNING THIS
set -eu


snap list --all | awk '/disabled/{print $1, $3}' |
    while read snapname revision; do
        snap remove "$snapname" --revision="$revision"
    done

```

---

### Post by oldfred on 2019-02-06
You can automount just by clicking on it in browser.
or manually mount, but have to create a mount point first.

[https://askubuntu.com/questions/1029040/how-to-manually-mount-a-partition](https://askubuntu.com/questions/1029040/how-to-manually-mount-a-partition)

       sudo umount /dev/sda2
sudo mkdir /media/temp
sudo mount /dev/sda2 /media/temp -o umask=000

---

