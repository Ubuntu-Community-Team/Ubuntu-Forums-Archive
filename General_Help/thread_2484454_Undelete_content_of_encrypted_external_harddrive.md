---
title: "Undelete content of encrypted external harddrive"
date: 2023-02-27
forum: General Help
---

### Post by buzlite on 2023-02-27
I'm using Xubuntu with a 5TB encrypted external drive. I unfortunately deleted a directory using "rm" and would like to recover it. The harddrive is /dev/sdb. I tried using testdisk but could not see any entries that looked like filenames. I tried using the recovery tool from [https://www.r-studio.com/free-linux-recovery/Download.shtml](https://www.r-studio.com/free-linux-recovery/Download.shtml) and it couldn't find any.
Could it be that my harddrive is encrypted. If so, what method could I use to undelete?
Thanks

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.2 LTS
Release:	22.04
Codename:	jammy

$ uname -a
Linux testhost 5.15.0-60-generic #66-Ubuntu SMP Fri Jan 20 14:29:49 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux

$ blkid
/dev/mapper/sda3_crypt: UUID="sg8Btm-7h0p-ZgZa-731j-Lb85-dp2s-W3rrdV" TYPE="LVM2_member"
/dev/mapper/vgxubuntu-swap_1: UUID="fc52b33e-f4b4-4a80-832e-bc791abcbd8b" TYPE="swap"
/dev/mapper/vgxubuntu-root: UUID="7f365286-37ba-413d-acf6-cb1eaf7096b2" BLOCK_SIZE="4096" TYPE="ext4"
/dev/loop1: TYPE="squashfs"
/dev/loop8: TYPE="squashfs"
/dev/sdb1: UUID="f137c593-659b-4863-98cb-cb0b265b54f9" TYPE="crypto_LUKS" PARTUUID="94777cec-b372-4b9a-8d0b-eaebe45fb72c"
/dev/loop6: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop0: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda2: UUID="0683b4bc-ba41-4be1-92d1-809d73e3cddd" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="f7cf206d-302f-48bb-bc0c-6c291f879c11"
/dev/sda3: UUID="aba32675-42fe-4730-91fa-986e6552c733" TYPE="crypto_LUKS" PARTUUID="026470f6-e059-4ddd-b6a2-9a082fc71a85"
/dev/sda1: UUID="05DB-18C2" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="2b5dd1ef-c7cd-45ed-88cb-1f5e2fd644a0"
/dev/loop5: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/mapper/luks-f137c593-659b-4863-98cb-cb0b265b54f9: LABEL="hdd3" UUID="d344ec6f-936c-4d0c-a9b6-444f7fd0329f" BLOCK_SIZE="4096" TYPE="ext4"



TestDisk 7.1, Data Recovery Utility, July 2019
Christophe GRENIER <grenier@cgsecurity.org>
https://www.cgsecurity.org

  TestDisk is free software, and
comes with ABSOLUTELY NO WARRANTY.

Select a media (use Arrow keys, then press Enter):
 Disk /dev/sda - 1000 GB / 931 GiB - WDC WD10JPVX-60JC3T0
>Disk /dev/sdb - 5000 GB / 4657 GiB - Seagate Expansion HDD
 Disk /dev/mapper/luks-f137c593-659b-4863-98cb-cb0b265b54f9 - 5000 GB / 4657 GiB
 Disk /dev/mapper/sda3_crypt - 997 GB / 929 GiB
 Disk /dev/mapper/vgxubuntu-root - 995 GB / 927 GiB
 Disk /dev/mapper/vgxubuntu-swap_1 - 2051 MB / 1956 MiB
 Disk /dev/dm-0 - 997 GB / 929 GiB
 Disk /dev/dm-1 - 995 GB / 927 GiB
 Disk /dev/dm-2 - 2051 MB / 1956 MiB
 Disk /dev/dm-3 - 5000 GB / 4657 GiB
 Disk /dev/loop0 - 4096 B (RO)
 Disk /dev/loop1 - 64 MB / 61 MiB (RO)
 Disk /dev/loop2 - 66 MB / 63 MiB (RO)
 Disk /dev/loop3 - 171 MB / 163 MiB (RO)
 Disk /dev/loop4 - 252 MB / 240 MiB (RO)
 Disk /dev/loop5 - 420 MB / 400 MiB (RO)
 Disk /dev/loop6 - 363 MB / 346 MiB (RO)
 Disk /dev/loop7 - 96 MB / 91 MiB (RO)
 Disk /dev/loop8 - 52 MB / 49 MiB (RO)

>[Proceed ]  [  Quit  ]

