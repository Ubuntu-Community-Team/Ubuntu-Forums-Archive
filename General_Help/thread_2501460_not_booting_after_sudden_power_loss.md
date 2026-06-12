---
title: "not booting after sudden power loss"
date: 2024-10-08
forum: General Help
---

### Post by sdayanik on 2024-10-08
Hi there,

my laptop's battery ran out and laptop suddenly shut down. When plugged the laptop to the power and restarted it, grub appeared with "Minimal BASH-like line editing is supported.." screen. Following the instructions on [this page]("https://askubuntu.com/questions/1484410/minimal-bash-like-line-editing-is-supported-errortoo-many-huffman-tables"), I have restarted the laptop with live usb, installed boot repair, and saved the boot-Info summary (accessible at [https://paste.ubuntu.com/p/26bJgdHrmT/](https://paste.ubuntu.com/p/26bJgdHrmT/) also pasted below). Can anyone tell what the problem is? Is the recommended repair appropriate? 

Thanks
-----
```

boot-repair-4ppa2081                                              [20241008_1515]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/fwupdx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg

nvme0n1p2: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04.6 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sda: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sda: /dev/sda already mounted or mount point busy.


================================ 1 OS detected =================================

OS#1 (linux):   Ubuntu 20.04.6 LTS on nvme0n1p2

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: NVIDIA Corporation UHD Graphics from NVIDIA Corporation Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04.6 LTS, focal, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 1.29.0(1.29) from Dell Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0004,0005,0001,0002,0000,0003,0006
Boot0000* UEFI BC501 NVMe SK hynix 512GB CD9AN8683113YBI1B 1    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/NVMe(0x1,00-00-00-00-00-00-00-00)/HD(1,GPT,7d00b35a-8068-4cf7-a855-b714713388a5,0x800,0x100000)/File(\EFI\Boot\BootX64.efi)N.....YM....R,Y.
Boot0001* ONBOARD NIC (IPV4)    PciRoot(0x0)/Pci(0x1d,0x5)/Pci(0x0,0x0)/MAC(70b5e8a9c5df,0)/IPv4(0.0.0.00.0.0.0,0,0)N.....YM....R,Y.
Boot0002* ONBOARD NIC (IPV6)    PciRoot(0x0)/Pci(0x1d,0x5)/Pci(0x0,0x0)/MAC(70b5e8a9c5df,0)/IPv6([::]:<->[::]:,0,0)N.....YM....R,Y.
Boot0003* Linux Firmware Updater    HD(1,GPT,7d00b35a-8068-4cf7-a855-b714713388a5,0x800,0x100000)/File(\EFI\ubuntu\fwupdx64.efi)
Boot0004* UEFI Generic Mass Storage 5470D802    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(2,MBR,0x405a23c7,0x573ca4,0x1fc0)/File(\EFI\Boot\BootX64.efi)N.....YM....R,Y.
Boot0005* ubuntu    HD(1,GPT,7d00b35a-8068-4cf7-a855-b714713388a5,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0006* UEFI Generic Mass Storage 5470D802 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/CDROM(1,0x573ca4,0x7f00)/File(\EFI\Boot\BootX64.efi)N.....YM....R,Y.

64e4182ead3316166f817dcc6131cd7a   nvme0n1p1/BOOT/fbx64.efi
522f1fff3eaefbaeb449d98436d24041   nvme0n1p1/BOOT/mmx64.efi
3dae829e41062a758307e7c3ca9e8b2f   nvme0n1p1/ubuntu/fwupdx64.efi
d4646b0af24b169d62bc44cff8967793   nvme0n1p1/ubuntu/grubx64.efi
522f1fff3eaefbaeb449d98436d24041   nvme0n1p1/ubuntu/mmx64.efi
07e25dcaf57c776875f78fa36827c58e   nvme0n1p1/ubuntu/shimx64.efi
07e25dcaf57c776875f78fa36827c58e   nvme0n1p1/BOOT/BOOTX64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p2    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, vfat
nvme0n1p2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ext4

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 476.96 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: 46B55DE5-F739-41D8-9CF7-503EE0C3C10C
           Start        End   Sectors   Size Type
nvme0n1p1    2048    1050623   1048576   512M EFI System
nvme0n1p2 1050624 1000214527 999163904 476.4G Linux filesystem
Disk sda: 15.24 GiB, 16357785600 bytes, 31948800 sectors
Disk identifier: 0x405a23c7
     Boot   Start      End  Sectors  Size Id Type
sda1  *          0  8498951  8498952  4.1G  0 Empty
sda2       5717156  5725283     8128    4M ef EFI (FAT-12/16/32)
sda3       8499200 31948799 23449600 11.2G 83 Linux

parted -lm (filtered): _________________________________________________________

sda:16.4GB:scsi:512:512:unknown:Generic Flash Disk:;
nvme0n1:512GB:nvme:512:512:gpt:BC501 NVMe SK hynix 512GB:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:512GB:512GB:ext4::;

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda         iso9660  2023-03-16-15-57-27-00                                                    Ubuntu 20.04.6 LTS amd64 
&#9500;&#9472;sda1      iso9660  2023-03-16-15-57-27-00               405a23c7-01                          Ubuntu 20.04.6 LTS amd64 
&#9500;&#9472;sda2      vfat     1544-BBA2                            405a23c7-02                                                   
&#9492;&#9472;sda3      ext4     057e7441-fd4f-4e35-bbc6-23cae93c5a6f 405a23c7-03                          writable                 
nvme0n1                                                                                                                 
&#9500;&#9472;nvme0n1p1 vfat     7477-E22F                            7d00b35a-8068-4cf7-a855-b714713388a5                          EFI System Partition
&#9492;&#9472;nvme0n1p2 ext4     57b8e19f-45d0-4737-8b97-45c67f5b95cd ac22aee6-9824-4b24-b748-246385401b17                          

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/nvme0n1p1                                                456.4M  11% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p2                                                107.2G  72% /mnt/boot-sav/nvme0n1p2
/dev/sda1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/nvme0n1p1                                                vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/nvme0n1p2                                                ext4            rw,relatime
/dev/sda1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8

=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid 57b8e19f-45d0-4737-8b97-45c67f5b95cd root 
set prefix=($root)'/boot/grub'

=================== nvme0n1p2/boot/grub/grub.cfg (filtered) ====================

Ubuntu   57b8e19f-45d0-4737-8b97-45c67f5b95cd
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

======================== nvme0n1p2/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during installation
UUID=57b8e19f-45d0-4737-8b97-45c67f5b95cd /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=7477-E22F  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

==================== nvme0n1p2/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

================= nvme0n1p2: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
 262,500125885 = 281,857363968  boot/grub/grub.cfg                             3
 286,832054138 = 307,983572992  boot/vmlinuz                                   2
 157,144542694 = 168,732667904  boot/vmlinuz-5.15.0-107-generic                1
 286,832054138 = 307,983572992  boot/vmlinuz-5.15.0-117-generic                2
 247,457061768 = 265,704996864  boot/vmlinuz-5.15.0-122-generic                2
 157,144542694 = 168,732667904  boot/vmlinuz.old                               1
 157,477535248 = 169,090215936  boot/initrd.img                               10
 183,383785248 = 196,906840064  boot/initrd.img-5.15.0-107-generic            10
 157,477535248 = 169,090215936  boot/initrd.img-5.15.0-117-generic            10
 183,383785248 = 196,906840064  boot/initrd.img.old                           10

=================== nvme0n1p2: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18224 Jan 11  2022 10_linux
-rwxr-xr-x 1 root root 42359 Aug 17  2020 10_linux_zfs
-rwxr-xr-x 1 root root 13101 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 12059 Jul 31  2020 30_os-prober
-rwxr-xr-x 1 root root  1424 Jul 31  2020 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 21  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Jul 31  2020 40_custom
-rwxr-xr-x 1 root root   216 Jul 31  2020 41_custom



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
nvme0n1p2,
using the following options:  nvme0n1p1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 20.04.6 LTS entry (nvme0n1p1/efi/****/grub****.efi (**** will be updated in the final message) file) !
```

---

### Post by tea for one on 2024-10-08
After a power interruption, your file systems may have suffered some damage.
Boot into a "Try Ubuntu" live session
Open a terminal and enter:-
```
sudo fsck /dev/nvme0n1p1
```
Follow terminal output to repair
Then
```
sudo fsck /dev/nvme0n1p1
```
Close terminal and power off.

Does your PC boot normally now?

---

### Post by sdayanik on 2024-10-08
Thanks. I booted into "Try Ubuntu" and ran the first command. Found that dirty bit set. Is it safe to go ahead with action 1)? Below is the screen shot.

