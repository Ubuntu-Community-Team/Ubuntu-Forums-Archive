---
title: "Setting up a RAID1 on lvm. is this normal"
date: 2022-02-16
forum: General Help
---

### Post by rsteinmetz70112 on 2022-02-16
In the past I've used mdadm with lvm2 on top. I decided to try Raid on lvm and I think I've almost got it.

I got two new hard drives.

I installed a GPT partition table and set up partitions on one including a UEFI partition in case I need it in the future. 

Using sfdisk I copied the partition table from sdg to sdf.

I created a pv on each of sdg3 and sdf3

I then created a volume group using sdg3 and sdf3

Next I created the lvs I wanted and installed an ext4 filesystem on each of the volumes

I was able to mount the new lv on /mnt to begin the file transfer from the old location.

However when I run lsblk, I see each lv 4 times - twice on each hard drive all 4 show they are mounted on /mnt. The other unmounted lvs show 4 times as well, once ending in rmeta_1 and once ending in rimage_1    

Is this normal? I'm used to how mdadm displays things and this is different.

---

### Post by TheFu on 2022-02-16
Can you please post all the LVM create commands for the PV, VG, and LV?  The exact commands with all options.

---

### Post by MAFoElffen on 2022-02-16
This is just a quirky behavior of and normal output for 'lsblk' when it concerns RAID Arrays... It is saying that those LVM elements exist within the md device. You will notice that is the same/unique md device, that just happens to exist on multiple disks... In RAID1, as mirrored on drives and or partitions. In RAID5, as spanned across disks and or partitions.

