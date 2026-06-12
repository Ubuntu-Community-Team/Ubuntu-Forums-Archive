---
title: "Grub minimal commandline on startup"
date: 2024-08-20
forum: General Help
---

### Post by kosecosa on 2024-08-20
Hi new to the forum. Wasn't sure where to post this so posted in general help.
When booting the computer I am first met with a Grub minimal command-line. 
Writing exit shows me the grub boot screen letting me pick between Ubuntu and Windows.
I would like to boot straight to this selection screen without having to write exit in the minimal command-line.
Googling lead me to believe it's something to do with the boot order starting up the wrong grub first then the correct one.
efibootmgr -v returns this:
```
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0000,0003,0002,0001,2001,2002,2003
Boot0000* Ubuntu    HD(1,GPT,a35208a8-c5f7-4c98-8258-a22ada66db3e,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
      dp: 04 01 2a 00 01 00 00 00 00 08 00 00 00 00 00 00 00 20 03 00 00 00 00 00 a8 08 52 a3 f7 c5 98 4c 82 58 a2 2a da 66 db 3e 02 02 / 04 04 34 00 5c 00 45 00 46 00 49 00 5c 00 75 00 62 00 75 00 6e 00 74 00 75 00 5c 00 73 00 68 00 69 00 6d 00 78 00 36 00 34 00 2e 00 65 00 66 00 69 00 00 00 / 7f ff 04 00
Boot0001* Windows Boot Manager    HD(1,GPT,a35208a8-c5f7-4c98-8258-a22ada66db3e,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000032000100000010000000040000007fff0400
      dp: 04 01 2a 00 01 00 00 00 00 08 00 00 00 00 00 00 00 20 03 00 00 00 00 00 a8 08 52 a3 f7 c5 98 4c 82 58 a2 2a da 66 db 3e 02 02 / 04 04 46 00 5c 00 45 00 46 00 49 00 5c 00 4d 00 69 00 63 00 72 00 6f 00 73 00 6f 00 66 00 74 00 5c 00 42 00 6f 00 6f 00 74 00 5c 00 62 00 6f 00 6f 00 74 00 6d 00 67 00 66 00 77 00 2e 00 65 00 66 00 69 00 00 00 / 7f ff 04 00
    data: 57 49 4e 44 4f 57 53 00 01 00 00 00 88 00 00 00 78 00 00 00 42 00 43 00 44 00 4f 00 42 00 4a 00 45 00 43 00 54 00 3d 00 7b 00 39 00 64 00 65 00 61 00 38 00 36 00 32 00 63 00 2d 00 35 00 63 00 64 00 64 00 2d 00 34 00 65 00 37 00 30 00 2d 00 61 00 63 00 63 00 31 00 2d 00 66 00 33 00 32 00 62 00 33 00 34 00 34 00 64 00 34 00 37 00 39 00 35 00 7d 00 00 00 32 00 01 00 00 00 10 00 00 00 04 00 00 00 7f ff 04 00
Boot0002* ubuntu    HD(1,GPT,a35208a8-c5f7-4c98-8258-a22ada66db3e,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
      dp: 04 01 2a 00 01 00 00 00 00 08 00 00 00 00 00 00 00 20 03 00 00 00 00 00 a8 08 52 a3 f7 c5 98 4c 82 58 a2 2a da 66 db 3e 02 02 / 04 04 34 00 5c 00 45 00 46 00 49 00 5c 00 75 00 62 00 75 00 6e 00 74 00 75 00 5c 00 73 00 68 00 69 00 6d 00 78 00 36 00 34 00 2e 00 65 00 66 00 69 00 00 00 / 7f ff 04 00
Boot0003* ubuntu    HD(1,GPT,a35208a8-c5f7-4c98-8258-a22ada66db3e,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
      dp: 04 01 2a 00 01 00 00 00 00 08 00 00 00 00 00 00 00 20 03 00 00 00 00 00 a8 08 52 a3 f7 c5 98 4c 82 58 a2 2a da 66 db 3e 02 02 / 04 04 34 00 5c 00 45 00 46 00 49 00 5c 00 75 00 62 00 75 00 6e 00 74 00 75 00 5c 00 73 00 68 00 69 00 6d 00 78 00 36 00 34 00 2e 00 65 00 66 00 69 00 00 00 / 7f ff 04 00
Boot2001* EFI USB Device    RC
      dp: 7f ff 04 00
    data: 52 43
Boot2002* EFI DVD/CDROM    RC
      dp: 7f ff 04 00
    data: 52 43
Boot2003* EFI Network    RC
      dp: 7f ff 04 00
    data: 52 43

```

