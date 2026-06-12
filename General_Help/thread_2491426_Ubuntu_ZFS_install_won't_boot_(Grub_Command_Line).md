---
title: "Ubuntu ZFS install won't boot (Grub Command Line)"
date: 2023-10-08
forum: General Help
---

### Post by david-reinhardt on 2023-10-08
Hello friends,

all of a sudden my ubuntu 22.04 LTS ZFS install doesn't boot anymore. It goes straight into Grub command line mode. I tried following tutorials but I think because I have an encrypted ZFS they don't work. Here is a boot info from Boot-Repair. Could you please help me out?

```
boot-repair-4ppa2056                                              [20231008_1132]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grub/grub.cfg /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

nvme0n1p2: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 

nvme0n1p3: _____________________________________________________________________

    File system:       zfs_member
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

nvme0n1p4: _____________________________________________________________________

    File system:       zfs_member
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sda: /dev/sda already mounted or mount point busy.


================================ 0 OS detected =================================


================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: Renoir from Advanced Micro Devices, Inc. [AMD/ATI]
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.3 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: S77 Ver. 01.02.02(2.2) from HP
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0005,0002,0004,0000
Boot0000  Network Boot:IPV4      PciRoot(0x0)/Pci(0x1,0x3)/Pci(0x0,0x0)/IPv4(0.0.0.00.0.0.0,0,0)N.....YM....R,Y..(..ISPH
Boot0002* JetFlash Mass Storage Device 1282477908    PciRoot(0x0)/Pci(0x8,0x1)/Pci(0x0,0x4)/USB(5,0)N.....YM....R,Y.....ISPH
Boot0003  Network Boot:IPV4      PciRoot(0x0)/Pci(0x8,0x1)/Pci(0x0,0x3)/USB(4,0)/MAC(3c18a07e7aaa,0)/IPv4(0.0.0.00.0.0.0,0,0)N.....YM....R,Y.....ISPH
Boot0004  Network Boot:IPV6      PciRoot(0x0)/Pci(0x8,0x1)/Pci(0x0,0x3)/USB(4,0)/MAC(3c18a07e7aaa,0)/IPv6([::]:<->[::]:,0,0)N.....YM....R,Y..0..ISPH
Boot0005* ubuntu    HD(1,GPT,02e5d4f5-b84e-477a-ad62-951397b93066,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)....ISPH

a9c517741ac31962d7feb152948ad1ee   nvme0n1p1/BOOT/fbx64.efi
a660182adef313615746a665966d2ccc   nvme0n1p1/BOOT/mmx64.efi
5ddf997e8b025bfbc2009e85b32f60dc   nvme0n1p1/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   nvme0n1p1/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   nvme0n1p1/ubuntu/shimx64.efi
64349b3622c65f495a99dbf6102496e3   nvme0n1p1/BOOT/BOOTX64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    grubenv-ok,    noupdategrub,    not-far
nvme0n1p3    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p3    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p3    : is--zfs-boot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p4    : maybesepboot,    with-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p2    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: DC84D234-028F-4AE0-9C1A-4EA281BFC6F0
            Start        End    Sectors  Size Type
nvme0n1p1    2048    1050623    1048576  512M EFI System
nvme0n1p2 1050624    5244927    4194304    2G Linux swap
nvme0n1p3 5244928    9439231    4194304    2G Solaris boot
nvme0n1p4 9439232 1953525134 1944085903  927G Solaris root
Disk sda: 29.44 GiB, 31608274944 bytes, 61734912 sectors
Disk identifier: F45E2FA1-C5A6-4D79-876F-C8245AF921E0
        Start      End  Sectors  Size Type
sda1       64  9828451  9828388  4.7G Microsoft basic data
sda2  9828452  9838519    10068  4.9M EFI System
sda3  9838520  9839119      600  300K Microsoft basic data
sda4  9842688 61734848 51892161 24.7G Linux filesystem
Disk zd0: 500 MiB, 524288000 bytes, 1024000 sectors

parted -lm (filtered): _________________________________________________________

sda:31.6GB:scsi:512:512:gpt:JetFlash Transcend 32GB:;
1:32.8kB:5032MB:5032MB::ISO9660:hidden, msftdata;
2:5032MB:5037MB:5155kB::Appended2:boot, esp;
3:5037MB:5038MB:307kB::Gap1:hidden, msftdata;
4:5039MB:31.6GB:26.6GB:ext4::;
nvme0n1:1000GB:nvme:512:512:gpt:KINGSTON SA2000M81000G:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:2685MB:2147MB:::swap;
3:2685MB:4833MB:2147MB:zfs::;
4:4833MB:1000GB:995GB:zfs::;
zd0:524MB:unknown:512:8192:unknown:Unknown:;

blkid (filtered): ______________________________________________________________

NAME        FSTYPE      UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda         iso9660     2023-08-08-01-19-05-00                                                    Ubuntu 22.04.3 LTS amd64 
&#9500;&#9472;sda1      iso9660     2023-08-08-01-19-05-00               f45e2fa1-c5a6-4d79-876e-c8245af921e0 Ubuntu 22.04.3 LTS amd64 ISO9660
&#9500;&#9472;sda2      vfat        F7DB-4D56                            f45e2fa1-c5a6-4d79-876d-c8245af921e0 ESP                      Appended2
&#9500;&#9472;sda3                                                       f45e2fa1-c5a6-4d79-876c-c8245af921e0                          Gap1
&#9492;&#9472;sda4      ext4        67c19720-23bb-40ba-9e8c-5515b1ce3a57 0eeffd4a-98dc-5240-b397-d9f35643b53d writable                 
zd0         crypto_LUKS c8d945b2-bf18-402e-baf7-2d5082db3f41                                                               
nvme0n1                                                                                                                    
&#9500;&#9472;nvme0n1p1 vfat        800D-4749                            02e5d4f5-b84e-477a-ad62-951397b93066                          EFI System Partition
&#9500;&#9472;nvme0n1p2                                                  ee061f36-8884-c648-b69d-de9e629fedf8                          
&#9500;&#9472;nvme0n1p3 zfs_member  10055664188803140528                 b478cca9-c427-b94f-a046-b9ec23251ea1 bpool                    
&#9492;&#9472;nvme0n1p4 zfs_member  5792523734577493029                  24d8727b-f1b9-774f-b926-cb44f9823e49 rpool                    

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
bpool/BOOT/ubuntu_1x5gh3                                       25.4M  92% /mnt/boot-sav/zfs/boot
/dev/disk/by-label/writable[/install-logs-2077-07-10.0/crash]  22.9G   0% /var/crash
/dev/disk/by-label/writable[/install-logs-2077-07-10.0/log]    22.9G   0% /var/log
/dev/nvme0n1p1                                                496.7M   3% /mnt/boot-sav/nvme0n1p1
/dev/sda1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________


====================== nvme0n1p1/grub/grub.cfg (filtered) ======================

Revert system only   gnulinux-${root_dataset}-${kversion}
Revert system and user data   gnulinux-${root_dataset}-${kversion}
Ubuntu 22.04.3 LTS   gnulinux-rpool/ROOT/ubuntu_1x5gh3-6.2.0-33-generic
* Ubuntu 22.04.3 LTS, with Linux 6.2.0-33-generic   gnulinux-rpool/ROOT/ubuntu_1x5gh3-6.2.0-33-generic
Ubuntu 22.04.3 LTS, with Linux 6.2.0-32-generic   gnulinux-rpool/ROOT/ubuntu_1x5gh3-6.2.0-32-generic
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid 800D-4749 root 
set prefix=($root)'/grub'
configfile $prefix/grub.cfg

================= nvme0n1p1: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             grub/grub.cfg                                  1

================= nvme0n1p3: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             vmlinuz
            ?? = ??             vmlinuz-6.2.0-32-generic
            ?? = ??             vmlinuz-6.2.0-33-generic
            ?? = ??             vmlinuz.old
            ?? = ??             initrd.img
            ?? = ??             initrd.img-6.2.0-32-generic
            ?? = ??             initrd.img-6.2.0-33-generic
            ?? = ??             initrd.img.old

================= nvme0n1p4: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/vmlinuz
            ?? = ??             boot/vmlinuz-6.2.0-32-generic
            ?? = ??             boot/vmlinuz-6.2.0-33-generic
            ?? = ??             boot/vmlinuz.old
            ?? = ??             boot/initrd.img
            ?? = ??             boot/initrd.img-6.2.0-32-generic
            ?? = ??             boot/initrd.img-6.2.0-33-generic
            ?? = ??             boot/initrd.img.old

======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown BootLoader on nvme0n1p2




================================ ZFS activation ================================

dpkg-query -W -f=${Version} zfsutils-linux : 2.1.5-1ubuntu6~22.04.1
zpool export -f -a 

zpool import -N -f -R /mnt/boot-sav/zfs rpool 
zpool import -N -f -R /mnt/boot-sav/zfs bpool 
If needed, type 'sudo zfs load-key -a' in another terminal.
zfs mount rpool/ROOT/ubuntu_1x5gh3 
zfs mount -a 
Error: could not activate ZFS. Please report this message to boot.repair@gmail.com
zpool list after activation
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool  1.88G  1.73G   153M        -         -    60%    92%  1.00x    ONLINE  /mnt/boot-sav/zfs
rpool   920G   652G   268G        -         -    26%    70%  1.00x    ONLINE  /mnt/boot-sav/zfs

zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                             1.72G  25.4M       96K  /mnt/boot-sav/zfs/boot
bpool/BOOT                                        1.72G  25.4M       96K  none
bpool/BOOT/ubuntu_1x5gh3                          1.72G  25.4M      304M  /mnt/boot-sav/zfs/boot
rpool                                              652G   239G      192K  /mnt/boot-sav/zfs
rpool/ROOT                                        57.3G   239G      192K  none
rpool/ROOT/ubuntu_1x5gh3                          57.3G   239G     9.83G  /mnt/boot-sav/zfs
rpool/ROOT/ubuntu_1x5gh3/srv                       432K   239G      192K  /mnt/boot-sav/zfs/srv
rpool/ROOT/ubuntu_1x5gh3/usr                       591M   239G      192K  /mnt/boot-sav/zfs/usr
rpool/ROOT/ubuntu_1x5gh3/usr/local                 591M   239G      570M  /mnt/boot-sav/zfs/usr/local
rpool/ROOT/ubuntu_1x5gh3/var                      27.3G   239G      192K  /mnt/boot-sav/zfs/var
rpool/ROOT/ubuntu_1x5gh3/var/games                 272K   239G      192K  /mnt/boot-sav/zfs/var/games
rpool/ROOT/ubuntu_1x5gh3/var/lib                  26.4G   239G     9.44G  /mnt/boot-sav/zfs/var/lib
rpool/ROOT/ubuntu_1x5gh3/var/lib/AccountsService  1.41M   239G      216K  /mnt/boot-sav/zfs/var/lib/AccountsService
rpool/ROOT/ubuntu_1x5gh3/var/lib/NetworkManager   12.7M   239G      948K  /mnt/boot-sav/zfs/var/lib/NetworkManager
rpool/ROOT/ubuntu_1x5gh3/var/lib/apt               337M   239G      111M  /mnt/boot-sav/zfs/var/lib/apt
rpool/ROOT/ubuntu_1x5gh3/var/lib/dpkg              957M   239G      137M  /mnt/boot-sav/zfs/var/lib/dpkg
rpool/ROOT/ubuntu_1x5gh3/var/log                   830M   239G      236M  /mnt/boot-sav/zfs/var/log
rpool/ROOT/ubuntu_1x5gh3/var/mail                  272K   239G      192K  /mnt/boot-sav/zfs/var/mail
rpool/ROOT/ubuntu_1x5gh3/var/snap                 47.8M   239G     9.11M  /mnt/boot-sav/zfs/var/snap
rpool/ROOT/ubuntu_1x5gh3/var/spool                2.84M   239G      352K  /mnt/boot-sav/zfs/var/spool
rpool/ROOT/ubuntu_1x5gh3/var/www                   272K   239G      192K  /mnt/boot-sav/zfs/var/www
rpool/USERDATA                                     594G   239G      192K  /mnt/boot-sav/zfs
rpool/USERDATA/mrtickle_j15ygf                     594G   239G      486G  /mnt/boot-sav/zfs/home/mrtickle
rpool/USERDATA/root_j15ygf                        73.8M   239G     69.8M  /mnt/boot-sav/zfs/root
rpool/keystore                                     518M   240G     48.1M  -

=================== findmnt (filtered) after ZFS activation ====================

SOURCE                                                        FSTYPE        SIZE   USED AVAIL USE% TARGET
/dev/sda1                                                     iso9660       4.7G   4.7G     0 100% /cdrom
/dev/disk/by-label/writable[/install-logs-2077-07-10.0/log]   ext4         24.2G     5M 22.9G   0% /var/log
/dev/disk/by-label/writable[/install-logs-2077-07-10.0/crash] ext4         24.2G     5M 22.9G   0% /var/crash
bpool/BOOT/ubuntu_1x5gh3                                      zfs         329.6M 304.4M 25.3M  92% /mnt/boot-sav/zfs/boot




Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.

Confirmation request before suggested repair: __________________________________

Warning: ZFS not activated correctly. Repair will fail unless you mount the pools on /mnt/boot-sav/zfs before continuing. Please report this message to boot.repair@gmail.com
Are you sure you want to continue anyway?
```