For example in this RAID1 Machine:
```

mafoelffen@test-UD-raid1:~$ lsblk | grep -v 'loop'
NAME             MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sr0               11:0    1  1024M  0 rom   
vda              252:0    0    25G  0 disk  
&#9500;&#9472;vda1           252:1    0   512M  0 part  
&#9492;&#9472;vda2           252:2    0  24.5G  0 part  
  &#9492;&#9472;md0            9:0    0  24.5G  0 raid1 
    &#9492;&#9472;md0p1      259:0    0  24.5G  0 part  
      &#9500;&#9472;vg0-swap 253:0    0     4G  0 lvm   [SWAP]
      &#9492;&#9472;vg0-root 253:1    0  16.4G  0 lvm   /
vdb              252:16   0    25G  0 disk  
&#9500;&#9472;vdb1           252:17   0   512M  0 part  /boot/efi
&#9492;&#9472;vdb2           252:18   0  24.5G  0 part  
  &#9492;&#9472;md0            9:0    0  24.5G  0 raid1 
    &#9492;&#9472;md0p1      259:0    0  24.5G  0 part  
      &#9500;&#9472;vg0-swap 253:0    0     4G  0 lvm   [SWAP]
      &#9492;&#9472;vg0-root 253:1    0  16.4G  0 lvm   /

```
On this Machine on RAID5 arrays:
```

mafoelffen@u-desktop-raid5-01:~$ lsblk | grep -v 'loop'
NAME               MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
sr0                 11:0    1  1.2G  0 rom   /media/mafoelffen/Ubuntu-Server 20.
vda                252:0    0   40G  0 disk  
&#9500;&#9472;vda1             252:1    0  512M  0 part  /boot/efi
&#9500;&#9472;vda2             252:2    0   20G  0 part  
&#9474; &#9492;&#9472;md127            9:127  0   40G  0 raid5 
&#9474;   &#9500;&#9472;md127p1      259:0    0   31G  0 part  
&#9474;   &#9474; &#9492;&#9472;vg--ubuntu--0-lv--root
&#9474;   &#9474;              253:0    0   31G  0 lvm   /
&#9474;   &#9492;&#9472;md127p2      259:2    0    9G  0 part  
&#9474;     &#9492;&#9472;vg--ubuntu--3-lv--swap
&#9474;                  253:1    0    9G  0 lvm   [SWAP]
&#9492;&#9472;vda3             252:3    0 19.5G  0 part  
  &#9492;&#9472;md126            9:126  0   39G  0 raid5 
    &#9492;&#9472;md126p1      259:1    0   39G  0 part  
      &#9492;&#9472;dm_crypt-1 253:2    0   39G  0 crypt 
        &#9492;&#9472;vg--ubuntu--1-lv--home
                   253:3    0   39G  0 lvm   /home
vdb                252:16   0   40G  0 disk  
&#9500;&#9472;vdb1             252:17   0  512M  0 part  
&#9500;&#9472;vdb2             252:18   0   20G  0 part  
&#9474; &#9492;&#9472;md127            9:127  0   40G  0 raid5 
&#9474;   &#9500;&#9472;md127p1      259:0    0   31G  0 part  
&#9474;   &#9474; &#9492;&#9472;vg--ubuntu--0-lv--root
&#9474;   &#9474;              253:0    0   31G  0 lvm   /
&#9474;   &#9492;&#9472;md127p2      259:2    0    9G  0 part  
&#9474;     &#9492;&#9472;vg--ubuntu--3-lv--swap
&#9474;                  253:1    0    9G  0 lvm   [SWAP]
&#9492;&#9472;vdb3             252:19   0 19.5G  0 part  
  &#9492;&#9472;md126            9:126  0   39G  0 raid5 
    &#9492;&#9472;md126p1      259:1    0   39G  0 part  
      &#9492;&#9472;dm_crypt-1 253:2    0   39G  0 crypt 
        &#9492;&#9472;vg--ubuntu--1-lv--home
                   253:3    0   39G  0 lvm   /home
vdc                252:32   0   40G  0 disk  
&#9500;&#9472;vdc1             252:33   0  512M  0 part  
&#9500;&#9472;vdc2             252:34   0   20G  0 part  
&#9474; &#9492;&#9472;md127            9:127  0   40G  0 raid5 
&#9474;   &#9500;&#9472;md127p1      259:0    0   31G  0 part  
&#9474;   &#9474; &#9492;&#9472;vg--ubuntu--0-lv--root
&#9474;   &#9474;              253:0    0   31G  0 lvm   /
&#9474;   &#9492;&#9472;md127p2      259:2    0    9G  0 part  
&#9474;     &#9492;&#9472;vg--ubuntu--3-lv--swap
&#9474;                  253:1    0    9G  0 lvm   [SWAP]
&#9492;&#9472;vdc3             252:35   0 19.5G  0 part  
  &#9492;&#9472;md126            9:126  0   39G  0 raid5 
    &#9492;&#9472;md126p1      259:1    0   39G  0 part  
      &#9492;&#9472;dm_crypt-1 253:2    0   39G  0 crypt 
        &#9492;&#9472;vg--ubuntu--1-lv--home
                   253:3    0   39G  0 lvm   /home

```

---

### Post by rsteinmetz70112 on 2022-02-17
**TheFu** 

Sorry it took so long. I went home and I needed to check the sources I used to recreate the commands I used. If this is not exact it's very very close. My bash history file doesn't go back far enough to get the exact commands.

I mostly followed this guide;