I tried changing it with sudo efibootmgr -o but after a reboot it was back to the old boot order.

---

### Post by Rubi1200 on 2024-08-20
Please run and post the output for these commands:

```
sudo fdisk -l

sudo lsblk -f
```

---

### Post by kosecosa on 2024-08-20
fdisk -l
```
Disk /dev/loop0: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 10.08 MiB, 10571776 bytes, 20648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 313.03 MiB, 328237056 bytes, 641088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 63.95 MiB, 67051520 bytes, 130960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 74.24 MiB, 77844480 bytes, 152040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 74.24 MiB, 77848576 bytes, 152048 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 10.72 MiB, 11239424 bytes, 21952 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 269.63 MiB, 282722304 bytes, 552192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: SKHynix_HFS512GD9TNG-L3A0B              
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: AB4BC259-3369-4C53-B308-5A342610E93F

Device             Start        End   Sectors  Size Type
/dev/nvme0n1p1      2048     206847    204800  100M EFI System
/dev/nvme0n1p2    206848     239615     32768   16M Microsoft reserved
/dev/nvme0n1p3    239616  499439615 499200000  238G Microsoft basic data
/dev/nvme0n1p4 998639616 1000212479   1572864  768M Windows recovery environment
/dev/nvme0n1p5 499439616  998639615 499200000  238G Linux filesystem

Partition table entries are not in disk order.


Disk /dev/loop8: 505.09 MiB, 529625088 bytes, 1034424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 10.32 MiB, 10821632 bytes, 21136 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 10.54 MiB, 11051008 bytes, 21584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 38.73 MiB, 40615936 bytes, 79328 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 38.83 MiB, 40714240 bytes, 79520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 476 KiB, 487424 bytes, 952 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 500 KiB, 512000 bytes, 1000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 149.63 MiB, 156901376 bytes, 306448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

lsblk -f
```
NAME FSTYPE FSVER LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINTS
loop0
     squash 4.0                                                    0   100% /snap/bare/5
loop1
     squash 4.0                                                    0   100% /snap/canonical-livepatch/282
loop2
     squash 4.0                                                    0   100% /snap/code/167
loop3
     squash 4.0                                                    0   100% /snap/core20/2318
loop4
     squash 4.0                                                    0   100% /snap/core22/1380
loop5
     squash 4.0                                                    0   100% /snap/core22/1439
loop6
     squash 4.0                                                    0   100% /snap/firmware-updater/127
loop7
     squash 4.0                                                    0   100% /snap/firefox/4173
loop8
     squash 4.0                                                    0   100% /snap/gnome-42-2204/176
loop9
     squash 4.0                                                    0   100% /snap/gtk-common-themes/1535
loop10
     squash 4.0                                                    0   100% /snap/snap-store/1124
loop11
     squash 4.0                                                    0   100% /snap/snap-store/1173
loop12
     squash 4.0                                                    0   100% /snap/snapd/21465
loop13
     squash 4.0                                                    0   100% /snap/snapd/21759
loop14
     squash 4.0                                                    0   100% /snap/snapd-desktop-integration/157
loop15
     squash 4.0                                                    0   100% /snap/snapd-desktop-integration/178
