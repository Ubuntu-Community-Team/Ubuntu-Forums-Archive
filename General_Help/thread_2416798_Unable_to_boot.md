---
title: "Unable to boot"
date: 2019-04-15
forum: General Help
---

### Post by dik232 on 2019-04-15
[COLOR=#222222][FONT=Verdana]Woke up today and my machine won't boot.  The bios posts and I'm able to enter the bios but I never get to grub.[/FONT][/COLOR]
 
 [COLOR=#222222][FONT=Verdana]This  machine has only ever had Ubuntu on it., currently 18.04.  The drive  has 3 partitions, EFI, boot and LVM encrypted.  With a liveusb I can access all partitions.

When I try to boot I get a cross between an odd screen with [blue squares]("https://i.imgur.com/02lKzuQ.jpg") and another screen telling me that I need to insert bootable media, more often the blue squares.

I can access the bios but when I enter the section for choosing which partition to boot from I'm told "Drive not present", which seems odd because it clearly detects it's presents.  There is a second drive but this has never contained an OS and is used purely as a data store.  Pictures [here]("https://i.imgur.com/wdAzlUx.jpg"), [here]("https://imgur.com/a/OJDtoSD") and [here]("https://i.imgur.com/QLeSPqy.jpg").
[/FONT][/COLOR]
[FONT=verdana]I have used 18.04 live and have reinstalled grub using chroot.  All went as planned with no errors but my situation hasn't changed.

I've been at this for hours now and am not getting anywhere, any help / advice would be very much appreciated.[/FONT]




fdisk
```

Disk /dev/loop0: 1.8 GiB, 1864450048 bytes, 3641504 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 86.9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 34.7 MiB, 36323328 bytes, 70944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 140.9 MiB, 147722240 bytes, 288520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 2.3 MiB, 2433024 bytes, 4752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 14.5 MiB, 15196160 bytes, 29680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 3.7 MiB, 3887104 bytes, 7592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 46324380-968E-4F8E-A75D-6249DCE9988F

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624   2050047    999424   488M Linux filesystem
/dev/sda3  2052096 976773134 974721039 464.8G Linux filesystem


Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 4D50312C-871C-45E8-8DE4-55745BEF78F5

Device          Start        End    Sectors   Size Type
/dev/sdb1          34 1953906215 1953906182 931.7G Linux filesystem
/dev/sdb2  1953906688 3802171391 1848264704 881.3G Linux filesystem
/dev/sdb3  3802171392 3907028991  104857600    50G Linux filesystem

Partition 1 does not start on physical sector boundary.


Disk /dev/sdc: 29.2 GiB, 31376707072 bytes, 61282631 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x663eb4c4

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdc1  *          0 3815135 3815136  1.8G  0 Empty
/dev/sdc2       3737268 3741939    4672  2.3M ef EFI (FAT-12/16/32)


Disk /dev/mapper/luks-4e038213-6dcd-4016-89ee-b8c63d6b7dc4: 464.8 GiB, 499055074816 bytes, 974716943 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-root: 464.8 GiB, 499050872832 bytes, 974708736 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

blkid
```
/dev/sda1: UUID="E96D-D680" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="b8bd42f2-1cc4-4504-8370-9f0af59b5329"
/dev/sda2: UUID="b63ea566-1950-449a-82e6-5a182ba74a67" TYPE="ext2" PARTUUID="c4a56eea-ee44-4fdb-a7ab-de20308efb1b"
/dev/sdb2: LABEL="Storage" UUID="7e44a15f-1e35-4f2f-bca2-0cb32bba35b4" TYPE="ext4" PARTLABEL="store" PARTUUID="50694b3c-af8c-4863-98e4-7ab8e4791016"
/dev/sdb3: UUID="4d0dfe92-c700-4db7-ba1d-9e69c350c13b" TYPE="ext4" PARTLABEL="SG10-backup" PARTUUID="fc35cad4-c01c-44d6-8c8e-99c8c21a7c54"
/dev/loop0: TYPE="squashfs"
.....
/dev/sda3: UUID="4e038213-6dcd-4016-89ee-b8c63d6b7dc4" TYPE="crypto_LUKS" PARTUUID="343028b5-bd7e-4971-8b52-421d75413b09"
/dev/sdb1: UUID="2bf2e97c-5b5f-4aab-9c2e-4f666e4cf2b7" TYPE="crypto_LUKS" PARTUUID="fe5338b4-a268-4702-93e2-0ed80e2c4d8a"
/dev/sdc2: SEC_TYPE="msdos" UUID="0D5F-1DB6" TYPE="vfat" PARTUUID="663eb4c4-02"
/dev/mapper/luks-4e038213-6dcd-4016-89ee-b8c63d6b7dc4: UUID="XddjHy-8x00-zxxE-cFLj-u8Du-kxNC-fvCInP" TYPE="LVM2_member"
/dev/mapper/ubuntu--vg-root: UUID="56d215c1-49b7-4ae1-9baf-370ecd386e89" TYPE="ext4"
/dev/sdc1: UUID="2018-07-25-03-21-56-00" LABEL="Ubuntu 18.04.1 LTS amd64" TYPE="iso9660" PTUUID="663eb4c4" PTTYPE="dos" PARTUUID="663eb4c4-01"
```

---

### Post by westie457 on 2019-04-15
Hi, could you post the output of these please.```
df -h
cat /etc/fstab
```

---

### Post by dik232 on 2019-04-15
I'm running from usb, do you want me to chroot before df -h?

---

### Post by westie457 on 2019-04-16
No need to chroot yet, just gathering info.

---

### Post by dik232 on 2019-04-16
Thanks for getting back.  I'm unsure what result you want for df -h, surely is will show the usb's filesystem?
df -h

```
Filesystem      Size  Used Avail Use% Mounted on
udev             16G     0   16G   0% /dev
tmpfs           3.1G  1.9M  3.1G   1% /run
/dev/sdc        1.9G  1.9G     0 100% /cdrom
/dev/loop0      1.8G  1.8G     0 100% /rofs
/cow             16G  556M   15G   4% /
tmpfs            16G   45M   16G   1% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs            16G     0   16G   0% /sys/fs/cgroup
tmpfs            16G  532K   16G   1% /tmp
tmpfs           3.1G   88K  3.1G   1% /run/user/999
/dev/loop1       87M   87M     0 100% /snap/core/4917
/dev/loop2       35M   35M     0 100% /snap/gtk-common-themes/319
/dev/loop3      141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/loop4      2.4M  2.4M     0 100% /snap/gnome-calculator/180
/dev/loop5       13M   13M     0 100% /snap/gnome-characters/103
/dev/loop6       15M   15M     0 100% /snap/gnome-logs/37
/dev/loop7      3.8M  3.8M     0 100% /snap/gnome-system-monitor/51

```

fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root            /    ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
#UUID=85bdac69-77fd-4bb0-a55e-ed3df1c1dd61 /boot           ext2    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
#UUID=F8F3-C2C5  /boot/efi       vfat    defaults        0       1
#/dev/mapper/cryptswap1 none swap sw 0 0

UUID=7e44a15f-1e35-4f2f-bca2-0cb32bba35b4 /mnt/store auto nosuid,nodev,nofail 0 0
UUID=4d0dfe92-c700-4db7-ba1d-9e69c350c13b /mnt/SG10-backup auto nosuid,nodev,nofail 0 0

UUID=b63ea566-1950-449a-82e6-5a182ba74a67    /boot   ext2    defaults        0       2


UUID=E96D-D680 /boot/efi    vfat    defaults        0       1

#/dev/mapper/ubuntu--vg-swap_1 none swap sw,noauto 0 0
/dev/disk/by-uuid/1e99864d-1836-4a5a-af9a-d5be86e57ab6 /mnt/Backup auto nosuid,nodev,nofail,x-gvfs-show 0 0


```

---

### Post by Rubi1200 on 2019-04-16
Posting the summary for the boot info (link in my signature) will hopefully give us all the information we need to help you.

Thanks.

---

### Post by dik232 on 2019-04-16
[http://paste.ubuntu.com/p/cqRQ4dNNbK/](http://paste.ubuntu.com/p/cqRQ4dNNbK/)

"No boot loader is installed in the MBR of /dev/sda" !!!

I did chroot yesterday???

---

### Post by Rubi1200 on 2019-04-16
If you have a desktop PC, not laptop, this is what I would do.

1. disconnect the data drive not containing an OS

2. decrypt the encrypted partition just to be on the safe side BEFORE attempting the GRUB repair: [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

3. if you do not already have a backup from the encrypted partition, please make one before proceeding

4. run the Boot Repair and let it perform the recommended fixes [https://help.ubuntu.com/community/Boot-Repair#Using_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Using_Boot-Repair)

5. last but not least, according to the summary: > Please do not forget to make your BIOS boot on sda1/efi/.../grub*.efi file

If all goes well, you should be able to boot normally and can then encrypt the data partition again.

If you run into any issues, please do not hesitate to ask first before you go on.

---

### Post by dik232 on 2019-04-16
Unable to agree to the [dialogue]("https://i.imgur.com/KHociIe.png") asking me to remove grub.

All tab does it highlight the sudo chroot text in the top of the window.  All I can do is choose forward where I'm told "GRUB is still present. Please try again."

EDIT: Sorry - being dumb

---

### Post by dik232 on 2019-04-16
Unplugged the data drive

fdisk -l

```
Disk /dev/loop0: 1.8 GiB, 1864450048 bytes, 3641504 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 86.9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

......


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 46324380-968E-4F8E-A75D-6249DCE9988F

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624   2050047    999424   488M Linux filesystem
/dev/sda3  2052096 976773134 974721039 464.8G Linux filesystem


Disk /dev/sdb: 29.2 GiB, 31376707072 bytes, 61282631 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x663eb4c4

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdb1  *          0 3815135 3815136  1.8G  0 Empty
/dev/sdb2       3737268 3741939    4672  2.3M ef EFI (FAT-12/16/32)
```


Ran boot repair, it says there was an [error]("http://paste.ubuntu.com/p/MHQNP4GrbK/")

Also there's no option in my BIOS to specify a .efi file.  I've owned this machine for 3yrs now and have never specified one before.

Rebooting now....

---

### Post by Rubi1200 on 2019-04-16
Did you decrypt or at least unmount the encrypted partition as suggested above before running the repair?

I will ask oldfred, our resident expert on booting issues, to take a look but he might not be online for a few more hours so please hang in there.

I am sure we can get this sorted out for you.

---

### Post by dik232 on 2019-04-16
Rebooted and ended up at the same screen with [blue squares]("https://imgur.com/02lKzuQ") as before.

Any other ideas other than backing up the encrypted LVM, flattening, reinstalling and restoring?

---

### Post by dik232 on 2019-04-16
I decrypted it using the Gnome Disks tool

---

### Post by dik232 on 2019-04-16
I've run boot-info again and it's given a different [result]("http://paste.ubuntu.com/p/g6Jft8GfVX/") this time

---

### Post by Rubi1200 on 2019-04-16
I would wait until oldfred sees my message and takes a look to offer advice.

Thanks for being patient with this and for running the summary again.

---

### Post by oldfred on 2019-04-16
You have newer UEFI hardware and Ubuntu installed in UEFI boot mode.
But you also installed grub in BIOS boot mode to gpt protective MBR and to PBR partition boot sector.

You want to always boot in UEFI mode. And make repairs in UEFI boot mode. UEFI boot of flash drive installer will always give both UEFI & BIOS boot modes, only ever select UEFI.
So always boot live installer in UEFI mode & run Boot-Repair, so it repairs in UEFI mode.

And then make sure system is set to boot in UEFI mode, never even turn on BIOS/Legacy/CSM mode (Which is separate from selection of USB flash drive boot).

The Boot-Repair summary report is only seeing /boot with grub files in it. Make sure you have mounted the LVM and decrypted your install, so Boot-Repair sees and can update settings in / also.

---

### Post by dik232 on 2019-04-16
Updated UEFI boot-info [here]("http://paste.ubuntu.com/p/y5tNRpQwmH/")

---

### Post by oldfred on 2019-04-16
It says noOS, or not seeing inside LVM & encryption.
It only is showing files (grub & kernel) from inside /boot which is not encrypted.
You need to mount LVM & decrypted it, so Boot-Repair can see entire system.

I do not know LVM, but it has not changed, the first few steps of this thread show the mount and decrypt commands. 
Follow steps until it starts on the resizing. and says this:
You can now manage your encrypted partitions, mount them, copy them, or perform maintenance (fsck, backup, resize).
[https://ubuntuforums.org/showthread.php?p=4530641](https://ubuntuforums.org/showthread.php?p=4530641)

---

### Post by dik232 on 2019-04-16
Decrypted and run boot-repair, output [here]("http://paste.ubuntu.com/p/M5cDJvfcNV/")

Rebooting now....

---

### Post by dik232 on 2019-04-16
Same blue squares :(

New boot-info [here]("http://paste.ubuntu.com/p/v54jgy4qx5/")

---

### Post by Rubi1200 on 2019-04-16
Just to step back a minute here. Was everything working normally before all this started? Did you update/upgrade something prior to the booting issues? Was there a power failure perhaps?

Before hopefully oldfred responds again please make full backups of your important files and folders if you have not already done so.

---

### Post by dik232 on 2019-04-16
Machine left on standby overnight as usual.  Woke up to being unable to write to disk.  I've been in this siltation before a year or so ago so booted to usb, unlocked my LVM and ran

```
sudo fsck.ext4 -v /dev/.....
```

Worked fine last time and this time it picked up a couple of errors and fixed them.  This was all on the LVM, not boot or EFI.  Rebooted and saw blue squares.  Manually chroot / reinstall grub - no joy.  Tried a few other things. none of which wrote to disk.  Here I am

---

### Post by oldfred on 2019-04-16
If possible drive issues have you checked in Disks, icon in upper right corner -  Smart Status?
All I know is pass/fail, but it can run lots of tests on drive.

---

### Post by dik232 on 2019-04-16
Looks [good]("https://i.imgur.com/kEhU6eZ.png") to me.  Is it worth running more tests?

Am thinking about imaging the LVM, flattening and starting from scratch unless you've got a better idea

---

### Post by oldfred on 2019-04-16
If fsck & reinstall of grub do not work I am not sure what else to suggest.
Perhaps those that know more about LVM & encryption should comment.

---

### Post by dik232 on 2019-04-17
Anyone out there like to comment?

---

### Post by Rubi1200 on 2019-04-18
Sorry, I don't have any other suggestions.

It seems obvious that something got corrupted somewhere along the way.

If you have good backups it is probably just easier to reinstall.

---

### Post by dre2fresh on 2019-04-18
Have you tried booting into grub by starting up the computer and pressing right shift multiple times then restore grub from there?

---