[https://wiki.gentoo.org/wiki/Raid1_with_LVM_from_scratch](https://wiki.gentoo.org/wiki/Raid1_with_LVM_from_scratch) 

Here is the partition table I created with parted;

```
~# parted /dev/sdg
GNU Parted 3.3
Using /dev/sdg
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: ATA TOSHIBA HDWR440 (scsi)
Disk /dev/sdg: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name     Flags
 1      32.8kB  4194kB  4162kB               primary  msftdata
 2      4194kB  537MB   533MB   fat32        primary  msftdata
 3      563MB   4001GB  4000GB               primary
```

I then copied the partition table to the second drive

```
# sfdisk -d /dev/sdg | sfdisk /dev/sdf
```

Next I created a PV on each drive

```
#lvm pvcreate /dev/sdg3
#lvm pvcreate /dev/sdf3
```

Then I created a Volume Group

```
#vgcreate raid1vg /dev/sdg3 /dev/sdf3
```

Finally I created the Logical Volumes. I'm only showing the final one as it's the only one I'm using at present.

```
# lvcreate --mirrors 1 --type raid1 -l 100%FREE --nosync -n home raid1vg

```
The other LVs were first created with the same command except for the size command option set  -L xxG

The final step was to create an ext4 file system on the LV

```
#mkfs.ext4 /dev/raid1vg/home
```


**MAFoElffen**

My md arrays look like what you list above here is lsblk one drive for one RAID1 array

```
                         8:64   0 931.5G  0 disk
&#9492;&#9472;sde1                      8:65   0 931.5G  0 part
  &#9492;&#9472;md126                   9:126  0 931.4G  0 raid1
    &#9500;&#9472;system-root         253:5    0    50G  0 lvm   /
    &#9500;&#9472;system-tmp          253:6    0    10G  0 lvm   /tmp
    &#9500;&#9472;system-var          253:7    0    10G  0 lvm   /var
    &#9500;&#9472;system-swap         253:8    0    16G  0 lvm   [SWAP]
    &#9500;&#9472;system-www          253:9    0    10G  0 lvm   /var/www
    &#9500;&#9472;system-home         253:10   0   500G  0 lvm   /mnt2
    &#9492;&#9472;system-xtra         253:11   0 335.4G  0 lvm   /var/mail
```

The lvm arrays don't look the same. Here is lsblk one drive:

```
sdg                         8:96   0   3.7T  0 disk
&#9500;&#9472;sdg1                      8:97   0     4M  0 part
&#9500;&#9472;sdg2                      8:98   0   508M  0 part
&#9492;&#9472;sdg3                      8:99   0   3.7T  0 part
  &#9500;&#9472;raid1vg-root_rmeta_1  253:14   0     4M  0 lvm
  &#9474; &#9492;&#9472;raid1vg-root        253:16   0    50G  0 lvm
  &#9500;&#9472;raid1vg-root_rimage_1 253:15   0    50G  0 lvm
  &#9474; &#9492;&#9472;raid1vg-root        253:16   0    50G  0 lvm
  &#9500;&#9472;raid1vg-tmp_rmeta_1   253:19   0     4M  0 lvm
  &#9474; &#9492;&#9472;raid1vg-tmp         253:21   0    10G  0 lvm
  &#9500;&#9472;raid1vg-tmp_rimage_1  253:20   0    10G  0 lvm
  &#9474; &#9492;&#9472;raid1vg-tmp         253:21   0    10G  0 lvm
  &#9500;&#9472;raid1vg-var_rmeta_1   253:24   0     4M  0 lvm
  &#9474; &#9492;&#9472;raid1vg-var         253:26   0    10G  0 lvm
  &#9500;&#9472;raid1vg-var_rimage_1  253:25   0    10G  0 lvm
  &#9474; &#9492;&#9472;raid1vg-var         253:26   0    10G  0 lvm
  &#9500;&#9472;raid1vg-swap_rmeta_1  253:29   0     4M  0 lvm
  &#9474; &#9492;&#9472;raid1vg-swap        253:31   0    16G  0 lvm
  &#9500;&#9472;raid1vg-swap_rimage_1 253:30   0    16G  0 lvm
  &#9474; &#9492;&#9472;raid1vg-swap        253:31   0    16G  0 lvm
  &#9500;&#9472;raid1vg-www_rmeta_1   253:34   0     4M  0 lvm
  &#9474; &#9492;&#9472;raid1vg-www         253:36   0    10G  0 lvm
  &#9500;&#9472;raid1vg-www_rimage_1  253:35   0    10G  0 lvm
  &#9474; &#9492;&#9472;raid1vg-www         253:36   0    10G  0 lvm
  &#9500;&#9472;raid1vg-home_rmeta_1  253:39   0     4M  0 lvm
  &#9474; &#9492;&#9472;raid1vg-home        253:41   0   3.6T  0 lvm   /mnt
  &#9492;&#9472;raid1vg-home_rimage_1 253:40   0   3.6T  0 lvm
    &#9492;&#9472;raid1vg-home        253:41   0   3.6T  0 lvm   /mnt
```

---

### Post by TheFu on 2022-02-17
I need some time to look up stuff. Nothing jumps out with the creation, but the use of all the storage for the last LV is worrying. No unused VG space for lvm snapshots or to expand other LVs?

For lsblk, this alias is very helpful:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

Which OS is this on? I'd like to try and recreate it. 20.04 or 21.10?

---

### Post by rsteinmetz70112 on 2022-02-17
It is on 20.04 
```
# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:        20.04
Codename:       focal
```

```
# lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                        SIZE TYPE  FSTYPE            MOUNTPOINT

sdg                         3.7T disk
&#9500;&#9472;sdg1                        4M part  vfat
&#9500;&#9472;sdg2                      508M part  vfat
&#9492;&#9472;sdg3                      3.7T part  LVM2_member
  &#9500;&#9472;raid1vg-root_rmeta_1      4M lvm
  &#9474; &#9492;&#9472;raid1vg-root           50G lvm   ext4
  &#9500;&#9472;raid1vg-root_rimage_1    50G lvm
  &#9474; &#9492;&#9472;raid1vg-root           50G lvm   ext4
  &#9500;&#9472;raid1vg-tmp_rmeta_1       4M lvm
  &#9474; &#9492;&#9472;raid1vg-tmp            10G lvm   ext4
  &#9500;&#9472;raid1vg-tmp_rimage_1     10G lvm
  &#9474; &#9492;&#9472;raid1vg-tmp            10G lvm   ext4
  &#9500;&#9472;raid1vg-var_rmeta_1       4M lvm
  &#9474; &#9492;&#9472;raid1vg-var            10G lvm   ext4
  &#9500;&#9472;raid1vg-var_rimage_1     10G lvm
  &#9474; &#9492;&#9472;raid1vg-var            10G lvm   ext4
  &#9500;&#9472;raid1vg-swap_rmeta_1      4M lvm
  &#9474; &#9492;&#9472;raid1vg-swap           16G lvm
  &#9500;&#9472;raid1vg-swap_rimage_1    16G lvm
  &#9474; &#9492;&#9472;raid1vg-swap           16G lvm
  &#9500;&#9472;raid1vg-www_rmeta_1       4M lvm
  &#9474; &#9492;&#9472;raid1vg-www            10G lvm   ext4
  &#9500;&#9472;raid1vg-www_rimage_1     10G lvm
  &#9474; &#9492;&#9472;raid1vg-www            10G lvm   ext4
  &#9500;&#9472;raid1vg-home_rmeta_1      4M lvm
  &#9474; &#9492;&#9472;raid1vg-home          3.6T lvm   ext4              /mnt
  &#9492;&#9472;raid1vg-home_rimage_1   3.6T lvm
    &#9492;&#9472;raid1vg-home          3.6T lvm   ext4              /mnt

```


The mount point is temporary, when I go live I'll move it and edit /etc/fstab
Effectively everything before the last one is spare at this point.  If I need to I can remove any of those LVs to create space if necessary.
Also there is a bunch of free space on home I could shrink it, but I'm not sure what that will get me.
```

# df -h
/dev/mapper/raid1vg-home  3.5T  447G  2.9T  14% /mnt
```

---

### Post by rsteinmetz70112 on 2022-02-17
OK I've discovered a new issue. Apparently lvm2 isn't starting during boot. The new LVs aren't available to mount from fstab. Oddly it is activation mdadm and the vgs on the existing arrays.

---

### Post by TheFu on 2022-02-20
So, I'm going to try setting up a new 20.04 server system today with LVM in RAID1. No mdadm.  

My plan is to do a normal install with 1 disk using defaults for LVM.  Then I'll add another device and tell LVM to mirror everything that's under LVM control to the other disk.  I think this will be the more typical method of an installation.  

Cross your fingers.

---

### Post by #&amp;thj^% on 2022-02-20
I usually just follow this for the most part instructions found:

[https://askubuntu.com/questions/1299978/install-ubuntu-20-04-desktop-with-raid-1-and-lvm-on-machine-with-uefi-bios](https://askubuntu.com/questions/1299978/install-ubuntu-20-04-desktop-with-raid-1-and-lvm-on-machine-with-uefi-bios)

my old log shows:
```
lsblk
NAME               MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
...
sda                  8:0    0  1000G  0 disk  
&#9500;&#9472;sda1               8:1    0   512M  0 part  
&#9492;&#9472;sda2               8:2    0 999.5G  0 part  
  &#9492;&#9472;md0              9:0    0 999.4G  0 raid1 
    &#9492;&#9472;md0p1        259:0    0 999.4G  0 part  
      &#9500;&#9472;vg0-root   253:0    0    25G  0 lvm   /target
      &#9500;&#9472;vg0-tmp    253:1    0    10G  0 lvm   
      &#9500;&#9472;vg0-var    253:2    0     5G  0 lvm   
      &#9500;&#9472;vg0-varlib 253:3    0    10G  0 lvm   
      &#9492;&#9472;vg0-home   253:4    0   200G  0 lvm   
sdb                  8:16   0  1000G  0 disk  
&#9500;&#9472;sdb1               8:17   0   512M  0 part  
&#9492;&#9472;sdb2               8:18   0 999.5G  0 part  
  &#9492;&#9472;md0              9:0    0 999.4G  0 raid1 
    &#9492;&#9472;md0p1        259:0    0 999.4G  0 part  
      &#9500;&#9472;vg0-root   253:0    0    25G  0 lvm   /target
      &#9500;&#9472;vg0-tmp    253:1    0    10G  0 lvm   
      &#9500;&#9472;vg0-var    253:2    0     5G  0 lvm   
      &#9500;&#9472;vg0-varlib 253:3    0    10G  0 lvm   
      &#9492;&#9472;vg0-home   253:4    0   200G  0 lvm   
...

```
As you can see, the installer left the installed system root mounted to /target. However, the other partitions are not mounted. More importantly, mdadm is not yet part of the installed system.
There was additional info for mdadm included
Hope this helps. @ TheFu would love to hear your input on this method.

---

### Post by TheFu on 2022-02-20
Ok, that was fun. I didn't have the boot issues. At install time, I chose BIOS boot, not UEFI. Could that be it?

I am seeing the same junk (rmeta/rimage). The lvmraid manpage has an explanation about using mdadm code between the LVM container and LVs.  The rimage is actually the data with the next level up where the file system sits.
```
$ df -Th -x tmpfs -x squashfs -x devtmpfs
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-ubuntu--lv ext4  8.9G  2.4G  6.1G  28% /
/dev/vda2                         ext4  526M  120M  368M  25% /boot

$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                                SIZE TYPE FSTYPE      MOUNTPOINT
sr0                                1024M rom              
vda                                  10G disk             
&#9500;&#9472;vda1                                1M part             
&#9500;&#9472;vda2                              550M part ext4        /boot
&#9492;&#9472;vda3                              9.1G part LVM2_member 
  &#9500;&#9472;ubuntu--vg-ubuntu--lv_rmeta_0     4M lvm              
  &#9474; &#9492;&#9472;ubuntu--vg-ubuntu--lv         9.1G lvm  ext4        /
  &#9492;&#9472;ubuntu--vg-ubuntu--lv_rimage_0  9.1G lvm              
    &#9492;&#9472;ubuntu--vg-ubuntu--lv         9.1G lvm  ext4        /
vdb                                  10G disk             
&#9500;&#9472;vdb1                                1M part             
&#9500;&#9472;vdb2                              550M part             
&#9492;&#9472;vdb3                              9.1G part LVM2_member 
  &#9500;&#9472;ubuntu--vg-ubuntu--lv_rmeta_1     4M lvm              
  &#9474; &#9492;&#9472;ubuntu--vg-ubuntu--lv         9.1G lvm  ext4        /
  &#9492;&#9472;ubuntu--vg-ubuntu--lv_rimage_1  9.1G lvm              
    &#9492;&#9472;ubuntu--vg-ubuntu--lv         9.1G lvm  ext4        /
```

Happy to share the steps. I tried to do it in the fewest commands.
[LIST=1]
[*]Copied the partition layout using  ```
$ sudo sgdisk -R /dev/vdb /dev/vda
```
[*]Then forced a unique GUID using ```
$ sudo gdisk -G /dev/vdb
```
[*]Add the 3rd partition to the VG. The pvcreate will happen automatically. ```
$ sudo vgextend ubuntu-vg /dev/vdb3
```
[*]Reduce the LV 4MB so there's room for metadata. Reduce the file system concurrently. ```
$ sudo lvreduce -r -L -4m  /dev/ubuntu-vg/ubuntu-lv
``` This step requires booting from alternate media.
[*]Finally use lvchange to modify an existing LV to be a raid1 LV. ```
$ sudo lvconvert --type raid1 -m 1 /dev/ubuntu-vg/ubuntu-lv
```
[/LIST]

Here's the result:
```
$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/ubuntu-lv
  LV Name                ubuntu-lv
  VG Name                ubuntu-vg
  LV UUID                hULLUt-4lkI-PM8Q-BrYm-HycF-78AL-djPXFo
  LV Write Access        read/write
  LV Creation host, time ubuntu-server, 2022-02-20 17:21:27 +0000
  LV Status              available
  # open                 1
  LV Size                <9.11 GiB
  Current LE             2331
  [B]Mirrored volumes       2
[/B]  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
```

```
$ blkid 
/dev/vda2: UUID="ee3f19e0-658e-493a-980f-fc29168f1e3a" TYPE="ext4" PARTUUID="18d2cd7b-c7b1-423a-9336-cee6597f1ddf"
/dev/vda3: UUID="PLgswd-faNc-rdjO-r9g8-3mW0-vBl5-GoeF5b" TYPE="LVM2_member" PARTUUID="1e737c0a-adc7-47f4-8330-aca900d057f4"
/dev/vdb3: UUID="qcIdHc-sU2c-8fsF-qhSC-KOjY-6Qx4-Tp719E" TYPE="LVM2_member" PARTUUID="1e737c0a-adc7-47f4-8330-aca900d057f4"
/dev/mapper/ubuntu--vg-ubuntu--lv: UUID="17224f46-ab63-4ba2-836e-b87e7bafd0c9" TYPE="ext4"

```
Note that the LVs have different UUIDs, but use the same PARTUUID.

I forced a sync-check and monitored the effort:
```
$ sudo lvs -a -o name,raid_sync_action,sync_percent
  LV                   SyncAction Cpy%Sync
  ubuntu-lv            [COLOR="#008000"]check[/COLOR]      [COLOR="#008000"]78.70[/COLOR]   
  [ubuntu-lv_rimage_0]                    
  [ubuntu-lv_rimage_1]                    
  [ubuntu-lv_rmeta_0]                     
  [ubuntu-lv_rmeta_1]   
```     
Took about 40 seconds. The backing devices are NVMe.

```
$ sudo lvs
  LV        VG        Attr       LSize  Pool Origin Data%  Meta%  Move Log **Cpy%Sync** Convert
  ubuntu-lv ubuntu-vg rwi-aor--- <9.11g                                    **100.00**          
```

My implementation is incomplete.  I need to copy everything in /boot (vda2) to vdb2 as part of any new kernel install/update.  But most Live-Boot environments will let us boot with a different root, so this really isn't too important unless in a business and they want to be extremely consistent in how they setup things.  When I needed to boot from alternate media to reduce the LV and file system sizes, I just pointed the VM at an ISO on some NFS storage. Worked great with next to zero hassle.  Just be 100% certain that no partition outside a formal RAID1 setup have the same UUID. Unexpected things happen if UUIDs match.

---

### Post by rsteinmetz70112 on 2022-02-20
Thanks to everyone who undertook the challenge.

I'm happy to see, unless I'm missing something, the rmeta and rimage are apparently more or less normal. .
I'd never previously set up a Raid Array without mdadm.
I did not start this for a new installation but rather to add additional storage to an existing installation. 
I've started transferring data to the new array and it seems to be working as expected.

---

