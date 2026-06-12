---
title: "problem with dual boot - boot menu disappeared"
date: 2022-10-18
forum: General Help
---

### Post by mark.n.berman on 2022-10-18
Hello,

I have a problem with my dual boot machine, on which I first installed Windows and then installed Ubuntu 22.04. I had been running both operating systems for several months without a problem. My version of Windows has Bitlocker and I am unable to disable this due to restrictions imposed by my institution. 

Recently, I got locked out of the usual bootup menu - now my machine boots up directly into Windows, even if I try to enter the bios (the button on my machine for this, F2, is ineffective). I discovered that I can access the bootup menu by pressing F12 at startup, but this is annoying. I tried running boot-repair from Ubuntu itself (not from Ubuntu live) but I did not obtain an option to repair the boot. Please see below the log report. 

I would be grateful if someone could help me to fix the issue, so that I can once again get the bootup menu automatically on startup. 

Best wishes
Mark

_____________________

boot-repair-4ppa200                                              [20221018_1324]


============================== Boot Info Summary ===============================


 => No boot loader is installed in the MBR of /dev/nvme0n1.


nvme0n1p1: _____________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi


nvme0n1p2: _____________________________________________________________________


    File system:       BitLocker
    Boot sector type:  Unknown
    Boot sector info: 


nvme0n1p3: _____________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub




================================ 1 OS detected =================================


OS#1:   The OS now in use - Ubuntu 22.04.1 LTS CurrentSession on nvme0n1p3


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: TigerLake-LP GT2 [Iris Xe Graphics] from Intel Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-5.15.0-48-generic root=UUID=3d797a19-b37e-4d9c-82bf-7d7be22be137 ro quiet splash vt.handoff=7
df -Th / : /dev/nvme0n1p3 ext4  252G   42G  198G  18% /


===================================== UEFI =====================================