[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAwwAAACQCAYAAAClM zeAAAABHNCSVQICAgIfAhkiAAAABl0RVh0U29mdHdhcmUAZ25vbWUtc2NyZWVuc2hvdO8Dvz4AAAAtdEVYdENyZWF0aW9uIFRpbWUAVHVlIDA4IE9jdCAyMDI0IDA0OjIwOjQ4IFBNIFVUQ2Im1BkAACAASURBVHic7N13fE3nH8Dxz7n3ZkgiIokYQcwqFduvtUqtGrVaW5XYalPlZ4/YVdSmRlCqRa3YQoRIRIwkJEGIkCFTZMi69/7 SBAjyblxEf0979crf5Cb5/k 4zz3ec55zjlS9erVtQiCIAiCIAiCILyB4kMHIAiCIAiCIAhCwaVKTU390DEIgiAIgiAIglBAqUxDxY4kQRAEQRAEQRDeTGxJEgRBEARBEAQhR2LBIAiCIAiCIAhCjsSCQRAEQRAEQRCEHMlbMEgaVJWTMfsyEWOLdxxRQfP/XPaPgbI8LaZOoV LokgfOpb8kixoNGsjGx0bY/gh8v831KEgCIIgCO MvAWDIg3z76Ox7PwEY/N3HNEzkhZFkXQMrTXvKcMc/D XPRvDtotxfbSM5kYfOpJXqKrw9fjv fJTk3c02VVi/dWPLHJ1weWRHxdD3dh7cildP1PqLwvJhLINGlGjnLney6D4ZCg7Yj2Y09Yk5w 98zrUMR5BEARBEAqUArslybBNBKVnh2PTMi3/kxhJg0H9xxSbGErpXx5QenYExdo/RaXSZ6T6p5ey64tJBb5esJEda9piZtqWhSHu7D85labFPnhk74Vk2ZZJ20dTM3ovi3r8wLCe/2X1ZhduPSo4i7mcKSnfuS2fPD7DiXPJHzoYCl48OZCKYD98EU43vfGMuYLzmUX0ql8k38eiUaUOzLrqw FF9XiboUdf6QiCIAiCrgru985bz0e1GDSNpninVDT3TEg6rUJr8xSzltEUU9oQcdCIAvtA2QIzFzemzowNOPaLZ  kocy FodUxJZKNVU8jCuwtadXinJVqGgSxokl6znukfGhw9GNshItunxC/NFfuZz0oYOh4MXzRgpKfL Y3xZU5 bS2YzzhFojJjF 72KSGg7n4EP5C0WlVTVaDh/O4BEtKWci8SifEekrHUEQBEHILwWqZKwXhVB2aQRFSgJoMeoSRtnlIdh2S3l57iqpMekVju3iB5SZF4bNt8kYGGT9Tk46inRMe0ZSYmoopRc/oOzSB5SeGollgzQUWRkp/hNFmeUhlGidnvnvLyIpszyEsstDKLskGhNDmXkVTsaiTQr4WfJopRVxR4vweJs18cFg8J8kjAxkpvMxlv15zJZ8uewwZ0OPMLW9le7rEKUd9ZrZojnnxMpt7tzw8cfP7RT7Vx0jSMe5s2RWlc7Lndh79xqX4m/iHurOwTOTaVj4WV5VGHLxJidXNORZtWLUhsUxN9k0wvbFpTCTirRdtIV/7vtyKfoS w8N5rNXl72qEjSYuIzt/lfwjPHG cyvDGxeAp02ERn8h0kBAVx2G0Z5ozL0Pe3P1aTbXE26idPoss/jybNcmYlRvJkD0w8c4miYH15xPrjecmb5yKo5xCRRuMEYnMK8cZpaB7N8LiCVn7Wh5adxuO67REr2X8ipQ0VRag6by1oPV85F 3LW70/mjqyLRVYsZl2W4xrvwoQG2f9QSaVJB7gUuowWhXnNG ORLGg4YwNO3q64RPjhFXeN4xfXMqKd7fOzGXLyUtZyYIXXBc5HX e09yam/7qKXXevcu7mDsZ9XexF/8mjXKiq8O3oJnDAkSmOB3E/cZC1DvNxkZrwfb9PMttLRsygpOKQ2YxqlsyhAePZdfcNCw3JgoazNrHT5yLnYwPwir7EgeOL6NskW7xy0hEEQRCEd0y3KwySFmURLekRKiiZjnGTGKw1SiL2yzxbL2kwrJKCoYWEOtKANI0agxIpmHWLRhtZkrggCW2cIU99QVE8FWMbDdpYI1JCs74 1YaoZX5fKj9LwthQReI5EzTFk7Ds/RhTWw2gBTJQmQC6nOX8iMr nKoc9VpWoogFNGhSDqVzDDrN8zWxREWko2rUC4fW3mw8EUr 3guuosbUVUztGMLmn4fhFpSEwtyGsuXTCdFlZ4pUlGbLNjOnQwwH50xg8T0D7Jp1x GL7B8yo57jFpY7ZHB8zmRW yuo3GcUw/dspWinrvziligvr3QfNrZry97ag1jxeyM8Bw1hm28GoCUlMgyN7HIpKPbtQrZsbo3aZQdOY5cT/OgphsXtML0XyutNqsDyq/Es396d9FVDGb/gCon5upij5JMubSgXdZqlF7ItF2TVYSHsp25hzeA0Ds6eybpriVg26ce42euZm9CRMU5hJJ09hVfy1zT8 lOWX/RDDaC0o0n7yjx12YDXa9WcUzwm2DVqTLXEP5j2wxnipGLUHjKBwVuXENegLzuD1LLyUpasSq2KD/ij03wCOi1gcf9EtvQcTPB385m5ZCCnXRbik553ubTFalOzoobryzwwd9jAX9OMcWo/HvfLGpp9UQsLKYAYGTGDmlsLu9NhgRatyp5R897QRJIJdg0aUCnGicmjz/DEsBR1B45i5D9bsOrUneUXkuWlIwiCIAjvmG4LBo2KhPWleHwfFDWjKdk/GYN6SRg7G/FUl0mNVknyn8WJC9Zi6hCGVY0MCn2WxuMgI7S3ixB9GwzbhVOitQbtrSJE/2n88qQ8z6i1GJROR8owJC1UjdmgWMzKgPqBEWrLFAwLaZF03Yz10ZQ9m/RrOA2bQ0pzCY/1V19ZLJgg2X LompZpJQwNLfd0QbdRWvbEeWnxmgv/40mKgrnKfNp9NdUBuw7RVf/cxz fRt/br/AQ522oKsoWtwC4s5y5awXftFqAHxcdUkDFKW/oXdXK3xmfs 8dQ/QABfPqqkzpD5WWZ RSrbHYYAdtxZ1YPbqINSAx7k7GFQ yKAJ7dh6/i iZbVXCrF37xFvGU 6No34 0EE31LrXi7DOvSb0x4z11n07PYnYc TcH89S8mYCn2WsOCX2tye1pcZmwJ5Kr96XmbwGa062xFzeA5Xs83PZdWhTTsGjyzNxdGtWbw7NrP/eQdiUNeVuT1bYLN9OxGPz3PKJZm57VtS2dGPgAxQfNKGVvYJuC1x5cmrdZxDPM9oHlzl7Al3UoHLfmbU9Z1C46ZF2RUUjVZGXoYAmhjuXvHhvIkvSf2LEOxxmZN4MaFbBcqagK9R3uWKsrHBUkrgekQKZk1KY2llTEmLZC6GJyPVKYalEmI0MmIG0GplnUzQhvpy4eylzHTOBsDZffwwoR3b3fcQo5WfjiAIgiC8K7rf9Jz1zaW5XYg0NVAoHVV nx6kVZAenrkpQ1FYv5faFWYaeKpErUrFuIwWHhUm6jdrEu6/xQ0CH0nZX9AQc2Ena b wZXIV/Io1RKlfSUklQoK26Go0xtl1ymoGtgjFVZCcubyIu3mn/xUtwX9HFbgElWZLr9s4e8LC2hZWpeuk4L7gnkcl7qy5sZJft80ga6tymOqY 9TVvmUSspwfD3D3nBmPpOqmj1VDMO44naf53PzjGC83EIxsLenokEOf5gveZdLUbom9rZqfPYeJ/zV9carsX81hfVrm/NozgAmv81iAVDVbkvzcpGc/cebtGz/L6sOq9eimklhmq1zwyP2Bp6xN/CM9cCxkxnKUqUopgC0jzm/ ywJlVvToroSUFK5azsqRR7n0KnXr LkFM baKIeEJooUcQy60ZjHfNCo0WLhKQANBq0SCgUkrxyPZeBv2MPvvmsCysupucR8Rtizq 0O7ifDcOwZg0991VBEARByD8VSGi1gKRF0mWTt0L74otRA/lNR5shZc7DdfqWlZGXBKglMNKgUIA2TkWGGgxe dC/sux5UiAZS2jjb6O9sBtNui2KKo2QypdD0kah8XZGk5TtnGZqJL5/r8P3701saDeNVTt68PPPhzk3 kKek79n0m7vY9rnZ9nWuh1tun7DwJ2DGOa9lkm9V IdqwU0aDSgNMjlEopWiyZr8pebnH r//O0eZZLq0EDaDR5LwrVN4/yT3oLek9dyFC/Yax1e5zPiA2o3qU1pcJOctLzlRaSU4eSBOqH7B8wjB03XlnlpMcTnnWpKvHUXk4/ p3W3WuwIUBFx54VeLh7Ct6vrXRyieeNNGjUIGWLUX5egFaNWq3JPE50LJcmMpJYbWGsS5ggqeN59BCQLChW0gRtVBSxanLoYK/HnD9a0GhAkgruI wEQRCE/zsKtAo0SYCUgYFtHqdAn9OiqpWMoRKINyTtCeQvnVxySMucTEtFM57fFIxh1kRdRl6apxIYa5BSFJlf5NbpvDYX/ZeW/QUFVo16MXx6H rYZJ9 aNDePYDa Q80jzMg6T6aKztR751Pxr6NaO7H5pBeOhHHd3IiUEuRMiUx0XVulB7LLecd/ObQk04NFxNUexij 2bdQKyJJSZag1mFcljlMFPKuOFDYFop6reoRE4nXzNu hKQVoo6Texe3FCsKkf9Jrak /oRlPfJYt3lUi5NqB/ 4UpqdG5F8TwWeNqIi6zp3JNphy34/u tjGtumb z1YY1adWxJI8OHsP3lfm5rDq84UNgWklq1DAm/NZdgrP/3It5cR9Lsid7tgdRonsPWnfrTVuba zZ4vf6fTK5xCOb3LyA9FPTaFn8R44k6F4ubdQ1rgcpqNGqAeZZlS9ZNKBBXQX3Pa7x F3vDVKUplYDW9T /tz7yB7KJQiCIPx7qVAb8tRfReHGGRTqGkHJJkokyxwmopIa0z4RGGvVGBRXI6Eg5WxhUtUAOqQjQ0aoIRptGspP4igxJRF1mgalhSFxc6xJTs0rL4mMCAO09dMxMLMgOVBBoeqJWI9OR1002zf v7Ls2RjUot 6mfStAO1MA gy2Vu3m54VtrSZ1R bG2743IokSWNCycZ9aVclnRu7vF/fp54jY qOmUqDpxfw8gnlSZoRNp/bY2OYSkhMUtZ 7zg8nb1JWzKYqZPj2OX2CHXRmhRX8DxmbYQzmzc5sGbCGpYoVrHvfBip5jUpoYBn6wBt GG2bHZg9c8rmJW2iqMBCir1Gsmg6iHs63RE5v0LeixXmjfbHU/Tat1MNu6pxB87PbgXmYbS3AZb/Nh36A4vtV5qCMdH9Cdds43521fzuMMANl/RbXOS4eft KpUKCf3X fV9ZGsOow4zMZ1fVk7bj1rimzk7xOBxKYXwrpySeKP7ORCyLOrJWpub/0D71HTmLJUIuXweJyDX7 Skls88snLKzeyypURwL6V5 n221Tm3Vax8xLYj5hEC9xw3HYLnY5qYyvKlLfCSFWWooYSKqsyVKwWT2rcQ 6HP31 9Uj1RU9GDJPwCkrHtvOPDKkXw/HeR3i i1BmOoIgCILwrqhAIuWwNbGqOMxrpGFgq0GboiA9xIDUYGXWZE5J2i0j0itmoCyajqFSQh1eiGTXIsRfenbaXkY6OtAGFiHWJQOLz1NRWaWjSFWQEaZEawCk5p1Xhp8Jae3jMGucTsTf1sRrH2P2aQqGkoKMUEMyUmXG/BGW/bmMYC6fCqJTdwkPt2DdJjsASlOMbarSpW93RlkXQiVl8CTYD/cFP7Jszb0c98C/RiqE0qgI9QfOpnfZIhiRSnxIIF5LxrFsd9YNomgI2zyJn21mMHqAIysmG6F5Gk9UoBcn7yRnfSYJ7 n9GBU5kWEO/2XxxMIoU58QFejFsdtJzz9zeVp/xj2ewshRC1lurSXmxjm2dF/IZrlPSNJzucJ3jqNfVD8Gj 3CgJV9sTKReBoVws2d8zlx A7xr6arjsBl7I sKv8XY7ZNIbDJDC7Ifu FEbW a4n1/cOcvPKm5aGcOkzm2qwfGPJgDMMGDWRqf2sKaRKJvOXJtgu7XkpN8/Ag2/4cxup Cfyx/DTxr4WZVzzy5Z1XXuSUS0PE9omMNp3CxDFzWfYTxF4/ybKu8zj4QLcFirJqP5afHU6FZ8NE cX82UtD9O8OtBvj/mKBlmZG9eGz6GFnTHKwN4eHTmSF84vtaHLTEQRBEIR3RaplUulfeoJKg1HHR9h8pSbd25wnHsakxSky9/5rlaTHiB3CujBsu5iTWw2YXXYcLvl7tqrwPhRqzDSfDdTZ2YNuM311XyT 2 MpSBSl6HX0FGOjfuLL74/k85HFgiAIgvDuFdw3Pb81BamHbYhKi6Vos8dY13vxG62fFaG/m8o/Qy4IHwnjxu1oan2f/f/cLBCT84IWjyAIgiAIuvsXLxgAjZKUY8UIP63GoGQ6SjMtkiSheWQoFgs6Sjv6M02Lf gohNwVov53X1Hk9m5O RWE6XlBi0cQBEEQhPz4F29JEgRBEARBEAThbYmN/IIgCIIgCIIg5EgsGARBEARBEARByNH7XTBIFjSatZGNjo0xfK8ZC4IgCIIgCIKQH9kWDEqsv/qRRa4uuDzy42KoG3tPLqXrZ3m8nlYXkgllGzSiRjnz/L3B9jXvIeYPwdQW zbNqGqdcy2ZfjmJ3Q892DLhs9fuXJeKdWd17G2uJmX eO5oh1E wtAlndziEQRBEARBED5ez d2kmVbJm0fjb3nShb1uEiE2gSr0kWIflRwnyf0McYsh7JqH bubMmZ1m74R7/p6TISxmUrYmtRlLQqNhhw46U3OGtjj PY8BqmSitar95Mv3zGIT d3OMpeCTMa3/H4Cnf06JhRawNU3jkd559s bj5BqlwxO0VJRqM4wfx3akQZ3SFJYSCL/qyp7ZC9hxIe6NL wzqtaHxQen0zBiBd2bruWeeHiQIAiCIAgF3PMFg6JcFSqahHFiyXqOexTs6d4zH2PM qEl5o/x9LxRhoxAf56  mt1POEB8aAoTp3kt3gIlux08oinoFHa0c5xJHUj/mL9EB8ileVoPnE8I3caEll7JM6RcutMQ0YhQxLPbMRx8UNSilSm ZjRjP1DwcMaP3HmycufVlXqxsL9o/hEk6bz278FQRAEQRA FAUG/2FSQACX3YZR3qgMfU/7Z21BuYnT6LLP9yxJZlXpvNyJvXevcSn Ju6h7hw8M5mGhbMnZ0DxZg5MP3CIo2F eMX54HrLmeUjq/LmTUIShRuMwSnMG6epdTCTu09JbswWtei68FfWXTjJsZBreMb74xHuxuofy7/Yi6UqQYOJy9jufwXPGG cz/zKwOYlnserrOXACq8LnI  zmnvTUz/dRW77l7l3M0djPu6mPybQJRVGHLxJidXNMTg2f8ZtWFxzE02jbDNTOdZuVwHY2dUnv6uAVnlCsRldRMMyLZNKPEqh84f5MCG/G030hdZ8UgWNJyxASdvV1wi/PCKu8bxi2sZ0c72xYpVRv0oSrVj4a0bHFrbHEvpWf4tme3vy75Fn8vvP pgdnduSd BazjgfJ6LB3ewePI IkxrUbOqLhuqNET 8ysLF/3NGZeLXPxnG0sWnyHJ4hMql3m5x0vm9Rm5fRzmG4az4PBjsWAQBEEQBOGjoSLdh43t2rK39iBW/N4Iz0FD2OabAWhJiQzL2p6hosbUVUztGMLmn4fhFpSEwtyGsuXTCUl lpSCYt8uZMvm1qhdduA0djnBj55iWNwO03uhb9jmocDyq/Es396d9FVDGb/gColyZ1GyYgbJ5nM6D22J1mk S fcJyYhA5W5NVLQs3jMqOe4heUOGRyfM5nV/goq9xnF8D1bKdqpK7 4JaIsWZVaFR/wR6f5BHRawOL iWzpOZjg7 Yzc8lATrssxCf9LVpAZrnU8RFkANrYo8z5/DKFFFa0XedEfz1lnV y4pFMsGvUmGqJfzDthzPEScWoPWQCg7cuIa5BX3YGyduXowk7yrzBddi6bwGzL/dg3JZkWiydTavYTQyZ7Sm//wDa9Ixsbx6WMClVHNOMEO6H5HePkBKTsnX5zqEByoC9XMxeJkUxWq5YQkv/OTj86ovdknxmIQiCIAiC8AGoIIXYu/eIt4wnXZtG/P0ggm 9OmlSUbS4BcSd5cpZL/yy9tX7uGb7iGEd s1pj5nrLHp2 5Ow50m4v56rZEyFPktY8Ettbk/ry4xNgTpuY5ET84vP3nHey8mTr8/qpZLtcRhgx61FHZi9Ogg14HHuDgaVDzJoQju2nv LJwCaGO5e8eG8iS9J/YsQ7HGZk3gxoVsFypqAT7xOwb9dudQJPLqdAIokYvSw90dRyBQTQ2XmTehaNWlJSaTqMmfWIR7Ng6ucPeFOKnDZz4y6vlNo3LQou4KiZZ5x15LguoQpC6qzaf4yplSNo2mrEDa0XINfct5/nRODil2Y7tiUyHUD2H9P9/tfJIvO/Bq4kKamCrQxHqzssh7flGe/VWDTbRYT67oxq lxojRK7PIfqiAIgiAIwnsnc0dNCu4L5nFc6sqaGyf5fdMEurYqj2m2v1aUrom9rRqfvccJz2PCqfpqCuvXNufRnAFM1nmxoD qavZUMQzjitv9F2ebM4LxcgvFwN6eigav/IFGixYJSQFoNGiRUCj087ynD0NFHcejuIZ5cy7Mm3MPnRnT4P0840gT9YDQRIkilkV0fGJWKoHLJrLC047Ow74gbOl0tt9Iy3cchar3YbHzTCqfn8K42ZdJykca2ienWfRVVwZ1ncKWy2UYdnAT/WtmPjhYsmzOqDk1uTxzGRfjxEYkQRAEQRA PrK34Kfd3se0z7 i14DN CjqM3DnEQ4cGU3dZ5vJtRo0gEaT9xla9c2j/HPhKXWmLmRoEws9PWI1f3LO w2TO60atVqDNl/zPg0aDSgN5EzItXmfcdfK Eye1ASuHc2QNt8zuM33DG4/ll0  dySo3M8GjRqkJ4vuOTXj6J0Pb74zICE AwqdelANdN8xIuEab2hrHCeiO2xCQwZepjQ/G4t0yQQcdOPK8f2sKrPJP55UoteDnUxAExbfUcrW2tabXLDI/YGnrHXWTO4BAY1x7A7bBPflviYF5yCIAiCIPw/0O3Fbemx3HLewW8OPenUcDFBtYcxum/mTcaaUD/8w5XU6NyK4nm8BkEbcZE1nXsy7bAF3/ 9lXHNLT/IoiHjpi8BaaWo08TuxU3ZqnLUb2JLuq8fQa9MINNPTaNl8R85kpCPzDSxxERrMKtQDqu8aj0lhTTJDDPz3D6YSspTLViYUzinytOmk5amBTNTTN74GS0Jd67h7ebJZTdPLrtd48GTNy2U8kpHZjy5kVs/harRf/N0avsuwKHpLDxKDWKuY2PMdcxTUaIt03eOwGr/WH4cf4pHOT5kS4FVo14Mn96HOjYyDhdt1sJHmfnZ5COz6VGnHd2 6ECPLzrQ44suzNkTTUbANsZ/OY2TUeKqgyAIgiAIBZvM/SfG1B0zlQZPL DlE8qTNCNsPrfHxjCVkJikzDPLad5sdzxNq3Uz2binEn/s9OBeZBpKcxts8WPfoTu8dO46NYTjI/qTrtnG/O2redxhAJuvvN/NSdrww2zZ7MDqn1cwK20VRwMUVOo1kkHVQ9jX6QjRWvT3RmptHJ7O3qQtGczUyXHscnuEumhNiit47Z0F6uAA7iRY0uKnUVxRXiRWZUN54wD /ifwRR1qE7njcx/FyF4M7RfJ2WhzSitvsufArWyfecI9/0coB/RkUK8oLjwpgi032Hf4lbbIM3YZ6ciJ563rx4Ta0xYzpLQLU5vs4m4kOE5owq7Njow93pm5x Q fcgA zHjaS6dYp5TGBaffoJF1m80iREEhzx5cZO QS36rZtJ3wrQzjSALpO9X8SjKEbDEd2wDbvJ/chkKFyamr2H8a1tKPv3XCMdICGC y8tMFVYx2WgTY0j9E44CeI9DIIgCIIgFHDyFgxSIZRGRag/cDa9yxbBiFTiQwLxWjKOZbuf3bCqIXznOPpF9WPw2C4MWNkXKxOJp1Eh3Nw5nxOH7/DavcHqCFzG/siq8n8xZtsUApvM4MJ73eedxOVp/Rn3eAojRy1kubWWmBvn2NJ9IZvdEvWcl4awzZP42WYGowc4smKyEZqn8UQFenHyTvLLE91EF1aPdMJyTg9m/D0ERWIofptn4rw/kITnH1QTsHIWG zn0PuX1XRMjcB/6wyOHLyV7TMZ K6Yzbbq0/h25Vq6pkRwc8sMjjnfyfYZOeSkk0s8eqofo/rD e/Qwhz7YR4uWe9KiNm/gN96ODNj4XAOnVvAVTk3PytsqF63FAal7Jjl1uGlX6Wd C9ff7uHx8/KlRHM5VNBdOou4eEW/PLiRzKhcNladBrSjwpliqBMiSX0mjubei1jm2t 7oYQBEEQBEEoeKRaJpXEnghBEARBEARBEN5It3sYBEEQBEEQBEH4vyIWDIIgCIIgCIIg5EgsGARBEARBEARByJFYMAiCIAiCIAiCkCOxYBAEQRAEQRAEIUfvd8EgWdBo1kY2OjbW3/sNhLwpilJ79AS  8zoQ0fyf6oQVYf RO//FPmgbzUXBEEQBEHIj2wLBiXWX/3IIlcXXB75cTHUjb0nl9L1szxe26wLyYSyDRpRo5y5niZOeorZ1Bb7Ns2oav0vnM5J1jRaso3VU5vzaXkLcUnpQ1BaU6HxN4w55MS4rz7MW80FQRAEQRDy6/n8UbJsy6Tto6kZvZdFPX5gWM//snqzC7ceaXL7 w9KXzErq/Zh7s4ptC6nn m0UbU rLgTgNf54ZTP53rLqFIHZl314fCienJfx/0GSuyGLGVef0OO9O/PgsOPXrzBGAnz2l2Z8Pd joT6cinKi0NnluHQtNjLiwqpCPbDF F00xvPmCs4n1lEr/pvPlOeY8wG/2FSQABXk26/9uN9Ywq1DHQokj7ikZeRvPrJnl9O7a5 gPPAfsw7bUWvrYvonN9OIQiCIAiC8AE8n0cpylWhokkYJ5as57hHxoeMSbaCGLOqUjcW7h/FJ5o08vNGPKVVNVoOH87gES0pZyLx6C1iUZTsxLjpdYhY0YclR6N4aRmltKOd40jqRvzF iE RCrL0XzieEbuNCSy9kicI7WAghLfL a3BdW5uXQ24zyh1ohJjN 7mKSGwzn4UCMv5owbbO/RgyNGL6b1kmVjRvz IyVd3AmW3XR6ikcOWfXzQp7tnnafQ8MmUvXcZkbOboNrP2dixSsTBUEQBEH4CCienf297DaM8kZl6Hvakba0TgAAIABJREFUP vs702cRpd9fjZVMqtK5 VO7L17jUvxN3EPdefgmck0LJw9OQOKN3Ng oFDHA3zwyvOB9dbziwfWZU3n1OVKNxgDE5h3jhNrYOZ3L0acmMu1obpHuc4G WP92MfTl11YkrfTzGRXknHdTB2RuXp7/rsLHggLquboMuJbwDJvD4jt4/DfMNwFhx nI8Fg5KKQ2YzqlkyhwaMZ9fdt7m6o6TCDz/QIO0Y61b4kvrqr9XB7O7ckr4D13DA TwXD 5g8eR9RJjWombVrHWkqgrfjm4CBxyZ4ngQ9xMHWeswHxepCd/3 ySrTWXErE0i7Pp1fC9dy/zxCsGqaw9qRW5n1n/P8lhuRekrHjnk1E8Wue2ufeLJesdTKNr345uK4iqDIAiCIAgfBxXpPmxs15a9tQex4vdGeA4awjbfDEBLSmRY1llpFTWmrmJqxxA2/zwMt6AkFOY2lC2fTkjys6QUFPt2IVs2t0btsgOnscsJfvQUw J2mN4L5fVpmwLLr8azfHt30lcNZfyCKyTKnTjKihm0j/05vngGRx5GkywV5dPe45mw8jeSb7VnuWd6rumo4yPQ6ZqFohgtVyyhpf8cHH71xW6JLn/8jJpbC7vTYYEWrcqeUfPyk0YWZRkata1MwrFlXIx/c8Vq0zNQP/ XhEmp4phmhHA/JPN/pWK1qVlRw/VlHpg7bOCvacY4tR P 2UNzb6ohYUUQIxW95gLNRrO2O UnOq/lquJ8ov0ruLJSV71A jY7loeHz3AhaQVNG1dgh133nRcCIIgCIIgFCwqSCH27j3iLeNJ16YRfz I4Fvq1z5WtLgFxJ3lylkv/KIzf /jmu0jhnXoN6c9Zq6z6NntT8KeJ H eq6SMRX6LGHBL7W5Pa0vMzYF8lSnsOXEDKTf59K  8//6e9rTL1uK6j1eUkUniFo5KaTJwU23WYxsa4bs5oeJ0qjxC4fqQCg1eZrK9NrVJX45FMI sOfNBkfN6jYhemOTYlcN4D99zKnsQobGyylBK5HpGDWpDSWVsaUtEjmYngyUp1iWCohJkPHmBUlafdzN4pd/o0NbzgbryhkiomhMvOeBK2atKQkUrOaRN/x5JaXnPrJV7s/DeCGv0TD6hVRIhYMgiAIgiAUfDLvBU3BfcE8ju eyZobX3H1sDPH/tzH0dP3SMqa8ShK18TeVo3P4uOE5zHnVn01hfUdlPhP6sLkTcHkZ4ouh6JYPXrOHEmnr6pQoqiC5MhkjAtJhBvr96GukmVzRs2pyeXJHbkYV0A2phuZYmqgJSk Kc/Jc6HqfZi/52cqnJ/Cj7Mvk/TaJzLwd zBN5sUxDxM5z998x WolpXujdJw9VhLyGvNbyKOo5HWT sZOa2MnUou9q1ZPH5V6/16CMeuXnlXD/5andNAk eaDExNxNPrBIEQRAE4aMg  Exabf3Me3zs2xr3Y42Xb9h4M5BDPNey6TeK/GO1YJWgwbQaPI Z6q eZR/0lvQe pChvoNY61bfvb750FRmq5bNzK23EXWTx De ATJKvGDN85HqvXPvx2Z/VNW31HK1trlJvcaLEp8/8klQEqaQy7w qxsOYg9kW854VEaiKJaRLFLc1RkJTDmWwJ03pDWLZ3OBb/TGDIT6d4lG2 rImMJFZbGOsSJkjqeB49BCQLipU0QRsVRazOKz0lVbt3oELsSVaciH9DnasJXDuaIfuNsp56lMojnxeZ6Dee3PPKlHv95KvdFaYUNpN4Gp0ori4IgiAIgvBR0O1pk mx3HLewS3nHayr7MDK8xMZ3fcADivuown1wz9cSbvOrSi aw8RuUzetBEXWTNwIzdXbGDm31sx7j2AZS6xr0wgFVg16kH35go81 /iSqSO0yuDKtSoY8yd5cvYsu925uTMsCjhKdrXFwwpKaRJZpiZKyAf1zuSj8ymR50l2R7tqaL65K3MsD/M O 3cD0qe8neslxyZQRxOwAa1qmKEeFv3PKlKNGW6TtHYLV/NEPHnyX6lVC0Ude4HqSga6sGmO86RrwWJIsGNKir4P76a/JvVn5G9QlN25Qm4dQCriS/6QNaEu5cw/vOm/9cv/HknhfkXT 6tXsW4yp8WlXL3cNB7 zKmiAIgiAIgj7JXDAYU3fMVBo8vYCXTyhP0oyw dweG8NUQmKytrykebPd8TSt1s1k455K/LHTg3uRaSjNbbDFj32H7rw8QUoN4fiI/qRrtjF/ 2oedxjA5ivZprUGtei3biZ9K0A70wC6TPbW7SbkjCAC/NJp1WMoPXz/5FpoMgrzahQ3ev1RTOrgAO4kWNLip1FcUV4kVmVDeeMA/v4nUNakTpMQwf2E7P jwjouA21qHKF3wknInkhe5TK2okx5K4xUZSlqKKGyKkPFavGkxj3kfvhT VdC1A 4cOw2P47oSGPLM5x87RmeBtiPGU9z6RTznMKw PQTLJ6VJzGC4JAnaDIC2LfyPN1 m8q82yp2XgL7EZNogRuO2269qBuZMSuK16VWJQ03V11//alNcug5ntzJqB9d2h0AicLN29O4cAB/nIgQVxgEQRAEQfgoyFswSIVQGhWh/sDZ9C5bBCNSiQ8JxGvJOJbtjs6agGkI3zmOflH9GDy2CwNW9sXKROJpVAg3d87nxOE7xL arjoCl7E/sqr8X4zZNoXAJjO48GwveEYwl08F0am7hIdbPu5zUAeze9BYzOeNoPea3xlrYYg6 Qnx4b5cuPfKLv1EF1aPdMJyTg9m/D0ERWIofptn4rw/kAR97yTKo1zKqv1YfnY4FZ61TPnF/NlLQ/TvDrQb40667IzU3N22jYuj5jJsYj3c/ v18r0JChuq1y2FQSk7Zrl1eOkv0078l6 /3cNjrYaI7RMZbTqFiWPmsuwniL1 kmVd53HwwYvprtyYlRUrYaeI4sTtJ/ncAqbfeHIlq350DL9QdfpOaYPi2BQO3hHXFwRBEARB DhItUwqFZC7dAX9U2I3dBNOi8pxcUgfpv0VKrbBfCiKYjRZvoNfOj9kSbMh7LkrWkIQBEEQhI DeFDLv5qa xt YuqmRJqu3cbsrqVEg38IihJ8tWIrC3umsW/gJPaKxYIgCIIgCB8RZQkDy1kfOgjhXUrmwaljXEuzIP3yWfwe6XQniKAPWjWFypUgfMU01rm enO/IAiCIAhCwSa2JAmCIAiCIAiCkCOxQ0UQBEEQBEEQhByJBYMgCIIgCIIgCDkSC4aPjWRKte/HM3FwDR3fuicIgiC8d8rytJg6hX4tivL6W4A gIIWz/v0/1z2/BDzDSEbsWAATL cxO6HHmyZ8NnbHRSmtti3aUZV63c4FElFqNl3EF2blkaZVzhyyqWnmPVWh /T 2gvQX9Ee72RVKw7q2NvczUp88dzRzuMPnRQH6t30cdUVfh6/Pd8 alJwZikFrR43qe3Kfv/4/ijw3xDyMO/oP9kLhikItgPX4TTTW88Y67gfGYRveoXeavBxKhaH1bcCcDr/HDKv6GnGVXqwKyrPhxeVO dTDAlixZMcjvBsYc XIq9ysmru1g4uyOVC79aKgnjshWxtSiKXRUbDN4iT2XVPszdOYXW5QrCOkxeufQTs/7q8H16P 2loPjQ7VxKejGhy/y5hfvW1hi w5z/bQrW8VVwaGOP49iwPd3 8wMbvcRT0N6G6GNCTkTfEN7Gv6H/qEBBie8X89uC6txcOptxnlBrxCTG711MUsPhHHyoyTuVVxOt1I2F 0fxiSbttUdIKq2q0XL4cAaPaEk5E4lH inH6wysKPtZaUKXOPDTGSXFazaj27gFbG35CaPaLuXKk2eRaYn5Yzw9b5QhI9Cfp 8qnvfufZbr31qHepTqxq/NF3Ix7dl/aNHEh vw5m5ByIE6nvCAeFAUp06yeOidIAiCoH8KVFX4dnQTOODIFMeDuJ84yFqH bhITfi 3ycoAUWpdiy8dYNDa5tjmXWCXirWktn vuxb9Dlm2U7aS b1Gbl9HOYbhrPg8ONXFgxKKg6ZzahmyRwaMJ5dd3NZjEiWfLnsMGdDjzC1vVU r3ZoeHLXDz8Pd06vn8 I9gvxreDAT8M/QUG2S/mJVzl0/iAHNrz5Ur5kUYuuC39l3YWTHAu5hme8Px7hbqz sXzmJRqD/zApIIDLroOxMypPf9eArLPIgbisboIBIBXtyK P/Nk3q3q2S3vGNFnviZf3OKrqeJlFWWcAK709uBjni8vVrfzcszLGz KVUy4ZMcshuw7NqtJ5uRN7717jUvxN3EPdOXhmMg0L61ZuWekoilJz2FzWerhyLtqXs35/MndkXSyedSI9lV0n2kTC/W9x5 azn9vcDU18fny8ff0Y0GjtJTwPdH9 jD5n2p5fIj2Y3iKzZFKxNkz3OMfZKH 8H/tw6qoTU/p ikn241gf7SVZ0HDGBpy8XXGJ8MMr7hrHL65lRDvbl68qqkrQYOIytvtfwTPGG czvzKweYkXx4m 2kuyoOGsTez0ucj52AC8oi9x4Pgi jYp9tLezDyPdzkxy8wrz74qN568iq6v8UdZhSEXb3JyRcMX9W7UhsUxN9k0wjYzHhntrqzlwAqvC5yPvs5p701M/3UVu 5e5dzNHYz7upj8etZTPLL7mIz2wqQibRdt4Z/7vlyKvsT Q4P5LB X0fM8TuUeX/qKR86YkEd7yW53OfUsh4yy51nPMvuGnHE1L3LrJ6 83ud8A9Bfe2FA8WYOTD9wiKNhfnjF eB6y5nlI6u KEdeYwLyxsw8PyN3bMlrnP8Q8413RCUVq03NihquL/PA3GEDf00zxqn9eNwva2j2RS0spABiwo4yb3Adtu5bwOzLPRi3JZkWS2fTKnYTQ2Z7kvhs1qMoRssVS2jpPweHX32xW/JqdmpuLexOhwVatCp7Rs3LLbJy1GtZiSIW0KBJOZTOMbztxXZ10D72nhzHvI4tKPdLIHdjjzLn88sUUljRdp0T/XP4O8nmczoPbYnWaT5L59wnJiEDlbk1UlAoGoB0Hza2a8ve2oNY8XsjPAcNYZtvBqBFHR9BBqB97M4593QaN2tAaaUf99WAqgp1Pjcn1tWTIB0LJxkkEbBiDk53MijTZTgj1m/CNKEjs5wfo5VTLhkxyyErL1TUmLqKqR1D2PzzMNyCklCY21C2fDohybqUWk46hbCfuoU1g9M4OHsm664lYtmkH Nmr2duQkfGOIWh0VPZ9Ucf9aMhOiwSrb01FgqINbDEtpSCmLvRpFlbU1SK5FZE5gJd 9if44tncORhNMlSUT7tPZ4JK38j VZ7lnum6ykeQDLBrlFjqiX wbQfzhAnFaP2kAkM3rqEuAZ92RmkBsyo57iF5Q4ZHJ8zmdX Cir3GcXwPVsp2qkrv7gl6q2vIplg16ABlWKcmDz6DE8MS1F34ChG/rMFq07dWX4hs3B5Hu9yYpaVl4y KiuevOl7/MmznvNod2XJqtSq IA/Os0noNMCFvdPZEvPwQR/N5 ZSwZy2mUhPuky6llP8cjrYzLaSypKs2WbmdMhhoNzJrD4ngF2zbrj8IXu1ZjncSqnXHqLR86YkHd7yWt3ecdFnmSWPc96ljn 5D2u5k1e/eSd13udb8gcx/KmoNi3C9myuTVqlx04jV1O8KOnGBa3w/SeDmMv8sZMfYyrssb5AjffyD VwsYGSymB6xEpmDUpjaWVMSUtkrkYnoxUpxiWSojJ0JLguoQpC6qzaf4yplSNo2mrEDa0XIPf88FCgU23WUys68aspseJ0iixe1OOWq28N92mX8Np2BxSmkt4rL qp0pN4cGdcKSmpSmhhLtpCTy6nQCKJGLy3EeTwh3nvZw8 aYDP4XYu/eIt4wnXZtG/P0ggm pX/6INpYLBy TsbQ5jcts4n6wBoVdferaJXHF5Tppb0g1Nxmeu1m9/gipAGcCMfj0CCN bMeaozt5pJZTLhkxyyErLxVFi1tA3FmunPXCLzozHx9XXTPLOx3Jph2DR5bm4ujWLN6d9VZl70AM6royt2cLbLZvJ0Kjp7LrwqgNi6ICXvw7zZuldfuy875GVrnypiHiXjiUKIG1UiKmyzz WlWYlbV YE JkhTThBL6IKuM6fe5tO/ 87/09zWmXrcV1Pq8JArPEDR6a6 syB5c5ewJd1KBy35m1PWdQuOmRdkVFA0l2 MwwI5bizowe3UQasDj3B0MKh9k0IR2bD3/F9Fa/baXNtSXC2cvZcZzNgDO7uOHCe3Y7r6HmOeDU87HuyQnZhl5xRaT01fzjkdeofU7/siRa7sDaGK4e8WH8ya JPUvQrDHZU7ixYRuFShrAr4m8uv5bePRyhgP5Ywtkbbf0LurFT4zv2feugdogItn1dQZUh8rXSswz M073JJpfUVj4yxV8Zx8QTybncjXY6LnCnklj3PepY5/shsrzzlUT8 8TLyeo/zjUhr/bQXhnXoN6c9Zq6z6NntT8KeV7H784/IGntljOEvvOW4miX375QPMN94R7Jd0c7A37EH33zWhRUX31R5qQQum8gKTzs6D/uCsKXT2X7jRbeTLJszak5NLs9cxsU4feyj1RBzYSdr5v7BlUjd76PI2Ye6Q11D9KFDXEqzp8U3tiiQKNr4CyqnenLunE6n2d Q9EOueYSirFqV8gXyEUUpuC Yx3GpK2tunOT3TRPo2qo8pjrf 5N3OqrqtahmUphm69zwiL2BZ wNPGM9cOxkhrJUKYp9qPuN0s6z/MuO9Pgi66fJJJzDnvVrfdSPlqT7IcRZlKRkYXO aFcfA6U9TVpYYVSmNJaPgnmQtaBTFKtH71Vb2X3jIq5hnhx1n0LDQhKGxs9uwdZXe71OE/WA0ESJIpaZD1VQVbOnimEYV9zu83wIzQjGyy0UA3t7Kr7r67Vpd3A/G4ZhzRqy88p3zK/k9X776jscf Tk/kq7v/xLLVokJAWg0aBFQqGQ3mnfyDWeHMhpL2WVT6mkDMfXU 5Z1ZzlfZzmXS79xSNj7NW1vXJqdz0dF3LLnp96fpfpPJdD/cjL6/3NN/TVXorSNbG3VeOz9zjhOcynP/j3hRz5 E75WKg0kZHEagtjXcIESR3Po4eAZEGxkiZoo6KIzdZwitL1 OIzAxLiM6jUpQPV1i7DNynzd6atvqOVrTXKTW602JT5f5LKAJU0ht1h9VhYcxD7Ij70DXnGlKlUAh4 5FH2Din3qkeeck9HG3OaQ0cnM797O8qu28knLWujPj8Pz8dvm7sEkvR6OWSVS09lzyOvtNv7mPb5Wba1bkebrt8wcOcghnmvZVLvlXjHyo8gz3QkCdQP2T9gGDtuvDLqpMcT/tKlKn21uwzP7mFIffOv9VE/6jt3CNF QWn7ZpRr4MvWX5V069iczy6VRrpzhvsZgKI0XbduZGy5i6yfPgb3wCdIVo0ZvnP8S2fd9NVer9OgUYOkeDFNy3nC9mo 76K9tKDRgCTp9Ixp THnkpdOffXt6Wf80aDRgNJA1zMTr7f7i8DUqNUatG8II 961nc8ufQxOe2l1aLJNrHLN5nH6eteKZe 4kHemKDTcZFTu vruJBTdp3qOZe ke/2yi3 HOpHZl7vbb6ht/bSoAE0mtyXtvkbe/Mjv2NLTt8p73G 8Y4otFHXuB6koEarBpg/u2HGogEN6iq473GN532rUDX6b55Obd8FODSdhUepQcx1bPz8b5KPzKZHnXZ0 6IDPb7oQI8vujBnTzQZAdsY/ U0TkbpWlUKrBr1Yvj0PtSx0c pNkW5jnRpZUTQYReCX rXqaQ81YKFOa89dVUXKSmkSWaYmecQr/YJbhsP8Kj6d3T sglffinhtfcsb31BxqA8n39pS7qPL3deujgko1x5xSybjLzSY7nlvIPfHHrSqeFigmoPY3Tfsrq/DCSXdDJu BCYVpIaNYwJv3WX4Ow/92J4ab4uq z674f5KZcc2ug7BEWXpObI76h5 QC7Nx7Cr25n jUrQ SN25n3GhlUoUYdY 5sW8aWfZfwvxHATY8bhKe8oRPqq71ykXHTl4C0UtRpYpftprZy1G9iS7qvH0HZ 7Pe mo2itLUamCL2t fezK/2HSKOZe8dOqrcmjTSUvTgpnpm2 01Mf4o4klJlqDWYVyWOmpGdJPTaNl8R85kvDy/8uqZ33Hk0sfk9NemZ8pRf0Wld7uZkZdjtNc6C2eZ3Ibe3U8LnJsdz0dF7LKrks95zb 6Km9ssupfmTn9Z7mG/pqL02oH/7hSmp0bkXxHF76kO xNz/yO7bk9J1S0OYb aAiI4B9K8/T7bepzLutYuclsB8xiRa44bjtVtZlHxNqT1vMkNIuTG2yi7uR4DihCbs2OzL2eGfmHnuMJiGC wkvJ20dl4E2NY7QO EkPJugG1tRprwVRqqyFDWUUFmVoWK1eFLjHnI//OmLFZhBLfqtm0nfCtDONIAuk73zcR DAvMK1alWV41ltSZ0nTiAWsHbGLUmkJfWC9pE7vjcRzGyF0P7RXI22pzSypvsOXALXXaaqYMDuJNgSYufRnFFeZFYlQ3ljQP4 58X aV57uTvKz0ZtGYSkuI8847F5WvVKZWuQeNm0SQUKk29/j/yQ7Vg/up8JNsebHnlkhOzLLnmZUzdMVNp8PQCXj6hPEkzwuZze2wMUwmJSdKh/Hmno404zMZ1fVk7bj1rimzk7xOBxKYXwrpySeKP7ORCyIuzF7LKrpd  PblkiXjNv43DOj5dRWO9jlNTIQS5/OTmN9JyamNdzPLlBFEgF86rXoMpYfvn1wLTUZhXo3iRtlnmPpqr7xpww zZbMDq39eway0VRwNUFCp10gGVQ9hX6cj2faj6q vqr7oyYhhEl5B6dh2/pEh9WI43vsIcnc yopZyjsvXfqqvMCecM//EcoBPRnUK4oLT4pgyw32Hb6jv/FHG4enszdpSwYzdXIcu9weoS5ak IK9H5cyOsb o0n1z4mo720Ec5s3uTAmglrWKJYxb7zYaSa16SEAt0eoSzrOM2b3uKRM/bKaC85m3P0dVzIKrsO9Zxr39BTe8miQ17vZb6hr3EszZvtjqdptW4mG/dU4o dHtyLTENpboMtfuw7dAe1Dt8Xb02HsU7Od0rBmW/knwo0RGyfyGjTKUwcM5dlP0Hs9ZMs6zqPgw8yS2tUfzj/HVqYYz/MwyUys0Vi9i/gtx7OzFg4nEPnFnBV5rY4ZdV LD87nArPrvKUX8yfvTRE/ 5AuzHu2Q7kYC6fCqJTdwkPt2DdJq8A6TGE3Ayl cjfcZqoJj4kAO/903FYeoDA Fd7lZqAlbPYYD H3r spmNqBP5bZ3Dk4C0SdOmAiS6sHumE5ZwezPh7CIrEUPw2z8R5f CLdNT3 WfpEb7/qws4TeOcrst9bTL3PS5xr/u3zP2nP4bqBMKuuLDm26X84Zake7nkxCxLLnlRCKVREeoPnE3vskUwIpX4kEC8loxj2e5o QOYJCedZK7N oEhD8YwbNBApva3ppAmkchbnmy7sOvl9OSU/W37od7KJYM2gQDve6R/6sXeEwmgBdctx4hs8wl 17IOUHUwuweNxXzeCHqv Z2xFoaok58QH 7LhXtJ o1HliQuT vPuMdTGDlqIcuttcTcOMeW7gvZ/OpTcPTUV7VpZlQfPosedsYkB3tzeOhEVji/ gho/cSce1469FVZMvBdMZtt1afx7cq1dE2J4OaWGRxzvqO/8QcNYZsn8bPNDEYPcGTFZCM0T OJCvTi5J3kD9A39BxPrn1MTnsl4T29H6MiJzLM4b8snlgYZeoTogK9OHZbh8W2nONUFj3FI2tM0OFYzpW jgsZZdelnnPrG3prLxl0yeu9zDf01V4awneOo19UPwaP7cKAlX2xMpF4GhXCzZ3zOXH4DvFaffUxefHIHVtkfacUlPnGW5BqmVT62LdVfXQUlQex5XwnPL/uwpprBWn9KAj/YopS9Dp6irFRP/Hl90d03/JTUPPSkRh/BOH/hzje36ECPM6/CwXymTr/RlLhsnz6iSmSuT1d5g3Het9Edl4XB68gCO eGH8E4f HON6Fd0EsGN4TVa3ezN/zA6XUEfjtnceYSS689cMKBEEQZBDjjyD8/xDHu/AuiC1JgiAIgiAIgiDkqOA9t0kQBEEQBEEQhAJDLBgEQRAEQRAEQciRDguGQlQd hO9/1MklzftCTpRlqfF1Cn0a1H0461TyZRq349n4uAa4oYYQRAEQRCEfyH5CwalNRUaf8OYQ06M 8ry453gFiSqKnw9/nu /NTkpfo0/XISux96sGXCZ283CTe1xb5NM6pav8PWkopQs 8gujYtTQ4vZ3wRjpxyvY YBUEQBEEQBNleWjAYVerArKs HF5U7/UJnfoBzgP7Me 0Fb22LqJz bymh29QuAVTr3lyIS6AKwn XHxwlp17ptG5trlYgDwnYVy2IrYWRbGrYpPzK 1lUFbtw9ydU2hdriDsPJNXroIVsyAIgiAIgqACUFpVo Xw4Qwe0ZJyJhKPcvp02n0ODZtI1XObGTm7Da79nInV4RlLkqoIJcoW5s5SBxYcSsKkxCd8OXYC0w7ZQYOh7H8g8xXi/2paYv4YT88bZcgI9Ofphw5Hb/6t5RIEQRAEQfh3U4CSikNmM6pZMocGjGfX3dwn7donnqx3PIWifT  qZiPqwxoSXwQSOB1H64c38Nvg9dw1bQhrVtm2 akKErNYXNZ6 HKuWhfzvr9ydyRdbHI oCylgMrvC5wPvo6p703Mf3XVey6e5VzN3cw7utiLy6bqErQYOIytvtfwTPGG czvzKweYnnW2fMuizHNd6FCQ2yX09RUmnSAS6FLqNFYXnxyGZSkbaLtvDPfV8uRV9i/6HBfJYta6lYd1bH3uZq4lUOnT/IgQ3tMHpDMpJFLbou/JV1F05yLOQanvH eIS7sfrH8pllN/gPkwICuOw6GDsNQhWPAAARRUlEQVSj8vR3DeBq0m2uJgXisroJBoBUtCO/PvJn36zq2bYSGdNkvSde3uOoquNeKGWdAaz09uBinC8uV7fyc8/KGOtSLhkxC4IgCIIgCO fAtTcWtidDi0n4XTyIWl5XjHQ8vjoAS4kVaNp6xJv/ZglbWISyRoJAyODrAVDIeynbmHNlCoEb5zJqK8dmP17FDVnr2fuD6VQAMqSValV8QF/dOmL45kSdPyhGG5DBrPQ1YaeSwZS3QDAjHqOW1j UyXurZrMmG5T fNuFQbu2cq4JmYAJJ09hVdySRp /emLSbPSjibtK/PU5RReifLikUUqSrNlm5nTtwhXFkxgTJ/Z/OmdiCrbokMbe5Q5n39Nlzq92XApPeekbD6n89CWmHptYung4Qxv wOjHeaz7WQoGoB0Hza2a0u3H/4iLC2Uf35oT5faX9Oldhv6zblMBqB97M4593RKN2tA6WeFV1WhzufmxJ7/X3v3Hphz f9x/Pn5bHPYmPMIJbEcflYk9a2ICjEd5CvH5JB0mlJI SYS/XKqrSKHsilWyymHUZLThs0522zY2ByHGTvZbLvv /sHxpabe M74vX463Z/Pruu63375/3 XNf1ucKJK ShkIZLBjHTRzOk82Cmry/Hs9O 58MO5TEcjcuBMYuIiIhI8Tv3HNlmo1Cnt2XGEBVt8GijOjhxPkktNIMSlTxp Z8 NMvewld/HMcKGB7evOpTk41vt2V8UPK5cW3djUvTtXza7Sk8fvyRZADrSfZt20moawQZfcoRH7aFP9jM4Bfv4S5XiHDtQN9 tdgz7lk mRyHBQhbF4uL52L6D/YmIPQXkk6HsnLVGT7t0BrPMZHE5IJ5bzvaeKURMmEtqTbHxpPowA9g1nyGHp0rsXPkS4ydehArsHGNhQcGNKPShZssaRzbmwZmBievumYni9jg fzxx US8CyS9 0npWIKObZsUhLiiN9jyX LLZn1i7eQO lJmt/5PQnxVsxazWhaK4Ntq/4i  oh5ZMbHsTkacs4C7B6Ny71l/HWm95MWR7IMYficmDMIiIiIlLsijZBYE0jNdWGq3uZIjTgwr/8Qgg7Fc3GhKWM9T6Bf9f3 CXuXHLo3KgxDV3L0mpqCGHJUYQnRxGeHMaY58vgVL06VQp2aLVhw8AwAasVGwamaeDc0It6JY6wLSSBvLQzN57NIYdx8fKijgtgO01o0BrSPNvyVCMnwAnPzt7UPf47S1amF208djjVq09dp6NEhB8pYoF1vVlJWrKETdlePPVMDUwMKjT/F55nw1m37sw1Nn2IHWGHcWrQgNp616qIiIjIP1rR0jnTjbJlDDKT0ouQ/Oay47OXGPNrJvcMmMSYZ5OJiz55sR3DAMshfu33OrOjCjxhzknhaMG1KTYLFosV22WmSOxvMbh4c/rK fx57DvadrmP6THOPNftHg4FDWfrhSfhhR2P3S5tWM8XM47cW6gZH/sNXbEd28k/WbL8Az7r4s1dUwO5t3UTLKFjCT99rb0b5363gnE4FNf1il1EREREroeiFQyl6lG/gY19S Mo/KIRG1nHEojfk8z ER9S77HZDBkdzNY315Big9yonezO7sR995Xi6MKIc0tcCihxyeeclR/Ruuq5z5dujM3dFUFMdiceaFELp03nx l8N81a1CAnIpK4Cyt5zoQz78c4nuvTlbbRJWnvsYPv/CPz1sw7Mh5HXGin2VN1cQmPwf4OBYCzZGXaoLw7ZQ04W9QMOiuLbKMMZdxNuNz/lC2VkBmLOLb033R8/CCVHzfY/MEaTl1rxu5Sm4cfr0HOzghi8wXqQFxXG7OIiIiIFKtzBUOpStxZuxIlne iQgkD50p3UqdhCmdPHSLhaGaBJ74GZZ/sQPOyMcxZkXhty2sydzJr EK8539A34AwfMOzsCUuZcbUXnz77jSmlJvB3BW7Sc4pTWXPO0hZFsj6A471aDu6FP ZfZn8vh jsr9heYxJ3e4 9G90gAXPLyMpLygLewPmsHXgRwyfZJC19D2C4y/2cd3GkxjMzO/7MmXwFCaY37Ag9Ahn3e nmsnfiwdbOrE7EzB9uvNa7 OsSXKnptMu5i3aU6gU2hIfQ2xaRZ4aMpBtThtJdvagdqkY5i7cnddOdnggc7d1o/ UYRhmKGN/O1WkJ/xGzfto3iqJtNI1ebDPm7zcMJ5fOi7j5KWNORCXI2MWERERkeJjAjg16I1vWDBzw3x5obYzHt3H8/Pmpcz4oMnfpyBKN6LX8HaYv81icey1p3AZa6cza0M1Oo/sTA0T4Aw7Rr3MgKEryHrsFf4TOJMpQePwefkR7ixXmPeYZrDloz68  U 6gz8HN gsXT33It/l758GZKe707rocX88HMSpUrsY77vn6Tky5iv33i2jujNwDFbce/yIeMXBfDNd/ m8u7N/LU3o0CSbiHm61FMX1uS1hMn88W0d2j/UFVcC/sa1/RVTPaZxe7qXfl4rj9fzXibNk2q5G/HksDCScvIqlGNzEVzWVfY6QXbGRLCNrG/aic XfgDU378kHYVtjKlUx/8QjIK3OxAXI6MWURERESKjdHYta7jGaJZhRa s5nY8RATWg1g3j49870VmJ798Q99nvCnX2DKDr3AVEREREQucnwPg1mNJ/y Z0zXbBb0HMZ8FQv/aEbZu6h/rxuGuxcvjH2DyguGEviXigURERERyc/xgsGaQuKudUzrOJ3ZG4q2zl1uHs6Ne/DZvJepbkkkcv5Y3hm2imt OZKIiIiI3HIKtyRJRERERERuK0U7uE1ERERERG4LKhhERERERMSuQhQMpWnw2hB6PFTuCicoi4iIiIjIrcTxgsGpMvc0f4Z3lszi3Scq3n5Fg1sNvNq1okFl 5G7PT6MoENh A/ vyIeoS0iIiIicnMxwcC9SWcGz/2VZYcj2HRiM0tWf0nfllXyVxOWgwS/0puxf1aie8A4OtZ2KnRnRoVOfJ28m9VBL CR17gLD/ttIGxhZ8rfxFWIU4OefBo4nLZ326uxDErdVYca5StQq54HLsU6OhERERGR/w0Tp1p4j/GhaeoKpg14g3de8SPMuSU gaNo71Egg89OYMnrQ5l36jF8PmlHxSIl Cbl2w/ijTa32tImGyfnvEe3Fh3pMWg1mTd6OCIiIiIi14GJJZ6gjq3p9coUFgWHsnHxbMZ/sIBEt8bc3 DvC2tsqeFMG7MSs0NvnqlT FkGrCfZFpJKm9H9aFDSzj3O1Xhk6Jf8GL2N8JNbCV79Ba88WY3C9mZUaceIsHWsORHN1tM7Wbl9FsN71cc1X6XiQtVWfRmxaAnLj0Sy dRO1u4Jxtenwbn XB5iWEwMW9a Sq2StemzNobtGXvZnrGbVZNb4AIYVbowOXkv29O3syR0MYume3PZ0K4Wl1GeRz ezqyta1mVGMnmUzv4feO3vOVdQ0ucREREROSGcAaw5eRy8dxmA9fqVXHLPUDCgcud5mzj9PJFrM/wo2XbasyOPYy1UF3mEvftRGL/fxIDe/3CW98dL3C9DA O8ce3by6/j/6AydEmnj0H8sa8ACo835mJIekO92Q7Hc3v4z9m2aEkzhgVqN/jPQZ//RVn9nTANzwHMKnS6XP8Z7bFsmo2swb5En8skxJVa G2/3xcOTuZ4d2e U364/fdY4T3H8APEbmADUtKIrmALXk5ox/eQmmzEu2nzqLPZUfjQFyGK7Uea07D9Dl89PJqThlVaDJgMK8GTODUI70IjNPp2iIiIiJSvP724NqlzguMGNOS41P78et O6VAZgxR0QaPNqqDE4UtGMCWGsbMidsJev9VHvx5bL5rxh0d6NuvFnvGPcsnk OwAGHrYnHxXEz/wd4EhP5CkqNHzeUksGlBQt4/oyNK8eCLfjR  A7M8ANYSzxA79EdKLN2FN1e/Jkjefn4hksaySJ5335SKqaQY8smJSGO D0FEndLGsf2poGZwUk7a5Eciuv8vdaD21mzYgNngS2RZWgaMZzmLSvwU1ySTtgWERERkWKVbwdv6UY9GR88Es/Q4bz7yRYy7P2VNY3UVBuu7mWKeJCDlWM/f82CrGd5pUfNfG04N/SiXokjbAtJuDjrkRvP5pDDuHh5UacQu4nNKg/S45sAgqI2svZIOMs3DOfR0gYlSpU4d73m/XjVsLBz/u8c/R8/vC9qXNYTBzmcblCu4q2250NERERE/gnO5 oGbg  hl/wUGr8NpgBry3lcM6V/sqNsmUMMtPSCz27kOdsJD/5bqXeGy/RqFT S/YT40I8Xzdr0jlgBoOeOMOKEe/wepveDH57DpEZl7Rhs2IFrFZHorBdvXfble8pWlxWrBYwTJULIiIiIlL8TACzWntGBL5FpV8H8eZ7KzmWe5W/KlWP g1s7IuMo gP5q2cmDedJcbzvNjaLS Zzt0VQUx2dR5oUeviZmDnu2nWogY5EZHEXamQuZRLPe57oBSxP3yJ/4JNREfFsCssiqNZF5Nz6 FIoo86cV/HNlS92o7qrCyyjTKUcb/SnMpZsjJtUN6dsgXy  sWl4iIiIhIMXIGF7zeeY8njZWMnXWE8vXvpfz5i9b0ROIPpBaYRTAo 2QHmpeNYc6KxKLPMABkbiNoxh46j2uW95Xt6FL8Z/Zl8vt jMr huUxJnW7 9C/0QEWPL/M8f0LuXHERObQputrdI34mR2Hz2C6N6RqyUsy eyt/DjmT9pMHcmMeXWZExjG/uPZOLl7UINIFiyJzSuILPExxKZV5KkhA9nmtJFkZw9ql4ph7sLdF4smWzqxOxMwfbrzWu/jrElyp6bTLuYt2oPFkbg0iSAiIiIiNxlnTA8aNa2OS/VajAp5Nt/F7BUf8nSneZy NEkv3Yhew9th/jacxbHXuvDfyuE5Afw5pClt8r7LYMtHfXj39HB8Bn6Ob2UbJ6PW4d/lc2YW4g1JWOIJ6j8I97Fv0WPKdwwqXwLLmVRSjkawfv F3RlWjga S 8TvXl10Av0 7oXlVwNMk8cYFfgZ6xYGkvKhdjTVzHZZxYVR3fl47kDMNMPEzlzJMG/7iYt7/exEPP1KKZ7jabHxMk8dzaR6ICPWbZ4D2m26xSXiIiIiEgxMhq71nV8Y4BZhRa s5nY8RATWg1g3j695lNERERE5Fbm HlgZjWe8PueMV2zWdBzGPNVLIiIiIiI3PIcLxisKSTuWse0jtOZveGUzgMQEREREbkNFG5J0hVsz9h71XuauHlej65ERERERKSYFO3cNRERERERuS2oYBAREREREbtUMIiIiIiIiF0qGERERERExC4TwLlBZ0YuD2b5wZ1sSt7G8hA/ j1eWdWEiIiIiMhtzgSwJB0hKngqo1/sQe/nPmZlbgveChjMo243engiIiIiInIjOQPYTmxg3jcXvooiac6LdBnnQWVXAzJ04oKIiIiIyO3qb6uOzCqP0ffVRhzy92d1kooFEREREZHbWb6CwfRoydClk2i6YShvDAslRfWCiIiIiMhtzTnvk1GO1hMm4H1kEt2GrOK45QaOSkREREREbgoXCwZsHFz0BZ/GLSNRxYKIiIiIiHBpwWDL4EjUXpyzrTdwOCIiIiIicjPJ28Ng3t2TSet/Ytb6cTxdwbiRYxIRERERkZtE3gyDLfUAcQfSqJO2l6NZ2u0sIiIiIiJgNHate12qg 0Ze696TxM3z vRlYiIiIiIFJO/ncMgIiIiIiJygQoGERERERGx67otSRIRERERkVuPZhhERERERMQuFQwiIiIiImKXCgYREREREbFLBYOIiIiIiNilgkFEREREROxSwSAiIiIiInapYBAREREREbtUMIiIiIiIiF0qGERERERExC4VDCIiIiIiYpcKBhERERERsUsFg4iIiIiI2KWCQURERERE7Pov3EaFl61mUUoAAAAASUVORK5CYII=[/IMG]

---

### Post by tea for one on 2024-10-08
Your screenshot is invisible.
"Dirty bit set" is probably the culprit after an ungraceful shutdown due to power loss.
Follow the repair instructions (I can't reproduce the problem without damaging my own ESP, although I have repaired this partition previously with fsck)

---

### Post by sdayanik on 2024-10-08
Apologies for failing to add the screenshot. I went ahead and applied fsck repair. Now it is not reporting any errors. Unfortunately, the laptop is still not booting. Stuck with the same grub screen.

---

### Post by tea for one on 2024-10-08
> **sdayanik said:**
> Apologies for failing to add the screenshot. I went ahead and applied fsck repair. Now it is not reporting any errors. Unfortunately, the laptop is still not booting. Stuck with the same grub screen.
When you reach the grub screen "Minimal BASH-like line editing is supported.."
Type exit and hit enter.
What happens?

---

### Post by sdayanik on 2024-10-08
The same grub screen comes back.

---

### Post by sdayanik on 2024-10-08
> **sdayanik said:**
> The same grub screen comes back.

Hmm. I tried a second time. Now it says "StartImage failed: Load Error"

---

### Post by sdayanik on 2024-10-08
> **sdayanik said:**
> Hmm. I tried a second time. Now it says "StartImage failed: Load Error"

OK. Rebooted again. Grub screen appeared. Typed exit and hit the key. The same grub screen came back again. If I try type exit and hit enter again, then "StartImage failed: Load Error" appears. Then it reboots by  itself. Back to the same grub screen.

---

### Post by tea for one on 2024-10-08
I've just noticed that I had an incorrect instruction in post 2.
I typed nvme0n1p1 twice by mistake - schoolboy error........
Can you boot into a live session again and run fsck on both partitions.
```
sudo fsck /dev/nvme0n1p1
```
```
sudo fsck /dev/nvme0n1p2
```

---

### Post by sdayanik on 2024-10-08
> **tea for one said:**
> I've just noticed that I had an incorrect instruction in post 2.
I typed nvme0n1p1 twice by mistake - schoolboy error........
Can you boot into a live session again and run fsck on both partitions.
```
sudo fsck /dev/nvme0n1p1
```
```
sudo fsck /dev/nvme0n1p2
```

No problem. Tried the new instructions. The second partition turned out to be clean. No new errors on the first. Rebooted, still no luck.

---

### Post by tea for one on 2024-10-08
Ah, that's a pity - I was very hopeful.
Boot into live session again, download the boot-repair utility and try the recommended repair.
All digits crossed for successful outcome

---

### Post by sdayanik on 2024-10-08
> **tea for one said:**
> Ah, that's a pity - I was very hopeful.
Boot into live session again, download the boot-repair utility and try the recommended repair.
All digits crossed for successful outcome

I did exactly that. After boot repair, tha computer experienced kernel panic. Apparently, initramfs for the default kernel was missing. Luckily an older kernel booted. I generated initramfs for the latest kernel as described in [this post]("https://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0"). Then the computer booted as usual.

Thanks for the help anyway. The dirty bit could have caused further trouble down the road.

---

### Post by yancek on 2024-10-08
Try running fsck.vfat or dosfsck on the first partition as it is a vfat filesystem and not a Linux filesystem.  fsck may detect the filesystem and run either but no harm in trying the commands.  The link below is to the manual pages for this software which gives an explanation and various options.  Unmount the partition before running fsck.

[https://man7.org/linux/man-pages/man8/fsck.vfat.8.html](https://man7.org/linux/man-pages/man8/fsck.vfat.8.html)

---

### Post by tea for one on 2024-10-08
> **sdayanik said:**
> I did exactly that. After boot repair, tha computer experienced kernel panic. Apparently, initramfs for the default kernel was missing. Luckily an older kernel booted. I generated initramfs for the latest kernel as described in [this post]("https://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0"). Then the computer booted as usual.
Thanks for the help anyway. The dirty bit could have caused further trouble down the road.
Splendid, well done.
I think that the "dirty bit" would need to have been repaired before the missing initramfs was spotted.
Anyway, all's well that ends well.
Worth marking the thread as solved?

---

### Post by yancek on 2024-10-08
Any time you have a sudden power loss it is likely to damage the filesystem so if you have problems in the future in that situation and booting fails, run a filesystem check on the unmounted partition.

---

