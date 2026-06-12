---
title: "Help Me Re-Access my Ubuntu 18.04 Installation"
date: 2024-06-04
forum: General Help
---

### Post by crispysonofa on 2024-06-04
First of all I want to say thank you and I'm so grateful for the  wonderful resource this forum provides. I have used it so many times in  my life but this is my first post. Grateful. 


2 Years ago, I  tried to upgrade windows on my dual boot Windows\ubuntu 18.04 studio  laptop. I stupidly deleted the wrong partition and realized then  stopped. I am only concerned with accessing UBUNTU at this point.

Life  got really busy, I want to fix what I broke. This is what I have done  so far. I used DMDE to restore the partitions since I didn't overwrite  anything. Still wouldn't detect the OS, so I booted to a live  environment again and installed boot-repair. It ran without error and  still wouldn't detect the OS on reboot. I am now unsure what I need to  do and I'm sure theres a lot of people here smarter than me when it  comes to Linux (obviously)

Please Help,

Crispy

---

### Post by tea for one on 2024-06-04
Well, looking at your screenshots (although difficult to interpret), you seem to have Windows 7 and Ubuntu 18.04 - is this correct?
If so, then both systems are end of life.
First priority is to ensure that you have personal data backups from both systems.

---

### Post by dragonfly41 on 2024-06-04
You have a two years old drive partitioned MBR instead of more modern GPT.

I can advise what I would do.

I would regard your drive as an archive holding data you want to recover.

