---
title: "Dual boot Ubuntu and Vmware Esxi using Grub bootloader"
date: 2020-09-25
forum: General Help
---

### Post by rdaji on 2020-09-25
Hello,

I need help on how to specify the Vmware Esxi path on the grub.cfg file.
I managed to add the menu entry but get different types of errors.

1) I added the below entry into the boot/grub/grub.cfg:

[COLOR=#202124][FONT=Roboto]menuentry 'VMWare ESXi' {        set root=(hd1)        drivemap -s hd0 hd1        chainloader +1}

[/FONT][/COLOR]Gave me the below Error: [COLOR=#202124][FONT=Roboto] ***"error: Invalid EFI file path.Press any key to continue... "***
[/FONT][/COLOR]
2) I amended the below entry into the boot/grub/grub.cfg:

[COLOR=#202124][FONT=Roboto]menuentry 'VMWare ESXi' {        set root=(sdb1)        drivemap -s sda sdb1        chainloader +1}

[/FONT][/COLOR]Gave me the below Errors:[COLOR=#202124][FONT=Roboto]
[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto][I][B]&#8220;can&#8217;t find command &#8216;drivemap' " 
"no server is specified"[/B][/I]

[/FONT][/COLOR]
Below is disk partitions in my server:



Disk /dev/sda: 447.1 GiB, 480103981056 bytes, 937703088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 4C359809-03B3-45EA-947D-61058EB6C7E9


Device         Start       End   Sectors   Size Type
/dev/sda1        512   1050623   1050112 512.8M EFI System
/dev/sda2    1050624  42010623  40960000  19.5G Linux filesystem
/dev/sda3   42010624  82970623  40960000  19.5G Linux filesystem
/dev/sda4   82970624 115738623  32768000  15.6G Linux swap
/dev/sda5  115738624 466812927 351074304 167.4G Linux filesystem




Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 9F43492A-8812-4572-AD7E-881EE1DD223B


Device        Start        End    Sectors   Size Type
/dev/sdb1        64       8191       8128     4M EFI System
/dev/sdb2   7086080   15472639    8386560     4G Microsoft basic data
/dev/sdb3  15472640 1953525134 1938052495 924.1G unknown
/dev/sdb5      8224     520191     511968   250M Microsoft basic data
/dev/sdb6    520224    1032191     511968   250M Microsoft basic data
/dev/sdb7   1032224    1257471     225248   110M unknown
/dev/sdb8   1257504    1843199     585696   286M Microsoft basic data
/dev/sdb9   1843200    7086079    5242880   2.5G unknown


~# lsblk

NAME   FSTYPE               SIZE MOUNTPOINT                       LABEL
sda                       447.1G
&#9500;&#9472;sda1 vfat               512.8M /boot/efi
&#9500;&#9472;sda2 ext4                19.5G
&#9500;&#9472;sda3 ext4                19.5G /
&#9500;&#9472;sda4 swap                15.6G [SWAP]
&#9492;&#9472;sda5 ext4               167.4G /var/lib/libvirt/images/accedian
sdb                       931.5G
&#9500;&#9472;sdb1 vfat                   4M                                  ESXi
&#9500;&#9472;sdb2 vfat                   4G
&#9500;&#9472;sdb3 VMFS_volume_member 924.1G
&#9500;&#9472;sdb5 vfat                 250M
&#9500;&#9472;sdb6 vfat                 250M
&#9500;&#9472;sdb7                      110M
&#9500;&#9472;sdb8 vfat                 286M
&#9492;&#9472;sdb9                      2.5G



Partition table entries are not in disk order.


Let me know if you require my grub.cfg file.

thanks heaps

---