---

### Post by #&amp;thj^% on 2023-10-08
here is a possible reason:
```
bpool/BOOT/ubuntu_1x5gh3                                       25.4M  92% /mnt/boot-sav/zfs/boot
```
No head room
and this:
```
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool  1.88G  1.73G   153M        -         -    60%    92%  1.00x    ONLINE  /mnt/boot-sav/zfs
```
I'm not sure it was all of the sudden though, 
> Warning: ZFS not activated correctly. Repair will fail unless you mount the pools on /mnt/boot-sav/zfs before continuing.
This looks like a Live installer will be needed to fix.

---

### Post by david-reinhardt on 2023-10-08
Thx for the reply. What to i need to do specifically to fix this? I already booted into a live system but I don't know what steps to take.

---

### Post by MAFoElffen on 2023-10-08
The boot-info script asks for intervention to unlock the pools in terminal by the user... so it can see what is going on inside the encrypted pools...

No matters. 

+1 on 1fallen's good eyes = bpool is full. 

To mount and chroot into the system to repair this, I had revised my instructions for rescuing ZFS systems, and ZFS encrypted systems. Do this:
```

sudo su -

zpool export -a
zpool import -N -R /mnt rpool
zpool import -N -R /mnt bpool

cryptsetup open /dev/zvol/rpool/keystore zfskey
# Enter passphrase for /dev/zvol/rpool/keystore: 


lsblk -e7 -o name,label,size,fstype
NAME     LABEL                   SIZE FSTYPE
sr0      Ubuntu 22.04 LTS amd64  3.4G iso9660
zd0                              500M crypto_LUKS
&#9492;&#9472;zfskey keystore-rpool          484M ext4
vda                               30G 
&#9500;&#9472;vda1                           512M vfat
&#9500;&#9472;vda2                           1.4G crypto_LUKS
&#9500;&#9472;vda3   bpool                   1.5G zfs_member
&#9492;&#9472;vda4   rpool                  26.7G zfs_member


ls /dev/mapper
# control  zfskey

mount /dev/mapper/zfskey /media
ls /media
# lost+found  system.key

cat /media/system.key | zfs load-key -L prompt rpool
# <No ouput indicates that it unlocked without an error>


zfs mount $(zfs list | awk '/rpool\/ROOT\/ubuntu_...... / {print $1}' )
zfs mount $(zfs list | awk '/bpool\/BOOT\/ubuntu_...... / {print $1}' )
zfs mount -a


zfs list
#NAME                                               USED  AVAIL     REFER  MOUNTPOINT
#bpool                                              270M  1010M       96K  /mnt/boot
#bpool/BOOT                                         269M  1010M       96K  none
#bpool/BOOT/ubuntu_5ylu87                           269M  1010M      269M  /mnt/boot
#rpool                                             9.65G  16.0G      192K  /mnt
#rpool/ROOT                                        9.00G  16.0G      192K  none
#rpool/ROOT/ubuntu_5ylu87                          9.00G  16.0G     5.35G  /mnt
#rpool/ROOT/ubuntu_5ylu87/srv                       192K  16.0G      192K  /mnt/srv
#rpool/ROOT/ubuntu_5ylu87/usr                       580K  16.0G      192K  /mnt/usr
#rpool/ROOT/ubuntu_5ylu87/usr/local                 388K  16.0G      388K  /mnt/usr/local
#rpool/ROOT/ubuntu_5ylu87/var                      3.65G  16.0G      192K  /mnt/var
#rpool/ROOT/ubuntu_5ylu87/var/games                 192K  16.0G      192K  /mnt/var/games
#rpool/ROOT/ubuntu_5ylu87/var/lib                  3.64G  16.0G     3.48G  /mnt/var/lib
#rpool/ROOT/ubuntu_5ylu87/var/lib/AccountsService   212K  16.0G      212K  /mnt/var/lib/#AccountsService
#rpool/ROOT/ubuntu_5ylu87/var/lib/NetworkManager    260K  16.0G      260K  /mnt/var/lib/NetworkManager
#rpool/ROOT/ubuntu_5ylu87/var/lib/apt              98.2M  16.0G     98.2M  /mnt/var/lib/apt
#rpool/ROOT/ubuntu_5ylu87/var/lib/dpkg             61.3M  16.0G     61.3M  /mnt/var/lib/dpkg
#rpool/ROOT/ubuntu_5ylu87/var/log                  10.4M  16.0G     10.4M  /mnt/var/log
#rpool/ROOT/ubuntu_5ylu87/var/mail                  192K  16.0G      192K  /mnt/var/mail
#rpool/ROOT/ubuntu_5ylu87/var/snap                 2.64M  16.0G     2.64M  /mnt/var/snap
#rpool/ROOT/ubuntu_5ylu87/var/spool                 276K  16.0G      276K  /mnt/var/spool
#rpool/ROOT/ubuntu_5ylu87/var/www                   192K  16.0G      192K  /mnt/var/www
#rpool/USERDATA                                     142M  16.0G      192K  /mnt
#rpool/USERDATA/mikeferreira_hsfoy4                 142M  16.0G      142M  /mnt/home/mikeferreira
#rpool/USERDATA/root_hsfoy4                         360K  16.0G      360K  /mnt/root
#rpool/keystore                                     518M  16.5G     63.4M  -

mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run

cd /mnt
chroot /mnt /bin/bash --login
mount -a

```
From there 1fallen can talk you through making room in your bpool...

