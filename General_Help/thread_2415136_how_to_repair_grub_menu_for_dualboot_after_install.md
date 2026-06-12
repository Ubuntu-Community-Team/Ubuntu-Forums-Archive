---
title: "how to repair grub menu for dualboot after installing windows ?"
date: 2019-03-20
forum: General Help
---

### Post by aramu on 2019-03-20
[SIZE=4]hi..
i ran in dualboot an encrypted ubuntu 16.04lts with a windows 8.1..after reinstalling windows i lost the grub menu..i tried fixing it by running bootrepair using recommended repair button but it didnt work..i think because the partition is encrypted.

from a live cd :

   ```
 ubuntu@ubuntu:~$ sudo fdisk -l
    Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    
    
    Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    
    
    Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    
    
    Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    
    
    Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    
    
    Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    
    
    Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    
    
    Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    
    
    Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    
    
    Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    
    
    Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    
    
    Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    
    
    Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    
    
    Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    
    
    Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    
    
    Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    
    
    Disk /dev/loop0: 1.3 GiB, 1433468928 bytes, 2799744 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    
    
    Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    Disklabel type: dos
    Disk identifier: 0x8448020a
    
    Device     Boot     Start       End   Sectors   Size Id Type
    /dev/sda1  *         2048 567158783 567156736 270.5G  7 HPFS/NTFS/exFAT
    /dev/sda2       567158784 568135679    976896   477M 83 Linux
    /dev/sda3       568137726 764157951 196020226  93.5G  5 Extended
    /dev/sda4       771971445 976768064 204796620  97.7G  7 HPFS/NTFS/exFAT
    /dev/sda5       568137728 764157951 196020224  93.5G 83 Linux
    
    Partition 3 does not start on physical sector boundary.
    Partition 4 does not start on physical sector boundary.
    Partition table entries are not in disk order.
    
    
    
    
    Disk /dev/sdb: 3.8 GiB, 4089970688 bytes, 7988224 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disklabel type: dos
    Disk identifier: 0x00255f71
    
    Device     Boot Start     End Sectors  Size Id Type
    /dev/sdb1  *     2048 7988223 7986176  3.8G  c W95 FAT32 (LBA)
    
    
    Disk /dev/mapper/encrypted-volume: 93.5 GiB, 100360257536 bytes, 196016128 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
```



the sda4:noname3 is a partition without any OS, and 
the sda1 has the windows 8.

    ```
ubuntu@ubuntu:~$ lsblk
    NAME                 MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
    sda                    8:0    0 465.8G  0 disk  
    &#9500;&#9472;sda1                 8:1    0 270.5G  0 part  
    &#9500;&#9472;sda2                 8:2    0   477M  0 part  /mnt
    &#9500;&#9472;sda3                 8:3    0     1K  0 part  
    &#9500;&#9472;sda4                 8:4    0  97.7G  0 part  /media/ubuntu/NoName3
    &#9492;&#9472;sda5                 8:5    0  93.5G  0 part  
      &#9492;&#9472;encrypted-volume 252:0    0  93.5G  0 crypt 
    sdb                    8:16   1   3.8G  0 disk  
    &#9492;&#9472;sdb1                 8:17   1   3.8G  0 part  /cdrom
    sr0                   11:0    1  1024M  0 rom   
    loop0                  7:0    0   1.3G  1 loop  /rofs

```

here are the errors i ran to :

    ```
ubuntu@ubuntu:~$ sudo update-grub
    /usr/sbin/grub-probe: error: failed to get canonical path of `/cow'. 

    ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda5 encrypted-volume
    Enter passphrase for /dev/sda5:
    Cannot use device /dev/sda5 which is in use (already mapped or mounted)

    ubuntu@ubuntu:~$ sudo vgchange -ay
    ubuntu@ubuntu:~$ sudo lvscan
    ubuntu@ubuntu:~$ sudo ls /dev/mapper/
    control  encrypted-volume
    ubuntu@ubuntu:~$ sudo mount /dev/mapper/sda5 /mnt/system/
    mount: special device /dev/mapper/sda5 does not exist
    ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/system/boot/
    mount: mount point /mnt/system/boot/ does not exist

    ubuntu@ubuntu:~$ sudo mount /dev/mapper/sda5 /mnt
    mount: special device /dev/mapper/sda5 does not exist

    ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
    mount: unknown filesystem type 'crypto_LUKS'
```[/SIZE]

[SIZE=4]i got to be honest i am a noob when it comes to linux but i really enjoyed working with ubuntu this past 2 years..i hope someone can help me fix it..thank you in advance.[/SIZE]

---

### Post by oldfred on 2019-03-20
/cow is copy on write or your live installer. You were trying to update the grub on your installer, not your actual install.

If you use Boot-Repair with LVM & encrypted volumes, you need to decrypt the install before hand.

       chroot & troubleshooting Full system encryption
[URL="https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting"]https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting
[https://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i](https://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i)
      [/URL]
 UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380) 
    [URL="https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting"]
[/URL]

---

### Post by aramu on 2019-03-21
[SIZE=3]hi..first thank you for your answer.
i tried all the solutions above but still i always get an error midways..[/SIZE]

```
ubuntu@ubuntu:~$ sudo cryptsetup open --type=luks /dev/sda5 system
Enter passphrase for /dev/sda5: 
ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount /dev/mapper/system-root /mnt/root
mount: special device /dev/mapper/system-root does not exist
ubuntu@ubuntu:~$ sudo mount /dev/mapper/system-boot /mnt/root/boot
mount: mount point /mnt/root/boot does not exist
ubuntu@ubuntu:~$ sudo mount /dev/sda2  /mnt/root/boot/efi
mount: mount point /mnt/root/boot/efi does not exist

