---
title: "ubuntu 18.04 LTS not booting after testing 22.10 on separate drive and swapping back"
date: 2023-03-31
forum: General Help
---

### Post by ugh25 on 2023-03-31
I installed 22.10 from a usb to a separate drive after first removing the original 18.04 LTS working system drive. All good.

After shutting down and swapping the 18.04 LTS drive back, its not showing the drive in the boot menu and its booting to the EFI shell now. 

I can confirm the efi file is working by manually following

```
map -r
fs0:
cd EFI
cd ubuntu
grubx64.efi

```

here is the report from boot-repair (which did not fix the problem)

```

boot-repair-4ppa203                                              [20230331_0633]


============================= Boot Repair Summary ==============================












Recommended repair: ____________________________________________________________


The default repair of the Boot-Repair utility will reinstall the grub-efi of
sda3,
using the following options:  sda1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file




sda3/boot/efi not empty


Unhide GRUB boot menu in sda3/etc/default/grub


======================== Reinstall the grub-efi of sda3 ========================


grub-install --version
grub-install (GRUB) 2.02-2ubuntu8.25
modprobe efivars


efibootmgr -v before grub install
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0004,0005,0006,0007,0002,0000
Boot0000  ubuntu    HD(1,GPT,c279fe80-2946-4f16-b617-eb1394989854,0x800,0x1dc800)/File(EFIUBUNTUSHIMX64.EFI)
Boot0002* UEFI: Built-in EFI Shell    VenMedia(5023b95c-db26-429b-a648-bd47664c8012)..BO
Boot0004* UEFI: Intel(R) I210 Gigabit  Network Connection    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/MAC(ac1f6b99c296,0)/IPv4(0.0.0.00.0.0.0,0,0)/Uri()..BO
Boot0005* UEFI: IP4 Intel(R) I210 Gigabit  Network Connection    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/MAC(ac1f6b99c296,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot0006* UEFI: Intel(R) I210 Gigabit  Network Connection    PciRoot(0x0)/Pci(0x1d,0x1)/Pci(0x0,0x0)/MAC(ac1f6b99c297,0)/IPv4(0.0.0.00.0.0.0,0,0)/Uri()..BO
Boot0007* UEFI: IP4 Intel(R) I210 Gigabit  Network Connection    PciRoot(0x0)/Pci(0x1d,0x1)/Pci(0x0,0x0)/MAC(ac1f6b99c297,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO


uname -r
4.15.0-208-generic


grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
Installation finished. No error reported.
df /dev/sda1
mv /boot/efi/EFI/Boot/bootx64.efi /boot/efi/EFI/Boot/bkpbootx64.efi
cp /boot/efi/efi/ubuntu/grubx64.efi /boot/efi/EFI/Boot/bootx64.efi


grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
Installation finished. No error reported.


efibootmgr -v after grub install
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0000,0004,0005,0006,0007,0002
Boot0000* ubuntu    HD(1,GPT,c279fe80-2946-4f16-b617-eb1394989854,0x800,0x1dc800)/File(EFIubuntushimx64.efi)
Boot0002* UEFI: Built-in EFI Shell    VenMedia(5023b95c-db26-429b-a648-bd47664c8012)..BO
Boot0004* UEFI: Intel(R) I210 Gigabit  Network Connection    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/MAC(ac1f6b99c296,0)/IPv4(0.0.0.00.0.0.0,0,0)/Uri()..BO
Boot0005* UEFI: IP4 Intel(R) I210 Gigabit  Network Connection    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/MAC(ac1f6b99c296,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot0006* UEFI: Intel(R) I210 Gigabit  Network Connection    PciRoot(0x0)/Pci(0x1d,0x1)/Pci(0x0,0x0)/MAC(ac1f6b99c297,0)/IPv4(0.0.0.00.0.0.0,0,0)/Uri()..BO
Boot0007* UEFI: IP4 Intel(R) I210 Gigabit  Network Connection    PciRoot(0x0)/Pci(0x1d,0x1)/Pci(0x0,0x0)/MAC(ac1f6b99c297,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO


update-grub
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-208-generic
Found initrd image: /boot/initrd.img-4.15.0-208-generic
Found linux image: /boot/vmlinuz-4.15.0-206-generic
Found initrd image: /boot/initrd.img-4.15.0-206-generic
Adding boot menu entry for EFI firmware configuration


Unhide GRUB boot menu in sda3/boot/grub/grub.cfg


Boot successfully repaired.


You can now reboot your computer.
Please do not forget to make your UEFI firmware boot on the Ubuntu 18.04.6 LTS entry (sda1/efi/ubuntu/grubx64.efi file) !




============================ Boot Info After Repair ============================


 => No boot loader is installed in the MBR of /dev/sda.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/ubuntu/fwupx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg


sda2: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sda3: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04.6 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub




================================ 1 OS detected =================================


OS#1:   Ubuntu 18.04.6 LTS on sda3


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: ASPEED Graphics Family from ASPEED Technology, Inc.
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-4.15.0-208-generic root=UUID=4143bc76-f85b-465d-b860-4960a689a7cb ro quiet splash vt.handoff=1
df -Th / : /dev/sda3      ext4  398G  144G  235G  38% /


===================================== UEFI =====================================


BIOS/UEFI firmware: 2.2 from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0000,0004,0005,0006,0007,0002
Boot0000* ubuntu    HD(1,GPT,c279fe80-2946-4f16-b617-eb1394989854,0x800,0x1dc800)/File(\EFI\ubuntu\shimx64.efi)
Boot0002* UEFI: Built-in EFI Shell    VenMedia(5023b95c-db26-429b-a648-bd47664c8012)..BO
Boot0004* UEFI: Intel(R) I210 Gigabit  Network Connection    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/MAC(ac1f6b99c296,0)/IPv4(0.0.0.00.0.0.0,0,0)/Uri()..BO
Boot0005* UEFI: IP4 Intel(R) I210 Gigabit  Network Connection    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/MAC(ac1f6b99c296,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot0006* UEFI: Intel(R) I210 Gigabit  Network Connection    PciRoot(0x0)/Pci(0x1d,0x1)/Pci(0x0,0x0)/MAC(ac1f6b99c297,0)/IPv4(0.0.0.00.0.0.0,0,0)/Uri()..BO
Boot0007* UEFI: IP4 Intel(R) I210 Gigabit  Network Connection    PciRoot(0x0)/Pci(0x1d,0x1)/Pci(0x0,0x0)/MAC(ac1f6b99c297,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO




============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda3    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far


Partitions info (2/3): _________________________________________________________


sda3    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot


Partitions info (3/3): _________________________________________________________


sda3    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: AE23F4AF-1923-41CB-B1B8-E87CF006D278
          Start       End   Sectors   Size Type
sda1       2048   1953791   1951744   953M EFI System
sda2    1953792 126953471 124999680  59.6G Linux swap
sda3  126953472 977104895 850151424 405.4G Linux filesystem


parted -lm (filtered): _________________________________________________________


sda:1000GB:scsi:512:512:gpt:ATA WDC WDS100T2B0A:;
1:1049kB:1000MB:999MB:fat32::boot, esp;
2:1000MB:65.0GB:64.0GB:linux-swap(v1)::;
3:65.0GB:500GB:435GB:ext4::;


Free space >10MiB: ______________________________________________________________


sda: 477102MiB:953870MiB:476768MiB


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL PARTLABEL
sda                                                                                             
&#9500;&#9472;sda1 vfat     35F4-B726                            c279fe80-2946-4f16-b617-eb1394989854       
&#9500;&#9472;sda2 swap     ec862452-98cb-4e10-ba36-521f853e99de 794979aa-e52c-43f1-9fa9-fb8de1a5a881       
&#9492;&#9472;sda3 ext4     4143bc76-f85b-465d-b860-4960a689a7cb 69e80e9f-2631-462e-ba33-a72e6738db25       


Mount points (filtered): _______________________________________________________


                        Avail Use% Mounted on
/dev/sda3              234.5G  36% /


Mount options (filtered): ______________________________________________________




===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================


search.fs_uuid 4143bc76-f85b-465d-b860-4960a689a7cb root hd0,gpt3 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


====================== sda3/boot/grub/grub.cfg (filtered) ======================


Ubuntu   4143bc76-f85b-465d-b860-4960a689a7cb
Ubuntu, with Linux 4.15.0-208-generic   4143bc76-f85b-465d-b860-4960a689a7cb
Ubuntu, with Linux 4.15.0-206-generic   4143bc76-f85b-465d-b860-4960a689a7cb
### END /etc/grub.d/30_os-prober ###
System setup   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###


========================== sda3/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=4143bc76-f85b-465d-b860-4960a689a7cb /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=35F4-B726  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda2 during installation
UUID=ec862452-98cb-4e10-ba36-521f853e99de none            swap    sw              0       0


======================= sda3/etc/default/grub (filtered) =======================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false


==================== sda3: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
 278.691322327 = 299.242528768  boot/grub/grub.cfg                             1
 346.887767792 = 372.467904512  boot/vmlinuz-4.15.0-206-generic                1
  80.442455292 = 86.374428672   boot/vmlinuz-4.15.0-208-generic                1
  80.442455292 = 86.374428672   vmlinuz                                        1
 346.887767792 = 372.467904512  vmlinuz.old                                    1
 104.917705536 = 112.654528512  boot/initrd.img-4.15.0-206-generic             2
 427.128864288 = 458.626125824  boot/initrd.img-4.15.0-208-generic             4
 427.128864288 = 458.626125824  initrd.img                                     4
 104.917705536 = 112.654528512  initrd.img.old                                 2


===================== sda3: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 12808 Aug 24  2020 10_linux
-rwxr-xr-x 1 root root 11298 Jul 17  2018 20_linux_xen
-rwxr-xr-x 1 root root 12059 Jul 17  2018 30_os-prober
-rwxr-xr-x 1 root root  1418 Jul 17  2018 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jul 17  2018 40_custom
-rwxr-xr-x 1 root root   216 Jul 17  2018 41_custom



```


