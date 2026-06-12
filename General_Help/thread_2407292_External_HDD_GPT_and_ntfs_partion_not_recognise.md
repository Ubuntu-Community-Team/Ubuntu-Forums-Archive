---
title: "External HDD GPT and ntfs partion not recognise"
date: 2018-12-02
forum: General Help
---

### Post by kxp on 2018-12-02
I have a Toshiba 3TB external HDD connected via USB 2.0 into a Ubuntu server using GPT and a NTFS file system. When I connect it in Windows 10 everything works properly, but I once I plug it into the Ubuntu server it doesn't work. 
It doesn't recognize the sdaX partion.

It also appears the the system thinks he only has 2TB. I did some googling but nothing clear showed up.

Ubuntu Version 
```
Linux kserver-2 4.15.0-39-generic #42-Ubuntu SMP Tue Oct 23 15:48:01 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

lsusb
```
Bus 001 Device 007: ID 1058:1021 Western Digital Technologies, Inc. Elements Desktop (WDBAAU)
```

lsblk
```
NAME         MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
loop0          7:0    0 87.9M  1 loop /snap/core/5742
loop1          7:1    0 88.2M  1 loop /snap/core/5897
loop2          7:2    0 87.9M  1 loop /snap/core/5662
sda            8:0    0    2T  0 disk
mmcblk1      179:0    0 58.2G  0 disk
&#9500;&#9472;mmcblk1p1  179:1    0  512M  0 part /boot/efi
&#9500;&#9472;mmcblk1p2  179:2    0    4G  0 part [SWAP]
&#9492;&#9472;mmcblk1p3  179:3    0 53.8G  0 part /
mmcblk1boot0 179:8    0    4M  1 disk
mmcblk1boot1 179:16   0    4M  1 disk
```

fdisk -l (removed the other drives)
```
Disk /dev/sda: 2 TiB, 2199020109824 bytes, 4294961152 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x8ac87419

Device     Boot Start        End    Sectors Size Id Type
/dev/sda1           1 4294967295 4294967295   2T ee GPT
```

Dmesg output:
```
[ 1572.230499] usb 1-1: new high-speed USB device number 6 using xhci_hcd
[ 1572.379174] usb 1-1: New USB device found, idVendor=1058, idProduct=1021
[ 1572.379183] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1572.379188] usb 1-1: Product: Ext HDD 1021
[ 1572.379193] usb 1-1: Manufacturer: Western Digital
[ 1572.379198] usb 1-1: SerialNumber: 373845574547524153
[ 1572.379907] usb-storage 1-1:1.0: USB Mass Storage device detected
[ 1572.382058] scsi host2: usb-storage 1-1:1.0
[ 1573.415716] scsi 2:0:0:0: Direct-Access     WD       Ext HDD 1021     2002 PQ: 0 ANSI: 4
[ 1573.416922] sd 2:0:0:0: Attached scsi generic sg0 type 0
[ 1573.417158] sd 2:0:0:0: [sda] 4294961152 512-byte logical blocks: (2.20 TB/2.00 TiB)
[ 1573.417737] sd 2:0:0:0: [sda] Test WP failed, assume Write Enabled
[ 1573.418215] sd 2:0:0:0: [sda] Asking for cache data failed
[ 1573.418275] sd 2:0:0:0: [sda] Assuming drive cache: write through
[ 1573.442319] sd 2:0:0:0: [sda] Attached SCSI disk
```

---

### Post by oldfred on 2018-12-02
Its not gpt:

> Disklabel type: dos

You need to redo with gpt or convert to gpt.

Also Windows 8 or 10 uses fast start up which is really hibernation. It sets hibernation flag on all NTFS partitions.
And the Linux NTFS driver will not default mount a hibernated NTFS partition. You can manually mount read only. 
Fast Start up off (always on hibernation), note that Windows turns this back on with update.[URL="http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472"]
http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472[/URL]
 [http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

    I would make sure fast start up or hibernation is off in Windows.
Maybe run chkdsk and defrag which you only can do from Windows or your Windows repair disk.

Best to have good backup, just in case, but Windows, Windows third party partition tools, & Linux have tools to convert from MBR to gpt.

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html) 
[https://docs.microsoft.com/en-us/windows-server/storage/disk-management/change-an-mbr-disk-into-a-gpt-disk](https://docs.microsoft.com/en-us/windows-server/storage/disk-management/change-an-mbr-disk-into-a-gpt-disk)

---

### Post by kxp on 2018-12-02
According to windows its already a GPT.
[https://imgur.com/ud3mbuL](https://imgur.com/ud3mbuL)

When I attempt to convert within the power shell it returns an error saying that cannot convert.

Should I do this process in a Linux environment?

Not sure if it helps but the final usage it will be using this disk as network storage using samba.

---

### Post by oldfred on 2018-12-02
Your fdisk shows a mismatch.
Disklable says MBR/dos, but the gpt protective MBR says gpt.

If a gpt drive is converted to MBR by Windows install in BIOS boot mode, it does it incorrectly and leaves some gpt bits and is running with MBR.

What does this show:
sudo gdisk -l /dev/sdX
Where sdX is your 3TB drive as sda, sdb or sdc?

You may have created this? Which is not recommended. It was used on Mac that was UEFI/gpt, back when Windows was only BIOS/MBR for dual boot on the Mac.
       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

### Post by kxp on 2018-12-02
> 
What does this show:
sudo gdisk -l /dev/sdXr>
Where sdX is your 3TB drive as sda, sdb or sdc?
It says gpt with a protected MBR.I already tried to erase it but now only seems to detect 2TB.
fdisks now says 2TB with the disklabel gpt.

How can I get the 3TB back? 
I backup the content.

---

### Post by oldfred on 2018-12-02
Post these:
sudo parted -l
sudo fdisk -lu
sudo gdisk -l /dev/sdc #or whatever drive it is

---

### Post by kxp on 2018-12-03
Here it is:

```
parted -l
Model: WD Ext HDD 1021 (scsi)
Disk /dev/sda: 2199GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  16.8MB  16.8MB               Microsoft reserved partition  msftres


