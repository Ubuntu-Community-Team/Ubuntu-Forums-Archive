---
title: "Fstab won't mount my auxiliary drive during startup."
date: 2017-03-02
forum: General Help
---

### Post by steve169 on 2017-03-02
I have successfully installed Lubuntu 16.04.2 onto a flash drive.

But when I tried to have it automatically mount one of my hard drives (E) when the flash drive is booted, it failed.

I tried to use the fstab specifications that work in my Ubuntu installation, but something's wrong.

Here are the contents of fstab in Ubuntu:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=6c46b513-f825-468a-ab65-d9aad86f0b48 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5f1b715b-7da4-4a7a-ab4f-a6984e4b7b5e none            swap    sw              0       0
# =========================
/dev/sda1: LABEL="C System" UUID="0CE2B73AE2B7273C" TYPE="ntfs" PARTUUID="e6dfe8c3-01"
/dev/sda2: LABEL="E Data" UUID="58BCDBEEBCDBC4A2" TYPE="ntfs" PARTUUID="e6dfe8c3-02"
/dev/sda3: UUID="73c7033a-5fa1-4e29-bd92-49c45db5233d" TYPE="swap" PARTUUID="e6dfe8c3-03"
/dev/sda5: UUID="90d0ae71-7fc8-4a31-80c3-6072560ad2c7" TYPE="ext4" PARTUUID="e6dfe8c3-05"
/dev/sdb1: LABEL="G Data" UUID="34B6CF29B6CEEA86" TYPE="ntfs" PARTUUID="f5d16308-01"
/dev/sdc1: LABEL="F Data" UUID="2ADBE8A42FE77935" TYPE="ntfs" PARTUUID="dde7d8b2-01"
/dev/sdd1: LABEL="MISC" UUID="1ADF-0316" TYPE="vfat" PARTUUID="1bcbaea9-01"
# ======================
# NOTE -- Current command for C:
# Mount C System
# UUID="0CE2B73AE2B7273C" /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```


And here is fstab in Lubuntu. (I simply copied the line for the E drive from Ubuntu fstab to Lubuntu.):
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/lubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=2d3b47c3-4b78-40f8-9ed4-cc6c1b3cf826 /boot           ext2    defaults        0       2
/dev/mapper/lubuntu--vg-swap_1 none            swap    sw              0       0
/dev/sda2: LABEL="E Data" UUID="58BCDBEEBCDBC4A2" TYPE="ntfs" PARTUUID="e6dfe8c3-02"
```


Any suggestions?

---

### Post by deadflowr on 2017-03-02
The final line in the Ubuntu fstab is basically what you need to mimic in the Lubuntu fstab:
```
UUID="0CE2B73AE2B7273C" /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```
changing the uuid number to that of the proper parttion you want.
(I also do not know if it should be wrapped in quotes, none I have ever are, but i also don't mount any ntfs file systems, so...)

Basically fstab should have
the device (in this case using the UUID of the partition) >> **UUID="0CE2B73AE2B7273C"**
then the mountpoint (where you want it to be mounted in your file system) >> **/media/windows**
the file system type it has (in this case ntfs) >> **ntfs-3g**
any options you want (defaults gives several, as it where default (things like rw access async and suid settings, among other settings; use man mount to find more on options)  options, and the there in the entry is an option to run it with the en_US.utf8 setting) >> **defaults,locale=en_US.utf8**
dump (unless you know anything about this never set it to anything but 0 (zero) >> **0**
the disk check ordering ( this set the system disk checking and in what order to do the checking, and if the disk should be checked at all) >>  **0**

Hope that makes sense

---

### Post by steve169 on 2017-03-05
Dear Deadflowr,

Many thanks. I followed your directions, and now it's working fine. We newbies would be lost without you experts.

---

### Post by steve169 on 2017-03-13
I thought I had this problem solved, but now it's misbehaving again.

My **fstab** file mounts Ubuntu, its swap file and the C drive. But the other drives are ignored.

I'm using Ubuntu 16.04.02 on a desktop PC. All the hard drives are formatted NTFS except Ubuntu's partitions, which are  ext4 and Linux swap.

Here's the **fstab** file as it stands now:

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=4896280b-f6d0-4b4b-81a5-5bf1085b1644 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0ea2c455-39bf-4c29-8d1a-2eecadb2b372 none            swap    sw              0       0
**# mount C System**
UUID="0CE2B73AE2B7273C" /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
**# mount E Data**
UUID="58BCDBEEBCDBC4A2" /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
**# mount F Data**
UUID="00088B8C088B8000" /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
**# mount G Data**
UUID="C0C6A98CC6A98370" /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```