How do I get automatic boot working again?

Its a supermicro server board, have not changed any settings and if I swap back, 22.10 loads automatically.

---

### Post by tea for one on 2023-03-31
> **ugh25 said:**
> I installed 22.10 from a usb to a separate drive after first removing the original 18.04 LTS working system drive. All good.
After shutting down and swapping the 18.04 LTS drive back, its not showing the drive in the boot menu and its booting to the EFI shell now. 
I can confirm the efi file is working by manually following
```
map -r
fs0:
cd EFI
cd ubuntu
grubx64.efi

```

After inserting and removing disks, the EFI shell sometimes elevates itself to be the first boot priority in the firmware?
Can you jump into your UEFI settings and double-check?

---

### Post by ugh25 on 2023-03-31
> **tea for one said:**
> After inserting and removing disks, the EFI shell sometimes elevates itself to be the first boot priority in the firmware?
Can you jump into your UEFI settings and double-check?

I appreciate your response. I am a newbie so I don't know what it means to "jump into my UEFI settings".

Can you provide specific steps for the supermicro startup screen? I don't see the drive in the list of drives to select after presing F11 at the startup screen. Only options are built-in EFI shell or a LAN interface.

---

### Post by mIk3_08 on 2023-04-01
> **ugh25 said:**
> 
How do I get automatic boot working again?
Its a supermicro server board, have not changed any settings and if I swap back, 22.10 loads automatically.
In my case, When I already installed the original ssd drive apart from the "other drive I've installed for OS testing" I then configured the bios/uefi to make it sure to boot it first from the ssd I installed before anything else and save the configuration setting and restart. Then when it boot I then try to boot it using boot device option by pressing "F9" on my system and selected the right drive to make it sure to boot it from the installed drive. Once it successfully booted, I think its already in the system that the configurations will now boot from the installed drive once it done successfully. Or maybe, you have to reset the memory by releasing the electric current from your motherboard. Regards and cheers.