---

### Post by david-reinhardt on 2023-10-08
Wow, your commands worked perfectly. I chrooted into the system successfully.
My "/boot" looks like this. Can I simply delete an old kernel file? If yes, after having more space again, will the system boot normally again?
How do I "un-chroot" everything?

Thank you guys so much.

```
root@ubuntu:/boot# ls -lah
total 305M
drwxr-xr-x  4 root root   19 Sep 29 09:31 .
drwxr-xr-x 19 root root   25 Sep 15 00:53 ..
-rw-r--r--  1 root root 270K Aug 18 11:38 config-6.2.0-32-generic
-rw-r--r--  1 root root 270K Sep  7 09:11 config-6.2.0-33-generic
drwxr-xr-x  4 root root 4.0K Jan  1  1970 efi
drwxr-xr-x  5 root root 4.0K Jul  6  2077 grub
lrwxrwxrwx  1 root root   27 Sep 29 09:31 initrd.img -> initrd.img-6.2.0-33-generic
-rw-r--r--  1 root root 137M Sep  5 08:22 initrd.img-6.2.0-32-generic
-rw-r--r--  1 root root 137M Sep 29 09:31 initrd.img-6.2.0-33-generic
lrwxrwxrwx  1 root root   27 Sep 24 16:20 initrd.img.old -> initrd.img-6.2.0-32-generic
-rw-r--r--  1 root root 179K Feb  6  2022 memtest86+.bin
-rw-r--r--  1 root root 181K Feb  6  2022 memtest86+.elf
-rw-r--r--  1 root root 181K Feb  6  2022 memtest86+_multiboot.bin
-rw-------  1 root root 7.6M Aug 18 11:38 System.map-6.2.0-32-generic
-rw-------  1 root root 7.7M Sep  7 09:11 System.map-6.2.0-33-generic
lrwxrwxrwx  1 root root   24 Sep 24 16:20 vmlinuz -> vmlinuz-6.2.0-33-generic
-rw-------  1 root root  14M Aug 18 11:40 vmlinuz-6.2.0-32-generic
-rw-------  1 root root  14M Sep  7 10:18 vmlinuz-6.2.0-33-generic
lrwxrwxrwx  1 root root   24 Sep 24 16:20 vmlinuz.old -> vmlinuz-6.2.0-32-generic
```