loop16
     squash 4.0                                                    0   100% /snap/thunderbird/507
nvme0n1
                                                                            
&#9500;&#9472;nvme0n1p1
&#9474;    vfat   FAT32       E865-F037                              63.2M    34% /boot/efi
&#9500;&#9472;nvme0n1p2
&#9474;                                                                           
&#9500;&#9472;nvme0n1p3
&#9474;    ntfs               36BC6C70BC6C2D15                                    
&#9500;&#9472;nvme0n1p4
&#9474;    ntfs               FA96EED796EE9403                                    
&#9492;&#9472;nvme0n1p5
     ext4   1.0         5d1464b5-41bf-4807-b702-1ee8b0e066f1    210G     5% /var/snap/firefox/common/host-hunspell

```

---

### Post by oldfred on 2024-08-20
I might delete the duplicate UEFI boot entries with sudo efibootmgr -b XXXX -B parameters.
see
man efibootmgr

But I do not think that is issue.
If you can boot and ESP mount in fstab is correct, just reinstall grub May make another entry in UEFI, you can then check again for duplicates.
But normally new Ubuntu entry should overwrite previous entry.
This uses all defaults, only run from a booted system with correct esp mount in fstab.
sudo grub-install

---

### Post by kosecosa on 2024-08-21
How do I check if ESP mount in fstab is correct?

---

### Post by tea for one on 2024-08-21
> **kosecosa said:**
> How do I check if ESP mount in fstab is correct?
```
redact@gmktec:~$ lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint
NAME          SIZE TYPE FSTYPE FSUSE% FSAVAIL MOUNTPOINT
nvme0n1     232.9G disk                       
&#9500;&#9472;nvme0n1p1     1G part vfat       1% 1015.8M [COLOR="#0000FF"]/boot/efi[/COLOR]
&#9500;&#9472;nvme0n1p2    40G part ext4      52%   16.7G /
&#9500;&#9472;nvme0n1p3    30G part ext4      41%   15.7G /home
&#9492;&#9472;nvme0n1p4   100G part ext4      75%   20.1G /mnt/381ee381-e1af-4ca4-9a8d-fcccf
redact@gmktec:~$ 