Error: /dev/mmcblk1boot0: unrecognised disk label
Model: Generic SD/MMC Storage Card (sd/mmc)
Disk /dev/mmcblk1boot0: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

Error: /dev/mmcblk1boot1: unrecognised disk label
Model: Generic SD/MMC Storage Card (sd/mmc)
Disk /dev/mmcblk1boot1: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

Model: MMC DF4064 (sd/mmc)
Disk /dev/mmcblk1: 62.5GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32                 boot, esp
 2      538MB   4833MB  4295MB  linux-swap(v1)
 3      4833MB  62.5GB  57.7GB  ext4


```


```
fdisk  -lu
Disk /dev/loop0: 87.9 MiB, 92123136 bytes, 179928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 87.9 MiB, 92114944 bytes, 179912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 88.2 MiB, 92483584 bytes, 180632 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mmcblk1: 58.2 GiB, 62537072640 bytes, 122142720 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 34574641-6238-4122-A43E-CE321995D2AA

Device           Start       End   Sectors  Size Type
/dev/mmcblk1p1    2048   1050623   1048576  512M EFI System
/dev/mmcblk1p2 1050624   9439231   8388608    4G Linux swap
/dev/mmcblk1p3 9439232 122140671 112701440 53.8G Linux filesystem


Disk /dev/mmcblk1boot1: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mmcblk1boot0: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 2 TiB, 2199020109824 bytes, 4294961152 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: E85C6F6D-772E-479E-BCCA-1AE40F096B28

Device     Start   End Sectors Size Type
/dev/sda1     34 32767   32734  16M Microsoft reserved
```

```
 gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.3

The protective MBR's 0xEE partition is oversized! Auto-repairing.

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 4294961152 sectors, 2.0 TiB
Model: Ext HDD 1021
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): E85C6F6D-772E-479E-BCCA-1AE40F096B28
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 4294961118
Partitions will be aligned on 8-sector boundaries
Total free space is 4294928351 sectors (2.0 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34           32767   16.0 MiB    0C01  Microsoft reserved ...
```

---

### Post by oldfred on 2018-12-03
Now all three tools show 2TB and one the small Microsoft reserved partition which it requires for any NTFS partition with gpt.

We have see a lot of users with older or inexpensive external USB caddies or cables that do not support either gpt or drives over 2TB.

---

### Post by kxp on 2018-12-03
But how could it work with Windows? At least it was displaying 3TB.

What if I plug it into my desktop and configure it in a live Ubuntu?

---

### Post by oldfred on 2018-12-03
If you can easily plug into a desktop directly with SATA port and partition with gparted there, and then see what the 3 partition tools say when plugged back into your USB adapter.

Be sure to choose gpt first before anything else. But gparted should see it as 3TB and only use gpt.

---

### Post by kxp on 2018-12-03
I manage to plug it into a sata port and the partions were all messed up. 
After erasing the MBR/GPT and making a new GPT everything was okey. After confirm it twice I plugged into the USB adapter and the problem was back, only 2.2/2TB available.
Seems like your suspicions were right, the adapter might be too old. 
Tomorrow I will get a new one, lets see how it goes.

Meanwhile, thanks for the help :)

---

### Post by kxp on 2018-12-05
It worked! Replacing the External Case worked perfectly!
Thanks :)

---