I would purchase a second drive or SSD, and swap the drive you have installed. Then use LiveUSB (perhaps prepared on another PC using Rufus (Windows) or MkUSB (Ubuntu) to install Ubuntu on modern SSD formatted GPT / UEFI instead of your older dated MBR.

Then you have your old drive which I would place into a drive container through USB port and your task is then to extract data from your external drive into your spanking new Ubuntu 22.04 or 24.04.

When you recover old data you can recycle/partition the spare drive to use as backup drive.

---

### Post by crispysonofa on 2024-06-04
Tea - You are correct. I really want to access the ubuntu installation on that drive. I agree I will replace them.

---

### Post by crispysonofa on 2024-06-04
DragonFly41- You are not wrong. I have a 2TB external hard drive that I can back up to, but my goal is to re access this installation first. I mainly want to access the chrome with the tabs that I had open when I last shut it own (I know its probably a long shot) I agree I will reformat and get newer OS installed on it!!

---

### Post by tea for one on 2024-06-04
Reading between the lines, I get the impression that you do not have data backups?

---

### Post by dragonfly41 on 2024-06-04
[COLOR=#000000]> but my goal is to re access this installation first. I mainly want to access the chrome with the tabs that I had open when I last shut it own (I know its probably a long shot

That indeed is a long boundary shot .. two years back?

My thought would be to use LiveUSB to at least be able to view the old drive from "Try Ubuntu" mode. Now the problem is that usually LiveUSB are not persistent so if apps are installed you lose them when you shut down. Spend time in researching/building a *persistent LiveUSB* where you can install added apps for drive analysis.

Now you can "try Ubuntu" and then install persistent copy of Recoll (indexing engine which I recommend since I use it daily). Then you can apply Recoll to index your mounted old drive, perhaps leaving it running overnight for 2TB. Now you can view chrome cache to see what tabs were last open and history. At least that is the theory.  Recoll is a very powerful indexing tool. But if you are indexing 2TB the size of the index file will be large so your persistent LiveUSB needs to be rather larger than the usual flash drive. Perhaps another external SSD. But you can restrict Recoll indexing to the locations of your browser cache files and session files making the index smaller.

Of course this is not the same as getting your old Ubuntu up and running again.[/COLOR]

---

### Post by crispysonofa on 2024-06-04
There is no way to do what I am asking to do? All the suggestions are appreciated. I have the data backed up, but I I just want to repair the current 18.04 installation so that I can boot into this OS that is installed on the system. I can view and mount the 230GB volume that it's on from USB stick ubuntu, I can see all the files. I just can't get the computer to realize that there is an OS installed on this machine.

---

### Post by Rubi1200 on 2024-06-04
First screenshot: boot device not found etc. Was this before or after running the boot repair?

It would be very helpful if you run the boot repair again but this time choose to create a summary report and upload to the pastebin.

Post the link back here.

Do agree, however, that it is probably time to move on.

---

### Post by crispysonofa on 2024-06-05
I included the paste-bin picture. I can type out the link, This was after the boot repair that it still doesn't detect a boot device. I appreciate you replying.

---

### Post by dragonfly41 on 2024-06-05
This is the type of article I would seek to follow.

[https://askubuntu.com/questions/84501/how-can-i-change-convert-a-ubuntu-mbr-drive-to-a-gpt-and-make-ubuntu-boot-from](https://askubuntu.com/questions/84501/how-can-i-change-convert-a-ubuntu-mbr-drive-to-a-gpt-and-make-ubuntu-boot-from)

---

### Post by yancek on 2024-06-05
When you run boot repair from any major Ubuntu using the 2nd option described at their page, to use an Ubuntu installed  or 'live' system, it will give you a link to post here when it finishes.  For this to happen, you need to seledct the Create Bootinfo Summary option before running boot repair.  I don't see a link like that in any of your posts.

Have you tried to re-install Grub to that drive using the Ubuntu 'live' usb?  Very detailed instructions on various ways to do this at the Ubuntu site from the link below.

  [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

If your system had windows 7 and Ubuntu 18.04, it would likely have been a Legacy install so if you try to reinstall, make sure you do a Legacy.
What partition do you think you mistakenly deleted?

---

### Post by crispysonofa on 2024-06-05
Here are the pastebin contents

boot-repair-4ppa2075                                              [20240604_1828]

============================= Boot Repair Summary ==============================




Default settings: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub2 of
sda5 into the MBR of sda.
Grub-efi would not be selected by default because no ESP detected.
Additional repair would be performed: unhide-bootmenu-10s

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your BIOS boot on sda (ATA ST2000LX001-1RG1) disk!

The boot files of [sda5 (end>100GB)] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

User settings: _________________________________________________________________

Please backup your data before this operation.
The settings chosen by the user will restore the [(generic mbr)] MBR in /dev/sda, and make it boot on sda5.
The boot flag will be placed on sda5.
Additional repair will be performed: unhide-bootmenu-10s


parted /dev/sda set 5 boot on
Information: You may need to update /etc/fstab.


                                                                          
[email]SET@_label0.set[/email]_text('''Checking full partitions. This may require several minutes...''')
/dev/sda2 is 98 % full

** (org.gnome.Nautilus:22671): WARNING **: 18:29:55.782: Unable to get contents of the bookmarks file: Error opening file /root/.gtk-bookmarks: No such file or directory

** (org.gnome.Nautilus:22671): WARNING **: 18:29:55.782: Unable to get contents of the bookmarks file: Error opening file /root/.gtk-bookmarks: No such file or directory
Nautilus-Share-Message: 18:29:55.904: Called "net usershare info" but it failed: Failed to execute child process &#8220;net&#8221; (No such file or directory)
Nautilus-Share-Message: 18:31:20.041: Called "net usershare info" but it failed: Failed to execute child process &#8220;net&#8221; (No such file or directory)
The /dev/sda2 (Windows 7) partition is still full. This can prevent to start it (e.g. you may get a Power Manager error).

=========================== Restore MBR of /dev/sda ============================

dd if=/usr/lib/syslinux/mbr/mbr.bin of=/dev/sda
parted /dev/sda set 5 boot on
Information: You may need to update /etc/fstab.


                                                                          
[email]SET@_label0.set[/email]_text('''Unhide boot menu. This may require several minutes...''')

Unhide GRUB boot menu in sda5/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.


============================ Boot Info After Repair ============================

 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04.6 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 29600 of /dev/sdc for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi


================================ 3 OS detected =================================

OS#1:   Windows 7 (boot) on sda1
OS#2:   Windows 7 on sda2
OS#3:   Ubuntu 18.04.6 LTS on sda5

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GK107GLM [Quadro K2000M] from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.2 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 68IAV Ver. F.61(15.97) from Hewlett-Packard
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).



============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes
sdb    : notGPT,    no-BIOSboot,    has-noESP,     liveusb,    not-mmc, no-os,    no-wind,    32 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda3    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda5    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB
sdb1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far

Partitions info (2/3): _________________________________________________________

sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot
sda2    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot
sda3    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda5    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda5    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sdb1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb

fdisk -l (filtered): ___________________________________________________________

Disk sda: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk identifier: 0x4537e8b6
     Boot     Start        End   Sectors   Size Id Type
sda1            2048     206847    204800   100M  7 HPFS/NTFS/exFAT
sda2          206848  409599999 409393152 195.2G  7 HPFS/NTFS/exFAT
sda3       976771072 1181571071 204800000  97.7G  7 HPFS/NTFS/exFAT
sda4       409604094  976771071 567166978 270.4G  f W95 Ext'd (LBA)
sda5  *    526790656  976771071 449980416 214.6G 83 Linux
Partition table entries are not in disk order.
Disk sdb: 7.45 GiB, 8004304896 bytes, 15633408 sectors
Disk identifier: 0x00000000
     Boot Start      End  Sectors  Size Id Type
sdb1          32 15633407 15633376  7.5G  b W95 FAT32
Disk sdc: 28.64 GiB, 30752636928 bytes, 60063744 sectors
Disk identifier: 0x20ac7dda
     Boot      Start        End    Sectors   Size Id Type
sdc1       3224498923 3657370039  432871117 206.4G  7 HPFS/NTFS/exFAT
sdc2       3272020941 5225480974 1953460034 931.5G 16 Hidden FAT16
sdc3                0          0          0     0B 6f unknown
sdc4         50200576  974536369  924335794 440.8G  0 Empty
Partition table entries are not in disk order.

parted -lm (filtered): _________________________________________________________

sda:2000GB:scsi:512:4096:msdos:ATA ST2000LX001-1RG1:;
1:1049kB:106MB:105MB:ntfs::;
2:106MB:210GB:210GB:ntfs::;
4:210GB:500GB:290GB:::lba;
5:270GB:500GB:230GB:ext4::;
3:500GB:605GB:105GB:ntfs::;
sdb:8004MB:scsi:512:512:msdos:SanDisk Cruzer:;
1:16.4kB:8004MB:8004MB:fat32::;
sdc:30.8GB:scsi:512:512:loop:SanDisk Ultra Fit:;
1:0.00B:30.8GB:30.8GB:fat32::;

Free space >10MiB: ______________________________________________________________

sda: 200002MiB:257220MiB:57218MiB
sda: 576939MiB:1907729MiB:1330790MiB

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL           PARTLABEL
sda                                                                                                       
&#9500;&#9472;sda1 ntfs     B272614272610D03                     4537e8b6-01                          System Reserved 
&#9500;&#9472;sda2 ntfs     C8E669DEE669CCEE                     4537e8b6-02                                          
&#9500;&#9472;sda3 ntfs     7C4AC3404AC2F644                     4537e8b6-03                          Backup          
&#9500;&#9472;sda4                                               4537e8b6-04                                          
&#9492;&#9472;sda5 ext4     76cf827a-f9ac-42b8-b0be-ae70555ca102 4537e8b6-05                                          
sdb                                                                                                       
&#9492;&#9472;sdb1 vfat     2896-5255                                                                                 
sdc    vfat     08BA-53DE                                                                 UUI             

Mount points (filtered): _______________________________________________________

                          Avail Use% Mounted on
/dev/sda1                 73.5M  27% /mnt/boot-sav/sda1
/dev/sda2                  5.5G  97% /mnt/boot-sav/sda2
/dev/sda3                 97.5G   0% /mnt/boot-sav/sda3
/dev/sda5                 15.3G  88% /media/ubuntu/76cf827a-f9ac-42b8-b0be-ae70555ca102
/dev/sdb1                  7.4G   1% /media/ubuntu/2896-5255
/dev/sdc                    24G  16% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sda1                 fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda2                 fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda3                 fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda5                 ext4            rw,nosuid,nodev,relatime,errors=remount-ro
/dev/sdb1                 vfat            rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro
/dev/sdc                  vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

====================== sda5/boot/grub/grub.cfg (filtered) ======================

Ubuntu (lowlatency)   76cf827a-f9ac-42b8-b0be-ae70555ca102
Windows 7 (on sda1)   B272614272610D03
Windows 7 (on sda2)   C8E669DEE669CCEE
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda5/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=76cf827a-f9ac-42b8-b0be-ae70555ca102 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9c36aea6-5866-422c-90b7-fed0498e229e none            swap    sw              0       0

======================= sda5/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sda5: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
 264.059047699 = 283.531243520  boot/grub/i386-pc/core.img                     1
 282.987976074 = 303.856025600  boot/vmlinuz-4.10.0-21-lowlatency              1
 273.106746674 = 293.246136320  boot/vmlinuz-4.10.0-22-lowlatency              1
 275.253959656 = 295.551688704  boot/vmlinuz-4.10.0-24-lowlatency              1
 276.654830933 = 297.055862784  boot/vmlinuz-4.10.0-26-lowlatency              1
 272.763435364 = 292.877508608  boot/vmlinuz-4.10.0-28-lowlatency              1
 275.301616669 = 295.602860032  boot/vmlinuz-4.10.0-30-lowlatency              1
 327.825450897 = 351.999897600  boot/vmlinuz-4.10.0-35-lowlatency              1
 328.466079712 = 352.687767552  boot/vmlinuz-4.10.0-37-lowlatency              1
 329.173545837 = 353.447403520  boot/vmlinuz-4.10.0-38-lowlatency              1
 346.153793335 = 371.679805440  boot/vmlinuz-4.13.0-16-lowlatency              1
 330.368640900 = 354.730627072  boot/vmlinuz-4.13.0-17-lowlatency              2
 360.134315491 = 386.691276800  boot/vmlinuz-4.13.0-36-lowlatency              2
 351.665565491 = 377.598025728  boot/vmlinuz-4.13.0-37-lowlatency              2
 306.576286316 = 329.183780864  boot/vmlinuz-4.15.0-190-lowlatency             2
 253.966911316 = 272.694894592  boot/vmlinuz-4.15.0-192-lowlatency             2
 284.996093750 = 306.012225536  boot/vmlinuz-4.8.0-39-lowlatency               1
 285.270332336 = 306.306686976  boot/vmlinuz-4.8.0-41-lowlatency               1
 286.495979309 = 307.622715392  boot/vmlinuz-4.8.0-45-lowlatency               1
 264.130046844 = 283.607478272  boot/vmlinuz-4.8.0-46-lowlatency               1
 288.205650330 = 309.458460672  boot/vmlinuz-4.8.0-49-lowlatency               1
 273.294105530 = 293.447311360  boot/vmlinuz-4.8.0-52-lowlatency               1
 274.044105530 = 294.252617728  boot/vmlinuz-4.8.0-53-lowlatency               1
 253.966911316 = 272.694894592  vmlinuz                                        2
 306.576286316 = 329.183780864  vmlinuz.old                                    2
 353.692596436 = 379.774533632  boot/initrd.img-4.10.0-21-lowlatency           5
 352.439113617 = 378.428616704  boot/initrd.img-4.10.0-22-lowlatency           4
 352.367641449 = 378.351874048  boot/initrd.img-4.10.0-24-lowlatency           6
 352.349174500 = 378.332045312  boot/initrd.img-4.10.0-26-lowlatency           4
 350.934585571 = 376.813142016  boot/initrd.img-4.10.0-28-lowlatency           5
 342.134376526 = 367.363989504  boot/initrd.img-4.10.0-30-lowlatency           4
 342.126831055 = 367.355887616  boot/initrd.img-4.10.0-35-lowlatency           4
 338.118755341 = 363.052249088  boot/initrd.img-4.10.0-37-lowlatency           6
 338.161834717 = 363.098505216  boot/initrd.img-4.10.0-38-lowlatency           6
 353.875717163 = 379.971158016  boot/initrd.img-4.13.0-16-lowlatency           4
 353.848369598 = 379.941793792  boot/initrd.img-4.13.0-17-lowlatency           4
 353.689075470 = 379.770753024  boot/initrd.img-4.13.0-36-lowlatency           3
 317.910984039 = 341.354319872  boot/initrd.img-4.13.0-37-lowlatency           4
 312.177730560 = 335.198285824  boot/initrd.img-4.15.0-190-lowlatency          5
 303.246696472 = 325.608660992  boot/initrd.img-4.15.0-192-lowlatency          6
 353.900405884 = 379.997667328  boot/initrd.img-4.8.0-39-lowlatency            5
 353.740158081 = 379.825602560  boot/initrd.img-4.8.0-41-lowlatency            4
 353.736232758 = 379.821387776  boot/initrd.img-4.8.0-45-lowlatency            4
 353.732303619 = 379.817168896  boot/initrd.img-4.8.0-46-lowlatency            3
 353.728374481 = 379.812950016  boot/initrd.img-4.8.0-49-lowlatency            5
 353.744163513 = 379.829903360  boot/initrd.img-4.8.0-52-lowlatency            5
 353.722675323 = 379.806830592  boot/initrd.img-4.8.0-53-lowlatency            6
 303.246696472 = 325.608660992  initrd.img                                     6
 312.177730560 = 335.198285824  initrd.img.old                                 5

===================== sda5: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root  9921 Sep  2  2016 09_lowlatency
-rwxr-xr-x 1 root root 12808 Aug 24  2020 10_linux
-rwxr-xr-x 1 root root 11298 Mar 11  2020 20_linux_xen
-rwxr-xr-x 1 root root 12059 Mar 30  2017 30_os-prober
-rwxr-xr-x 1 root root  1418 Sep  6  2016 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Sep  6  2016 40_custom
-rwxr-xr-x 1 root root   216 Sep  6  2016 41_custom

=================== sda5/etc/grub.d/09_lowlatency (filtered) ===================

#! /bin/sh
set -e
# grub-mkconfig helper script.
#
# Ubuntustudio customization that keeps the latest lowlatency kernel
# as the first menu item and default boot even if there is a newer
# generic or other kernel. Often the updated generic kernel is
# released a few days earlier than the lowlatency kernel
prefix="/usr"
exec_prefix="${prefix}"
datarootdir="${prefix}/share"
. "${datarootdir}/grub/grub-mkconfig_lib"
export TEXTDOMAIN=grub
export TEXTDOMAINDIR="${datarootdir}/locale"
CLASS="--class gnu-linux --class gnu --class os"
if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
  OS=GNU/Linux
else
  if [ "${GRUB_DISTRIBUTOR}" = "Ubuntu" ] ; then
    OS="${GRUB_DISTRIBUTOR}"
  else
    OS="${GRUB_DISTRIBUTOR} GNU/Linux"
  fi
  CLASS="--class $(echo ${GRUB_DISTRIBUTOR} | tr 'A-Z' 'a-z' | cut -d' ' -f1) ${CLASS}"
fi
# loop-AES arranges things so that /dev/loop/X can be our root device, but
# the initrds that Linux uses don't like that.
case ${GRUB_DEVICE} in
  /dev/loop/*|/dev/loop[0-9])
    GRUB_DEVICE=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
    # We can't cope with devices loop-mounted from files here.
    case ${GRUB_DEVICE} in
      /dev/*) ;;
      *) exit 0 ;;
    esac
  ;;
esac
if [ "x${GRUB_DEVICE_UUID}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] \
    || ! test -e "/dev/disk/by-uuid/${GRUB_DEVICE_UUID}" \
    || uses_abstraction "${GRUB_DEVICE}" lvm; then
  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
else
  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
fi
GRUBFS="`${grub_probe} --device ${GRUB_DEVICE} --target=fs 2>/dev/null || true`"
if [ x"$GRUBFS" = x ]; then
    GRUBFS="$(stat -f --printf=%T / || true)"
fi
case x"$GRUBFS" in
    xbtrfs)
    rootsubvol="`make_system_path_relative_to_its_root /`"
    rootsubvol="${rootsubvol#/}"
    if [ "x${rootsubvol}" != x ]; then
        GRUB_CMDLINE_LINUX="rootflags=subvol=${rootsubvol} ${GRUB_CMDLINE_LINUX}"
    fi;;
    xzfs)
    rpool=`${grub_probe} --device ${GRUB_DEVICE} --target=fs_label 2>/dev/null || true`
    bootfs="`make_system_path_relative_to_its_root / | sed -e "s,@$,,"`"
    LINUX_ROOT_DEVICE="ZFS=${rpool}${bootfs}"
    ;;
esac
title_correction_code=
for word in $GRUB_CMDLINE_LINUX_DEFAULT; do
  if [ "$word" = splash ]; then
    GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT \$vt_handoff"
  fi
# add crashkernel option if we have the required tools
if [ -x "/usr/bin/makedumpfile" ] && [ -x "/sbin/kexec" ]; then
    GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA crashkernel=384M-2G:64M,2G-:128M"
fi
linux_entry ()
{
  os="$1"
  version="$2"
  type="$3"
  args="$4"
  if [ -z "$boot_device_id" ]; then
      boot_device_id="$(grub_get_device_id "${GRUB_DEVICE}")"
  fi
  if [ x$type != xsimple ] ; then
      case $type in
      recovery)
          title="$(gettext_printf "%s, with Linux %s (recovery mode)" "${os}" "${version}")" ;;
      *)
          title="$(gettext_printf "%s, with Linux %s" "${os}" "${version}")" ;;
      esac
      if [ x"$title" = x"$GRUB_ACTUAL_DEFAULT" ] || [ x"Previous Linux versions>$title" = x"$GRUB_ACTUAL_DEFAULT" ]; then
      replacement_title="$(echo "Advanced options for ${OS}" | sed 's,>,>>,g')>$(echo "$title" | sed 's,>,>>,g')"
      quoted="$(echo "$GRUB_ACTUAL_DEFAULT" | grub_quote)"
      title_correction_code="${title_correction_code}if [ \"x\$default\" = '$quoted' ]; then default='$(echo "$replacement_title" | grub_quote)'; fi;"
      grub_warn "$(gettext_printf "Please don't use old title \`%s' for GRUB_DEFAULT, use \`%s' (for versions before 2.00) or \`%s' (for 2.00 or later)" "$GRUB_ACTUAL_DEFAULT" "$replacement_title" "gnulinux-advanced-$boot_device_id>gnulinux-$version-$type-$boot_device_id")"
      fi
      echo "menuentry '$(echo "$title" | grub_quote)' ${CLASS} \$menuentry_id_option 'gnulinux-$version-$type-$boot_device_id' {" | sed "s/^/$submenu_indentation/"
  else
      echo "menuentry '$(echo "$os" | grub_quote)' ${CLASS} \$menuentry_id_option 'gnulinux-simple-$boot_device_id' {" | sed "s/^/$submenu_indentation/"
  fi      
  echo "recordfail" | sed "s/^/$submenu_indentation/"
  if [ x$type != xrecovery ] ; then
      save_default_entry | sed -e "s/^/\t/"
  fi
  # Use ELILO's generic "efifb" when it's known to be available.
  # FIXME: We need an interface to select vesafb in case efifb can't be used.
  if [ "x$GRUB_GFXPAYLOAD_LINUX" = x ]; then
      echo "    load_video" | sed "s/^/$submenu_indentation/"
  else
      if [ "x$GRUB_GFXPAYLOAD_LINUX" != xtext ]; then
      echo "    load_video" | sed "s/^/$submenu_indentation/"
      fi
  fi
  if [ x$type != xrecovery ] ; then
      echo "    gfxmode \$linux_gfx_mode" | sed "s/^/$submenu_indentation/"
  fi
  echo "    insmod gzio" | sed "s/^/$submenu_indentation/"
  if [ x$dirname = x/ ]; then
    if [ -z "${prepare_root_cache}" ]; then
      prepare_root_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE} | sed -e "s/^/\t/")"
    fi
    printf '%s\n' "${prepare_root_cache}" | sed "s/^/$submenu_indentation/"
  else
    if [ -z "${prepare_boot_cache}" ]; then
      prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
    fi
    printf '%s\n' "${prepare_boot_cache}" | sed "s/^/$submenu_indentation/"
  fi
  if [ x$type != xsimple ]; then
    message="$(gettext_printf "Loading Linux %s ..." ${version})"
    sed "s/^/$submenu_indentation/" << EOF
    echo    '$(echo "$message" | grub_quote)'
EOF
  fi
  if test -d /sys/firmware/efi && test -e "${linux}.efi.signed"; then
    sed "s/^/$submenu_indentation/" << EOF
    linux    ${rel_dirname}/${basename}.efi.signed root=${linux_root_device_thisversion} ro ${args}
EOF
  else
    sed "s/^/$submenu_indentation/" << EOF
    linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  fi
  if test -n "${initrd}" ; then
    # TRANSLATORS: ramdisk isn't identifier. Should be translated.
    if [ x$type != xsimple ]; then
      message="$(gettext_printf "Loading initial ramdisk ...")"
      sed "s/^/$submenu_indentation/" << EOF
    echo    '$(echo "$message" | grub_quote)'
EOF
    fi
    sed "s/^/$submenu_indentation/" << EOF
    initrd    ${rel_dirname}/${initrd}
EOF
  fi
  sed "s/^/$submenu_indentation/" << EOF
}
EOF
}
machine=`uname -m`
case "x$machine" in
    xi?86 | xx86_64)
    list=`for i in /boot/vmlinuz-*lowlatency /boot/kernel-*lowlatency ; do
                  if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
              done` ;;
    *) 
    list=`for i in /boot/vmlinuz-*lowlatency /boot/vmlinux-*lowlatency /boot/kernel-*lowlatency ; do
                  if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
         done` ;;
esac
case "$machine" in
    i?86) GENKERNEL_ARCH="x86" ;;
    mips|mips64) GENKERNEL_ARCH="mips" ;;
    mipsel|mips64el) GENKERNEL_ARCH="mipsel" ;;
    arm*) GENKERNEL_ARCH="arm" ;;
    *) GENKERNEL_ARCH="$machine" ;;
esac
prepare_boot_cache=
prepare_root_cache=
boot_device_id=
title_correction_code=
cat << 'EOF'
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
EOF
# Use ELILO's generic "efifb" when it's known to be available.
# FIXME: We need an interface to select vesafb in case efifb can't be used.
if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
  echo "set linux_gfx_mode=$GRUB_GFXPAYLOAD_LINUX"
else
  cat << EOF
if [ "\${recordfail}" != 1 ]; then
  if [ -e \${prefix}/gfxblacklist.txt ]; then
    if hwmatch \${prefix}/gfxblacklist.txt 3; then
      if [ \${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
EOF
fi
cat << EOF
export linux_gfx_mode
EOF
# Extra indentation to add to menu entries in a submenu. We're not in a submenu
# yet, so it's empty. In a submenu it will be equal to '\t' (one tab).
submenu_indentation=""
is_first_entry=true
if [ "x$list" != "x" ]; then
  linux=`version_find_latest $list`
  case $linux in
    *.efi.signed)
      # We handle these in linux_entry.
      list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
      continue
      ;;
  esac
  gettext_printf "Found linux image: %s\n" "$linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"
  initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" "initrd-${version}.gz" \
       "initrd-${version}" "initramfs-${version}.img" \
       "initrd.img-${alt_version}" "initrd-${alt_version}.img" \
       "initrd-${alt_version}" "initramfs-${alt_version}.img" \
       "initramfs-genkernel-${version}" \
       "initramfs-genkernel-${alt_version}" \
       "initramfs-genkernel-${GENKERNEL_ARCH}-${version}" \
       "initramfs-genkernel-${GENKERNEL_ARCH}-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done
  config=
  for i in "${dirname}/config-${version}" "${dirname}/config-${alt_version}" "/etc/kernels/kernel-config-${version}" ; do
    if test -e "${i}" ; then
      config="${i}"
      break
    fi
  done
  initramfs=
  if test -n "${config}" ; then
      initramfs=`grep CONFIG_INITRAMFS_SOURCE= "${config}" | cut -f2 -d= | tr -d \"`
  fi
  if test -n "${initrd}" ; then
    gettext_printf "Found initrd image: %s\n" "${dirname}/${initrd}" >&2
  elif test -z "${initramfs}" ; then
    # "UUID=" and "ZFS=" magic is parsed by initrd or initramfs.  Since there's
    # no initrd or builtin initramfs, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi
  if [ "x$is_first_entry" = xtrue ]; then
    linux_entry "${OS} (lowlatency)" "${version}" simple \
    "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}"
  fi
fi
echo "$title_correction_code"

====================== sdc/boot/grub/grub.cfg (filtered) =======================

Try or Install Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory

==================== sdc: Location of files loaded by Grub =====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

---

### Post by crispysonofa on 2024-06-05
Also, If I go into the boot-repair advanced functions and select legacy, it gives me this error.

Please enable a repository containing the [grub] packages in the software sources of Ubuntu 18.04.6 LTS (/dev/sda5). Then try again.

So does anyone know what I would enter into terminal to enable that repository?

---

### Post by crispysonofa on 2024-06-05
I used the Repair MBR and now the machine boots to windows fine. I think the issue is the boot-repair is picking the wrong partition by default for grub, im going to try and manually select sda1. im not sure if it will break anything if I use the latest version of grub, but I'm a step in the right direction I believe!!

---

### Post by Rubi1200 on 2024-06-05
The Ubuntu install is on sda5 so...question is which OS is more important for you to boot into, Windows or Ubuntu.

Based on your posts, I suppose Ubuntu.

If it was me, I would do a chroot from the live USB into sda5 and reinstall GRUB to the MBR of sda.

---

### Post by crispysonofa on 2024-06-05
> **Rubi1200 said:**
> The Ubuntu install is on sda5 so...question is which OS is more important for you to boot into, Windows or Ubuntu.

Based on your posts, I suppose Ubuntu.

If it was me, I would do a chroot from the live USB into sda5 and reinstall GRUB to the MBR of sda.

Definitely Ubuntu! It just felt good that it booted an OS at all, and everything was just as it was 2 years ago, including my browser tabs! Wild! Now to get into Ubuntu.

---

### Post by crispysonofa on 2024-06-05
> **Rubi1200 said:**
> The Ubuntu install is on sda5 so...question is which OS is more important for you to boot into, Windows or Ubuntu.

Based on your posts, I suppose Ubuntu.

If it was me, I would do a chroot from the live USB into sda5 and reinstall GRUB to the MBR of sda.

Can you give me a little more guidance here, I know enough to be dangerous obviously, I think I understand what you are saying. but I don't want to make things worse. I really appreciate it. I feel so close.

---

### Post by crispysonofa on 2024-06-06
I now have grub giving me boot options but Ubuntu hangs when booting and says gave up waiting for suspend/resume device. I am researching now, just wanted to update.

---

### Post by Rubi1200 on 2024-06-06
> **crispysonofa said:**
> Can you give me a little more guidance here, I know enough to be dangerous obviously, I think I understand what you are saying. but I don't want to make things worse. I really appreciate it. I feel so close.

From the live USB, open a terminal and do as follows:

```
sudo mount /dev/sda5 /mnt

sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
```

Press enter after each command

```
sudo chroot /mnt

grub-install /dev/sda
```

Assuming no errors, now this:

```
update-grub
```

Finally,

```
exit
```

And then,

```
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt
```

Reboot, keeping fingers crossed

---

### Post by crispysonofa on 2024-06-06
I walked away, came back and everything is working!! I got an error that chrome didnt shut down correctly last time but then it restored all my tabs even. Thanks so much for all the help im one happy camper!!!!!!

---

### Post by Rubi1200 on 2024-06-06
Excellent! Glad to hear it all worked out in the end.

Please mark this as solved using the Thread Tools at the top of your original post.

---

### Post by yancek on 2024-06-06
Glad you got it working but for future reference you might make note of some of the information from boot repair.
One of the reasons your windows likely failed is that the main filesystem partition (sda2) was 98% full.  Keep a closer watch on that with any filesystem. 

>  im going to try and manually select sda1. im not sure if it will break anything if I use the latest version of grub,

If you look at boot repair you will see that sda1 is a windows partition, in this case the boot partition and you never install Grub files to an ntfs partition.

I would also suggest you make note somewhere of the method you used to access the installed system or bookmark the link I posted in post 12 which explains the method as well as several others in detail.

It is preferable  to post the link to pastebin which you get when running boot repair as suggested at the boot repair site.  One advantage is that the lines are numbered so referencing things is much easier.

---