EDIT:
Should I remove some snapshots?

```
root@ubuntu:/boot# zfs list -t snap -r -o name,used,refer,creation bpool
NAME                                       USED     REFER  CREATION
bpool/BOOT/ubuntu_1x5gh3@autozsys_h7oeuy    72K      439M  Thu Apr 27 19:17 2023
bpool/BOOT/ubuntu_1x5gh3@autozsys_2h4n1n    72K      439M  Sat Apr 29 11:09 2023
bpool/BOOT/ubuntu_1x5gh3@autozsys_n3hvgh     0B      439M  Sat Apr 29 23:26 2023
bpool/BOOT/ubuntu_1x5gh3@autozsys_tq0r74     0B      439M  Sat Apr 29 23:26 2023
bpool/BOOT/ubuntu_1x5gh3@autozsys_kl9nau    80K      439M  Fri May  5 13:44 2023
bpool/BOOT/ubuntu_1x5gh3@autozsys_iasblp     0B      439M  Sun May  7 21:10 2023
bpool/BOOT/ubuntu_1x5gh3@autozsys_hmmg66     0B      439M  Sun May  7 21:10 2023
bpool/BOOT/ubuntu_1x5gh3@autozsys_bq8aq7    72K      439M  Wed May 10 18:17 2023
bpool/BOOT/ubuntu_1x5gh3@autozsys_65hthm    72K      439M  Fri May 12 19:09 2023
bpool/BOOT/ubuntu_1x5gh3@autozsys_whhz4f    80K      439M  Sat May 13 20:45 2023
bpool/BOOT/ubuntu_1x5gh3@autozsys_zjanwo     0B      439M  Tue May 16 18:13 2023
bpool/BOOT/ubuntu_1x5gh3@autozsys_5wwrat     0B      439M  Tue May 16 18:13 2023
bpool/BOOT/ubuntu_1x5gh3@autozsys_ypjp3x   279M      309M  Sat Aug 12 20:00 2023
bpool/BOOT/ubuntu_1x5gh3@autozsys_y3zn0c   143M      309M  Mon Aug 14 18:10 2023
bpool/BOOT/ubuntu_1x5gh3@autozsys_mqrxq5    56K      309M  Mon Aug 14 22:11 2023
bpool/BOOT/ubuntu_1x5gh3@autozsys_xxcnxq    56K      309M  Wed Aug 16 17:08 2023
bpool/BOOT/ubuntu_1x5gh3@autozsys_cnxqbz     0B      309M  Wed Aug 16 20:38 2023
bpool/BOOT/ubuntu_1x5gh3@autozsys_70u26b     0B      309M  Wed Aug 16 20:38 2023
bpool/BOOT/ubuntu_1x5gh3@autozsys_57ev3g    64K      309M  Mon Aug 21 13:28 2023
```