Note: Disk capacity must be correctly detected for a successful recovery.
If a disk listed above has an incorrect size, check HD jumper settings and BIOS
detection, and install the latest OS patches and disk drivers.

```

---

### Post by TheFu on 2023-02-27
Restore from backups.  I know that isn't the answer you wanted, but making recovery of data difficult is an important part of using encryption.

BTW, the system is using a default LUKS + LVM setup.  Did you happen to create any snapshots for the root LV?  If so, there will be hope.  Mount the storage and run
```
sudo pvs
sudo vgs
sudo lvs

```to get the basic LVM information.

Snapshots are generally used to aid creating perfectly clean backups, but they aren't automatic.  YOU have to create them.

I don't want to provide false hope.  You can point data recovery tools at the root LV raw device file and see of scanning it finds anything.  The easiest way to get the correct device file is with /dev/{vgname}/{lvname} . Fill in those values for your system.  The /dev/mapper/vgxubuntu-root can be used too, it just isn't a clear for which is the VG name and which is the LV name.  

To see the full relationship between these things, use this command:
```
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'
```

---

### Post by buzlite on 2023-02-28
> **TheFu said:**
> Restore from backups.  I know that isn't the answer you wanted, but making recovery of data difficult is an important part of using encryption.

BTW, the system is using a default LUKS + LVM setup.  Did you happen to create any snapshots for the root LV?  If so, there will be hope.  Mount the storage and run
```
sudo pvs
sudo vgs
sudo lvs

```to get the basic LVM information.

Snapshots are generally used to aid creating perfectly clean backups, but they aren't automatic.  YOU have to create them.

I don't want to provide false hope.  You can point data recovery tools at the root LV raw device file and see of scanning it finds anything.  The easiest way to get the correct device file is with /dev/{vgname}/{lvname} . Fill in those values for your system.  The /dev/mapper/vgxubuntu-root can be used too, it just isn't a clear for which is the VG name and which is the LV name.  

To see the full relationship between these things, use this command:
```
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'
```


Thanks for the reply. Unfortunately I have not done backups. Something learned. :-)

---

### Post by TheFu on 2023-02-28
> **buzlite said:**
> Thanks for the reply. Unfortunately I have not done backups. Something learned. :-)

Did you try the "false hope" instructions?  Might work.  IDK. The more data written to the system, the more likely incomplete and old data will be found.

Using encryption means having excellent backups that you already KNOW how to restore.  Until you actually test the restore, you don't really know.  When I was setting up my backups, it took over 5 attempts to get everything necessary and a few times I ran into problems like capturing everything, but storing it encrypted ... with the unlock information stored inside the encrypted data ... where it couldn't be accessed.  Things like that are needed as part of the restore test process.

For most end users, only 2 things are really game-changers for backups and system restores on a desktop.
a) Get a list of manually installed packages - that's 1 command. Be certain to include this list somewhere that gets backed up!
b) Backup your HOME directory, careful to retain owner, group, permissions, ACLs and xattrs.
c) Clean up old backups so storage doesn't run out.

Here's some commands that will do a little more ... for a basic system backup. Run as root or schedule it to run automatically via cron daily or weekly.  Just drop the script into /etc/cron.daily/ ... make it executable and owned by root:root

```
#!/bin/bash

# ###########[ Change these for your situation ]######
TGT=/Backups     # Needs to be a native Linux file system, not MS-Windows.  ext4 preferred.
DAYS=120
# ########################################
# Save manually installed package list
/usr/bin/apt-mark showmanual > /root/backups/apt-mark.manual

# Local Backups; all backups need to run as root, to capture file metadata
/usr/bin/rdiff-backup \
        --exclude-sockets --exclude-device-files --exclude-fifos \
        --exclude '**/.cache'  --exclude "$TGT" \
        --include /usr/local   --include /etc  \
        --include /root        --include /home \
        --exclude '**'   /       "$TGT"

# Trim old backups from long ago
/usr/bin/rdiff-backup  --remove-older-than "$DAYS"  --force "$TGT"
```

Hope that's helpful.  It gets all user's HOME directories, system settings in /etc/, any manually installed programs that don't use APT in /usr/local, and some super-secret stuff you should place under root's HOME, /root/.

The first run will take as much time as rsync does, but all later runs will be faster than rsync, sometimes much faster.
Using LVM snapshots is an advanced part of this, but not covered. If you aren't running a DBMS, then it probably isn't THAT important.

There are other methods.  Be certain /Backups is another partition on a different HDD. USB is fine.  It needs to be mounted BEFORE any backup runs. A smart backup script would validate that mount exists.  That's left for you to handle.  Writing 20G of data to the same disk and partition as the main OS is on would be mostly useless under most failures.

---