As advised, I ran **blkip** is Terminal. Here are the results:

```
/dev/sda1: LABEL="**C System**" UUID="0CE2B73AE2B7273C" TYPE="ntfs" PARTUUID="e6dfe8c3-01"
/dev/sda2: LABEL="**E Data**" UUID="58BCDBEEBCDBC4A2" TYPE="ntfs" PARTUUID="e6dfe8c3-02"
/dev/sda3: UUID="73c7033a-5fa1-4e29-bd92-49c45db5233d" TYPE="**swap**" PARTUUID="e6dfe8c3-03"
/dev/sda5: UUID="4896280b-f6d0-4b4b-81a5-5bf1085b1644" TYPE="**ext4**" PARTUUID="e6dfe8c3-05"
/dev/sdb1: LABEL="**F Data**" UUID="00088B8C088B8000" TYPE="ntfs" PARTUUID="f5d16308-01"
/dev/sdc1: LABEL="**G Data**" UUID="C0C6A98CC6A98370" TYPE="ntfs" PARTUUID="dde7d8b2-01"
/dev/sdd1: LABEL="**MISC**" UUID="1ADF-0316" TYPE="vfat" PARTUUID="1bcbaea9-01" [*This is a USB thumb drive*.]
```

The Ubuntu fstab guide says you must created a **mount point** before a drive can be mounted.

My mount point is specified as /media/windows in all cases, but there's nothing there that suggests a mount point to me.

Here's what Terminal shows as the contents of** /media/windows**:

```
{1D,877,185-E,DCA-4,0A9-8A27-04E90FAA770D}.CBM    NBRT93ecad7337c27f78bcdc2a37            pagefile.sys
A-master.adr 
BOOT
bootmgr 
boot-sav
{C0,A60,D2D-5,AAC-4,F91-B245-AD94E90044B6}.CBM 
Config.Msi 
Dell                        Report
Disk 
Documents and Settings 
Drivers 
EUMONBMP.SYS 
hiberfil.sys 
Hotfix 
Intel 
MASTER.LOG
MGADiagToolOutput 
MSSTBJ.CAT
PerfLogs
ProgramData
Program Files
Program Files (x86)
Recovery
$RECYCLE.BIN
RPSetup.exe.log
System Volume Information
Trash Bin
Temp
USER
Users
VProRecovery
VSNAP.IDX
Windows
$windows.~bt
```

***If anyone can set me straight on this problem, I'd be one happy newbie.***

---

### Post by Dennis N on 2017-03-13
> My fstab file mounts Ubuntu, its swap file and the C drive. But the other drives are ignored

The mount point for each file system in your /etc/fstab has to be unique - only one can be mounted at /media/windows.

---

### Post by deadflowr on 2017-03-13
^that
I'd suggest creating several sub-directories in the /media/windows directory, one for each windows drive, so
/media/windows/c 
/media/windows/e
/media/windows/g
and so on,
then make those new sub-directories the new mount point for each drive.
I suggest using the drive letter as then you can differentiate between them easily.

Hope it helps, or make sense

---

### Post by vasa1 on 2017-03-13
Please use code tags instead of quote tags when posting content from the terminal. Text is aligned properly when you do so. Thanks!

---

### Post by steve169 on 2017-03-14
I created the subdirectories for mounting points, and all now works well.

Many thanks to all of you.

---

