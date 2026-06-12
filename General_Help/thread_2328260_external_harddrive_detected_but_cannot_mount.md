---
title: "external harddrive detected but cannot mount"
date: 2016-06-19
forum: General Help
---

### Post by derfred on 2016-06-19
hi there,

i know the title has been around for a while, and i have dug my way through multiple forums yesterday. yet, it seems, that none of the answers (which did become quite repetitive) worked for me.
so I shall dare asking here, hoping you will just shake your head, pointing me to the one link I have overseen

THE STORY:

i recently bought an intenso 4TB harddrive and it worked fine on all laptops available to me with all sorts of different OS (windows 10, lubuntu) - i used it to back all my data and set up my laptop with ubuntu 16.10 (which was not as straightforward as it sounds, as i I was missing a DVD, I tried the server version but failed to install lubunut-desktop. So I borrowed a USB on which I put 16.04 and installed it from there - regular installation with LVM - everything worked nicely, i. e. i am now on lubuntu 16.10. weird thing though: the bootable USB failed to boot, when I tried again to see if my harddrive shows in live USB)

THE ACTUAL PROBLEM:

The Intenso 4TB HDD does not show in the file manager and cannot be accessed. Not on ubuntu, not on windows (two different machines).
The windows Disk Management Tool shows me that my harddrive is plugged in and partitioned. Trying to assign a disk name via right click is not possible, as the option is greyed out.
In Ubuntu I get the following results for different tests:

```
derfred@ghettofred:~$ lsblk
NAME                   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                      8:0    0   3,7T  0 disk 
&#9500;&#9472;sda1                   8:1    0   3,6T  0 part 
&#9500;&#9472;sda2                   8:2    0     4K  0 part 
&#9492;&#9472;sda5                   8:5    0  93,8G  0 part 
sdb                      8:16   0 232,9G  0 disk 
&#9500;&#9472;sdb1                   8:17   0   487M  0 part /boot
&#9500;&#9472;sdb2                   8:18   0     1K  0 part 
&#9492;&#9472;sdb5                   8:21   0 232,4G  0 part 
  &#9500;&#9472;lubuntu--vg-root   252:0    0 228,5G  0 lvm  /
  &#9492;&#9472;lubuntu--vg-swap_1 252:1    0   3,9G  0 lvm  [SWAP]
sr0                     11:0    1 625,5M  0 rom  

```
yesterday it used to be sdb - don't know why that changed - may be because i used the 'mount' command?

```
derfred@ghettofred:~$ sudo dosfsck /dev/sda1
[sudo] Passwort für derfred: 
fsck.fat 3.0.28 (2015-05-16)
Logical sector size is zero.

```

```
derfred@ghettofred:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 174c:55aa ASMedia Technology Inc. ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0a5c:2145 Broadcom Corp. BCM2045B (BDC-2.1) [Bluetooth Controller]
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. AES2810
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
derfred@ghettofred:~$ sudo mount -t vfat /dev/sda1 /media/georg/
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

```
derfred@ghettofred:~$ dmesg | tail -n 20
[ 7823.582915] usb 1-1: USB disconnect, device number 6
[ 7823.587547] sd 7:0:0:0: [sda] Synchronizing SCSI cache
[ 7823.704113] sd 7:0:0:0: [sda] Synchronize Cache(10) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 7826.732117] usb 1-1: new high-speed USB device number 7 using ehci-pci
[ 7826.866397] usb 1-1: New USB device found, idVendor=174c, idProduct=55aa
[ 7826.866404] usb 1-1: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[ 7826.866408] usb 1-1: Product: USB 3.0 device
[ 7826.866413] usb 1-1: Manufacturer: Intenso
[ 7826.866417] usb 1-1: SerialNumber: 8050000000000000099D
[ 7826.874346] scsi host8: uas
[ 7826.875760] scsi 8:0:0:0: Direct-Access     Intenso  USB 3.0 device   0    PQ: 0 ANSI: 6
[ 7826.879675] sd 8:0:0:0: Attached scsi generic sg0 type 0
[ 7826.879997] sd 8:0:0:0: [sda] Spinning up disk...
[ 7827.884118] .......ready
[ 7833.909669] sd 8:0:0:0: [sda] 976754646 4096-byte logical blocks: (4.00 TB/3.64 TiB)
[ 7833.911031] sd 8:0:0:0: [sda] Write Protect is off
[ 7833.911037] sd 8:0:0:0: [sda] Mode Sense: 43 00 00 00
[ 7833.911780] sd 8:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 7833.959075]  sda: sda1 sda2 < sda5 >
[ 7833.962544] sd 8:0:0:0: [sda] Attached SCSI disk

```

```
derfred@ghettofred:~$ sudo fdisk -l
Medium /dev/ram0: 64 MiB, 67108864 Bytes, 131072 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 4096 Bytes
I/O Größe (minimal/optimal): 4096 Bytes / 4096 Bytes


