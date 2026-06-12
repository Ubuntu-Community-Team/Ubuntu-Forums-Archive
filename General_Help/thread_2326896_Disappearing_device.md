---
title: "Disappearing device"
date: 2016-06-05
forum: General Help
---

### Post by makem2 on 2016-06-05
I have an SSD drive in a DVD drive caddy which disappears if I shut down the laptop. If I reboot the laptop it is recognized.

After a shutdown:

```

makem@newTOSH:~$ sudo mount -a
[sudo] password for makem: 
mount: special device UUID=8bd0b7e3-f657-43d2-b412-7dc9a37f9097 does not exist
mount: special device UUID=be063e8a-9244-48e4-8738-0858b1798a65 does not exist
makem@newTOSH:~$ 

```

Partitions listed after a shutdown:

```

makem@newTOSH:~$ sudo parted -l
Model: ATA TOSHIBA MQ02ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  1075MB  1074MB  ntfs            Basic data partition          hidden, diag
 2      1075MB  1180MB  105MB   fat32           EFI system partition          boot
 3      1180MB  1314MB  134MB   fat32           Microsoft reserved partition  msftres
 4      1314MB  82.7GB  81.3GB  ntfs            Basic data partition          msftdata
 5      82.7GB  450GB   367GB   ntfs            Basic data partition          msftdata
 8      450GB   516GB   66.6GB  ext4
 9      516GB   980GB   464GB   ext4
10      980GB   986GB   6300MB  linux-swap(v1)
 6      986GB   987GB   500MB   ntfs                                          hidden, diag
 7      987GB   1000GB  13.2GB  ntfs            Basic data partition          hidden, diag


```

fstab (edited to remove entries for system HDD for clarity) showing entries for SSD


```

# /etc/fstab: static file system information.
#
# /dev/sdb3    /home/makem/linux2    ext4    defaults    0    1
#/dev/sdb4    /home/makem/data    ext4    defaults    0    1


UUID=8bd0b7e3-f657-43d2-b412-7dc9a37f9097       /home/makem/linux2    ext4    defaults,errors=remount-ro    0    1
UUID=be063e8a-9244-48e4-8738-0858b1798a65       /home/makem/data    ext4    defaults,errors=remount-ro    0    1


```

Partitions after a reboot:

```

makem@newTOSH:~$ sudo parted -l
Model: ATA TOSHIBA MQ02ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  1075MB  1074MB  ntfs            Basic data partition          hidden, diag
 2      1075MB  1180MB  105MB   fat32           EFI system partition          boot
 3      1180MB  1314MB  134MB   fat32           Microsoft reserved partition  msftres
 4      1314MB  82.7GB  81.3GB  ntfs            Basic data partition          msftdata
 5      82.7GB  450GB   367GB   ntfs            Basic data partition          msftdata
 8      450GB   516GB   66.6GB  ext4
 9      516GB   980GB   464GB   ext4
10      980GB   986GB   6300MB  linux-swap(v1)
 6      986GB   987GB   500MB   ntfs                                          hidden, diag
 7      987GB   1000GB  13.2GB  ntfs            Basic data partition          hidden, diag




Model: ATA OCZ-VERTEX2 (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system     Name  Flags
 1      1049kB  316MB   315MB   fat32                 msftdata
 2      316MB   318MB   2097kB                        bios_grub
 3      318MB   32.5GB  32.2GB  ext4
 4      32.5GB  118GB   85.4GB  ext4
 5      118GB   120GB   2147MB  linux-swap(v1)




makem@newTOSH:~$

```



Can anyone suggest why the devices would not exist after a shut down but exists after a reboot?

---

### Post by makem2 on 2016-06-06
This drive is now unusable as it is never discovered.

Edit: I now find that after a shutdown the drive is not detected but if I then reboot the drive is detected.

It is as if the drive does not have power following a shutdown so is not detected, but does have power during a reboot and is detected.

---

### Post by makem2 on 2016-06-07
[COLOR=#000000]Thank you all for your input.[/COLOR]

[COLOR=#000000]The SSD is not compatible with Intel chip set 8 or greater. My chipset is greater.[/COLOR]

[COLOR=#000000]Reason why it works in Windows - windows does not need special drivers.[/COLOR]

[COLOR=#000000]It 'may' work as a main drive.[/COLOR]

[COLOR=#000000]This information comes from OCZ the suppliers of the SSD. As a matter of interest that are part of Toshiba, have online chat and great quick support.[/COLOR]

[COLOR=#000000]Having had the SSD as a gift I have lost nothing but have gained much knowledge and also got the bug for SSD[/COLOR]

[COLOR=#000000]I am considering the OCZ-Vector-180-SSD-VTR180-25SAT3-240G-2-5-SATA-6Gb-240GB-SSD.[/COLOR]

[COLOR=#000000]They supply free cloning software (one of the worries I had) and a 5 year guarantee.[/COLOR]

[COLOR=#000000]I will dispose of the SSD somehow and have the new SSD as main drive and the current HDD in the caddy.[/COLOR]

---

