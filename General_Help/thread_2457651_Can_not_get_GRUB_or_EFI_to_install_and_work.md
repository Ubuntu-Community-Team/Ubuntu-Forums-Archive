---
title: "Can not get GRUB or EFI to install and work"
date: 2021-02-06
forum: General Help
---

### Post by Jonners59 on 2021-02-06
I was having some issues with my PC, and ended up having to rebuild it.  It runs on a Rampage V motherboard and has 2 x 1Tb hard drives.  One solely for storing images and videos, and the other split between OS sda1, Documents (general)sda2, SWAP sda4, expansion sda3, spare block sda6, Games sda5.

I downloaded the latest ubuntu 20:10 iso build and burned it on to an SDCard and tried installing which installs but says GRUB and sometime EFI has failed to install.  I have tried to fix using the latest Boot Repair which loads and goes through the repair process, but then always fails.  I have tried running in trial mode and copying files over.  I have tried running these instructions from various forums:

[SIZE=2][FONT=arial][COLOR=#000000]In Grub Rescue[/COLOR]
[/FONT][/SIZE]
[HTML]type:
set
Result =
cmdpath=(hd0)
prefix=(hd0,msdos1)/grub
root=hd0,msdos1

Type:
set prefix=(hd0,msdos1)/grub
insmod normal
normal

grub-install

or

copy /usr/lib/grub/i386-pc to /boot/grub

cp -r /usr/lib/grub/i386-pc /boot/grub

or

from live CD type

sudo mount /dev/sda1 /mnt
sudo grub-install - -boot-directory=/mnt  /dev/sda
sudo reboot

or

in this grub rescue> command line type
ls
... to list all available devices, then you have to go through each, type something like (depends what is shown by the ls command):
ls (hd0,1)/
ls (hd0,2)/ 
... and so on, until you find
(hd0,1)/boot/grub   OR (hd0,1)/grub
In case of efi
(hd0,1)/efi/boot/grub OR (hd0,1)/efi/grub
... now set the boot parameters accordingly, just type this with the correct numbers and after each line press return
set prefix=(hd0,1)/grub
or (if grub is in a sub-directory)
set prefix=(hd0,1)/boot/grub

Then continue with

set root=(hd0,1)

insmod linux

insmod normal

normal

Now it should boot. Start a command-line now (a terminal) and execute

sudo update-grub[/HTML]

Nothing is working for me.  Even tried the last xUbuntu build both installing and copying GRUB...
  I also get another message, which is concerning...  something like "can't find /boot/grub/i836-pc/normal.mod"  Most worrying is this is a 64bit machine!


[ATTACH=CONFIG]287914[/ATTACH][ATTACH=CONFIG]287915[/ATTACH]

---

### Post by Jonners59 on 2021-02-06
GRUB RESCUE report

```
                        boot-repair-4ppa125                                              [20210206_1348]

============================= Boot Repair Summary ==============================




=================== /boot detected. Please check the options.

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of
sda1,
using the following options:        sda6/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s  use-standard-efi-file


/boot/efi added in sda1/fstab
Mount sda6 on /mnt/boot-sav/sda1/boot/efi

Unhide GRUB boot menu in sda1/etc/default/grub

================= Reinstall the grub-efi-amd64-signed of sda1 ==================

grub-install --version
grub-install (GRUB) 2.04-1ubuntu26.8

efibootmgr -v from chroot before grub install
BootCurrent: 0005
Timeout: 1 seconds
BootOrder: 0005,0003,0004
Boot0003* CD/DVD Drive     BBS(CDROM,,0x0)AMGOAMNO........o.A.S.U.S. . . . . .D.R.W.-.2.4.F.1.S.T. . . .a....................A...........................>..Gd-.;.A..MQ..L.1.S.A.3.8.6.F.E.0.B.1.0.X.8. . . . . . ......AMBOAMNO........o.A.S.U.S. . . . . .D.R.W.-.2.4.F.1.S.T. . . .a....................A...........................>..Gd-.;.A..MQ..L.1.S.A.3.8.6.F.E.0.B.1.0.N.8. . . . . . ......AMBO
Boot0004* Hard Drive     BBS(HD,,0x0)AMGOAMNO..........S.T.1.0.0.0.D.X.0.0.1.-.1.C.M.1.6.2....................A........................1.N........>.;.....................:..Gd-.;.A..MQ..L.S.T.1.0.0.0.D.X.0.0.1.-.1.C.M.1.6.2......AMBOAMNO..........S.T.1.0.0.0.D.X.0.0.1.-.1.C.M.1.6.2....................A........................1.N........>.;.....................:..Gd-.;.A..MQ..L.S.T.1.0.0.0.D.X.0.0.1.-.1.C.M.1.6.2......AMBO
Boot0005* UEFI: ASUS     DRW-24F1ST   a    PciRoot(0x0)/Pci(0x1f,0x2)/Sata(4,65535,0)/CDROM(1,0xc16a5,0x1f00)AMBO

uname -r
5.4.0-26-generic

grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
grub-install: warning: Internal error.
grub-install: error: failed to register the EFI boot entry: Operation not permitted.
Exit code: 1
df /dev/sda6
mv /mnt/boot-sav/sda1/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/sda1/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/sda1/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda1/boot/efi/EFI/Boot/bootx64.efi
cp /mnt/boot-sav/sda1/boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/sda1/boot/efi/EFI/Boot/

grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
grub-install: warning: Internal error.
grub-install: error: failed to register the EFI boot entry: Operation not permitted.
Exit code: 1

---- Grub-install recheck

/sbin/grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot --recheck
Installing for x86_64-efi platform.
/sbin/grub-install: warning: Internal error.
/sbin/grub-install: error: failed to register the EFI boot entry: Operation not permitted.
Exit code: 1
---- End of grub-install recheck


efibootmgr -v from chroot after grub install
BootCurrent: 0005
Timeout: 1 seconds
BootOrder: 0005,0003,0004
Boot0003* CD/DVD Drive     BBS(CDROM,,0x0)AMGOAMNO........o.A.S.U.S. . . . . .D.R.W.-.2.4.F.1.S.T. . . .a....................A...........................>..Gd-.;.A..MQ..L.1.S.A.3.8.6.F.E.0.B.1.0.X.8. . . . . . ......AMBOAMNO........o.A.S.U.S. . . . . .D.R.W.-.2.4.F.1.S.T. . . .a....................A...........................>..Gd-.;.A..MQ..L.1.S.A.3.8.6.F.E.0.B.1.0.N.8. . . . . . ......AMBO
Boot0004* Hard Drive     BBS(HD,,0x0)AMGOAMNO..........S.T.1.0.0.0.D.X.0.0.1.-.1.C.M.1.6.2....................A........................1.N........>.;.....................:..Gd-.;.A..MQ..L.S.T.1.0.0.0.D.X.0.0.1.-.1.C.M.1.6.2......AMBOAMNO..........S.T.1.0.0.0.D.X.0.0.1.-.1.C.M.1.6.2....................A........................1.N........>.;.....................:..Gd-.;.A..MQ..L.S.T.1.0.0.0.D.X.0.0.1.-.1.C.M.1.6.2......AMBO
Boot0005* UEFI: ASUS     DRW-24F1ST   a    PciRoot(0x0)/Pci(0x1f,0x2)/Sata(4,65535,0)/CDROM(1,0xc16a5,0x1f00)AMBO
Error: NVram is locked (Ubuntu not found in efibootmgr).

chroot /mnt/boot-sav/sda1 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-26-generic
Found initrd image: /boot/initrd.img-5.4.0-26-generic
Adding boot menu entry for UEFI Firmware Settings

Unhide GRUB boot menu in sda1/boot/grub/grub.cfg

An error occurred during the repair.

Locked-NVram detected. Please disable SecureBoot in the BIOS. Then try again.


============================ Boot Info After Repair ============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp fat part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk search_fs_uuid
    ---------------------------------------------------------------------------
    
    config script
    ---------------------------------------------------------------------------
    search.fs_uuid ab34b4b4-72dd-4f56-8ecb-6f23fea2d37d root hd0,msdos1 
    set prefix=($root)'/grub'
    
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/grubx64.efi 
                       /efi/BOOT/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /boot/grub/i386-pc/core.img

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


================================ 1 OS detected =================================

OS#1:   Ubuntu 20.04 LTS on sda1

============================ Architecture/Host Info ============================

CPU architecture: 64-bit
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04 LTS, focal, x86_64)


===================================== UEFI =====================================

BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.

efibootmgr -v
BootCurrent: 0005
Timeout: 1 seconds
BootOrder: 0005,0003,0004
Boot0003* CD/DVD Drive     BBS(CDROM,,0x0)AMGOAMNO........o.A.S.U.S. . . . . .D.R.W.-.2.4.F.1.S.T. . . .a....................A...........................>..Gd-.;.A..MQ..L.1.S.A.3.8.6.F.E.0.B.1.0.X.8. . . . . . ......AMBOAMNO........o.A.S.U.S. . . . . .D.R.W.-.2.4.F.1.S.T. . . .a....................A...........................>..Gd-.;.A..MQ..L.1.S.A.3.8.6.F.E.0.B.1.0.N.8. . . . . . ......AMBO
Boot0004* Hard Drive     BBS(HD,,0x0)AMGOAMNO..........S.T.1.0.0.0.D.X.0.0.1.-.1.C.M.1.6.2....................A........................1.N........>.;.....................:..Gd-.;.A..MQ..L.S.T.1.0.0.0.D.X.0.0.1.-.1.C.M.1.6.2......AMBOAMNO..........S.T.1.0.0.0.D.X.0.0.1.-.1.C.M.1.6.2....................A........................1.N........>.;.....................:..Gd-.;.A..MQ..L.S.T.1.0.0.0.D.X.0.0.1.-.1.C.M.1.6.2......AMBO
Boot0005* UEFI: ASUS     DRW-24F1ST   a    PciRoot(0x0)/Pci(0x1f,0x2)/Sata(4,65535,0)/CDROM(1,0xc16a5,0x1f00)AMBO

2895d47544fd587b26c7e29be1295c27   sda6/BOOT/fbx64.efi
dc3c47be2f78a78e5e57d097ae6c5c84   sda6/BOOT/mmx64.efi
637fa7fabc8a2f70312edf2f15e275ff   sda6/ubuntu/grubx64.efi
dc3c47be2f78a78e5e57d097ae6c5c84   sda6/ubuntu/mmx64.efi
78415fb8fb9b909f8029858113f1335f   sda6/ubuntu/shimx64.efi
78415fb8fb9b909f8029858113f1335f   sda6/BOOT/BOOTX64.efi


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : notGPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes
sdb    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
sda2    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    grubenv-ok,    noupdategrub,    farbios
sda5    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda6    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdb1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

sda1    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda6    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not-sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda2    : is-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda5    : maybesepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda6    : not-sepboot,    no-kernel,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sdb1    : maybesepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sdb

fdisk -l (filtered): ___________________________________________________________

Disk sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 0x0009b5f7
      Boot      Start        End    Sectors   Size Id Type
sda1             2048  266649599  266647552 127.2G 83 Linux
sda2        266649600 1350946815 1084297216   517G 83 Linux
sda3       1422628862 1953523711  530894850 253.2G  5 Extended
sda4       1350946816 1422626815   71680000  34.2G 82 Linux swap / Solaris
sda5       1432926208 1953523711  520597504 248.2G 83 Linux
sda6  *    1422628864 1432926207   10297344   4.9G ef EFI (FAT-12/16/32)
Partition table entries are not in disk order.
Disk sdb: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 0x0007c84e
      Boot Start        End    Sectors   Size Id Type
sdb1        2048 1953523711 1953521664 931.5G 83 Linux

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:4096:msdos:ATA ST1000DX001-1CM1:;
1:1049kB:137GB:137GB:ext4::;
2:137GB:692GB:555GB:ext4::;
4:692GB:728GB:36.7GB:linux-swap(v1)::;
3:728GB:1000GB:272GB:::;
6:728GB:734GB:5272MB:fat32::boot, esp;
5:734GB:1000GB:267GB:ext4::;
sdb:1000GB:scsi:512:4096:msdos:ATA ST1000DX001-1CM1:;
1:1049kB:1000GB:1000GB:ext4::;
sr0:1663MB:scsi:2048:2048:mac:ASUS DRW-24F1ST a:;
1:2048B:6143B:4096B::Apple:;
2:1622MB:1627MB:4063kB::EFI:;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                   PARTLABEL
sda                                                                                                               
&#9500;&#9472;sda1 ext4     687192f6-44d3-4c70-b89b-03fa3b0260ab 0009b5f7-01                                                  
&#9500;&#9472;sda2 ext4     14c4cb48-f927-426d-ac55-2836a6d88848 0009b5f7-02                          Documents               
&#9500;&#9472;sda3                                               0009b5f7-03                                                  
&#9500;&#9472;sda4 swap     8847cc1b-17ef-42a3-a851-dca1cd3b520f 0009b5f7-04                                                  
&#9500;&#9472;sda5 ext4     9783d144-806c-4951-8254-157164f5969d 0009b5f7-05                          GAMES                   
&#9492;&#9472;sda6 vfat     1B76-D392                            0009b5f7-06                                                  
sdb                                                                                                               
&#9492;&#9472;sdb1 ext4     49edc58d-2c86-4524-b850-0b872ada1114 0007c84e-01                          Tv and Video Rec        

df (filtered): _________________________________________________________________

       Avail Use% Mounted on
sda1     113G   4% /mnt/boot-sav/sda1
sda2   476.3G   1% /mnt/boot-sav/sda2
sda5   216.3G   6% /mnt/boot-sav/sda5
sda6     4.9G   0% /mnt/boot-sav/sda6
sdb1   869.2G   0% /mnt/boot-sav/sdb1

Mount options: __________________________________________________________________

sda1   rw,relatime
sda2   rw,relatime,stripe=32746
sda5   rw,relatime
sda6   rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
sdb1   rw,relatime

====================== sda1/boot/grub/grub.cfg (filtered) ======================

Ubuntu   687192f6-44d3-4c70-b89b-03fa3b0260ab
Ubuntu, with Linux 5.4.0-26-generic   687192f6-44d3-4c70-b89b-03fa3b0260ab
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda1/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=687192f6-44d3-4c70-b89b-03fa3b0260ab /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda6 during installation
# swap was on /dev/sda4 during installation
UUID=8847cc1b-17ef-42a3-a851-dca1cd3b520f none            swap    sw              0       0
UUID=1B76-D392  /boot/efi       vfat    defaults      0       1

======================= sda1/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
   0.000980377 = 0.001052672    boot/grub/grub.cfg                             1
 100.135765076 = 107.519959040  boot/grub/i386-pc/core.img                     1
   2.418083191 = 2.596397056    boot/vmlinuz                                   1
   2.418083191 = 2.596397056    boot/vmlinuz-5.4.0-26-generic                  1
   3.462127686 = 3.717431296    boot/initrd.img                                2
   3.462127686 = 3.717431296    boot/initrd.img-5.4.0-26-generic               2
   3.462127686 = 3.717431296    boot/initrd.img.old                            2

===================== sda1: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 17622 Jan 13 14:12 10_linux
-rwxr-xr-x 1 root root 42359 Jan 13 14:12 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Apr 15  2020 20_linux_xen
-rwxr-xr-x 1 root root 12059 Apr 15  2020 30_os-prober
-rwxr-xr-x 1 root root  1424 Apr 15  2020 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr 15  2020 40_custom
-rwxr-xr-x 1 root root   216 Apr 15  2020 41_custom

======================== sda2/grub/grub.cfg (filtered) =========================

Ubuntu   acd94238-622c-41eb-9138-8cf7e9bd3606
Ubuntu, with Linux 5.8.0-41-generic   acd94238-622c-41eb-9138-8cf7e9bd3606
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 355.773437500 = 382.008819712  grub/grub.cfg                                  2
 127.801834106 = 137.226174464  vmlinuz                                        1
 127.801834106 = 137.226174464  vmlinuz-5.8.0-41-generic                       1
 127.801834106 = 137.226174464  vmlinuz.old                                    1
 127.881195068 = 137.311387648  initrd.img                                     2
 127.881195068 = 137.311387648  initrd.img-5.8.0-41-generic                    2
 127.881195068 = 137.311387648  initrd.img.old                                 2

===================== sda6/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 687192f6-44d3-4c70-b89b-03fa3b0260ab root hd0,msdos1 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

==================== sda6: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/i386-pc/core.img                     1
 ]
```


grub-efi-amd64-signedzsudo apt-get purge grub\*
sudo apt-get install grub-efi
sudo apt-get autoremove
sudo update-grub

---

### Post by oldfred on 2021-02-06
Whiel you have UEFI system, it looks more like an old BIOS install with MBR partitions.
UEFI suggests gpt, Microsoft has required gpt partitioning with UEFI installs since 2012. So newer hardware is UEFI.

But both of your drives are MBR(msdos) partitioned and you show older grub boot loaders in MBRs. And now ESP - efi system partition is shown as sda6. Typically is is first or second partition but can be anywhere.

You show UEFI Secure Boot on which prevents BIOS/CSM/Legacy boot.
And you show this which may be Secure Boot related or a separate UEFI setting to prevent unauthorized changes.
Error: NVram is locked (Ubuntu not found in efibootmgr).

How you boot install and repair media UEFI or BIOS is then how it installs or repairs.

Do you want UEFI or BIOS boot?
If you want BIOS, you need to turn off UEFI Secure Boot and maybe change other UEFI settings.
If you updated UEFI, it probably reset some UEFI settings to defaults & you have to redo your changes. On of my system has 6 or 7 settings I change with each UEFI update.

---

### Post by Jonners59 on 2021-02-06
> **oldfred said:**
> Whiel you have UEFI system, it looks more like an old BIOS install with MBR partitions.
UEFI suggests gpt, Microsoft has required gpt partitioning with UEFI installs since 2012. So newer hardware is UEFI.

Hello, OldFred.  Lovely to hear from yo, so long. 

> **oldfred said:**
> 
But both of your drives are MBR(msdos) partitioned and you show older  grub boot loaders in MBRs. And now ESP - efi system partition is shown  as sda6. Typically is is first or second partition but can be anywhere.

You show UEFI Secure Boot on which prevents BIOS/CSM/Legacy boot.
And you show this which may be Secure Boot related or a separate UEFI setting to prevent unauthorized changes.
Error: NVram is locked (Ubuntu not found in efibootmgr).

How you boot install and repair media UEFI or BIOS is then how it installs or repairs.
Well, it explains a lot, but TBH I just put the disc in and follow the instructions....

Boot-Repair told me to change some settings, on the BIOS, which I followed...
[ATTACH=CONFIG]287916[/ATTACH]
> **oldfred said:**
> 
Do you want UEFI or BIOS boot?
If you want BIOS, you need to turn off UEFI Secure Boot and maybe change other UEFI settings.
If you updated UEFI, it probably reset some UEFI settings to defaults  & you have to redo your changes. On of my system has 6 or 7 settings  I change with each UEFI update.
Do not mind, but I guess UEFI is more future proof...  So what do I need to do where and how, please?

---

### Post by Jonners59 on 2021-02-06
> **oldfred said:**
> Whiel you have UEFI system, it looks more like an old BIOS install with MBR partitions.
UEFI suggests gpt, Microsoft has required gpt partitioning with UEFI installs since 2012. So newer hardware is UEFI.

Hello, OldFred.  Lovely to hear from yo, so long. 

> **oldfred said:**
> 
But both of your drives are MBR(msdos) partitioned and you show older   grub boot loaders in MBRs. And now ESP - efi system partition is shown   as sda6. Typically is is first or second partition but can be anywhere.

You show UEFI Secure Boot on which prevents BIOS/CSM/Legacy boot.
And you show this which may be Secure Boot related or a separate UEFI setting to prevent unauthorized changes.
Error: NVram is locked (Ubuntu not found in efibootmgr).

How you boot install and repair media UEFI or BIOS is then how it installs or repairs.
Well, it explains a lot, but TBH I just put the disc in and follow the instructions....

Boot-Repair told me to change some settings, on the BIOS, which I followed...
[ATTACH=CONFIG]287916[/ATTACH]
> **oldfred said:**
> 
Do you want UEFI or BIOS boot?
If you want BIOS, you need to turn off UEFI Secure Boot and maybe change other UEFI settings.
If you updated UEFI, it probably reset some UEFI settings to defaults   & you have to redo your changes. On of my system has 6 or 7 settings   I change with each UEFI update.
Do not mind, but I guess UEFI is more future proof...  So what do I need to do where and how, please?

I  just found this and tried it.  But it failed at the last couple of  comds before reboot.  Said an internal error, not allowed.  Tried with  Sudo too, just in case
[https://techbit.ca/2018/09/repair-grub2-efi-boot/](https://techbit.ca/2018/09/repair-grub2-efi-boot/)

```

Now for the fun part.
 
[LIST=1]
[*] Open a terminal and mount the root partition (/) of the device  containing your OS. If you only have one hard drive in your computer it  is likely to be /dev/sda.
 	
$ sudo mount /dev/sda2 /mnt
 You can verify that this device contains your root partition (/) by doing an “ls” on the directory you mounted
 	
$ ls /mnt
bin  boot  dev  etc  home  initrd.img  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  snap  srv  sys  tmp  usr  var  vmlinuz

[*] Mount the /dev/sda1 partition as that is likely your efi partition and do an “ls” to check
 $ sudo mount /dev/sda1 /mnt/boot/efi
$ ls /mnt/boot/efi
EFI

[*] Mount the rest of the directories that GRUB needs to use to check for other operating systems, etc.
 We can do this one at a time with multiple commands like this: 
$ sudo mount -B /dev /mnt/dev
$ sudo mount -B /dev/pts /mnt/dev/pts
$ sudo mount -B /proc /mnt/proc
$ sudo mount -B /sys /mnt/sys
 Or we can do this much easier in one command with the help of a for loop: $ [COLOR=#66d9ef]for[/COLOR] i in /dev /dev/pts /proc /sys; [COLOR=#66d9ef]do[/COLOR] sudo mount -B $i /mnt$i; [COLOR=#66d9ef]done[/COLOR]

[*] Chroot into your environment
 $  sudo chroot /mnt

[*] Fix grub
 $ grub-install /dev/sda
$ grub-install --recheck /dev/sda
$ update-grub

[*] Now you can exit the chroot environment
 $ exit

[*] Turn off the computer and remove the USB stick. Then turn your computer back on. If all went according to plan your computer should boot normally into Ubuntu 18.04.
[/LIST]
 After the computer starts, open a terminal and update all packages:

 $ sudo apt update [COLOR=#f92672]&&[/COLOR] sudo apt upgrade -y
 If you receive an error about dpkg being interrupted you will need to run an automatic configure to fix it.
 $ sudo dpkg --configure -a
 If dpkg finishes without errors your system should be back to a fully functional state : )
```

---

### Post by oldfred on 2021-02-06
As I mentioned, ESP is often first (or second) partition, but in your case it is sda6.
So you have to mount sda6 as ESP if you are using the chroot method and not Boot-Repair.

```
Disk sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 0x0009b5f7
      Boot      Start        End    Sectors   Size Id Type
sda1             2048  266649599  266647552 127.2G 83 Linux
sda2        266649600 1350946815 1084297216   517G 83 Linux
sda3       1422628862 1953523711  530894850 253.2G  5 Extended
sda4       1350946816 1422626815   71680000  34.2G 82 Linux swap / Solaris
sda5       1432926208 1953523711  520597504 248.2G 83 Linux
[COLOR=#ff0000]sda6  *    1422628864 1432926207   10297344   4.9G ef EFI (FAT-12/16/32)[/COLOR]

```

I would still turn UEFI Secure Boot off, but then you still can use UEFI (or BIOS).
Long term, you need to plan to convert drives to gpt from the now very old MBR(msdos). I started my conversion from MBR to gpt in 2010.

Are you using Boot-Repair ISO or Ubuntu live installer and adding the Boot-Repair ppa?
 I prefer ppa only because it often is updated and then may have fixes that ISO does not yet have.
See option 2:
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

If doing the full chroot, be sure to mount correct ESP. UEFI only boots from a FAT32 partition with boot/esp flags, your sda6. So it needs the correct boot files.
Not sure if you incorrectly installed boot files into sda1, or what that did.

Your ESP is very large. Typically recommended size is 300 to 600MB, yours is 4.9GB. And most of the 300MB is unused and more for future use.
I do use my ESP to have the UEFI update file for my motherboard. UEFI only reads FAT32. But I have to change default permissions to let me use it from my working system.

---

### Post by Jonners59 on 2021-02-06
> **oldfred said:**
> As I mentioned, ESP is often first (or second) partition, but in your case it is sda6.
So you have to mount sda6 as ESP if you are using the chroot method and not Boot-Repair.

```
Disk sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 0x0009b5f7
      Boot      Start        End    Sectors   Size Id Type
sda1             2048  266649599  266647552 127.2G 83 Linux
sda2        266649600 1350946815 1084297216   517G 83 Linux
sda3       1422628862 1953523711  530894850 253.2G  5 Extended
sda4       1350946816 1422626815   71680000  34.2G 82 Linux swap / Solaris
sda5       1432926208 1953523711  520597504 248.2G 83 Linux
[COLOR=#ff0000]sda6  *    1422628864 1432926207   10297344   4.9G ef EFI (FAT-12/16/32)[/COLOR]

```

I would still turn UEFI Secure Boot off, but then you still can use UEFI (or BIOS).
Long term, you need to plan to convert drives to gpt from the now very old MBR(msdos). I started my conversion from MBR to gpt in 2010.


It was because it already existed on the machine and when installing it said I needed an EFI partition - sometimes.
So how do I clean up the machine to get rid of all the rubbish?  ANd why doesn't the ubuntu install put the correct components?

Will do re security

How do I ?

> **oldfred said:**
> 
Are you using Boot-Repair ISO or Ubuntu live installer and adding the Boot-Repair ppa?
 I prefer ppa only because it often is updated and then may have fixes that ISO does not yet have.
See option 2:
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 


iso

> **oldfred said:**
> 
If doing the full chroot, be sure to mount correct ESP. UEFI only boots  from a FAT32 partition with boot/esp flags, your sda6. So it needs the  correct boot files.
Not sure if you incorrectly installed boot files into sda1, or what that did.
There seems to be files on ALMOST all partitions.  How is it cleaned up?

> **oldfred said:**
> 
Your ESP is very large. Typically recommended size is 300 to 600MB,  yours is 4.9GB. And most of the 300MB is unused and more for future use.
I do use my ESP to have the UEFI update file for my motherboard. UEFI  only reads FAT32. But I have to change default permissions to let me use  it from my working system
I had quite a bit of space and it does not show a recommended size.

Thank you.  I shall turn off security.  Run that set of cmds again, but try SDA6 instead,

---

### Post by Jonners59 on 2021-02-06
Tried the chroot method but couldn't mount the additional partitions it required, so rebooted into Boot-Repair after just checking in case it did work.  Neither worked.  Depending which of the HDs I boot from, sdc or sda I get different messages.  sda I end up in Grub rescue and sdc I get a message that grub can't findxxxxx partition.  "error: no such device: sb34b4b4-72dd-4f56-8ecb-6fea2d37d" and "error: unknown filesystem"  "entering rescue mode"  "grub rescue".

WHAT next????

---

### Post by CelticWarrior on 2021-02-06
It seems you tried to reuse the partitions from the old system. That works (eventually) if you set and install Legacy/CSM mode.
I wouldn't do it, at all, for many reasons. I would always cleanup the drive and start fresh if coming from an old BIOS system to a new UEFI system and if using MBR before also change to GPT and this change alone would result in the intended cleanup.

Not really a suggestion for you unless you can and want to start over and have good backups.
I see many partitions including the absurdly large EFI partition as commented above but also an absurdly large swap partition (Ubuntu now can and by default does use a swap file instead).

Currently and for a UEFI system only the EFI partition (FAT32 ~512MB) and / is needed. This is simplest partitioning layout. If you want - and there are good reasons for it - you can have a separated /home (probably the one you referred as "Documents"??) and an additional partition for games (why not?) can be useful for Steam and others when reinstalling/recovering the OS.

Now, if if don't mind cleaning up the drive (musty have backups) you can start with Gparted. Device menu > Create new partition table..., select "GPT". Then you can partition in advance, always starting by the EFI partition. Then add / with the size according to your needs - it depends on the software you intend to install minus games so 30GB to 50GB should be enough. Then decide how much for you personal files (and settings) - /home - and how much for the games partition. Please note that at this point you don't need to create that partition, just leave enough unallocated space. It can be created after installing Ubuntu. ESP (EFI System Partition), / and /home are the ones you need to define before starting the installation and use "something else" to define each and every one as intended.

---

### Post by oldfred on 2021-02-06
First need to be consistent. 
UEFI or BIOS?
Only boot in one mode or other both live installer, Boot-Repair ISO (but I prefer installer) and settings in system UEFI or CSM/BIOS.
the Summary Report you posted above shows the mount of an ESP in fstab. So system was/is?  configured for UEFI boot.

But if you want UEFI, then you must always boot in UEFI mode.

If a UUID not found, it typically is booting an old version of grub which is linked to an old partition.
So that could be booting the BIOS mode grub in MBR which is looking for your old install.

Are you getting grub> or grub rescue> ?

Error is correct that UUID does not exist.

---

### Post by Jonners59 on 2021-02-06
Grub Rescue...
How do you make it one or the other????  I am using the ios to build the machines, and they do not offer a choice.  Where does the choice come from?

I tried to rebuild again, given your comment on efi being 1st partition.  So shuffled a bit to get it to be sda1.  / is now further up, I think 6 or 7...  Can the partitions be renumbered?  They are not sequential.

Anyway after using Boot-Repair and selecting as you suggested, and trying to install the latest from an SDCard (which failed and gave a bug report) and then an older CD (xUbuntu 20.04 LTS), which did install.  However after reboot back to Grub Rescue.

To confirm.
Have turned OFF fast boot on the BIOS.
Have turned off Security on BIOS.
Have selected 1st option is UEFI on BIOS.
I can't wipe the whole drive, either of them as they have data on them, but can and have wiped the old OS and started afresh, many times.

And pref is UEFI

[ATTACH=CONFIG]287917[/ATTACH]  BIOS

What am I doing wrong?

---

### Post by oldfred on 2021-02-06
If you want UEFI, change settings to UEFI only.
My older system only booted in UEFI with UEFI only. The UEFI or CSM/BIOS mode always booted in BIOS mode.

The ISO is configured for both UEFI or BIOS and then in UEFI one time boot menu (often f12) should be two entries, one clearly UEFI and one not which is the BIOS boot entry. Setting in UEFI on boot mode are really only for installed system, not one time boot of a flash drive.

Some tools to create an installer only create UEFI or only BIOS versions of installer. Not sure what yours does.

ESP does not have to be sda1, but you can only have one ESP per drive, so make sure you only have one.

---

### Post by Jonners59 on 2021-02-07
[FONT=arial]> **oldfred said:**
> If you want UEFI, change settings to UEFI only.

Done.  Only UEFI on fw and have ALSO taken the 2nd HD out of the boot options, just in case there is stuff there that interferes.  I can always go back and fix after.

> **oldfred said:**
> 
Some tools to create an installer only create UEFI or only BIOS versions of installer. Not sure what yours does.
I used the USB Startup Disc Creator app in Ubuntu and the ios

> **oldfred said:**
> 
ESP does not have to be sda1, but you can only have one ESP per drive, so make sure you only have one.
Well it is sda1 now.  I do not understand this and what is what.  The installation creates a Boot directory inside the ubuntu build directory, and inside that there is GRUB and EFI etc...  so why the extra partition and what is the difference and which one do I point the boot and grub too???

I also tried several times to reinstall the ubuntu ios try and install.  Latest version.  It fails, seems it is GRUB and files a bug report.  I see many there and there is a log going back a couple of builds....  to do with AMD, third party SW etc.

I also did this:[SIZE=2]
[/SIZE][/FONT][h=2][FONT=arial][SIZE=2]Identifying if the computer boots the HDD in UEFI mode
```
ubuntu@ubuntu:~/Desktop$ [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
EFI boot on HDD

```[/SIZE]
[/FONT][/h][FONT=arial]Also checked if installed version was UEFI with:
```
[ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"
```
Though not sure if that relates to the installed OR the Live CD.  Eitherway it should have detected UEFI in the build and only installed that.

And UEFI only is on.  Fast Boot off.  Secure Boot SRT is Off...  but it still fails.

Just revbooted back in to LiveCD and tried Boot Repair in LiveCD.
```

[/FONT][FONT=arial]sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

```
Followed the install inc.```
sudo chroot "/mnt/boot-sav/sda4" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda4" apt-get install -fy
sudo chroot "/mnt/boot-sav/sda4" apt-get purge -y grub*-common shim-signed
```
But then it did this:
```
sudo chroot "/mnt/boot-sav/sda4" apt-get purge -y grub*-common shim-signed
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'grub-common' for glob 'grub*-common'
Note, selecting 'grub2-common' for glob 'grub*-common'
The following additional packages will be installed:
  localechooser-data
The following packages will be REMOVED:
  grub-common* grub-efi-amd64-bin* grub-efi-amd64-signed*
  grub-gfxpayload-lists* grub-pc* grub-pc-bin* grub2-common* os-prober*
  shim-signed* ubiquity* ubiquity-frontend-gtk* zsys*
The following NEW packages will be installed:
  localechooser-data
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  shim-signed grub-efi-amd64-signed (due to shim-signed)
  grub2-common (due to shim-signed)
0 upgraded, 1 newly installed, 12 to remove and 294 not upgraded.
E: Essential packages were removed and -y was used without --allow-remove-essential.

```
I didn't get the window confirming deletion and the ap wouldn't progress

I just do not get what is wrong and why and how to get it working?????
[/FONT][FONT=arial]
[/FONT]

---

### Post by Jonners59 on 2021-02-07
Did another reboot and failed again, this time the fw BIOS is saying current BIOS setting does not fully support the boot device.

Rebooted back into the LiveCD and tried Boot Repair again X 2 and getting the same message each reboot into the OS.

So we know it is to do with UEFI but it is worse as it does not even get to grub.

I'll try a purge grub

So now I have downloaded another copy of the 20.10 iso and burnt it on to another brand new stick.  Just tried again and the install fails with a message about unable to install GRUB, and filed a report...

Spent ages trying to upload images, but the forum is too restrictive and the Live Boot not able to downsize the images to use.  Crazy!!!!
Link to images
[https://photos.app.goo.gl/Xthzxr5WdSciwmaE6](https://photos.app.goo.gl/Xthzxr5WdSciwmaE6)
Link to bug report.
[https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1914925](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1914925)

---

### Post by dragonfly41 on 2021-02-07
I hesitate to suggest anything at this stage .. but all this Grub stuff can be gobbledegook.
I have had success in installing [rEFInd]("https://www.rodsbooks.com/refind/") .. in your case I guess in /dev/sda1.
Important to understand that rEFind adds to your grub options. That is it can be removed easily frpm /boot/efi/EFI  if the experiment fails.
I hope that this idea does not add a layer of confusion.But it has got me out of a hole.

---

### Post by Jonners59 on 2021-02-07
> **dragonfly41 said:**
> I hesitate to suggest anything at this stage .. but all this Grub stuff can be gobbledegook.
I have had success in installing [rEFInd]("https://www.rodsbooks.com/refind/") .. in your case I guess in /dev/sda1.
Important to understand that rEFind adds to your grub options. That is it can be removed easily frpm /boot/efi/EFI  if the experiment fails.
I hope that this idea does not add a layer of confusion.But it has got me out of a hole.

Way above my pay grade

---

### Post by dragonfly41 on 2021-02-07
[COLOR=#000000]> Way above my pay grade

[/COLOR]Referring here ...

[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html)

While in LiveUSB run this series of commands

**sudo apt-add-repository ppa:rodsmith/refind**
**sudo apt update**
[B]sudo apt install refind
[/B]
and point to /dev/sda1 at installation point.

---

### Post by oldfred on 2021-02-07
I have several flash drives with rEFInd for emgency boot. It works well. But is for UEFI systems, but can reboot into a BIOS install. Grub cannot seem to do that.
But I still use grub.

I see your settings seem to be UEFI or legacy/BIOS/CSM.
You need to decide if you want UEFI or BIOS and then set to UEFI only or CSM only. This is mode for installed system only.
And then only boot live installer in that mode to reinstall grub. But you have to choose each time you boot.

---

### Post by Jonners59 on 2021-02-07
> **dragonfly41 said:**
> [COLOR=#000000]

[/COLOR]Referring here ...

[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html)

While in LiveUSB run this series of commands

**sudo apt-add-repository ppa:rodsmith/refind**
**sudo apt update**
[B]sudo apt install refind
[/B]
and point to /dev/sda1 at installation point.

Shoot, just come out of LiveCD, after 

I loosened the UEFI option to allow legacy and got the GRUB back.  Though said couldn't find a specific UUID.  After doing this:

```
sudo -i
mount /dev/sda4 /mnt
mount /dev/sda1 /mnt/boot/efi
grub-install --boot-directory=/mnt/boot --bootloader-id=ubuntu  --target=x86_64-efi --efi-directory=/mnt/boot/efi  
reboot
```
it now just says "error: unknown file system"

I'll go back in and add this too.

---

### Post by Jonners59 on 2021-02-07
> **oldfred said:**
> I have several flash drives with rEFInd for emgency boot. It works well. But is for UEFI systems, but can reboot into a BIOS install. Grub cannot seem to do that.
But I still use grub.

I see your settings seem to be UEFI or legacy/BIOS/CSM.
You need to decide if you want UEFI or BIOS and then set to UEFI only or CSM only. This is mode for installed system only.
And then only boot live installer in that mode to reinstall grub. But you have to choose each time you boot.


????  I changed it to UEFI ONLY  in the photos are the options in BOOT I have 
CSM (Compatability Support Module) and I have selected "ENABLE"
Menu below it says:[INDENT]BOOT Device: and options are: [/INDENT]
[INDENT=2]"UEFI and Legacy OPROM", 
"Legacy OPROM" only" and 
"UEFI only".  
[/INDENT]
[INDENT]I first had this at both.  I changed it to UEFI only and now back at both, as UEFI only didn't work at all.  But at the time of below was UEFI only.

Boot from Network: and options are: [/INDENT]
[INDENT=2]"Legacy OPROM first", 
"UEFI driver first" or
"Ignore".
[/INDENT]
[INDENT]Was "Legacy", then changed to "UEFI" and now "ignore" as I do not use Network boot.

Boot from Storage Devices: and options are:[/INDENT]
[INDENT=2]"Both, Legacy OPROM first",
"Both, UEFI first",
"Legacy OPROM first" and
"UEFI driver first" and
"Ignore" 
[/INDENT]
[INDENT]There is no UEFI only and have tried both, though left on "UEFI driver first" especially given the SDCards are working.

Last but far from least is
Boot from PCIe Expansion Devices:  options are only: 
[/INDENT]
[INDENT=2]"Legacy OPROM first" and
"UEFI driver first". 
[/INDENT]
[INDENT]I have "UEFI driver first"
[/INDENT]

So bar "Boot Device Control" which was inc legacy, then UEFI only and now UEFI with Legacy..  it is all UEFI.

If I force boot into E2 (other HD) from the BIOS I get:
"error: no such device ab34b4b4-72dd-4f56-8ecb-6f23fea2d37d
error: unknown file system
Entering rescue mode...
grub rescue>"

If I boot normally, or force E1 or remove E2 from the bootable options in BIOS or in BootDisc and chose boot from next directory then I get:
"error: unknown file system
Entering rescue mode...
grub rescue>"

Happy to go with whatever you suggest.....  in the meantime I shall add the below

AN add:
I just changed to turn CSM off, which forces full Windows UEFI (so the notes say).  It failed on boot and says "The VGA card is not supported by UEFI drive.  CSM settings have been changed for better compatibility".  VGA is NOT supported!  I get the same message IF I go into CSM and change it to UEFI only.
[ATTACH=CONFIG]287921[/ATTACH]

---

### Post by Jonners59 on 2021-02-07
> **dragonfly41 said:**
> [COLOR=#000000]

[/COLOR]Referring here ...

[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html)

While in LiveUSB run this series of commands

**sudo apt-add-repository ppa:rodsmith/refind**
**sudo apt update**
[B]sudo apt install refind
[/B]
and point to /dev/sda1 at installation point.
OK, came back when installing as error writing /boot/efi//EFI/refind/refind.conf: no space left on device...

There was NO option to chose sda1  Clearly I did something wrong.  I'll try again.

---

### Post by dragonfly41 on 2021-02-07
[COLOR=#000000]> error writing /boot/efi//EFI/refind/refind.conf: no space left on device...

Some time since I last installed rEFInd (it has been rock solid for me)
but the double forward slash efi//EFI looks odd
as does "no space left"

Can you see anything in /boot/efi/EFI/refind and is there any unused space in that partition (mine is 500kB). [/COLOR]

---

### Post by Jonners59 on 2021-02-07
> **dragonfly41 said:**
> [COLOR=#000000]

Some time since I last installed rEFInd (it has been rock solid for me)
but the double forward slash efi//EFI looks odd
as does "no space left"

Can you see anything in /boot/efi/EFI/refind and is there any unused space in that partition (mine is 500kB). [/COLOR]

I'll look tomorrow as time for kids now...
PS should be loads of space as gave loads for all partitions.  Even the Live boot SD cards are huge to what is needed.  Anyway.  Harry Potter with no 3 son now.  Good night.

Oh given the VGA comment, I have just bought a new graphics card:  [ASUS TUF Nvidia GeForce GTX 1650]("https://www.amazon.co.uk/gp/product/B08FSXCP85/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1")

---

### Post by rbmorse on 2021-02-07
I may have missed this in the thread, but make sure that your compatibility support mode (CSM) is set to off/disabled in the EFI setup.  Probably under the boot options menu.

---

### Post by Jonners59 on 2021-02-08
> **rbmorse said:**
> I may have missed this in the thread, but make sure that your compatibility support mode (CSM) is set to off/disabled in the EFI setup.  Probably under the boot options menu.
Huh ha, yes, you did.  I was told to turn it on.  Will try in a while.  Still a tad early here.

---

### Post by dragonfly41 on 2021-02-08
> There was NO option to chose sda1 Clearly I did something wrong. I'll try again.

Instead of typing /dev/sda1 (which is a guess from me based on this thread) just accept the default location which rEFInd should pick up.

After that you should see refind installed in /boot/efi/EFI/refind/
alongside the other loaders.

---

### Post by Jonners59 on 2021-02-08
> **dragonfly41 said:**
> Instead of typing /dev/sda1 (which is a guess from me based on this thread) just accept the default location which rEFInd should pick up.

After that you should see refind installed in /boot/efi/EFI/refind/
alongside the other loaders.

Thank you.  Tried again this AM and it too failed.  I only did the default install.  The irony is it fails saying directory is full so no room for .config file, but the directory has 180Gb free.  I think the best bet is wait for the new AV card and see what happens.  It SHOULD arrive late tomorrow, so probably Wednesday.

---

### Post by dragonfly41 on 2021-02-08
Puzzled by this error I dug around ..
[https://forum.endeavouros.com/t/install-failing-no-space-left-on-device-grub-install-error/8783/18](https://forum.endeavouros.com/t/install-failing-no-space-left-on-device-grub-install-error/8783/18)
This cites rEFInd and at end states that boot entries are kept in NVRAM.
Possibly, it might be this which is full?
I have not encountered this issue so far in my configuration experiments.

---

### Post by Jonners59 on 2021-02-08
> **dragonfly41 said:**
> Puzzled by this error I dug around ..
[https://forum.endeavouros.com/t/install-failing-no-space-left-on-device-grub-install-error/8783/18](https://forum.endeavouros.com/t/install-failing-no-space-left-on-device-grub-install-error/8783/18)
This cites rEFInd and at end states that boot entries are kept in NVRAM.
Possibly, it might be this which is full?
I have not encountered this issue so far in my configuration experiments.

My understanding is that LiveCD works in RAM or something like that...  Anyway, I do aim to please.  Glad also I am not the only one lost on this.  I don't feel so stupid.

---

### Post by oldfred on 2021-02-08
Many systems have "Windows UEFI" as Secure Boot. My system is older from when Windows 7 was still available and it said if installing Windows 7 you have to use "Other" in UEFI settings as Windows 7 did not support UEFI Secure Boot.
And then when Secure Boot is on, if you need proprietary drivers like nVidia, it will require you to provide your own key for secure boot. Neither nVidia can give a key, nor Ubuntu as it is a proprietary blob and it cannot verify it. A user who believes code is ok, can provide his own key using MOKmanager. Easier just to turn UEFI Secure Boot off, or change from "Windows" to "Other".

---

### Post by Jonners59 on 2021-02-08
> **oldfred said:**
> Many systems have "Windows UEFI" as Secure Boot. My system is older from when Windows 7 was still available and it said if installing Windows 7 you have to use "Other" in UEFI settings as Windows 7 did not support UEFI Secure Boot.
And then when Secure Boot is on, if you need proprietary drivers like nVidia, it will require you to provide your own key for secure boot. Neither nVidia can give a key, nor Ubuntu as it is a proprietary blob and it cannot verify it. A user who believes code is ok, can provide his own key using MOKmanager. Easier just to turn UEFI Secure Boot off, or change from "Windows" to "Other".

This machine has nothing else on it.  Fortunately, it is not used a great deal so not causing me pain, just a lot of wasted time and frustration.  Anyway.  tried CSM on and off, Security on and off, and UEFI on and also both and none have worked.  A clean install, bar the directories with docs in and it still does not install.

I have shared screen images of the options, if you want to take a gander and make suggestions, please feel free.  At the moment security is off and CMS...

Personally, I am at a complete loss.  Tomorrow marks day 7!

---

### Post by oldfred on 2021-02-08
If you did a new install with UEFI on, CSM off and booted Ubuntu live installer in UEFI boot mode, and it does not work, post a new link to a Summary Report from Boot-Repair.
What video card/chip?

Or because you were originally BIOS/MBR, it may be better just to revert to that. Then you have to have UEFI off, CSM on and boot installer in CSM/Legacy/BIOS boot mode.

---

### Post by Jonners59 on 2021-02-09
> **oldfred said:**
> If you did a new install with UEFI on, CSM off and booted Ubuntu live installer in UEFI boot mode, and it does not work, post a new link to a Summary Report from Boot-Repair

If CSM is off, then I get no options for the bootloader.  I can not choose whether legacy or UIEF.  See below images.  As you can see the options are below the CSM and disappear.  This I have done as per below.  The install said that it failed with a GRUB error, unable to install and no further information, and the Boot-Repair error was that the options to confirm removing GRUB for reinstall did not appear and so it wouldn't progress as it kept saying GRUB was still installed.  It was some of the attempts to do the other installs via cmd that gave the message that directories were full so no room for config file.  On rebooting the BIOS failure message was that the VGA was incompatible with the BIOS setting using UEFI as per screenshots.


> **oldfred said:**
> What video card/chip?
NVIDIA, but can't recall.  I should get the new one today, ASUS TUF Nvidia GeForce GTX 1650, just hope no major jigging to get it fitted.  Seems no point looking at the old one now.


> **oldfred said:**
> 
Or because you were originally BIOS/MBR, it may be better just to revert  to that. Then you have to have UEFI off, CSM on and boot installer in  CSM/Legacy/BIOS boot mode.

Well, the thing is that is how I started.  I changed nothing when I updated, but it failed.  After that everything was tried over and over.  I think at this stage should see what the new card has to offer.  I have just checked my main PC and it is running Legacy.  I hope I don't have all this hassle on that one too, later on, if I need to rebuild.  What a pain.  Would have thought by now that installs would be straight forward.

---

### Post by oldfred on 2021-02-09
Did you say what model motherboard this is?

I have not done an upgrade since 2009. Before that every upgrade was a huge hassle.
Now I do a new install into a 30GB / (root) partition. I have all data in separate data partition(s). 
And I still have multiple old installs that still work. I only use LTS versions as main working install, but regularly install the interim releases, just to see what is different & coming up on next LTS.

I think your issue started with using the now 30 year old BIOS/MBR configuration with your system. I started converting to the better gpt partitioning in 2010, and then had first UEFI build in 2014. 
Then now trying to use UEFI when you originally had BIOS/MBR. Not sure why update failed, usually issue is system is not fully updated and you have proprietary drivers. You have to uninstall proprietary drivers & then reinstall after update.

---

### Post by Jonners59 on 2021-02-09
> **oldfred said:**
> Did you say what model motherboard this is?
No, hadn't got that far.  But new board arrived and installed so got the old out.  It was a GXT 430.  The new is in but still the same issues.
I tried with CSM - off
paste.ubuntu.com/p/mp2qQRK46C/

Now trying with it on and looking at the various boot options.
I am getting beyond fedup and may just delete the whole HD sda and start over.  Will be extremely p155ed off though as will lose so much, films and pics and videos.  This shouldn't be so difficult.

Not sure what to make of Storage and PCIe.  I assume PCIe will be video board and another...  and Storage would be Live Boot CD and also HDDs, etc.  Not 100% sure.

> **oldfred said:**
> 
I have not done an upgrade since 2009. Before that every upgrade was a huge hassle.
Now I do a new install into a 30GB / (root) partition. I have all data in separate data partition(s). 
And I still have multiple old installs that still work. I only use LTS  versions as main working install, but regularly install the interim releases, just to see what is different & coming up on next LTS.
Lucky you.  When you do the separate data partition, I assume just like my Documents partition and also when I used to have a separate Home partition (which you introduced me to and showed me how), I assume a new build does not recognise them and so the build needs repointing after as in fstab and mount points, etc.  Always was disappointed in that...  Would have thought by now it would have been in the build to look for existing partitions.

> **oldfred said:**
> 
I think your issue started with using the now 30 year old BIOS/MBR  configuration with your system. I started converting to the better gpt  partitioning in 2010, and then had first UEFI build in 2014. 
Then now trying to use UEFI when you originally had BIOS/MBR. Not sure  why update failed, usually issue is system is not fully updated and you  have proprietary drivers. You have to uninstall proprietary drivers  & then reinstall after update.

No idea, but given I have done a fresh build after wiping the / and UEFI partitions, I am not sure how.  As above I am staggered that after all these years that we get this on such a basic aspect.  Whether legacy (30 years old) or UEFI (15 years old) or something newer, they are all standard.

In the meantime all my other chores, stuff also that went wrong and needs fixing, the kids, inc their home tutoring and the SWMBO are getting ignored.

---

### Post by oldfred on 2021-02-09
New board will be UEFI, but have CSM. 
CSM is now being obsoleted, starting this year. Some vendors already announced no more CSM/BIOS mode.
[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)

Do you not have backup? 
That is one thing we always are suggesting. 

If new motherboard in UEFI mode, you have to add a new entry into motherboard's UEFI to have it know where to boot.
You can use efibootmgr, but most just reinstall grub in UEFI mode from live installer or use Boot-Repair.
If nVidia, you may need nomodeset.

I would suggest also converting to gpt, it can be done without data loss, but backup still required just in case.
And using gparted to make a drive gpt erases it, you have to use gdisk to convert it.

Bit surprised you are doing new motherboard & video card, but not new drives. Adding an SSD in 2011 was one of the best things I did. It was very small as then expensive, so just a 60GB for booting.

I typically do new drive with every new build and often replace main working drive inbetween new builds.
Just do not trust drives as they have failed. And I have multiple back ups. Old drives become backup drives, so used less, but many still functional (for now).

Another user who started upgrade and now needed backup.
[https://ubuntuforums.org/showthread.php?t=2457692&p=14019693#post14019693](https://ubuntuforums.org/showthread.php?t=2457692&p=14019693#post14019693)

---

### Post by Jonners59 on 2021-02-09
> **oldfred said:**
> New board will be UEFI, but have CSM. 
CSM is now being obsoleted, starting this year. Some vendors already announced no more CSM/BIOS mode.
[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)

Do you not have backup? 
That is one thing we always are suggesting. 

If new motherboard in UEFI mode, you have to add a new entry into motherboard's UEFI to have it know where to boot.
You can use efibootmgr, but most just reinstall grub in UEFI mode from live installer or use Boot-Repair.
If nVidia, you may need nomodeset.

I would suggest also converting to gpt, it can be done without data loss, but backup still required just in case.
And using gparted to make a drive gpt erases it, you have to use gdisk to convert it.

Bit surprised you are doing new motherboard & video card, but not new drives. Adding an SSD in 2011 was one of the best things I did. It was very small as then expensive, so just a 60GB for booting.

I typically do new drive with every new build and often replace main working drive inbetween new builds.
Just do not trust drives as they have failed. And I have multiple back ups. Old drives become backup drives, so used less, but many still functional (for now).

Another user who started upgrade and now needed backup.
[https://ubuntuforums.org/showthread.php?t=2457692&p=14019693#post14019693](https://ubuntuforums.org/showthread.php?t=2457692&p=14019693#post14019693)

 No, only video board.  The HDDs and motherboard, etc were installed, I think 2014ish.

I have been in a conf call and come down with a to hell with it....  I have just booted into Live CD and used gParted -> Device -> Create new partition -> Select new partition table = gpt.  THAT deleted the whole HDD.

Now installing the 20.10 and as there are many reported bugs with 'install 3rd party software', so I have not ticked that...  Now just waiting to see if GRUB fails yet again.  Oh and BIOS has fast boot, security turned off CSM on and UEFI on

---

### Post by Jonners59 on 2021-02-09
OK.  That worked, BUT I have to start from scratch and I do not know if it was the gpt, the wiped HDD which came with the change to gpt, or the not include 3rd party SW...

So a new issue, besides setting up again...  The mouse and keyboard suddenly become unresponsive...

---

### Post by oldfred on 2021-02-09
Motherboard my have setting for USB. Full USB support or just a USB keyboard & mouse enable type setting.
Or you may need some boot parameter in grub.

What motherboard?

---

### Post by Jonners59 on 2021-02-09
Maybe.  I was wondering if something was going on in the background or it does not like the mouse and keyboard for some reason....

Because you said "If new motherboard in UEFI mode," so wondered if I had changed both mother and video...  That's all.  Anyway, at the moment this is frustrating.  I can't do anything with it, so going to just leave it on for a tad incase it is settling down and address tomorrow.

PS:  Is it best to use the X-org or nvidia driver?

DON'T BELIEVE THIS!!!!!!!!!  Just rebooted and now I just get "system bootorder missing  loading default"
I then get the login page
Add my pw
and then get a purple screen.  Been into BIOS and there are about 6 entries, one being the CD/DVD drive which just gives the old error message, but the others all do as above, error message and  purple screen after login

---

### Post by oldfred on 2021-02-09
If you have nVidia, you need nomodeset to boot until you install the proprietary nVidia driver.
Now it offers to install correct driver as part of install, but if you did not, you use the old way of nomodeset.
You also may be able to boot recovery mode & install nVidia from terminal. With nomodeset you should get gui and then can use system settings & drivers tab to choose recommended nVidia driver. Do not install from nvidia directly.

Run a new copy of the Boot-Repair report adn post link. Do not run any fixes, just report. Be sure to boot installer in UEFI mode.

---

### Post by Jonners59 on 2021-02-10
> **oldfred said:**
> If you have nVidia, you need nomodeset to boot until you install the proprietary nVidia driver.
Now it offers to install correct driver as part of install, but if you did not, you use the old way of nomodeset.
You also may be able to boot recovery mode & install nVidia from terminal. With nomodeset you should get gui and then can use system settings & drivers tab to choose recommended nVidia driver. Do not install from nvidia directly.

Run a new copy of the Boot-Repair report adn post link. Do not run any fixes, just report. Be sure to boot installer in UEFI mode.

Cheers.  TBH I somehow managed to get it working again late last night.  I plan to spend about an hour or so tonight on it.  I live in fear of touching anything.  There are loads of boot options.  Some work and some don't.  All created as part of the install.

So.  Now it is up, what readings should I look for to give some background.  Just run a boot repair log?  Also, would it help to check how the BIOS is set up?  Perhaps run these? ```
[FONT=arial]ubuntu@ubuntu:~/Desktop$ [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"[/FONT]
```
```
[FONT=arial][ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"[/FONT]
```

[FONT=arial]
Also interested in partitioning and backups.  If I need to rebuild again, I do not want to lose my docs and pics etc and also I would like to keep all the apps and settings and desktop layout, etc, and not have to go through all that rebuilding every time.  be interested in your views on new partitions and how.

[/FONT]

---

### Post by oldfred on 2021-02-10
As part of my documentation I run a script that runs a variety of the commands that show hardware, Internet, settings, etc. I also run bootinfoscript which was part of Boot-Repair's Report, but Yann rewrote & improved the bootinfoscript to include NVMe & other fixes. The bootinfoscript can be run from terminal where Boot-Repair requires a gui. I do also typically run the report from Boot-Repair.

I have a simple desktop, but am a snowbird and spend most of my time in Florida, but summers in Illinois. So I have two systems and copy everything including configurations in /home to flash drive, (now SSD) and then also have rsync copy to another drive on each system.  And typically several flash drives with older copies, so if I delete something I should not have, I can probably go back an get it. So I have multiple copies but not totally organized. I would not pass audit by TheFu on my backup procedures. 

I started with simple rsync to second drive, then added more documention of system, and exclusion of files not needed. Then similar rsync to flash drives and other external drives. And sneaker-net with flash drive to my other system. One system still has DVD, so photos of grandkids & critical data is also copied yearly to DVD.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) & 
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)
[https://stackoverflow.com/questions/8270519/rsync-exclude-a-directory-but-include-a-subdirectory/37219769#37219769](https://stackoverflow.com/questions/8270519/rsync-exclude-a-directory-but-include-a-subdirectory/37219769#37219769)

Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[https://ubuntuforums.org/showthread.php?t=2368992&](https://ubuntuforums.org/showthread.php?t=2368992&) 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
[https://ubuntuforums.org/showthread.php?t=2311501](https://ubuntuforums.org/showthread.php?t=2311501)
[https://ubuntuforums.org/showthread.php?t=2419993](https://ubuntuforums.org/showthread.php?t=2419993)

---

### Post by Jonners59 on 2021-02-12
> **oldfred said:**
> As part of my documentation I run a script that runs a variety of the commands that show hardware, Internet, settings, etc. I also run bootinfoscript which was part of Boot-Repair's Report, but Yann rewrote & improved the bootinfoscript to include NVMe & other fixes. The bootinfoscript can be run from terminal where Boot-Repair requires a gui. I do also typically run the report from Boot-Repair.

I have a simple desktop, but am a snowbird and spend most of my time in Florida, but summers in Illinois. So I have two systems and copy everything including configurations in /home to flash drive, (now SSD) and then also have rsync copy to another drive on each system.  And typically several flash drives with older copies, so if I delete something I should not have, I can probably go back an get it. So I have multiple copies but not totally organized. I would not pass audit by TheFu on my backup procedures. 

I started with simple rsync to second drive, then added more documention of system, and exclusion of files not needed. Then similar rsync to flash drives and other external drives. And sneaker-net with flash drive to my other system. One system still has DVD, so photos of grandkids & critical data is also copied yearly to DVD.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) & 
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)
[https://stackoverflow.com/questions/8270519/rsync-exclude-a-directory-but-include-a-subdirectory/37219769#37219769](https://stackoverflow.com/questions/8270519/rsync-exclude-a-directory-but-include-a-subdirectory/37219769#37219769)

Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[https://ubuntuforums.org/showthread.php?t=2368992&](https://ubuntuforums.org/showthread.php?t=2368992&) 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
[https://ubuntuforums.org/showthread.php?t=2311501](https://ubuntuforums.org/showthread.php?t=2311501)
[https://ubuntuforums.org/showthread.php?t=2419993](https://ubuntuforums.org/showthread.php?t=2419993)

I am going to have to get my head around this.

I have the PC all but set up now, but before I crack on I would like to ask a few questions:
1. The resolution is set correctly, but I note that the actual desktop goes off-screen and moves in the background.  I do not want to drop the resolution (not sure if that will fix things anyway) as that would defeat the object of the exercise a 4k Tv/Monitor, with 4K graphics card....  Why drop the source down to just 2k.  So how do I fix this annoyance?

2. I built the OS straight out of the box and did NOT do any partitions.  I will reduce the size of the partition, but what partitions do you recommend and what size?  I know you like to separate out /home, and of course, there is Documents..  What else?

3.  I can not access anything (other PCs) on the LAN.  No idea why.

---

### Post by yancek on 2021-02-12
>  what partitions do you recommend and what size?  I know you like to  separate out /home, and of course, there is Documents..  What else?

20-30GB should be enough for / (root filesystem) but that all depends upon how much new software you install.  Thee /home partition will contain most user data so is generally a larger partition.  How much you use depends upon what else you have (a second OS) and the size of the drive.  Documents is in the /home directory/partition.  Some users create a separate data partition.

---

### Post by oldfred on 2021-02-12
Partitioning is very user based. We all have opionins but how much data you have and where you may want to store it determines your need.
I find my optimal partitioning, is not so good three years later when I typically get a new drive for main working install. I also like to have multiple installs, so have many 30GB partitions.
With my new larger NVMe drive I moved my data partition from sda to NVMe. Now sda is mostly backups and other installs.

This is my working partitions, excluding the system files that df also shows.
```
fred@z170-focal-k:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p3   29G  8.4G   19G  31% /
/dev/nvme0n1p5  192G  136G   47G  75% /mnt/data
/dev/nvme0n1p1  511M   12M  500M   3% /boot/efi
```

I do not have my other / & backup partitions mounted, so not shown. And I have not fully allocated either NVMe nor sda drives. They still have about 20% as unallocated.
I do totally uninstall all snaps which now are larger versions of applications as each includes all its dependencies. I prefer standard apps.
I also move some larger hidden folders normally in /home into my data partition like Firefox & Thunderbird profiles.  Then I keep /home inside / as it is tiny with only the hidden user configuration data files.

```
[FONT=monospace][FONT=arial][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo du -hx --max-depth=1 / 2> /dev/null [/COLOR]
[sudo] password for fred:  
104K    /mnt 
8.0K    /media 
561M    /var 
4.0K    /opt 
4.0K    /srv 
1.1M    /root 
6.1G    /usr 
16K     /lost+found 
233M    /home 
9.2M    /etc 
196M    /boot 
4.0K    /cdrom 
8.4G    /
[/FONT]
[/FONT]
```

---

### Post by Jonners59 on 2021-02-14
> **oldfred said:**
> Oldfred [FONT=monospace][FONT=arial][/FONT][/FONT], > **yancek said:**
> Yancek
Gentlemen, thank you for your replies and apologies for my tardy response.  Everything is falling down around me with about 7 projects to fix things that failed/broke in the past 3 weeks, and only 2 so far completed.  They refuse to work, this being one of them.  No sooner had I sent out my last message than the PC stopped working again.  This time I couldn't load even the recovery or the LiveCD.  Same issue, something to do with booting.  I did a few times get into an odd-looking GRUB I'd never seen before, and that then would lead to another I'd never seen before and would in all instances fail on booting whatever I selected, and trust me, I have tried EVERY combination...  I have only now, just managed to boot into a LiveCD (well, memory stick with the latest iso) and that has just installed with, the old GRUB install error message...  However, I am back in again.  I will need to start setting things up again though...  This will take a tad of time.

Just in case there was something on the 2nd HD I have also takemn the time to wipe that too.  So I installed:
sda:
1 = efi 1Gb
2 = / 50Gb
3 = SWAP = 32Gb to match RAM
Extn
5 = Home = the rest of the drive c910Gb

sdb:
1 = Multi Media files 900Gb (Tv, Films, Videos, Music, etc)
2 = Backup, & Copies 200Gb (somewhere to keep backups, copies of important config files and applications downloaded, etc...

All will need mount points.  Some like Multi Media, Backup, shall be in Documents, in Home.
  I hope this is the last of this....

> **yancek said:**
> 20-30GB should be enough for / (root filesystem)  but that all depends upon how much new software you install.  Thee /home  partition will contain most user data so is generally a larger  partition.  How much you use depends upon what else you have (a second  OS) and the size of the drive.  Documents is in the /home  directory/partition.  Some users create a separate data  partition.

Thank you Yancek, yes, understand.  I have done this many times before but TBH with what happens when things go wrong, I started to see no point.  The repairs and new installs do not see or recognise the directories, which is silly after all this time, and even if selected in a custom repair or install, just wipes them clean.  So all the hard work becomes futile.  Hence my query to OldFred



> **oldfred said:**
> Partitioning is very user based. We all have opionins but how much data you have and where you may want to store it determines your need.
I find my optimal partitioning, is not so good three years later when I typically get a new drive for main working install. I also like to have multiple installs, so have many 30GB partitions.
With my new larger NVMe drive I moved my data partition from sda to NVMe. Now sda is mostly backups and other installs.

This is my working partitions, excluding the system files that df also shows.
```
fred@z170-focal-k:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p3   29G  8.4G   19G  31% /
/dev/nvme0n1p5  192G  136G   47G  75% /mnt/data
/dev/nvme0n1p1  511M   12M  500M   3% /boot/efi
```

I do not have my other / & backup partitions mounted, so not shown. And I have not fully allocated either NVMe nor sda drives. They still have about 20% as unallocated.
I do totally uninstall all snaps which now are larger versions of applications as each includes all its dependencies. I prefer standard apps.
I also move some larger hidden folders normally in /home into my data partition like Firefox & Thunderbird profiles.  Then I keep /home inside / as it is tiny with only the hidden user configuration data files.

```
[FONT=monospace][FONT=arial][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo du -hx --max-depth=1 / 2> /dev/null [/COLOR]
[sudo] password for fred:  
104K    /mnt 
8.0K    /media 
561M    /var 
4.0K    /opt 
4.0K    /srv 
1.1M    /root 
6.1G    /usr 
16K     /lost+found 
233M    /home 
9.2M    /etc 
196M    /boot 
4.0K    /cdrom 
8.4G    /
[/FONT]
[/FONT]
```

Interesting.  Not sure how some of those work.  My real concern and interest is, naturally to preserve all my docs, etc after a repair or fresh install as well as a HW failure, but also the settings, configurations and layouts of the machine as well as the apps, and assume that also means the repositories.

---

### Post by Jonners59 on 2021-02-15
> **oldfred said:**
> Partitioning is very user based. We all have opionins but how much data you have and where you may want to store it determines your need.

OK, As of late last night I now have a working PC.  I know there will be a few more apps and settings to add, but, it is now there.  Can not believe how painful that was.

Next.  I am not turning it on until the next step, which is your advise on backing up.  Things important to me are the desktop layout, panels etc, the booting to mount points of partitions (fstab), repositories and even more so the actual apps and their settings.  Sharing, whether access on the LAN or sharing things.  Access to the directories (I sometimes find I have no read-write access, especially write to some mounted partitions), and of course any data, which I can store on another machine with IP ending 50.

```
$ df -h
df: /run/user/1000/doc: Operation not permitted
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           3.2G  4.0M  3.2G   1% /run
/dev/sda2        51G   26G   23G  53% /
tmpfs            16G     0   16G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           4.0M     0  4.0M   0% /sys/fs/cgroup
/dev/sdb2       192G  339M  182G   1% /media/Administration
/dev/sdb1       724G  280M  687G   1% /media/MultiMedia
/dev/sda4       834G   23G  769G   3% /home
/dev/sda1       511M   12M  500M   3% /boot/efi
tmpfs           3.2G  156K  3.2G   1% /run/user/1000

```

```
 sudo du -hx --max-depth=1 / 2> /dev/null

4.5G    /var
16K    /lost+found
144K    /tmp
4.0K    /mnt
178M    /boot
30M    /etc
12K    /srv
68K    /snap
189M    /opt
12K    /media
4.0K    /cdrom
21G    /usr
7.7M    /root
26G    /

```

For this, I would like some help, please.

---

### Post by oldfred on 2021-02-15
Go back & review post #43, If then there is something you do not understand, may be better to start new post with backup in title.
I do not backup system nor /etc as some suggest. I only edit a few files in /etc and copy those into /home, so they are backed up.

---

### Post by Jonners59 on 2021-02-15
> **oldfred said:**
> Go back & review post #43, If then there is something you do not understand, may be better to start new post with backup in title.
I do not backup system nor /etc as some suggest. I only edit a few files in /etc and copy those into /home, so they are backed up.
Cheers, probably right.

I have another problem that has materialised so will start a new one for that too;. The app stores do not install apps and thumbnails don't show and in synaptic it keeps telling me that install didn't fully work as problem with snap.

---

### Post by oldfred on 2021-02-15
First thing I do is uninstall all snaps.
I do not use Software Center as it tends to install snaps.
I only use terminal or synaptic and even then for example the install of Chromium is a .deb that installs a snap. Or I stopped having that as an optional Web Browser.

---

### Post by Jonners59 on 2021-02-16
> **oldfred said:**
> Go back & review post #43, If then there is something you do not understand, may be better to start new post with backup in title.
I do not backup system nor /etc as some suggest. I only edit a few files in /etc and copy those into /home, so they are backed up.

Yup too much to absorb.  I shall open a new Query.  ANd that snap thing is annoying.  It gives errors no matter how I install apps - synaptic or apt-get install.  I'm also having a problem in that it can not open any directories on the LAN.  Tried everything.  So frustrating.

ANyway.  I shall close this as solved but can not say I really know why or how, so not much use to me or others in the future should they get the same problems.  I am not sure WHY booting up should be such problem, at the end of the day there are only a half dozen types and all standard and all been around for long enough to make this a simple task.  Looking at my other machines I am concerned if they should ever need to be rebuilt.

So nutshell was no fast boot, no secure boot, CSM on and ideally force UEFI, turn of install 3rd party SW and just keep your fingers crossed!

---

### Post by CelticWarrior on 2021-02-16
No.

In a nutshell, UEFI mode only (no CSM), no Secure Boot or Fast Boot, install 3rd party drivers, codecs, firmware, etc. (or install the requirewd proprietary drivers after) which is exactly the same as saying "the usual", end of story.

---

### Post by Jonners59 on 2021-02-16
Can't have UEFI only with no CSM.  CSM has to be turned on for UEFI to be shown.
3rd party, defiantly no.  There is a known bug and I certainly could not install anything if selected in this 20:10 install on the PC.  In the past, yes, but not in this build.  Comes up with a GRUP failure and sends out a bug report, and when checking it is well known...  So yes, AFTER the install is completed.

---

### Post by oldfred on 2021-02-16
My motherboard is also backwards. 
CSM should be under UEFI, but it has UEFI settings under CSM. But I still have to then set to UEFI only under the CSM sub menu.

Its almost 10 years since UEFI started for PC, even longer for Mac.
So now they are starting to eliminate CSM, which is called UEFI class 3 system.
[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)
Intel is planning to end "legacy BIOS" support in their new platforms by 2020 in requiring UEFI Class 3 or higher.
[http://www.uefi.org/sites/default/files/resources/Brian_Richardson_Intel_Final.pdf](http://www.uefi.org/sites/default/files/resources/Brian_Richardson_Intel_Final.pdf)

---

### Post by Jonners59 on 2021-02-16
Glad I'm not the only one.  Will this cause a problem for those of us with a slightly older board?

---

### Post by oldfred on 2021-02-16
Older motherboards will not change to class 3.
You should update UEFI to latest available for security issues, but after a few years updates stop being available. Vendors are perfectly happy to sell you a new motherboard to get all the latest bells & whistles and perhaps security issues. If it still works, keep using it.

---

### Post by dragonfly41 on 2021-02-16
When these UEFI boot threads spring up frequently it is like groundhog day.
I am drawn to the conclusion that some form of helper (smart) script should be written to guide users through this obstacle course rather than repeating links.
One such container could be **Albert** with a python extension. It is quite a handy tool and for a start all the links could be listed in a bookmarks file. If Albert is installed there are examples in the Python Extensions section.
Just an idea.

---

### Post by Jonners59 on 2021-02-16
> **dragonfly41 said:**
> When these UEFI boot threads spring up frequently it is like groundhog day.
I am drawn to the conclusion that some form of helper (smart) script should be written to guide users through this obstacle course rather than repeating links.
One such container could be **Albert** with a python extension. It is quite a handy tool and for a start all the links could be listed in a bookmarks file. If Albert is installed there are examples in the Python Extensions section.
Just an idea.

Hello, been a long time.  Yes, can't agree more.  Bad enough for those who understand this stuff, but for us mere mortal folk it's impossible.  I got there in the end, after 3 weeks of trying everything, all day and into the evening.  Shouldn't be this tough, esp as not even dual boot or nasty windows OS...   I had to clean wipe both drives before I could get it to work.

---