Medium /dev/ram1: 64 MiB, 67108864 Bytes, 131072 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 4096 Bytes
I/O Größe (minimal/optimal): 4096 Bytes / 4096 Bytes


Medium /dev/ram2: 64 MiB, 67108864 Bytes, 131072 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 4096 Bytes
I/O Größe (minimal/optimal): 4096 Bytes / 4096 Bytes


Medium /dev/ram3: 64 MiB, 67108864 Bytes, 131072 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 4096 Bytes
I/O Größe (minimal/optimal): 4096 Bytes / 4096 Bytes


Medium /dev/ram4: 64 MiB, 67108864 Bytes, 131072 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 4096 Bytes
I/O Größe (minimal/optimal): 4096 Bytes / 4096 Bytes


Medium /dev/ram5: 64 MiB, 67108864 Bytes, 131072 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 4096 Bytes
I/O Größe (minimal/optimal): 4096 Bytes / 4096 Bytes


Medium /dev/ram6: 64 MiB, 67108864 Bytes, 131072 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 4096 Bytes
I/O Größe (minimal/optimal): 4096 Bytes / 4096 Bytes


Medium /dev/ram7: 64 MiB, 67108864 Bytes, 131072 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 4096 Bytes
I/O Größe (minimal/optimal): 4096 Bytes / 4096 Bytes


Medium /dev/ram8: 64 MiB, 67108864 Bytes, 131072 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 4096 Bytes
I/O Größe (minimal/optimal): 4096 Bytes / 4096 Bytes


Medium /dev/ram9: 64 MiB, 67108864 Bytes, 131072 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 4096 Bytes
I/O Größe (minimal/optimal): 4096 Bytes / 4096 Bytes


Medium /dev/ram10: 64 MiB, 67108864 Bytes, 131072 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 4096 Bytes
I/O Größe (minimal/optimal): 4096 Bytes / 4096 Bytes


Medium /dev/ram11: 64 MiB, 67108864 Bytes, 131072 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 4096 Bytes
I/O Größe (minimal/optimal): 4096 Bytes / 4096 Bytes


Medium /dev/ram12: 64 MiB, 67108864 Bytes, 131072 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 4096 Bytes
I/O Größe (minimal/optimal): 4096 Bytes / 4096 Bytes


Medium /dev/ram13: 64 MiB, 67108864 Bytes, 131072 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 4096 Bytes
I/O Größe (minimal/optimal): 4096 Bytes / 4096 Bytes


Medium /dev/ram14: 64 MiB, 67108864 Bytes, 131072 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 4096 Bytes
I/O Größe (minimal/optimal): 4096 Bytes / 4096 Bytes


Medium /dev/ram15: 64 MiB, 67108864 Bytes, 131072 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 4096 Bytes
I/O Größe (minimal/optimal): 4096 Bytes / 4096 Bytes


Medium /dev/sdb: 232,9 GiB, 250059350016 Bytes, 488397168 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 512 Bytes
I/O Größe (minimal/optimal): 512 Bytes / 512 Bytes
Typ der Medienbezeichnung: dos
Medienkennung: 0xfb77bfe4

Gerät      Boot   Start      Ende  Sektoren Größe Id Typ
/dev/sdb1  *       2048    999423    997376   487M 83 Linux
/dev/sdb2       1001470 488396799 487395330 232,4G  5 Erweiterte
/dev/sdb5       1001472 488396799 487395328 232,4G 8e Linux LVM




Medium /dev/mapper/lubuntu--vg-root: 228,5 GiB, 245312258048 Bytes, 479125504 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 512 Bytes
I/O Größe (minimal/optimal): 512 Bytes / 512 Bytes


Medium /dev/mapper/lubuntu--vg-swap_1: 3,9 GiB, 4181721088 Bytes, 8167424 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 512 Bytes
I/O Größe (minimal/optimal): 512 Bytes / 512 Bytes


Medium /dev/sda: 3,7 TiB, 4000787030016 Bytes, 976754646 Sektoren
Einheiten: sectors von 1 * 4096 = 4096 Bytes
Sektorengröße (logisch/physisch): 4096 Bytes / 4096 Bytes
I/O Größe (minimal/optimal): 4096 Bytes / 268431360 Bytes
Typ der Medienbezeichnung: dos
Medienkennung: 0x00071df0

Gerät      Boot     Start      Ende  Sektoren Größe Id Typ
/dev/sda1             256 952179711 952179456  3,6T 83 Linux
/dev/sda2       952179966 976754431  24574466 93,8G  5 Erweiterte
/dev/sda5       952179968 976754431  24574464 93,8G 82 Linux Swap / Solaris

```

```
derfred@ghettofred:~$ sudo mount /dev/sda1 /media/georg/ -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.