BIOS/UEFI firmware: FNCN30WW(V2.00)(1.30) from LENOVO
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
SecureBoot disabled - SecureBoot disabled - Please report this message to [email]boot.repair@gmail.com[/email].
BootCurrent: 0003
Timeout: 2 seconds
BootOrder: 0004,0003,2001,2002,2003
Boot0000* EFI PXE 0 for IPv4 (08-92-04-BC-85-56) 	PciRoot(0x0)/Pci(0xd,0x0)/USB(2,0)/USB(5,0)/MAC(089204bc8556,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0001* EFI PXE 0 for IPv6 (08-92-04-BC-85-56) 	PciRoot(0x0)/Pci(0xd,0x0)/USB(2,0)/USB(5,0)/MAC(089204bc8556,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0003* ubuntu	HD(1,GPT,7c56bd11-c5d6-4b00-9eb9-f80148632ee2,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0004* Windows Boot Manager	HD(1,GPT,7c56bd11-c5d6-4b00-9eb9-f80148632ee2,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...o................
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC


728124f6ec8e22fbdbe7034812c81b95   nvme0n1p1/Boot/bootx64.efi
c152ec201c37b6e97bbc2207e49d1271   nvme0n1p1/Boot/fbx64.efi
fdafb5eece6caeccb788c946a28e6872   nvme0n1p1/Boot/mmx64.efi
f62c28d9b477b6a1a7b1c991b2b6637d   nvme0n1p1/ubuntu/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   nvme0n1p1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   nvme0n1p1/ubuntu/shimx64.efi
72293f4ecf0f5b24dce601d2c3c4b26e   nvme0n1p1/Microsoft/Boot/bootmgfw.efi
75641ea3cae97c7ea935e501d6e5e227   nvme0n1p1/Microsoft/Boot/bootmgr.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


nvme0n1	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	no-wind,	2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


nvme0n1p3	: is-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
nvme0n1p1	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
nvme0n1p2	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios


Partitions info (2/3): _________________________________________________________


nvme0n1p3	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
nvme0n1p1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
nvme0n1p2	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot


Partitions info (3/3): _________________________________________________________


nvme0n1p3	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1
nvme0n1p1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1
nvme0n1p2	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1


fdisk -l (filtered): ___________________________________________________________


Disk nvme0n1: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: DF1A4C09-D854-42B8-B2CC-FCA54D915E4E
              Start        End   Sectors   Size Type
nvme0n1p1      2048     206847    204800   100M EFI System
nvme0n1p2    206848  461590527 461383680   220G Microsoft basic data
nvme0n1p3 461590528 1000214527 538624000 256.8G Linux filesystem


parted -lm (filtered): _________________________________________________________


nvme0n1:512GB:nvme:512:512:gpt:SAMSUNG MZALQ512HALU-000L2:;
1:1049kB:106MB:105MB:fat32::boot, esp;
2:106MB:236GB:236GB:::msftdata;
3:236GB:512GB:276GB:ext4::;


blkid (filtered): ______________________________________________________________


NAME        FSTYPE    UUID                                 PARTUUID                             LABEL PARTLABEL
nvme0n1                                                                                               
&#9500;&#9472;nvme0n1p1 vfat      BC5A-9C72                            7c56bd11-c5d6-4b00-9eb9-f80148632ee2       
&#9500;&#9472;nvme0n1p2 BitLocker                                      8a99f7e1-4b40-4cb3-92cb-b9cd86ba2a92       
&#9492;&#9472;nvme0n1p3 ext4      3d797a19-b37e-4d9c-82bf-7d7be22be137 42cd9b6f-3f1e-4b3c-9791-269227d30ae0       


Mount points (filtered): _______________________________________________________


                                     Avail Use% Mounted on
/dev/nvme0n1p1                       49.4M  49% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p3                      197.2G  17% /
/dev/nvme0n1p3[/usr/share/hunspell] 197.2G  17% /var/snap/firefox/common/host-hunspell


Mount options (filtered): ______________________________________________________


/dev/nvme0n1p1                      vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/nvme0n1p3                      ext4            rw,relatime,errors=remount-ro
/dev/nvme0n1p3[/usr/share/hunspell] ext4            ro,noexec,noatime,errors=remount-ro


=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================


search.fs_uuid 3d797a19-b37e-4d9c-82bf-7d7be22be137 root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


=================== nvme0n1p3/boot/grub/grub.cfg (filtered) ====================


Ubuntu   3d797a19-b37e-4d9c-82bf-7d7be22be137
Ubuntu, with Linux 5.15.0-48-generic   3d797a19-b37e-4d9c-82bf-7d7be22be137
Ubuntu, with Linux 5.15.0-47-generic   3d797a19-b37e-4d9c-82bf-7d7be22be137
Windows Boot Manager (on nvme0n1p1)   osprober-efi-BC5A-9C72
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###


======================== nvme0n1p3/etc/fstab (filtered) ========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p3 during installation
UUID=3d797a19-b37e-4d9c-82bf-7d7be22be137 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=BC5A-9C72  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0


==================== nvme0n1p3/etc/default/grub (filtered) =====================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


================= nvme0n1p3: Location of files loaded by Grub ==================


           GiB - GB             File                                 Fragment(s)
 407.362754822 = 437.402427392  boot/grub/grub.cfg                             1
 253.614250183 = 272.316227584  boot/vmlinuz                                   1
 237.228511810 = 254.722174976  boot/vmlinuz-5.15.0-47-generic                 2
 253.614250183 = 272.316227584  boot/vmlinuz-5.15.0-48-generic                 1
 237.228511810 = 254.722174976  boot/vmlinuz.old                               2
 385.599983215 = 414.034829312  boot/initrd.img                                1
 388.670291901 = 417.331548160  boot/initrd.img-5.15.0-47-generic              1
 385.599983215 = 414.034829312  boot/initrd.img-5.15.0-48-generic              1
 388.670291901 = 417.331548160  boot/initrd.img.old                            1


=================== nvme0n1p3: ls -l /etc/grub.d/ (filtered) ===================


-rwxr-xr-x 1 root root 18683 Apr 16  2022 10_linux
-rwxr-xr-x 1 root root 43031 Apr 16  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14180 Apr 16  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Apr 16  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Apr 16  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 19  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Apr 16  2022 40_custom
-rwxr-xr-x 1 root root   215 Apr 16  2022 41_custom


======================== nvme0n1p3/etc/grub.d/35_fwupd =========================


#! /bin/sh
# SPDX-License-Identifier: LGPL-2.1+
set -e
[ -d ${pkgdatadir:?} ]
# shellcheck source=/dev/null
. "$pkgdatadir/grub-mkconfig_lib"
if [ -f /var/lib/fwupd/uefi_capsule.conf ] &&
   ls /sys/firmware/efi/efivars/fwupd-*-0abba7dc-e516-4167-bbf5-4d9d1c739416 1>/dev/null 2>&1; then
      . /var/lib/fwupd/uefi_capsule.conf
      if [ "${EFI_PATH}" != "" ] && [ "${ESP}" != "" ]; then
      echo "Adding Linux Firmware Updater entry" >&2
cat << EOF
menuentry 'Linux Firmware Updater' \$menuentry_id_option 'fwupd' {
EOF
      ${grub_probe:?}
      prepare_grub_to_access_device '`${grub_probe} --target=device \${ESP}` | sed -e "s/^/\t/"'
cat << EOF
	chainloader ${EFI_PATH}
}
EOF
      fi
fi


======================== Unknown MBRs/Boot Sectors/etc =========================


Unknown BootLoader on nvme0n1p2


00000000  eb 58 90 2d 46 56 45 2d  46 53 2d 00 02 08 00 00  |.X.-FVE-FS-.....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 03 00  |........?....(..|
00000020  00 00 00 00 e0 1f 00 00  00 00 00 00 00 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 00 00 00 00 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  a0 fb 7d b4 7d 8b f0 ac  |{......|..}.}...|
00000070  98 40 74 0c 48 74 0e b4  0e bb 07 00 cd 10 eb ef  |.@t.Ht..........|
00000080  a0 fd 7d eb e6 cd 16 cd  19 00 00 00 00 00 00 00  |..}.............|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  3b d6 67 49 29 2e d8 4a  83 99 f6 a3 39 e3 d0 01  |;.gI)..J....9...|
000000b0  00 d0 11 04 00 00 00 00  00 c0 77 48 00 00 00 00  |..........wH....|
000000c0  00 00 d1 87 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  0d 0a 52 65 6d 6f 76 65  20 64 69 73 6b 73 20 6f  |..Remove disks o|
00000110  72 20 6f 74 68 65 72 20  6d 65 64 69 61 2e ff 0d  |r other media...|
00000120  0a 44 69 73 6b 20 65 72  72 6f 72 ff 0d 0a 50 72  |.Disk error...Pr|
00000130  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 72  |ess any key to r|
00000140  65 73 74 61 72 74 0d 0a  00 00 00 00 00 00 00 00  |estart..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000190  00 00 00 00 00 00 00 00  78 78 78 78 78 78 78 78  |........xxxxxxxx|
000001a0  78 78 78 78 78 78 78 78  78 78 78 78 78 78 78 78  |xxxxxxxxxxxxxxxx|
*
000001e0  78 78 78 78 78 78 78 78  ff ff ff ff ff ff ff ff  |xxxxxxxx........|
000001f0  ff ff ff ff ff ff ff ff  ff ff ff 00 1f 2c 55 aa  |.............,U.|
00000200








Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would not act on the boot.

---

### Post by yancek on 2022-10-18
>  My version of Windows has Bitlocker and I am unable to disable this due to restrictions imposed by my institution. 


What does that mean "my institution".  If you have been booting up until now what changed with your institution?  Was it disabled when you were successfully able to boot?  The link below purports to explain the process so you might take a look at it.

[https://itsfoss.com/dual-boot-ubuntu-windows-bitlocker/](https://itsfoss.com/dual-boot-ubuntu-windows-bitlocker/)

---

### Post by yancek on 2022-10-18
>  My version of Windows has Bitlocker and I am unable to disable this due to restrictions imposed by my institution. 


What does that mean "my institution".  If you have been  booting up until now what changed with your institution?  Was it  disabled when you were successfully able to boot?  The link below  purports to explain the process so you might take a look at it.  I have not done this so have no idea if it will work. 

[https://itsfoss.com/dual-boot-ubuntu-windows-bitlocker/](https://itsfoss.com/dual-boot-ubuntu-windows-bitlocker/)

---

### Post by tea for one on 2022-10-18
> **mark.n.berman said:**
>  My version of Windows has Bitlocker and I am unable to disable this due to restrictions imposed by my institution.
Are you the owner of this PC?
Is the PC supplied by your employer or institution?

> **mark.n.berman said:**
>  I discovered that I can access the bootup menu by pressing F12 at startup, but this is annoying.
Just continue with this - it is hardly onerous.

It's surprising that your device has [COLOR="#0000FF"]SecureBoot disabled[/COLOR], yet you do not have the authority to disable bitlocker?

If OS security is important, then you will have to have a discussion with the institution.

---