```
Should be where I've indicated above in blue

You can also see the mountpoint in Disks (gnome-disk-utility)

---

### Post by kosecosa on 2024-08-21
Running efibootmgr shows:
```
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0003,0002,0000,0001,2001,2002,2003
Boot0000* ubuntu    HD(1,GPT,a35208a8-c5f7-4c98-8258-a22ada66db3e,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* Windows Boot Manager    HD(1,GPT,a35208a8-c5f7-4c98-8258-a22ada66db3e,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000032000100000010000000040000007fff0400
Boot0002* ubuntu    HD(1,GPT,a35208a8-c5f7-4c98-8258-a22ada66db3e,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0003* Ubuntu    HD(1,GPT,a35208a8-c5f7-4c98-8258-a22ada66db3e,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC
```
I tried removing all ubuntu enteries using the following commands:
```
sudo efibootmgr --delete-bootnum --bootnum 0
sudo efibootmgr --delete-bootnum --bootnum 2
sudo efibootmgr --delete-bootnum --bootnum 3
```
Resulting in:
```
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0001,2001,2002,2003
Boot0001* Windows Boot Manager    HD(1,GPT,a35208a8-c5f7-4c98-8258-a22ada66db3e,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000032000100000010000000040000007fff0400
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC
```
Then I ran:
```
sudo grub-install
```
Resulting in:
```
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0000,0001,2001,2002,2003
Boot0000* Ubuntu    HD(1,GPT,a35208a8-c5f7-4c98-8258-a22ada66db3e,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* Windows Boot Manager    HD(1,GPT,a35208a8-c5f7-4c98-8258-a22ada66db3e,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000032000100000010000000040000007fff0400
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC
```

After this it boots like I want directly to the grub boot selection screen. I can boot windows and nothing changes, but if I boot into ubuntu it recreates the extra enteties and I am back to booting into the grub minimal command line interface which I have to use the exit command on before being booted into the correct selection screen.

efibootmgr after first reboot (working as intended):
```
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,0001,2001,2002,2003
Boot0000* ubuntu    HD(1,GPT,a35208a8-c5f7-4c98-8258-a22ada66db3e,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* Windows Boot Manager    HD(1,GPT,a35208a8-c5f7-4c98-8258-a22ada66db3e,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000032000100000010000000040000007fff0400
Boot0002* EFI PXE 0 for IPv4 (60-6D-3C-4B-97-EF)     PciRoot(0x0)/Pci(0xd,0x0)/USB(1,0)/USB(0,0)/MAC(606d3c4b97ef,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0003* EFI PXE 0 for IPv6 (60-6D-3C-4B-97-EF)     PciRoot(0x0)/Pci(0xd,0x0)/USB(1,0)/USB(0,0)/MAC(606d3c4b97ef,0)/IPv6([::]:<->[::]:,0,0)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC
```
efibootmgr after second reboot (not working as intended sending me to grub minimal command line)
```
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0004,0000,0001,2001,2002,2003
Boot0000* ubuntu    HD(1,GPT,a35208a8-c5f7-4c98-8258-a22ada66db3e,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* Windows Boot Manager    HD(1,GPT,a35208a8-c5f7-4c98-8258-a22ada66db3e,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)57494e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d0034006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000032000100000010000000040000007fff0400
Boot0002* EFI PXE 0 for IPv4 (60-6D-3C-4B-97-EF)     PciRoot(0x0)/Pci(0xd,0x0)/USB(1,0)/USB(0,0)/MAC(606d3c4b97ef,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0003* EFI PXE 0 for IPv6 (60-6D-3C-4B-97-EF)     PciRoot(0x0)/Pci(0xd,0x0)/USB(1,0)/USB(0,0)/MAC(606d3c4b97ef,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0004* Ubuntu    HD(1,GPT,a35208a8-c5f7-4c98-8258-a22ada66db3e,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC
```

---

### Post by oldfred on 2024-08-21
What brand, model system?
sudo lshw | grep -m 1 -A 1 "product"
What version, flavor of Ubuntu?
lsb_release -a
I use Kubuntu so it would show plasma.
[FONT=monospace][COLOR=#000000]echo $DESKTOP_SESSION[/COLOR]
[/FONT]

---

### Post by kosecosa on 2024-08-21
sudo lshw | grep -m 1 -A 1 "product"
```
    product: 81Q9 (LENOVO_MT_81Q9_BU_idea_FM_Yoga C940-14IIL)
    vendor: LENOVO
```
lsb_release -a
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 24.04 LTS
Release:    24.04
Codename:    noble
```
[FONT=monospace][COLOR=#000000]echo $DESKTOP_SESSION
```
ubuntu
```
[/COLOR][/FONT]

---

### Post by tea for one on 2024-08-21
In your UEFI settings, do you have various Security options i.e.
TPM or FTPM (or similarly names)
If you disable them, does it allow Grub to behave itself?

---

### Post by kosecosa on 2024-08-21
I have the following security options (besides different kinds of passwords):
- Intel Platform Trust Technology
- Clear Intel PTT Key
- Intel (R) SGX
- Secure Boot
Tried disabling Secure Boot without it changing anything.

---

### Post by tea for one on 2024-08-21
> **kosecosa said:**
>  Intel Platform Trust Technology
Try disabling Intel PTT - you never know ;)
There is very little consistency in UEFI settings (even within PCs from the same vendor)

Edit:- Intel PTT enabled on my Lenovo Ideapad 11.6" prevents booting Xubuntu completely.
Screen message displays "Reset system"

---