```

did i forget something?
probably. 

thanks for any kind of hint!

btw: i do not want to lose the data on the disk.

---

### Post by banceu_sergiu_ione on 2016-06-19
Try a [boot repair]("https://help.ubuntu.com/community/Boot-Repair") ( use the 2nd option via terminal ) from the live USB. Do not reboot at end of processes but go for Shut Down. Once the pc is off, unplug the live USB and leave only the HDD plugged in. Switch on and see if it boot.

If that don't work try this via USB live terminal

> sudo sh -ec "apt-get install lvm2; vgchange -ay" 

> sudo mount /dev/sda1 /mnt

> sudo mount /dev/sdb1 /mnt/boot

mount critical filesystem

> for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done

chroot intoo the system

> sudo chroot /mnt

reinstall grub

> grub-install /dev/sdb

> update-grub

exit chroot : CTRL+D on kayboard

shut down / remove USB install media

---

### Post by derfred on 2016-06-27
Thanks for your reply!

I am not sure if I made myself clear. I have a stable lubuntu 16.10 on my system right now (so I do not see the need for a live USB atm). The 4TB external harddrive should not have any bootable section on it (unless I completely messed up and accidentally installed a live system on it, which should have gone on the USB).

So why would I want to boot from the HDD?

I did try the boot-repair part though (17972078), and now when booting with a switched on HDD it stalls with my hp-logo showing <press Esx to change boot order> <press F10 to enter setup> 
pressing either of the two does not give any result.
would the second part you proposed (which to my dismay, I do not understand) help?

edit: i had the HDD checked by an it-service from my university and they said that the data is not recoverable. i do not like to believe that. 
[http://askubuntu.com/questions/716161/external-usb-harddrive-not-recognized](http://askubuntu.com/questions/716161/external-usb-harddrive-not-recognized)

---

### Post by banceu_sergiu_ione on 2016-06-27
So what you say is that you have an external HDD ( with only data on it, not OS ) and possibly its dead ( as an IT had checked it ) and you try to see if you can mount this HDD and recover the data? Meanwhile you have a system run good.
The 2nd part wont help. 
Just plug off the external HDD and run your system. Once log in, plug back the external drive and see if you can mount it with GParted.
If GParted do not reconize it and is not able to mount, will be hard you get it.

---

### Post by banceu_sergiu_ione on 2016-06-27
You can try this also.

Use blkid command to find the exact type format

```
sudo blkid
```

And then you can try to use once again the mount command giving the exact type of format. Just in case the vfat type you used before is not the right on.

```
sudo mount /dev/sdXY -t *type format* /media/georg
``` #pay attention if mount path change /sdXY to replace as well *type format*

Let me know if work and if not the type format.

---

### Post by oldfred on 2016-06-27
You are showing LVM which is an advanced logical partitioning system.
Windows tools will not see any Linux partitions. And standard Linux tools do not see LVM partitions.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by banceu_sergiu_ione on 2016-06-27
> **oldfred said:**
> You are showing LVM which is an advanced logical partitioning system.
Windows tools will not see any Linux partitions. And standard Linux tools do not see LVM partitions.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

I had thought at this too 1st when seen it. But he try to mount the /dev/sda disk which it not have an install OS on it either a boot, but is only a backup data HDD. He can boot on his /dev/sdb, see lsblk output.

Seen this 
> derfred@ghettofred:~$ sudo mount -t vfat /dev/sda1 /media/georg/
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

on output
-notice wrong fs type, so i asked for a blkid output to see the right fs type
- bad superblock --maybe will need a check of superblocks and an attempt to fix it ( maybe the use of dumpe2fs with a fallow attempt to fix it with e2fsck in case teh mount with the right fs type not work ) 
What do you think ?

---

### Post by oldfred on 2016-06-27
I cannot really tell much from the lsblk. But it shows sda1 as 3.6TB, which should then be a FAT32 partition as that is for smaller partitions.
Post this
sudo parted -l

---

### Post by derfred on 2016-06-29
wow, thank you so much for the help.

here are the replies from my terminal:
```

/dev/sda1: UUID="5cf79b42-cf3b-4ad4-bd56-ef1bcecac7a3" TYPE="ext2" PARTUUID="fb77bfe4-01"
/dev/sda5: UUID="mQYhri-l5L9-4z2A-Czzq-ckuO-wj1K-SmJLXK" TYPE="LVM2_member" PARTUUID="fb77bfe4-05"
/dev/mapper/lubuntu--vg-root: UUID="0f8a4486-8dd3-48e3-8ba8-7229f0a861b8" TYPE="ext4"
/dev/mapper/lubuntu--vg-swap_1: UUID="0589b343-4396-4920-8efd-0b79ac342191" TYPE="swap"
/dev/sdb5: UUID="cd8aa90a-148c-40dd-86a9-7ee987b1fd85" TYPE="swap"
/dev/sdb2: PTTYPE="dos"
derfred@ghettofred:~$ sudo mount /dev/sdb2 -t dos /media/georg/
mount: unknown filesystem type 'dos'
```

I  hope the German won't confuse you.

```
derfred@ghettofred:~$ sudo parted -l
Modell: ATA TOSHIBA MK2552GS (scsi)
Festplatte  /dev/sda:  250GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos
Disk-Flags: 

