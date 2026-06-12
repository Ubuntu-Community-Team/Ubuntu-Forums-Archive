---
title: "Boot issue and stuck at GRUB."
date: 2022-08-18
forum: General Help
---

### Post by draginbyu on 2022-08-18
After working flawlessly for a week with multiple restarts, my luck ran out and I was prompted with the "GNU Grub v2.06 Minimal BASH like commands...." error and my device now fails to boot into Ubuntu 20.04.

Searching through forums I performed the following with output:

grub>ls
(proc) (hd0) (hd1) (hd2)  (hd2,gpt2) (hd2,gpt1) (hd3) (hd3,gpt1) 

Performing an ls on the individual drives shows no grub files located.

While trying to use boot-repair, I do not even get the "Recommended Repair" option and can only create a pastebin file

[https://pastebin.ubuntu.com/p/7D9tTrjBxX/](https://pastebin.ubuntu.com/p/7D9tTrjBxX/)

Before I completely reinstall ubuntu again, I'd like to see if I can troubleshoot and rescue my current setup.

[B]Output of Pastebin

[/B]```
boot-repair-4ppa200                                              [20220818_1032]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => No boot loader is installed in the MBR of /dev/nvme1n1.
 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.

nvme0n1p1: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

nvme1n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

nvme1n1p2: _____________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32800 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys


================================ 0 OS detected =================================


================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GP104M [GeForce GTX 1080 Mobile] GP104M [GeForce GTX 1080 Mobile] from NVIDIA Corporation NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Boot-Repair-Disk 64bit 20200604, bionic, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: E1816IMS.10F from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled - SecureBoot disabled - Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL].
BootCurrent: 0006
Timeout: 1 seconds
BootOrder: 0005,0006
Boot0005* ubuntu    HD(1,GPT,a40e7b91-948b-4d61-8783-2a7e9ff416dd,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0006* UEFI: SanDisk, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(7,0)/HD(1,MBR,0x7ee6add,0x800,0x1dcf800)..BO

c152ec201c37b6e97bbc2207e49d1271   nvme1n1p1/BOOT/fbx64.efi
fdafb5eece6caeccb788c946a28e6872   nvme1n1p1/BOOT/mmx64.efi
f62c28d9b477b6a1a7b1c991b2b6637d   nvme1n1p1/ubuntu/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   nvme1n1p1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   nvme1n1p1/ubuntu/shimx64.efi
728124f6ec8e22fbdbe7034812c81b95   nvme1n1p1/BOOT/BOOTX64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes
nvme1n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme1n1p1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme1n1p2    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme1n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme1n1p2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme1n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme1n1
nvme1n1p2    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme1n1

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 477 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: EEFD26B2-29C0-45DA-A4BD-25E8E2B26D4F
          Start        End    Sectors  Size Type
nvme0n1p1  2048 1000214527 1000212480  477G Linux filesystem
Disk nvme1n1: 477 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: D6D0D56B-27F0-4FF5-AE6E-564DCB8A50E1
            Start        End   Sectors   Size Type
nvme1n1p1    2048    1050623   1048576   512M EFI System
nvme1n1p2 1050624 1000214527 999163904 476.4G Linux LVM
Disk sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 9801D735-7A20-4A1F-A812-C011EE40B200
Disk sdb: 14.9 GiB, 16005464064 bytes, 31260672 sectors
Disk identifier: 0x07ee6add
      Boot Start      End  Sectors  Size Id Type
sdb1  *     2048 31260671 31258624 14.9G  c W95 FAT32 (LBA)
Disk zram0: 1.3 GiB, 1399300096 bytes, 341626 sectors
Disk zram1: 1.3 GiB, 1399300096 bytes, 341626 sectors
Disk zram2: 1.3 GiB, 1399300096 bytes, 341626 sectors
Disk zram3: 1.3 GiB, 1399300096 bytes, 341626 sectors
Disk zram4: 1.3 GiB, 1399300096 bytes, 341626 sectors
Disk zram5: 1.3 GiB, 1399300096 bytes, 341626 sectors
Disk zram6: 1.3 GiB, 1399300096 bytes, 341626 sectors
Disk zram7: 1.3 GiB, 1399300096 bytes, 341626 sectors
Disk zram8: 1.3 GiB, 1399300096 bytes, 341626 sectors
Disk zram9: 1.3 GiB, 1399300096 bytes, 341626 sectors
Disk zram10: 1.3 GiB, 1399300096 bytes, 341626 sectors
Disk zram11: 1.3 GiB, 1399300096 bytes, 341626 sectors

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:4096:gpt:ATA HGST HTS721010A9:;
sdb:16.0GB:scsi:512:512:msdos:SanDisk Cruzer Glide:;
1:1049kB:16.0GB:16.0GB:fat32::boot, lba;
nvme0n1:512GB:nvme:512:512:gpt:SAMSUNG MZVLB512HAJQ-00000:;
1:1049kB:512GB:512GB:ext4:D:;
nvme1n1:512GB:nvme:512:512:gpt:SAMSUNG MZVLB512HAJQ-00000:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:512GB:512GB:::lvm;

Free space >10MiB: ______________________________________________________________

sda: 0.02MiB:953870MiB:953870MiB

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                        
sdb                                                                                                        
&#9492;&#9472;sdb1      vfat     7EE1-8239                            07ee6add-01                          BOOT-REPAIR 
nvme0n1                                                                                                    
&#9492;&#9472;nvme0n1p1 ext4     d39d6ddc-e2e5-42af-9804-8d170cc2e22d 9182a495-13e7-4f59-b53a-52a4dba0b946             D
nvme1n1                                                                                                    
&#9500;&#9472;nvme1n1p1 vfat     4B8B-4069                            a40e7b91-948b-4d61-8783-2a7e9ff416dd             EFI System Partition
&#9492;&#9472;nvme1n1p2                                               d8a3e02c-3785-48d4-ab3e-3fa5179eb4bc             

Mount points (filtered): _______________________________________________________

                Avail Use% Mounted on
/dev/nvme0n1p1 444.5G   0% /mnt/boot-sav/nvme0n1p1
/dev/nvme1n1p1 505.8M   1% /mnt/boot-sav/nvme1n1p1
/dev/sdb1         14G   6% /cdrom

Mount options (filtered): ______________________________________________________

/dev/nvme0n1p1 ext4            rw,relatime
/dev/nvme1n1p1 vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sdb1      vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

=================== nvme1n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid f50ec201-93d4-46a6-b917-615086eee532 root lvmid/iGKJUj-bWRS-8626-9C82-k1Zi-dvVP-CBK557/IpksPe-T0Ax-RCvH-ZaJk-YPw3-M8PZ-noAB2H 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sdb1/boot/grub/grub.cfg (filtered) ======================

Boot-Repair-Disk session
Boot-Repair-Disk session (failsafe)

========================= sdb1/syslinux.cfg (filtered) =========================

DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/

==================== sdb1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

================== sdb1: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.
```

---

### Post by tea for one on 2022-08-18
[COLOR="#0000FF"]Line 46[/COLOR] - 0 (zero) OS detected
Therefore boot-repair will not help at the moment.

When you originally installed Ubuntu, was it on nvme0n1 or nvme1n1?
Any unusual event before boot failure?

---

### Post by oldfred on 2022-08-18
You did not need to post report, you posted link to it.
But if posting terminal output use Code Tags.
How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

Your fstab shows mount of LVM in nvme0n1p1 (?) in line 170

But report shows nothing in nvme0n1p1. That may be because it is encrypted & you did not decrypt it before running report.
Or you may have issues with LVM and encryption?

I do not know LVM nor encryption but have these links.
How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

You may need to add these to live installer to see LVM.
sudo apt-get update && sudo apt-get install lvm2 cryptsetup

Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
[https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621](https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621)
For mounting encrypted see first few lines:
[https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu)

---

### Post by draginbyu on 2022-08-21
So after reading your documentation and attempting for multiple hours I went scorched earth and started over using Angryant's tutorial ([https://forum.level1techs.com/t/raid0-nvme-on-ubuntu-repost/153779](https://forum.level1techs.com/t/raid0-nvme-on-ubuntu-repost/153779))

Goal is to have ubuntu on RAID0 across two nvme drives with sda (1TB 3.5) holding boot and efi partitions.

I create the md0 array with 

```

sudo apt-get install mdadm
sudo mdadm --zero-superblock /dev/nvme0n1
sudo mdadm --zero-superblock /dev/nvme1n1
sudo dd if=/dev/zero of=/dev/nvme0n1 bs=1M count=1000
sudo dd if=/dev/zero of=/dev/nvme1n1 bs=1M count=1000
sudo mdadm --create --verbose --level=0 --raid-devices=2 /dev/md0 /dev/nvme0n1 /dev/nvme1n1

```

and lsblk follows with:

```

ubuntu@ubuntu:~$ lsblk
NAME    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINTS
loop0     7:0    0   2.1G  1 loop  /rofs
loop1     7:1    0    62M  1 loop  /snap/core20/1587
loop2     7:2    0     4K  1 loop  /snap/bare/5
loop3     7:3    0 163.3M  1 loop  /snap/firefox/1635
loop4     7:4    0 400.8M  1 loop  /snap/gnome-3-38-2004/112
loop5     7:5    0  91.7M  1 loop  /snap/gtk-common-themes/1535
loop6     7:6    0    47M  1 loop  /snap/snapd/16292
loop7     7:7    0  45.9M  1 loop  /snap/snap-store/582
loop8     7:8    0   284K  1 loop  /snap/snapd-desktop-integration/14
sda       8:0    0 931.5G  0 disk  
sdb       8:16   1  29.9G  0 disk  
&#9492;&#9472;sdb1    8:17   1  29.9G  0 part  /cdrom
sr0      11:0    1  1024M  0 rom   
nvme1n1 259:0    0 476.9G  0 disk  
&#9492;&#9472;md0     9:0    0 953.6G  0 raid0 
nvme0n1 259:1    0 476.9G  0 disk  
&#9492;&#9472;md0     9:0    0 953.6G  0 raid0 


```

I then partition with /,/home, and swap on the md0 array.  I also put 5gb /boot and 2gb /boot/efi in fat32 on sda.  I attempted to install however was told I needed to create and efi partition.  I then changed the /boot/efi to an EFI partition and selected /dev/sda5 (the efi partition) as where store the bootloader.

Install fails with "Executing 'grub-install/dev/sda5" failed error.  I've tried shifting around where to install the bootloader and get the same error with the target being where I selected.

---

### Post by oldfred on 2022-08-21
You do not install grub to a partiiton like sda5, but install to a drive like sda.
If UEFI it auto finds the ESP - efi system partition on sda.
But if from Ubiquity installer, you have to have ESP on first drive.

Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

Do not know RAID, but RAID 0 nor normally recommended. You have to have data well backed up. 
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[https://ubuntuforums.org/showthread.php?t=2444499](https://ubuntuforums.org/showthread.php?t=2444499)
SSD better than RAID 0
[https://ubuntuforums.org/showthread.php?t=2435221](https://ubuntuforums.org/showthread.php?t=2435221)

---

