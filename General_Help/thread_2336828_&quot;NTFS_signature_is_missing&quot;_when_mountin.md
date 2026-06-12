---
title: "&quot;NTFS signature is missing&quot; when mounting device"
date: 2016-09-11
forum: General Help
---

### Post by hallaplay835 on 2016-09-11
I've installed Ubuntu 16.04 on a Windows 10 machine which had two Western Digital 1 TB HDD attached. Win 10 was installed on an SSD.
While installing Ubuntu I unplugged both HDDs and formatted the SSD.

Upon starting Ubuntu everything works fine except that only one HDD is automatically mounted. Fine, I'll mount the other one manually:

```


david@denna:~$ sudo fdisk -l
Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x6aa79942

Device     Boot Start        End    Sectors   Size Id Type
/dev/sda1  *     2048 1953521663 1953519616 931,5G  7 HPFS/NTFS/exFAT


Disk /dev/sdb: 232,9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x70bc234c

Device     Boot    Start       End   Sectors   Size Id Type
/dev/sdb1  *        2048  39063551  39061504  18,6G 82 Linux swap / Solaris
/dev/sdb2       39065598 488396799 449331202 214,3G  5 Extended
/dev/sdb5       39065600  78125055  39059456  18,6G 83 Linux
/dev/sdb6       78127104 488396799 410269696 195,6G 83 Linux




Disk /dev/sdc: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: E1E8B6AA-414C-4A3B-B3C7-BCA62D61B1B1

Device      Start        End    Sectors   Size Type
/dev/sdc1      34     262177     262144   128M Microsoft reserved
/dev/sdc2  264192 1953523711 1953259520 931,4G Microsoft basic data

Partition 1 does not start on physical sector boundary.

```

/dev/sdb is the SSD where Ubuntu is installed.

/dev/sdc is the HDD which Ubuntu automatically mounts and works fine.

/dev/sda is the other HDD I'm unable to mount.

```

david@denna:~$ sudo mount -t ntfs /dev/sda1 /mnt
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

sudo mount -t ntfs-3g yields the same output.

Other info:

```

sudo blkid
/dev/sda1: PARTUUID="6aa79942-01"
/dev/sdb1: UUID="db26f4c3-df6b-42ab-aa68-5ec01db53516" TYPE="swap" PARTUUID="70bc234c-01"
/dev/sdb5: UUID="d96a6722-3e94-4fdc-926b-1b64033334c6" TYPE="ext4" PARTUUID="70bc234c-05"
/dev/sdb6: UUID="3570220d-4ea0-44fb-8b9f-19d6861d0598" TYPE="ext4" PARTUUID="70bc234c-06"
/dev/sdc1: PARTLABEL="Microsoft reserved partition" PARTUUID="573745ec-92f6-41cf-81a8-670a296a89c0"
/dev/sdc2: LABEL="HDD" UUID="BEE8BCDEE8BC965D" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="79a6d892-4a65-40b3-8353-9bf769e02880"

```

```

david@denna:~$ sudo ntfsfix /dev/sda1 
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
Unrecoverable error
Volume is corrupt. You should run chkdsk.

```

---

### Post by oldfred on 2016-09-11
If Windows 8 or 10 you have to make sure Windows fast start up or always on hibernation is off. That leaves all NTFS partitions mounted. And then Linux NTFS driver will  not mount it to prevent damage to NTFS that chkdsk from Windows may not fix.

But often NTFS signature missing is major corruption of PBR or NTFS's partition boot sector, or grub written into PBR. NTFS PBR must have Windows boot info in it. If that is the case, testdisk may be able to restore the backup PBR that NTFS has.

       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by hallaplay835 on 2016-09-12
I ran boot-info from a live USB installation of Ubuntu. This is the output to boot-info.
[http://paste2.org/c1cBB14U](http://paste2.org/c1cBB14U)

---

### Post by oldfred on 2016-09-12
The error messages on mounting sda1 is generic. So it could be you left it hibernated or it could be a corrupted partition table entry.

Is error from directly booting Windows from BIOS boot of sda?

If error is from Windows boot on sda, not from grub menu boot of Windows,  then it may be missing or corrupted PBR. See what testdisk says.

 You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by hallaplay835 on 2016-09-12
testdisk found no PBR, raw filesystem after deep search. Seems the drive is corrupted.

Plugged it back into a Windows machine and running data recovery tools on it.

---

### Post by oldfred on 2016-09-12
Test disk can create a new NTFS PBR, see link [Rebuild BS]. And as long as RAW Windows chkdsk does not work.
But it may be the older XP type PBR/BS that uses ntldr. Then chkdsk will work and will convert it to the newer PBR that refers to bootmgr which has been used by all BIOS Windows since Windows 7.

---