---

### Post by david-reinhardt on 2023-10-08
SOLVED!

- I removed some snapshots on bpool
- I ran "apt dist-upgrade"
- I ran "grub-install --bootloader-id ubuntu /dev/nvme..." (on the EFI partition)

After that I was able to boot normally into the system.

Thank you so much for your help guys! You rock!

---

### Post by MAFoElffen on 2023-10-08
I asked you to wait for 1fallen's instructions. His thread, and I don't want to barge in (proper etiquette)...

While chrooted into the system, you can make changes to fix your install...

You do not have extra kernels. It looks like you originally installed you system from 20.04 LTS, where it installed zsys to do snapshot backups during any update and it has filled your bpool. I've posted previously on fixes for that an a script to maintain that... I haven't updated that script in a while (I really need to.)

You can use the commands from the script to get an idea of how to remove the snapshots... Before you do anything, let me explain (after posting the code of that old script) what also needs to be done, that explains why that script needs to be updated...
```

#!/bin/bash
# MAFoElffen, <mafoelffen@ubuntu.com>, 2021.12.28, last modified: 2022.02.23
# Purpose: ZFS Snapshots bpool maintenance

function ZfsShowFreeSpace ()
{
    zfs list -o space
    zpool list
}

function ZfsListBpool() {
   zfs list -r -t snapshot -o name,used,referenced,creation bpool/BOOT | less
}

function GetZfsBpoolSnapshotCount()
{
    ZfsSnapshotCount=$(zfs list -r -t snapshot -o name,used,referenced,creation bpool/BOOT | wc -l)
    line_count="$(($ZfsSnapshotCount-1))"
    echo -e "There are $line_count snapshots in bpool."
}

function ZSysTrimLast5()
{
    # Command for removing is: zsysctl state remove --system <statename>
    # zfs list -r -t snapshot -o name bpool/BOOT | grep auto-snap | xargs -n 1 sudo zfs destroy
    zfs list -r -t snapshot -o name,used,referenced,creation bpool/BOOT | \
         head -n 5 | \
         cut -c 35-40 | \
         xargs -n 1 zsysctl state remove --system
}

function ZfsTrimLast5()
{
    # Command for removing is: zsysctl state remove --system <statename>
    zfs list -H -o name -t snapshot | head -n 5 | xargs -n1 zfs destroy
}

function ShowMenu() {
    
    while [[ "$menu_response" !=  "5" ]]
    do
        clear
        echo -e "=== ZFS BPool Maintenance ==="
        echo
        echo -e "1 - Show space in Zpools"
        echo -e "2 - Show list of BPool Snapshots."
        echo -e "3 - Show count of BPool Snapshots"
        echo -e "4 - Destroy oldest 5 BPool ZSys SnapShots"
        echo -e "5 - Destroy oldest 5 Bpool SnapShots
        echo -e "5 - Exit"
        echo 
        read -p "Enter a valid menu response from 1 through 5:  " menu_response
        case $menu_response in
            1) ZfsShowFreeSpace;;
            2) ZfsListBpool;;
            3) GetZfsBpoolSnapshotCount;;
            4) ZSysTrimLast5;;
            5} ZfsTrimLast5;;
            6) exit;;
            *) echo -e "The response was not a valid choice.";; 
        esac
        
        echo
        read -p "Press any <Enter> key to continue" trashbin
    done
}

ShowMenu

exit

```
You can see (there) that snapshots are just special "datasets". The format for removing snapshots are 
```

sudo zfs destroy <snapshot_name>

```
We'll use the oldest as an example...
```

bpool/BOOT/[COLOR=#ff0000]ubuntu_1x5gh3@autozsys_h7oeuy[/COLOR]    72K      439M  Thu Apr 27 19:17 2023

```
Indicated in Red is the snapshot in bpool, that you would destroy... My script, as it is now, just removes that snapshot in bpool, using the full path. The problem with that, is if you list the snapshots in rpool, you are most likely going to find a corresponding snapshot in rpool called rpool/ROOT/ubuntu_1x5gh3@autosys_h7oeuy, that could be removed also to roll off that corresponding old snapshot there in rpool. It does no no harm in just removing the snapshot in bpool, and corrects the problem for the user to be able to boot, but can be improved, to sync the maintenance in both pools. Does that make sense to you?