```


```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
mount: unknown filesystem type 'crypto_LUKS'
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/boot
mount: mount point /mnt/boot does not exist
ubuntu@ubuntu:~$ sudo mkdir -p /mnt/boot/efi
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/boot/efi
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
mount: mount point /mnt/proc does not exist
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
mount: mount point /mnt/sys does not exist
ubuntu@ubuntu:~$ apt-get install grub-efi-amd64
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```


```
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# apt-get update
Ign:1 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial InRelease
Hit:2 cdrom://Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1) xenial Release
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [109 kB]
Get:5 http://archive.ubuntu.com/ubuntu xenial InRelease [247 kB]         
Get:6 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [626 kB]
Get:7 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]       
Get:8 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages [1,201 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [259 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [67.9 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [67.1 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages [7,204 B]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/restricted Translation-en [2,152 B]
Get:14 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata [200 B]
Get:15 http://archive.ubuntu.com/ubuntu xenial/main Translation-en [568 kB]    
Get:16 http://archive.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata [733 kB]
Get:17 http://archive.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons [409 kB]
Get:18 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [925 kB]
Get:19 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [372 kB]
Get:20 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [318 kB]
Get:21 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [227 kB]
Get:22 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages [7,616 B]
Get:23 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en [2,272 B]
Get:24 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 DEP-11 Metadata [157 B]
Fetched 6,258 kB in 15s (399 kB/s)                                             

** (appstreamcli:3318): CRITICAL **: Error while moving old database out of the way.
AppStream cache update failed.
Reading package lists... Done
root@ubuntu:~# apt-get install cryptsetup lvm2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lvm2 is already the newest version (2.02.133-1ubuntu10).
The following packages will be upgraded:
  cryptsetup
1 upgraded, 0 newly installed, 0 to remove and 857 not upgraded.
Need to get 123 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 cryptsetup amd64 2:1.6.6-5ubuntu2.1 [123 kB]
Fetched 123 kB in 1s (76.7 kB/s)                     
Preconfiguring packages ...
(Reading database ... 191101 files and directories currently installed.)
Preparing to unpack .../cryptsetup_2%3a1.6.6-5ubuntu2.1_amd64.deb ...
Unpacking cryptsetup (2:1.6.6-5ubuntu2.1) over (2:1.6.6-5ubuntu2) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (229-4ubuntu4) ...
Setting up cryptsetup (2:1.6.6-5ubuntu2.1) ...
update-initramfs is disabled since running on read-only media
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Service checkroot has to be enabled to start service cryptdisks-early
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package cryptsetup (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:~# fdisk -l
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.3 GiB, 1433468928 bytes, 2799744 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x8448020a

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 567158783 567156736 270.5G  7 HPFS/NTFS/exFAT
/dev/sda2       567158784 568135679    976896   477M 83 Linux
/dev/sda3       568137726 764157951 196020226  93.5G  5 Extended
/dev/sda4       771971445 976768064 204796620  97.7G  7 HPFS/NTFS/exFAT
/dev/sda5       568137728 764157951 196020224  93.5G 83 Linux

Partition 3 does not start on physical sector boundary.
Partition 4 does not start on physical sector boundary.
Partition table entries are not in disk order.




Disk /dev/sdb: 3.8 GiB, 4089970688 bytes, 7988224 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00255f71

Device     Boot Start     End Sectors  Size Id Type
/dev/sdb1  *     2048 7988223 7986176  3.8G  c W95 FAT32 (LBA)


Disk /dev/mapper/system: 93.5 GiB, 100360257536 bytes, 196016128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
root@ubuntu:~# cryptsetup luksOpen /dev/sda5 TAG
Enter passphrase for /dev/sda5: 
Cannot use device /dev/sda5 which is in use (already mapped or mounted).
root@ubuntu:~# vgchange -ay
root@ubuntu:~# vgscan
  Reading all physical volumes.  This may take a while...
root@ubuntu:~# vgchange -ay
root@ubuntu:~# lvscan
root@ubuntu:~# 
```

---

### Post by oldfred on 2019-03-21
Are you using the correct names.

Per link to see your volumes:

sudo -i
apt-get update
apt-get install cryptsetup lvm2
fdisk -l
cryptsetup luksOpen /dev/sda? TAG #sda? is your root partition
vgchange -ay
vgscan
vgchange -ay [VOLUME GROUP NAME]
lvscan
/dev/[VOLUME GROUP NAME]/[LOGICAL VOLUME NAME] /mnt

---