Nummer  Anfang  Ende   Größe  Typ       Dateisystem  Flags
 1      1049kB  512MB  511MB  primary   ext2         boot
 2      513MB   250GB  250GB  extended
 5      513MB   250GB  250GB  logical                LVM


Modell: Intenso USB 3.0 device (scsi)
Festplatte  /dev/sdb:  4001GB
Sektorgröße (logisch/physisch): 4096B/4096B
Partitionstabelle: msdos
Disk-Flags: 

Nummer  Anfang  Ende    Größe   Typ       Dateisystem     Flags
 1      1049kB  3900GB  3900GB  primary
 2      3900GB  4001GB  101GB   extended
 5      3900GB  4001GB  101GB   logical   linux-swap(v1)


Modell: Linux device-mapper (linear) (dm)
Festplatte  /dev/mapper/lubuntu--vg-swap_1:  4182MB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: loop
Disk-Flags: 

Nummer  Anfang  Ende    Größe   Dateisystem     Flags
 1      0,00B   4182MB  4182MB  linux-swap(v1)


Modell: Linux device-mapper (linear) (dm)
Festplatte  /dev/mapper/lubuntu--vg-root:  245GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: loop
Disk-Flags: 

Nummer  Anfang  Ende   Größe  Dateisystem  Flags
 1      0,00B   245GB  245GB  ext4

```

I could not get it to work with gparted, neither did the IT guy.
but may be we are just noobs, and you can figure it out.

cheerio

---

### Post by banceu_sergiu_ione on 2016-06-29
> **derfred said:**
> 
/dev/sdb5: UUID="cd8aa90a-148c-40dd-86a9-7ee987b1fd85" TYPE="swap"
/dev/sdb2: PTTYPE="dos"

derfred@ghettofred:~$ sudo parted -l

Modell: Intenso USB 3.0 device (scsi)
Festplatte  /dev/sdb:  4001GB
Sektorgröße (logisch/physisch): 4096B/4096B
Partitionstabelle: msdos
Disk-Flags: 

Nummer  Anfang  Ende    Größe   Typ       Dateisystem     Flags
 1      1049kB  3900GB  3900GB  primary
 2      3900GB  4001GB  101GB   extended
 5      3900GB  4001GB  101GB   logical   linux-swap(v1)


As it say you have not file system ( Dateisystem )since your HDD its corrupted. You may not be able to recover your data.

What you can do is to try TestDisk and see if its helpful.

Here you [download]("http://www.cgsecurity.org/wiki/TestDisk_Download") it. Make sure you get the correct version for your OS.

[Fallow this for what you could try to do]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step"),read it all before you do it, this in case TestDisk detect your HDD. Be careful when you chose the disk. Better run first in a terminal [code]sudo parted -l[code] to see where your 4T HDD mount .. /dev/sdb?.

---

### Post by derfred on 2016-06-29
Thank you so much,

I have tried testdisk before and it would not help.
So I guess I will hand in the drive, call it a day and forget about the files.

but thanks anyway!

may be a 4TB harddrive for back up is not as reasonable as i thought, as they can go corrupt as well.
rather multiple small ones.

---

### Post by oldfred on 2016-06-29
I do not know if testdisk works on the LVM.
The LVM is logical partitions inside the large physical partition.

You probably need to mount the LVM and then maybe run fsck. This is about resizing but the first commands are just mounting it.
 How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724) 

      
 fsck on encrypted LUKS 
[http://serverfault.com/questions/375090/using-fsck-to-check-and-repair-luks-encrypted-disk](http://serverfault.com/questions/375090/using-fsck-to-check-and-repair-luks-encrypted-disk)

---

### Post by CharlesA on 2016-06-29
> **derfred said:**
> Thank you so much,

I have tried testdisk before and it would not help.
So I guess I will hand in the drive, call it a day and forget about the files.

but thanks anyway!

may be a 4TB harddrive for back up is not as reasonable as i thought, as they can go corrupt as well.
rather multiple small ones.

Hardware fails. How long have you had the drive?

If it was being used with Windows, it should have been formatted as NTFS, which is contradicted by the output of fdisk. Did you reformat the drive?

If you can get another 4TB drive, look into running [ddrescue]("http://www.forensicswiki.org/wiki/Ddrescue") from a livecd and see if you can recover the data that way. Check [here]("https://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html") the the manual.

---

