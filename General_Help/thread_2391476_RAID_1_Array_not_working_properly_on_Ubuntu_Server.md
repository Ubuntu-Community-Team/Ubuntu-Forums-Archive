---
title: "RAID 1 Array not working properly on Ubuntu Server 16.04.3"
date: 2018-05-09
forum: General Help
---

### Post by maxj345 on 2018-05-09
[SIZE=3][FONT=arial]I followed [this guide]("https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04") [COLOR=#111111]to set up a RAID 1 array on my installation of Ubuntu Server (version: 16.04.3 with HWE Kernel).

[/COLOR][COLOR=#111111]Here's a summary of the steps I took to set it up:

[/COLOR]```

*# NOTE: All of this was done with a fresh installation of the operating system.*

[I]# References:
#   The device files for my hard-drives are:
#     /dev/sdb
#     /dev/sdc
#   The device file for my main drive - where the operating system is installed is:
#     /dev/sda
#   The directory that will be mounted to the RAID array is:
#     /mnt/raid1[/I]

*# Reset any RAID array info on the drives.*
mdadm --zero-superblock /dev/sdb
mdadm --zero-superblock /dev/sdc

*# Create the RAID array:*
mdadm --create --verbose /dev/md/raid1 --level=1 --raid-devices=2 /dev/sdb /dev/sdc

*# Create a file system on the array:*
mkfs.ext4 -F /dev/md/raid1

*# Create the directory to mount the RAID array on:*
mkdir -p /mnt/raid1

*# Manually mount the filesystem:*
mount /dev/md/raid1 /mnt/raid1

*# Add the entry in /etc/fstab to make sure the filesystem is manually mounted at boot-time:*
echo '/dev/md/raid1 /mnt/raid1 ext4 defaults,nofail,discard 0 0' | tee -a /etc/fstab

*# Add the entry in /etc/mdadm/mdadm.conf to make sure the RAID array is assembled automatically at boot-time:*
mdadm --detail --scan | tee -a /etc/mdadm/mdadm.conf

*# Update the initial RAM file system:*
update-initramfs -u

*# I then proceed to create a test file and write to it and make sure the RAID array is actually working:*
touch /mnt/raid1/test.txt
echo "testing testing testing" | tee -a /mnt/raid1/test.txt
cat /mnt/raid1/test.txt

```

[COLOR=#111111]When I rebooted the computer, everything seemed to work fine. The file was still there, and it's contents were intact.
[/COLOR]
[COLOR=#111111]But when I test the RAID array for redundancy, it does not work:[/COLOR]
[/FONT][/SIZE]
[LIST=1]
[*][SIZE=3][FONT=arial]I turn off the system.[/FONT][/SIZE]
[*][SIZE=3][FONT=arial]I unplug one of the drives from the system.[/FONT][/SIZE]
[*][SIZE=3][FONT=arial]I turn on the system.[/FONT][/SIZE]
[*][SIZE=3][FONT=arial]The RAID array is inactive; the filesystem is not mounted.[/FONT][/SIZE]
[/LIST]
[SIZE=3][FONT=arial][COLOR=#111111]
For reference, here's what the [FONT=courier new]/etc/fstab[/FONT] file looks like:[/COLOR]

```

[I]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation[/I]
UUID=e501436e-23c9-4994-97f3-e5c8e6165c2c /               ext4    errors=remount-ro 0       1
*# /boot was on /dev/sda1 during installation*
UUID=642669a6-3d69-46fd-af0f-0c5c00df384b /boot           ext4    defaults        0       2
*# swap was on /dev/sda2 during installation*
UUID=bb572957-4a2c-4ac0-9037-773b428ec0fd none            swap    sw              0       0
/dev/md/raid1 /mnt/raid1 ext4 defaults,nofail,discard 0 0

```

[COLOR=#111111]For reference, here's what the [/COLOR][FONT=courier new]/etc/mdadm/mdadm.conf[/FONT][COLOR=#111111] file looks like:
[/COLOR]
```

[I]# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#[/I]

[I]# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers
[/I]
*# auto-create devices with Debian standard permissions*
CREATE owner=root group=disk mode=0660 auto=yes

*# automatically tag new arrays as belonging to the local system*
HOMEHOST <system>

*# instruct the monitoring daemon where to send mail alerts*
MAILADDR root

*# definitions of existing MD arrays*

[I]# This file was auto-generated on Sat, 05 May 2018 15:31:12 -0400
# by mkconf $Id$[/I]
ARRAY /dev/md/raid1 metadata=1.2 name=andromeda:raid1 UUID=a5585762:a311c411:157f85e5:4e4537fe

```

[COLOR=#111111]Here are some other tests I ran to try and debug this:

[/COLOR]```

*# One drive connected to the system.*
ls /mnt/raid1/
    (nothing)
ls /dev
    md127
    sdb
cat /proc/mdstat
    Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
    md127 : inactive sdb[1](S)
      976631512 blocks super 1.2

    unused devices: <none>
mdadm --detail /dev/md127
    /dev/md127:
            Version : 1.2
        Raid Level : raid0
    Total Devices : 1
        Persistence : Superblock is persistent

            State : inactive

            Name : mycomputer:raid1  (local to host mycomputer)
            UUID : a5585762:a311c411:157f85e5:4e4537fe
            Events : 1557

        Number   Major   Minor   RaidDevice

        -       8       16        -        /dev/sdb
mdadm --detail /dev/sdb
    mdadm: /dev/sdb does not appear to be an md device
mdadm --detail /dev/sdc
    mdadm: cannot open /dev/sdc: No such file or directory


*# One drive (other drive this time) connected to the system.*
ls /mnt/raid1/
    (nothing)
ls /dev
    md127
    sdb    # Why is this not /dev/sdc?
cat /proc/mdstat
    Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
    md127 : inactive sdb[0](S)
    976631512 blocks super 1.2

    unused devices: <none>
mdadm --detail /dev/md127
    /dev/md127:
            Version : 1.2
        Raid Level : raid0
    Total Devices : 1
        Persistence : Superblock is persistent

            State : inactive

            Name : mycomputer:raid1  (local to host mycomputer)
            UUID : a5585762:a311c411:157f85e5:4e4537fe
            Events : 1557

        Number   Major   Minor   RaidDevice

        -       8       16        -        /dev/sdb
mdadm --detail /dev/sdb
    mdadm: /dev/sdb does not appear to be an md device
mdadm --detail /dev/sdc
    mdadm: cannot open /dev/sdc: No such file or directory


*# Both drives connected to the system*
ls /mnt/raid1/
    lost+found
    testfile.txt
cat /mnt/raid1/testfile.txt
    testing testing testing
ls /dev
    md
    md127
    sdb
    sdc
ls /dev/md
    raid1
ls /dev/md -la
    total 0
    drwxr-xr-x  2 root root   60 May  6 13:40 .
    drwxr-xr-x 20 root root 4120 May  6 13:40 ..
    lrwxrwxrwx  1 root root    8 May  6 13:40 raid1 -> ../md127
cat /proc/mdstat
    Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
    md127 : active raid1 sdc[1] sdb[0]
        976631488 blocks super 1.2 [2/2] [UU]
        bitmap: 0/8 pages [0KB], 65536KB chunk

    unused devices: <none>
mdadm --detail /dev/md127
    /dev/md127:
            Version : 1.2
    Creation Time : Sat May  5 17:44:07 2018
        Raid Level : raid1
        Array Size : 976631488 (931.39 GiB 1000.07 GB)
    Used Dev Size : 976631488 (931.39 GiB 1000.07 GB)
    Raid Devices : 2
    Total Devices : 2
        Persistence : Superblock is persistent

    Intent Bitmap : Internal

        Update Time : Sun May  6 13:44:27 2018
            State : clean
    Active Devices : 2
    Working Devices : 2
    Failed Devices : 0
    Spare Devices : 0

            Name : mycomputer:raid1  (local to host mycomputer)
            UUID : a5585762:a311c411:157f85e5:4e4537fe
            Events : 1557

        Number   Major   Minor   RaidDevice State
        0       8       16        0      active sync   /dev/sdb
        1       8       32        1      active sync   /dev/sdc
mdadm --detail /dev/md/raid1
    /dev/md/raid1:
            Version : 1.2
    Creation Time : Sat May  5 17:44:07 2018
        Raid Level : raid1
        Array Size : 976631488 (931.39 GiB 1000.07 GB)
    Used Dev Size : 976631488 (931.39 GiB 1000.07 GB)
    Raid Devices : 2
    Total Devices : 2
        Persistence : Superblock is persistent

    Intent Bitmap : Internal

        Update Time : Sun May  6 13:44:27 2018
            State : clean
    Active Devices : 2
    Working Devices : 2
    Failed Devices : 0
    Spare Devices : 0

            Name : mycomputer:raid1  (local to host mycomputer)
            UUID : a5585762:a311c411:157f85e5:4e4537fe
            Events : 1557

        Number   Major   Minor   RaidDevice State
        0       8       16        0      active sync   /dev/sdb
        1       8       32        1      active sync   /dev/sdc
mdadm --detail /dev/sdb
    mdadm: /dev/sdb does not appear to be an md device
mdadm --detail /dev/sdc
    mdadm: /dev/sdc does not appear to be an md device


*# No drives connected to the system.*
ls /mnt/raid1/
    (nothing)
ls /dev
    (nothing)
cat /proc/mdstat
    Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
    unused devices: <none>

```

[/FONT][/SIZE][COLOR=#111111][FONT=Ubuntu][SIZE=3][FONT=arial]I expected the [FONT=courier new]mdadm[/FONT] details to show the RAID array as degraded, not inactive. What is going on? Is the RAID array failing to reassemble properly on start-up? Why?
[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][SIZE=3][FONT=arial]Also, shouldn't [FONT=courier new]mdadm --detail /dev/sdb and mdadm --detail /dev/sdc[/FONT] show that those **are indeed** md devices?
[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][SIZE=3][FONT=arial]Are my assumptions correct about how the RAID array should work? Should it still work when I unplug one of the hard-drives from the system? What is [FONT=courier new]/dev/md127[/FONT]? How did it get there? Why is [FONT=courier new]/dev/md/raid1[/FONT] pointing (?) to it?
[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][SIZE=3][FONT=arial]Why is [FONT=courier new]/dev/md/raid1[/FONT] not present when when at least one of the hard-drives is unplugged?
[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][SIZE=3][FONT=arial]No matter which hard-drive I unplug, the hard-drive that is still connected to the system seems to be handled by the device file [FONT=courier new]/dev/sdb[/FONT]? I would've expected it to oscillate between [FONT=courier new]/dev/sdb[/FONT] and [FONT=courier new]/dev/sdc[/FONT] depending on which hard-drive was left plugged in. Why is this? Is this what's causing problems with the RAID array?
[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][SIZE=3][FONT=arial]I apologize for the flurry of questions, but I'm truly at a loss trying to figure out why this isn't working as I expected.[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by maxj345 on 2018-05-12
Also, does anyone know what the difference between whole devices and partitions is - with regards to setting a RAID array?
In one guide, it just used the whole drives ([FONT=courier new]/dev/sdb[/FONT], [FONT=courier new]/dev/sdc[/FONT]). In another guide, it used partitions ([FONT=courier new]/dev/sdb1[/FONT], [FONT=courier new]/dev/sdc1[/FONT]) to set up the array.
What are the pros/cons of each method?

---

### Post by maxj345 on 2018-05-15
bump

---

### Post by maxj345 on 2018-05-19
One thing I notice is that when only one drive is plugged into the machine, the array is marked as a RAID 0 array:

```
mdadm --detail /dev/md127
[FONT=courier new]    /dev/md127:
          Version : 1.2
**        Raid Level : raid0**
    Total Devices : 1
      Persistence : Superblock is persistent


            State : inactive


             Name : mycomputer:raid1  (local to host mycomputer)
             UUID : a5585762:a311c411:157f85e5:4e4537fe
           Events : 1557


        Number   Major   Minor   RaidDevice


        -       8       16        -        /dev/sdb[/FONT]

```

---