Next, and I've posted about this in various posts here... The underlying problem with zsys needs to be dealt with after you make room... So that it doesn't happen again. Zsys'es default number of snapshots kept before it starts rolling off the old outdated ones is set too high. At first, I was recommending for people to change this to 8. I now recommend that you only need 5. The default is hard coded within Zsys, but can be changed by file /etc/zsys.conf. If it doesn't have that file, just add it.
```

history:
  # Keep at least n history entry per unit of time if enough of them are present
  # The order condition the bucket start and end dates (from most recent to oldest)
  gcstartafter: 1
  [COLOR=#ff0000]keeplast: 5[/COLOR] # Minimum number of recent states to keep. Default was 20.
  #    - name:             Abitrary name of the bucket
  #      buckets:          Number of buckets over the interval
  #      bucketlength:     Length of each bucket in days
  #      samplesperbucket: Number of datasets to keep in each bucket
  gcrules:
    - name: PreviousDay
      buckets: 1
      bucketlength: 1
      samplesperbucket: 3
    - name: PreviousWeek
      buckets: 5
      bucketlength: 1
      samplesperbucket: 1
    - name: PreviousMonth
      buckets: 4
      bucketlength: 7
      samplesperbucket: 1
general:
  # Minimal free space required before taking a snapshot
  minfreepoolspace: 20
  # Daemon timeout in seconds
  timeout: 60

```
After making that change or adding that zsys.conf file, then you restart the daemon to pick up the change.
```

sudo zsysctl service reload

```
Of course, zsys had some plus's, but had been found to have problems and did cause the user some extra work to maintain. 22.04 LTS did not install zsys, nor has it been installed in the canned ZFS installs since, even though I do see some recent maintenance going on with the code at GitHub...

You could always decide to disable the zsys daemon, then uninstall zsys... And then just do manual snapshots and restores of them if needed. 'zsys' just automated what is already there, and additionally add's access to it from the Grub2 menu. There are also some other ways to automate the snapshot maintenance and ZFS boot menu's...

---

### Post by MAFoElffen on 2023-10-08
As a sidenote: Let your computer run overnight on the first and second Saturday/Sunday of the month. There are 2 ZFS zpool maintenance jobs, that are scheduled in cron to run at 1st and 2nd Sunday @ midnight for trim and scrub. If you usually shutdown your computer at night, then they haven't ran, and should be run the commands manually to ensure your pools are maintained.

---

### Post by #&amp;thj^% on 2023-10-08
> **david-reinhardt said:**
> SOLVED!

- I removed some snapshots on bpool
- I ran "apt dist-upgrade"
- I ran "grub-install --bootloader-id ubuntu /dev/nvme..." (on the EFI partition)

After that I was able to boot normally into the system.

Thank you so much for your help guys! You rock!

Good job,  MAFoElffen and I usually double team on zfs problems.
This time of year I have plenty to do before the snow falls.
Thanks  MAFoElffen for your guidance in my absence.

---

