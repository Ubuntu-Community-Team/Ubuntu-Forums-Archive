---
title: "Confused on LVM lost space"
date: 2014-05-20
forum: General Help
---

### Post by andrew0401 on 2014-05-20
I am running Ubuntu 12.04 Server and am getting totally confused about where the space on the LVM has gone.
The LVM is 35GB but the only files/directories I can find are barely 2GB - yet it is reporting as 90% full.  
Sure I am missing something obvious - just not sure what!
Thanks
Andrew
[EMAIL="root@dell1600"]root@dell1600[/EMAIL]:~# pvdisplay
  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               dell1600
  PV Size               37.03 GiB / not usable 1.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              9480
  Free PE               0
  Allocated PE          9480
  PV UUID               Bc25HQ-2Rgd-LfFc-1hvL-1r4x-2BKB-IVXPGq
[EMAIL="root@dell1600"]root@dell1600[/EMAIL]:~# lvdisplay
  --- Logical volume ---
  LV Name                /dev/dell1600/root
  VG Name                dell1600
  LV UUID                yPw3oD-fk6q-VEPd-Q9KR-MG2l-E4i7-vnYD0T
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                35.46 GiB
  Current LE             9079
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
  --- Logical volume ---
  LV Name                /dev/dell1600/swap_1
  VG Name                dell1600
  LV UUID                sC0OMg-rmN1-C2n5-gXx0-iPuX-WjIp-EbrgYd
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                1.57 GiB
  Current LE             401
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
[EMAIL="root@dell1600"]root@dell1600[/EMAIL]:~# df -h
Filesystem                 Size  Used Avail Use% Mounted on
/dev/mapper/dell1600-root   35G   31G  3.5G  90% /
udev                       1.5G  4.0K  1.5G   1% /dev
tmpfs                      303M  692K  302M   1% /run
none                       5.0M     0  5.0M   0% /run/lock
none                       1.5G     0  1.5G   0% /run/shm
/dev/sda1                  228M   30M  187M  14% /boot
[EMAIL="root@dell1600:/"]root@dell1600:/[/EMAIL]# du -xks * | sort -n
du: cannot access `proc/9884/task/9884/fd/4': No such file or directory
du: cannot access `proc/9884/task/9884/fdinfo/4': No such file or directory
du: cannot access `proc/9884/fd/4': No such file or directory
du: cannot access `proc/9884/fdinfo/4': No such file or directory
0       initrd.img
0       proc
0       sys
0       vmlinuz
4       dev
4       selinux
4       srv
4       webmin-setup.out
8       media
8       tmp
12      mnt
12      opt
16      lost+found
20      export
692     run
4708    root
8564    bin
9096    sbin
13680   home
29714   boot
32560   etc
184056  lib
352356  var
714052  usr
[EMAIL="root@dell1600:/"]root@dell1600:/[/EMAIL]#

---

### Post by J_Me on 2014-05-20
You may have better luck with gparted or your partition manager. I'm no expert on this but as far as I understood LVM uses up space dynamically when it's needed. For me 'df -h' doesn't even list my lvm partition.

---

### Post by oldfred on 2014-05-20
I did not think gparted worked on LVM.

But with LVM you have the physical partitions that the LVM are in and the logical partitions that are the LVM. You may need to resize the LVM?

       LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by steeldriver on 2014-05-20
What usually causes these anomalies is when a mounted filesystem 'drops off', and data gets written to the root disk via the empty mount point - and then hidden from 'du' once the filesystem is remounted

---