---

### Post by MAFoElffen on 2023-04-01
I have a SuperMicro Motherboard. May be the same hot-key as yours. 

The hotkey to get into my BIOS setting is the <Delete> key. When you get into the BIOS, the first thing I would look at is the boot order set in the BIOS. Mine is selectable for which of the drives is the boot drive.

---

### Post by tea for one on 2023-04-01
> **ugh25 said:**
> I appreciate your response. I am a newbie so I don't know what it means to "jump into my UEFI settings".
Can you provide specific steps for the supermicro startup screen? I don't see the drive in the list of drives to select after presing F11 at the startup screen. Only options are built-in EFI shell or a LAN interface.
You previously booted Ubuntu via the EFI shell, not really a newbie activity ;)

MAFoElffen mentioned the <Delete> key to access the UEFI settings but, if this doesn't work, you can use a terminal command.
After you have booted into Ubuntu, open a terminal and enter:-
```
sudo systemctl reboot --firmware-setup
```

---

### Post by ugh25 on 2023-04-08
Thanks both. Newbie to me means I'm good at following instructions, beyond which I can get stuck. Here are my exact steps followed to resolve the problem, in case they may help others.


I was only noticing the "FIXED BOOT ORDER Priorities" which were set correctly, #1 UEFI Hard Disk, #2 USB Hard Disk and so on.


Looking closer at the Boot menu, I noticed further down the "> UEFI Hard Disk Drive BBS Priorities"


expanding THIS item, under UEFI Boot Order #1 it was set to Disabled, which I changed to ubuntu, then pressed F4 (Save & Exit).

---

