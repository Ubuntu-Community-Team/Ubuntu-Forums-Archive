---
title: "Unable to boot into grub Single Boot Ubuntu 22.04: start_image() Device error"
date: 2024-01-16
forum: General Help
---

### Post by ankit.pgupta26 on 2024-01-16
Getting the following error on Asus K501UX-AH71 after a fresh installation of Ubuntu 22.04  


start_image() returned device error. I have already tried using the boot-repair application, didn't help below is the boot repair summary.


```

boot-repair-4ppa2075                                              [20240116_1453]


============================= Boot Repair Summary ==============================






==================== blkid (filtered) before lvm activation ====================


/dev/mapper/vgubuntu-root: UUID="2e3cf0f5-c1ac-46de-9444-73b035815609" BLOCK_SIZE="4096" TYPE="ext4"
/dev/sda1: UUID="24B3-17F1" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="493e7dae-ec4e-441a-ba47-aae666f7dd02"
/dev/sdb1: BLOCK_SIZE="2048" UUID="2023-08-08-01-19-05-00" LABEL="Ubuntu 22.04.3 LTS amd64" TYPE="iso9660" PARTLABEL="ISO9660" PARTUUID="f45e2fa1-c5a6-4d79-876e-c8245af921e0"
/dev/mapper/vgubuntu-swap_1: UUID="a5fcd603-3577-4ff6-b88d-6fb9ff677027" TYPE="swap"
/dev/sdb4: LABEL="writable" UUID="66fa44dd-ac91-4db5-9ab7-1f2059af74e1" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="c570f350-0b07-4843-93b0-05267fb860ff"
/dev/sdb2: SEC_TYPE="msdos" LABEL_FATBOOT="ESP" LABEL="ESP" UUID="F7DB-4D56" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="Appended2" PARTUUID="f45e2fa1-c5a6-4d79-876d-c8245af921e0"
/dev/sda2: UUID="lAMWbH-879l-8Qs3-1EIP-RoSN-cY9g-4ozhKc" TYPE="LVM2_member" PARTUUID="a5cc3c68-21d9-4e91-8c9b-8296569ef1e6"
/dev/sdb3: PARTLABEL="Gap1" PARTUUID="f45e2fa1-c5a6-4d79-876c-c8245af921e0"




================================ LVM activation ================================


modprobe dm-mod  
vgscan --mknodes
  Found volume group "vgubuntu" using metadata type lvm2
vgchange -ay
  2 logical volume(s) in volume group "vgubuntu" now active
lvscan
  ACTIVE            '/dev/vgubuntu/root' [<929.10 GiB] inherit
  ACTIVE            '/dev/vgubuntu/swap_1' [1.91 GiB] inherit
blkid -g








[dmraid -sa -c] no
[dmraid -sa -c] raid
[dmraid -sa -c] disks
[dmraid -sa -c] no
[dmraid -sa -c] raid
[dmraid -sa -c] disks
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.2.0-26-generic


Recommended repair: ____________________________________________________________


The default repair of the Boot-Repair utility will purge (in order to enable-lvm) and reinstall the grub-efi of
mapper/vgubuntu-root,
using the following options:  sda1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file




Mount /dev/sda1 on /mnt/boot-sav/mapper/vgubuntu-root/boot/efi
chroot /mnt/boot-sav/mapper/vgubuntu-root apt-get -y update
Running in chroot, ignoring command 'start'
Purge the GRUB of /dev/mapper/vgubuntu-root
grub-efi available


The following additional packages will be installed:
grub-efi-amd64
The following packages will be REMOVED:
grub-gfxpayload-lists grub-pc
The following NEW packages will be installed:
grub-efi grub-efi-amd64
0 upgraded, 2 newly installed, 2 to remove and 154 not upgraded.
DEBCHECK debOK, grub-efi
DEBCHECK debOK
Please type: sudo chroot "/mnt/boot-sav/mapper/vgubuntu-root" dpkg --configure -ansudo chroot "/mnt/boot-sav/mapper/vgubuntu-root" apt-get install -fynsudo chroot "/mnt/boot-sav/mapper/vgubuntu-root" apt-get install -y lvm2nsudo chroot "/mnt/boot-sav/mapper/vgubuntu-root" apt-get purge --allow-remove-essential -y grub-com*nsudo chroot "/mnt/boot-sav/mapper/vgubuntu-root" apt-get purge --allow-remove-essential -y grub2-com*nsudo chroot "/mnt/boot-sav/mapper/vgubuntu-root" apt-get purge --allow-remove-essential -y shim-signednsudo chroot "/mnt/boot-sav/mapper/vgubuntu-root" apt-get purge --allow-remove-essential -y grub-common:*nsudo chroot "/mnt/boot-sav/mapper/vgubuntu-root" apt-get purge --allow-remove-essential -y grub2-common:*n
Then type: sudo chroot "/mnt/boot-sav/mapper/vgubuntu-root" apt-get install -y grub-efi


Unhide GRUB boot menu in mapper/vgubuntu-root/etc/default/grub


============= Reinstall the grub-efi of /dev/mapper/vgubuntu-root ==============


chroot /mnt/boot-sav/mapper/vgubuntu-root grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.2
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.2.0-26-generic
chroot /mnt/boot-sav/mapper/vgubuntu-root modprobe efivars


chroot /mnt/boot-sav/mapper/vgubuntu-root efibootmgr -v before grub install
EFI variables are not supported on this system.




chroot /mnt/boot-sav/mapper/vgubuntu-root uname -r
6.2.0-26-generic


chroot /mnt/boot-sav/mapper/vgubuntu-root grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 20580: grub-install
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 20580: grub-install
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
df /dev/sda1
mv /mnt/boot-sav/mapper/vgubuntu-root/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/mapper/vgubuntu-root/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/mapper/vgubuntu-root/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/mapper/vgubuntu-root/boot/efi/EFI/Boot/bootx64.efi


chroot /mnt/boot-sav/mapper/vgubuntu-root grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 20779: grub-install
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 20779: grub-install
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.


chroot /mnt/boot-sav/mapper/vgubuntu-root efibootmgr -v after grub install
EFI variables are not supported on this system.


Warning: NVram is locked (Ubuntu not found in efibootmgr).


chroot /mnt/boot-sav/mapper/vgubuntu-root update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 20982: grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 20982: grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21034: /usr/sbin/grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21034: /usr/sbin/grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21046: /usr/sbin/grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21046: /usr/sbin/grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21058: /usr/sbin/grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21058: /usr/sbin/grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21071: /usr/sbin/grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21071: /usr/sbin/grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21133: /usr/sbin/grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21133: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-6.5.0-14-generic
Found initrd image: /boot/initrd.img-6.5.0-14-generic
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21221: /usr/sbin/grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21221: /usr/sbin/grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21233: /usr/sbin/grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21233: /usr/sbin/grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21245: /usr/sbin/grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21245: /usr/sbin/grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21257: /usr/sbin/grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21257: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-6.2.0-26-generic
Found initrd image: /boot/initrd.img-6.2.0-26-generic
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21540: /usr/sbin/grub-probe
File descriptor 63 (pipe:[57908]) leaked on vgs invocation. Parent PID 21540: /usr/sbin/grub-probe


Unhide GRUB boot menu in mapper/vgubuntu-root/boot/grub/grub.cfg


Boot successfully repaired.


Locked-NVram detected. Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.3 LTS entry (sda1/efi/ubuntu/grubx64.efi file) !




============================ Boot Info After Repair ============================


 => No boot loader is installed in the MBR of /dev/sda.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg


sda2: __________________________________________________________________________


    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 


sdb: ___________________________________________________________________________


    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sdb and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sdb: /dev/sdb already mounted or mount point busy.




================================ 1 OS detected =================================


OS#1:   Ubuntu 22.04.3 LTS on mapper/vgubuntu-root


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: Skylake GT2 [HD Graphics 520] GM107M [GeForce GTX 950M] from Intel Corporation NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.3 LTS, jammy, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: K501UX.208(5.11) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0006
Timeout: 2 seconds
BootOrder: 0005,0006,0000,0004,0001,0003
Boot0000* Windows Boot Manager	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* Windows Boot Manager	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0003* grub	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0004* Windows Boot Manager	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0005* ubuntu	HD(1,GPT,493e7dae-ec4e-441a-ba47-aae666f7dd02,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0006* UEFI: hp v220w 1100, Partition 2	PciRoot(0x0)/Pci(0x14,0x0)/USB(2,0)/HD(2,GPT,f45e2fa1-c5a6-4d79-876d-c8245af921e0,0x95f864,0x2754)..BO


a1da253696a304dce6b4668b70151c0e   sda1/BOOT/bkpbootx64.efi
a1da253696a304dce6b4668b70151c0e   sda1/BOOT/bootx64.efi
a9c517741ac31962d7feb152948ad1ee   sda1/BOOT/fbx64.efi
a660182adef313615746a665966d2ccc   sda1/BOOT/mmx64.efi
a1da253696a304dce6b4668b70151c0e   sda1/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   sda1/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   sda1/ubuntu/shimx64.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	no-wind,	2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


mapper/vgubuntu-root	: is-os,	64, apt-get,	signed grub-pc grub-efi ,	grub2,	grub-install,	grubenv-ok,	update-grub,	not-far
sda1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far


Partitions info (2/3): _________________________________________________________


mapper/vgubuntu-root	: isnotESP,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot


Partitions info (3/3): _________________________________________________________


mapper/vgubuntu-root	: not--sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sda
sda1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 40ABA3F4-2B32-4A88-B36E-7250C2EDF02C
       Start        End    Sectors  Size Type
sda1     2048    1050623    1048576  512M EFI System
sda2  1050624 1953523711 1952473088  931G Linux LVM
Disk mapper/vgubuntu-root: 929.1 GiB, 997611012096 bytes, 1948459008 sectors
Disk mapper/vgubuntu-swap_1: 1.91 GiB, 2051014656 bytes, 4005888 sectors
Disk sdb: 15.02 GiB, 16131293184 bytes, 31506432 sectors
Disk identifier: F45E2FA1-C5A6-4D79-876F-C8245AF921E0
       Start      End  Sectors  Size Type
sdb1       64  9828451  9828388  4.7G Microsoft basic data
sdb2  9828452  9838519    10068  4.9M EFI System
sdb3  9838520  9839119      600  300K Microsoft basic data
sdb4  9842688 31506368 21663681 10.3G Linux filesystem


parted -lm (filtered): _________________________________________________________


sda:1000GB:scsi:512:4096:gpt:ATA HGST HTS541010A9:;
1:1049kB:538MB:537MB:fat32::boot, esp;
2:538MB:1000GB:1000GB:::lvm;
sdb:16.1GB:scsi:512:512:gpt:hp v220w:;
1:32.8kB:5032MB:5032MB::ISO9660:hidden, msftdata;
2:5032MB:5037MB:5155kB::Appended2:boot, esp;
3:5037MB:5038MB:307kB::Gap1:hidden, msftdata;
4:5039MB:16.1GB:11.1GB:ext4::;
mapper/vgubuntu-swap_1:2051MB:dm:512:4096:loop:Linux device-mapper (linear):;
1:0.00B:2051MB:2051MB:linux-swap(v1)::;
mapper/vgubuntu-root:998GB:dm:512:4096:loop:Linux device-mapper (linear):;
1:0.00B:998GB:998GB:ext4::;


blkid (filtered): ______________________________________________________________


NAME                FSTYPE      UUID                                   PARTUUID                             LABEL                    PARTLABEL
sda                                                                                                                                  
&#9500;&#9472;sda1              vfat        24B3-17F1                              493e7dae-ec4e-441a-ba47-aae666f7dd02                          
&#9492;&#9472;sda2              LVM2_member lAMWbH-879l-8Qs3-1EIP-RoSN-cY9g-4ozhKc a5cc3c68-21d9-4e91-8c9b-8296569ef1e6                          
  &#9500;&#9472;vgubuntu-root   ext4        2e3cf0f5-c1ac-46de-9444-73b035815609                                                                 
  &#9492;&#9472;vgubuntu-swap_1 swap        a5fcd603-3577-4ff6-b88d-6fb9ff677027                                                                 
sdb                 iso9660     2023-08-08-01-19-05-00                                                      Ubuntu 22.04.3 LTS amd64 
&#9500;&#9472;sdb1              iso9660     2023-08-08-01-19-05-00                 f45e2fa1-c5a6-4d79-876e-c8245af921e0 Ubuntu 22.04.3 LTS amd64 ISO9660
&#9500;&#9472;sdb2              vfat        F7DB-4D56                              f45e2fa1-c5a6-4d79-876d-c8245af921e0 ESP                      Appended2
&#9500;&#9472;sdb3                                                                 f45e2fa1-c5a6-4d79-876c-c8245af921e0                          Gap1
&#9492;&#9472;sdb4              ext4        66fa44dd-ac91-4db5-9ab7-1f2059af74e1   c570f350-0b07-4843-93b0-05267fb860ff writable                 


Mount points (filtered): _______________________________________________________


                                                               Avail Use% Mounted on
/dev/mapper/vgubuntu-root                                     857.8G   1% /mnt/boot-sav/mapper/vgubuntu-root
/dev/sda1                                                     500.9M   2% /mnt/boot-sav/sda1
/dev/sdb1                                                          0 100% /cdrom


Mount options (filtered): ______________________________________________________


/dev/mapper/vgubuntu-root                                     ext4            rw,relatime
/dev/sda1                                                     vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sdb1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8


============================== ls -R /dev/mapper/ ==============================


/dev/mapper:
control
vgubuntu-root
vgubuntu-swap_1


===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================


search.fs_uuid 2e3cf0f5-c1ac-46de-9444-73b035815609 root lvmid/r1fmGK-061E-c7GW-cDI1-ufJb-VSSp-hj2co1/rltK8g-Hxxg-b9CB-Dz1K-G26G-LblT-0PCIGj 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

---

### Post by Rubi1200 on 2024-01-18
Hi and welcome to the forums :-)

The problem is likely this from your report > Warning: NVram is locked

Search the forums for possible solutions.

If you still need help, post back here.

---

### Post by oldfred on 2024-01-18
You have UEFI boot entry using GUID/partUUID of sda1.
And grub.cfg in sda1 referring to LVM.

Do you have esp,boot flags on sda1?
It looks like it should boot with current entries, unless something wrong with grub & LVM?

Have you always booted in UEFI boot mode?
Do you have latest UEFI firmare for your system?
You can see it in UEFI/BIOS settings & then go to Asus support for your system for downloads.

May have similar UEFI settings.
Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

The Locked NVRAM issue does not seem to have one solution. Varies by configuration/vendor.
Locked NVram
[https://askubuntu.com/questions/1488426/trying-to-reinstall-grub-after-windows-update-messed-it-up](https://askubuntu.com/questions/1488426/trying-to-reinstall-grub-after-windows-update-messed-it-up) & 
[https://ubuntuforums.org/showthread.php?t=2491460](https://ubuntuforums.org/showthread.php?t=2491460)  &
[https://ubuntuforums.org/showthread.php?t=2482909](https://ubuntuforums.org/showthread.php?t=2482909)
[https://ubuntuforums.org/showthread.php?t=2490084](https://ubuntuforums.org/showthread.php?t=2490084)
Locked NVRAM - turning on Secure boot & reset UEFI Dell XPS 9530
[https://ubuntuforums.org/showthread.php?t=2490359](https://ubuntuforums.org/showthread.php?t=2490359)
Locked UEFI/BIOS setting: Lenovo UEFI screen
[https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg)
add "--no-nvram" to the "grub-install" command 
[https://forums.gentoo.org/viewtopic-p-8789559.html?sid=4a2d572fa0b04d7a1a150a2c7d7b89d0](https://forums.gentoo.org/viewtopic-p-8789559.html?sid=4a2d572fa0b04d7a1a150a2c7d7b89d0)

---

