---
title: "PC only boots to Memtest"
date: 2016-05-06
forum: General Help
---

### Post by Fabian_Poehler on 2016-05-06
Hey guyz,

1 week ago i got my new pc and had a few freezes on it. So i decided to run memtest. And now it seems like i made any mistake and the pc onlz boots to memtest. 
In another thread i read about this too, but i couldnt figure it out.

Actually i already startet Ubuntu from the LiveUSB and already got the boot/info/script..

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20120702
    Boot sector info:  Syslinux looks at sector 10748 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the /syslinux 
                       directory. The integrity check of the ADV area failed. 
                       According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /efi/BOOT/BOOTIA32.efi 
                       /efi/BOOT/BOOTX64.efi /syslinux/ldlinux.sys

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 104448.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /efi/BOOT/BOOTIA32.efi 
                       /efi/BOOT/BOOTX64.efi

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32776 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1       307,199       307,199  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       102,400       100,353 Data partition (Windows/Linux)
/dev/sda2         104,448       307,166       202,719 EFI System partition

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 7.5 GiB, 8064598016 bytes, 15751168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    15,751,167    15,749,120   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7D96-BB50                              vfat       
/dev/sda2        7D96-CC91                              vfat       
/dev/sdb1        5ACB-93E1                              vfat       UBUNTU 16_0

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sda1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
PROMPT 1 
TIMEOUT 60 
DISPLAY boot.txt 
 
DEFAULT 1 
LABEL 1 
    kernel memtest  
 
LABEL 2 
    kernel memtest  
    append onepass 
 
LABEL 3 
    kernel memtest 
    append btrace 
 
LABEL 4 
    kernel memtest 
    append maxcpus=1 
 
LABEL 5 
    kernel memtest 
    append console=ttyS0,9600--------------------------------------------------------------------------------

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


========================= sda2/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
PROMPT 1 
TIMEOUT 60 
DISPLAY boot.txt 
 
DEFAULT 1 
LABEL 1 
    kernel memtest  
 
LABEL 2 
    kernel memtest  
    append onepass 
 
LABEL 3 
    kernel memtest 
    append btrace 
 
LABEL 4 
    kernel memtest 
    append maxcpus=1 
 
LABEL 5 
    kernel memtest 
    append console=ttyS0,9600--------------------------------------------------------------------------------

================= sda2: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig 
 
LABEL loadconfig 
  CONFIG /isolinux/isolinux.cfg 
  APPEND /isolinux/ 
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

/home/ubuntu/Downloads/bootinfoscript-061/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo-IYo18kp5/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-IYo18kp5/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-IYo18kp5/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-IYo18kp5/Tmp_Log: No such file or directory


```


There you can see that sda1 has no OS, and i think thats the problem. Has anyone alreadz solved this and can help me out?



Best regards,

aTTeX

---

### Post by leunam12 on 2016-05-06
Have you tried boot-repair?

---

### Post by Fabian_Poehler on 2016-05-06
Yes, i already did boot-repair, but it stil runs memtest... anyone?

---

### Post by ian-weisser on 2016-05-06
Did you manually repartition before (or during) the Ubuntu install?
Seems like you have 400G devoted to EFI instead of Ubuntu.

---

### Post by Fabian_Poehler on 2016-05-07
Nope, i didnt. 

Can i install ubuntu on a new partition without losing all the data?



Actually by creating the LiveUSB:

```
sudo blkid 
sudo mount /dev/sdx2 /mnt
cat /mnt/EFI/BOOT/MemTest86.log > MemTest86.log
sudo rm -f /mnt/EFI/BOOT/MemTest86.log
sudo umount /mnt
```

I accidentally overwrote sda1 and not sdb1.   

Can anyone tell me how to fix this?

---

### Post by leunam12 on 2016-05-07
Is re-installing not an option?

---

