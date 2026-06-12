---
title: "Can fdisk ignore certain devices?"
date: 2014-07-27
forum: General Help
---

### Post by terminator14 on 2014-07-27
When I plug a USB/hard drive into my computer that's not formatted (doesn't automatically mount a partition),
the first thing I do is run:
```
$ sudo fdisk -l
```
to figure out the device of what I just plugged in. This has worked great for years.
Now, my system has FakeRAID and LVM, so fdisk displays info for:

[LIST]
[*]Actual hard drives in my RAID0 (/dev/sda, /dev/sdb)
[*]The RAID0 itself (/dev/mapper/isw_dcddcgedij_Volume0)
[*]The partitions on my RAID0 (/dev/mapper/isw_dcddcgedij_Volume0p[1-4]
[*]Some weird output for partitions under my EFI partition (/dev/mapper/isw_dcddcgedij_Volume0p1p[1-4])
[*]The LVM volume group device (/dev/mapper/vg0)
[*]Some warnings about LVM (because fdisk doesn't support LVM)
[/LIST]

The whole thing looks like this:

```
$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.1 GB, 250059350016 bytes
256 heads, 63 sectors/track, 30282 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976783871   488391935+  ee  GPT

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/isw_dcddcgedij_Volume0'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/mapper/isw_dcddcgedij_Volume0: 500.1 GB, 500113342464 bytes
256 heads, 63 sectors/track, 60564 cylinders, total 976783872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000

                              Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_dcddcgedij_Volume0p1               1   976783871   488391935+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/mapper/isw_dcddcgedij_Volume0p1: 104 MB, 104857600 bytes
255 heads, 63 sectors/track, 12 cylinders, total 204800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

                                Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_dcddcgedij_Volume0p1p1   ?   778135908  1919645538   570754815+  72  Unknown
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_dcddcgedij_Volume0p1p2   ?   168689522  2104717761   968014120   65  Novell Netware 386
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_dcddcgedij_Volume0p1p3   ?  1869881465  3805909656   968014096   79  Unknown
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_dcddcgedij_Volume0p1p4   ?  2885681152  2885736650       27749+   d  Unknown

Partition table entries are not in disk order

Disk /dev/mapper/isw_dcddcgedij_Volume0p2: 134 MB, 134217728 bytes
255 heads, 63 sectors/track, 16 cylinders, total 262144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_dcddcgedij_Volume0p2 doesn't contain a valid partition table

Disk /dev/mapper/isw_dcddcgedij_Volume0p3: 244.1 GB, 244078084096 bytes
255 heads, 63 sectors/track, 29674 cylinders, total 476715008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

                                Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_dcddcgedij_Volume0p3p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_dcddcgedij_Volume0p3p2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_dcddcgedij_Volume0p3p3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_dcddcgedij_Volume0p3p4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/mapper/isw_dcddcgedij_Volume0p4: 255.8 GB, 255794610176 bytes
255 heads, 63 sectors/track, 31098 cylinders, total 499598848 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_dcddcgedij_Volume0p4 doesn't contain a valid partition table

Disk /dev/mapper/vg0-lv_root: 255.8 GB, 255789629440 bytes
255 heads, 63 sectors/track, 31097 cylinders, total 499589120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg0-lv_root doesn't contain a valid partition table

```

This makes any newly plugged in devices take forever to find among all the junk output.
I don't really want fdisk to do anything with my existing partitions (especially since it doesn't
support most of them anyway) but I would like it to still display partitions of USB devices
I plug into my computer. Is it possible to have fdisk ignore all the extra devices?

---

### Post by oldfred on 2014-07-27
You can use parted to see gpt partitioned drives.
But with RAID & LVM you have to use those tools to see them.

sudo parted -l
or
 sudo parted /dev/sdc unit s print



       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by terminator14 on 2014-07-27
That's the thing - I'm not trying to see my LVM volumes, or GPT drives - I'm trying
to see everything else (any USB drives I plug in, 99% of which have an MBR partition table).

Also, parted is not a big fan of my setup:

```
$ sudo parted -l
Error: Invalid argument during seek for read on /dev/sda                  
Retry/Ignore/Cancel? Ignore
Error: The backup GPT table is corrupt, but the primary appears OK, so that will be used.
OK/Cancel? OK                                                             
Backtrace has 8 calls on stack:
  8: /lib/x86_64-linux-gnu/libparted.so.0(ped_assert+0x2e) [0x7f34efc412ee]
  7: /lib/x86_64-linux-gnu/libparted.so.0(+0x4551b) [0x7f34efc7251b]
  6: /lib/x86_64-linux-gnu/libparted.so.0(ped_disk_new+0x58) [0x7f34efc474f8]
  5: parted() [0x4075cf]
  4: parted() [0x4083ca]
  3: parted(main+0x148a) [0x406cfa]
  2: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xfd) [0x7f34ef450ead]
  1: parted() [0x406d49]
                                                                          

You found a bug in GNU Parted! Here's what you have to do:

Don't panic! The bug has most likely not affected any of your data.
Help us to fix this bug by doing the following:

Check whether the bug has already been fixed by checking
the last version of GNU Parted that you can find at:

	http://ftp.gnu.org/gnu/parted/

Please check this version prior to bug reporting.

If this has not been fixed yet or if you don't know how to check,
please visit the GNU Parted website:

	http://www.gnu.org/software/parted

for further information.

Your report should contain the version of this release (2.3)
along with the error message below, the output of

	parted DEVICE unit co print unit s print

and the following history of commands you entered.
Also include any additional information about your setup you
consider important.

Assertion (last_usable <= disk->dev->length) at ../../../libparted/labels/gpt.c:723 in function _parse_header() failed.

```

Side note: Yup - I see the error it shows about my GPT table, but gdisk says it's fine, and considering the fact that
gdisk isn't freaking out like gparted is, I tend to put more faith in its analysis.

> **oldfred said:**
> sudo parted /dev/sdc unit s print

This defeats the purpose - if I knew what the device was, I wouldn't need fdisk to tell me.

---

### Post by terminator14 on 2014-07-28
I just wrote a simple wrapper for fdisk. I haven't fully tested it yet, but it seems to work. If anyone wants to test it and reply if it works, I would appreciate it.
So far, I've tried it on CentOS and Debian.

To get it, make sure you have git
```
sudo apt-get install git
```
and run this to download the latest version of the script:

```
git clone git://github.com/terminator14/fdisk_wrapper.git
```

Then run:
```
cd fdisk_wrapper
sudo ./install.sh
```

The wrapper passes all arguments to real fdisk unless it's only argument is "-l".
So if you run "sudo fdisk -l", it will ignore the devices you told it to ignore.

Edit: I just updated the script above to check for lsblk.
Edit 2: Updated script with some additional output
Edit 3: I made a ton of updates, and put it up on github

---

### Post by terminator14 on 2014-07-29
If anyone has problems with it, or knows a better way to do this, let me know.
Otherwise, as far as I can tell, this is the only way (other than using other tools, or modifying fdisk's source code).

---

