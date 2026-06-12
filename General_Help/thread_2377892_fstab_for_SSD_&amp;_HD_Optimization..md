---
title: "fstab for SSD &amp; HD Optimization."
date: 2017-11-17
forum: General Help
---

### Post by makem2 on 2017-11-17
I have a dual boot system with windows on the 1TB HD the machine came with and xubuntu on an SSD in a carrier in the DVD drive bay. The machine did not have a DVD drive fitted when purchased.

I read:

"Add the "noatime" (or "relatime") mount option in /etc/fstab, to disable  (or significantly reduce) disk writes whenever a file is read. Please  note that since Linux kernel 2.6.30, "relatime" is the default. This improves filesystem read performance for both SSDs and HDDs"

I have checked the warning given on the page from which that exerpt comes and find no problems with my machine mentioned.

[https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)

I hope I have given sufficient information below to ask the question:

Can I change the current fstab entries to include the "noatime" (or "relatime") mount option? If so which is better in my case and replace what in the entries?

Thank you.

My fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

# / was on /dev/sda2 during installation
UUID=2409904c-8bce-4e97-9def-b6732140babe              /               ext4    errors=remount-ro 0       1

# /boot/efi was on /dev/sda1 during installation
UUID=CCBC-12A0                                                       /boot/efi       vfat    umask=0077      0       1

# /home was on /dev/sda3 during installation
UUID=d78428d2-66ad-474b-a7bc-8144945dd6a1            /home           ext4    defaults        0       2

# swap was on /dev/sda4 during installation
UUID=68342eb5-6386-48f4-a2ef-e1683ff58be5               none            swap    sw              0       0

#Data
UUID=b15b5fdc-a6ee-4fd9-add9-1039d86dfee2              /media/Data     ext4    defaults        0        2

#WinData
UUID=D232DC8B32DC75C7                                        /media/WinData       ntfs    defaults        0   2
 

``` 

```

makem@ssdTOSH:~$ sudo fdisk -l
[sudo] password for makem: 
Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 9EFB600C-A9FF-4A05-863B-84E383D8B32F

Device         Start       End   Sectors  Size Type
/dev/sda1       2048    487423    485376  237M EFI System
/dev/sda2     487424  40486911  39999488 19.1G Linux filesystem
/dev/sda3   40486912 240486399 199999488 95.4G Linux filesystem
/dev/sda4  240486400 244486143   3999744  1.9G Linux swap
/dev/sda5  244486144 468860927 224374784  107G Linux filesystem


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: C79D48CD-4D4D-4DAA-A116-0A83EBA9B7EC

Device          Start        End    Sectors   Size Type
/dev/sdb1        2048    2099199    2097152     1G Windows recovery environment
/dev/sdb2     2099200    2303999     204800   100M EFI System
/dev/sdb3     2304000    2566143     262144   128M Microsoft reserved
/dev/sdb4     2566144  159461860  156895717  74.8G Microsoft basic data
/dev/sdb5   159463424  161425407    1961984   958M Windows recovery environment
/dev/sdb6   161427456 1914398719 1752971264 835.9G Microsoft basic data
/dev/sdb7  1926705152 1927682047     976896   477M Windows recovery environment
/dev/sdb8  1927682048 1953523711   25841664  12.3G Windows recovery environment
makem@ssdTOSH:~$

makem@ssdTOSH:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  9.6M  1.6G   1% /run
/dev/sda2        19G  5.7G   13G  32% /
tmpfs           7.8G   44M  7.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
none            2.0G  108K  2.0G   1% /media/ramdisk
/dev/sda3        94G   41G   49G  46% /home
/dev/sda5       106G   38G   63G  38% /media/Data
/dev/sda1       234M  3.4M  230M   2% /boot/efi
/dev/sdb6       836G  351G  486G  42% /media/WinData
tmpfs           1.6G   40K  1.6G   1% /run/user/1000
makem@ssdTOSH:~$


```

My xubuntu:

```

makem@ssdTOSH:~$ uname -a
Linux ssdTOSH 4.10.0-38-generic #42~16.04.1-Ubuntu SMP Tue Oct 10 16:32:20 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
makem@ssdTOSH:~$

makem@ssdTOSH:~$ lsb_release -a
LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial
makem@ssdTOSH:~$

makem@ssdTOSH:~$ sudo fdisk -l
Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 9EFB600C-A9FF-4A05-863B-84E383D8B32F

Device         Start       End   Sectors  Size Type
/dev/sda1       2048    487423    485376  237M EFI System
/dev/sda2     487424  40486911  39999488 19.1G Linux filesystem
/dev/sda3   40486912 240486399 199999488 95.4G Linux filesystem
/dev/sda4  240486400 244486143   3999744  1.9G Linux swap
/dev/sda5  244486144 468860927 224374784  107G Linux filesystem


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: C79D48CD-4D4D-4DAA-A116-0A83EBA9B7EC

Device          Start        End    Sectors   Size Type
/dev/sdb1        2048    2099199    2097152     1G Windows recovery environment
/dev/sdb2     2099200    2303999     204800   100M EFI System
/dev/sdb3     2304000    2566143     262144   128M Microsoft reserved
/dev/sdb4     2566144  159461860  156895717  74.8G Microsoft basic data
/dev/sdb5   159463424  161425407    1961984   958M Windows recovery environment
/dev/sdb6   161427456 1914398719 1752971264 835.9G Microsoft basic data
/dev/sdb7  1926705152 1927682047     976896   477M Windows recovery environment
/dev/sdb8  1927682048 1953523711   25841664  12.3G Windows recovery environment
makem@ssdTOSH:~$

makem@ssdTOSH:~$ smartctl -a /dev/sda
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.10.0-38-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

Smartctl open device: /dev/sda failed: Permission denied
makem@ssdTOSH:~$ sudo smartctl -a /dev/sda
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.10.0-38-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Indilinx Barefoot 3 based SSDs
Device Model:     OCZ-VECTOR180
Serial Number:    A22K3061603000032
LU WWN Device Id: 5 e83a97 1000914d2
Firmware Version: 1.01
User Capacity:    240,057,409,536 bytes [240 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Fri Nov 17 16:49:02 2017 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
makem@ssdTOSH:~$

makem@ssdTOSH:~$ sudo smartctl -a /dev/sdb
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.10.0-38-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     TOSHIBA MQ02ABD100H
Serial Number:    35ERCBT9T
LU WWN Device Id: 5 000039 624004be2
Firmware Version: HKF03M
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Fri Nov 17 16:54:47 2017 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


```

---

### Post by oldfred on 2017-11-17
I use noatime for partitions on SSD, and relatime  for partitions on HDD.

You should not use discard as that is trim with each transaction, but just use trim.
I turn off the Ubuntu weekly trim and use my own script like this:
 Shows both discard (not recommended) & fstrim methods for trim and script with log, I like the log
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html) 


I follow some of these suggestions, but SSD now do not need much  change over HDD.
[https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Still-relevant-for-Ubuntu-16.04-and-Linux-Mint-18.x:-select-your-TRIM-method](https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Still-relevant-for-Ubuntu-16.04-and-Linux-Mint-18.x:-select-your-TRIM-method)

---

### Post by makem2 on 2017-11-17
> **oldfred said:**
> I use noatime for partitions on SSD, and relatime  for partitions on HDD.

You should not use discard as that is trim with each transaction, but just use trim.
I turn off the Ubuntu weekly trim and use my own script like this:
 Shows both discard (not recommended) & fstrim methods for trim and script with log, I like the log
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html) 


I follow some of these suggestions, but SSD now do not need much  change over HDD.
[https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Still-relevant-for-Ubuntu-16.04-and-Linux-Mint-18.x:-select-your-TRIM-method](https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Still-relevant-for-Ubuntu-16.04-and-Linux-Mint-18.x:-select-your-TRIM-method)

Hi oldfred, oldmakem here lol.

I use: sudo mv -v /etc/cron.weekly/fstrim /etc/cron.daily

I am concerned about changing the fstab entires because I remember some while ago I changed 'defautls'  and was unable to boot back in. I had to chroot in and change it back.

Are you able to guide me on what to change?

---

### Post by oldfred on 2017-11-17
typos are a problem. 
But whenever you edit fstab you run this and if it remounts everything ok, you get no error messages. Otherwise you need to fix first.
sudo mount -a

This is my fstab:

```
fred@Z170N:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=5c1e1a3f-261f-4da5-a0c2-8f479b3039de /               ext4    noatime,errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=D966-440A  /boot/efi       vfat    defaults      0       1
# swap was on /dev/sdb7 during installation
UUID=3ef43e7c-8a35-4f8b-bc73-c91d6098d4cd none            swap    sw              0       0
# Entry for /dev/sdb4 :
UUID=f9537995-8b44-4abb-b5fb-ec27023f57b2 /mnt/data ext4 relatime 0 2
# Reduce SSD wear
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
UUID=D966-440A    /boot/efi    vfat    defaults    0    1

```

I have just added noatime to / mount & changed defaults to relatime.
I have mis-spelled both and the remount command saved me as it gave errors.

---

### Post by makem2 on 2017-11-17
Thank you for that help. I will digest and implement when i get home.

I also use sudo mount -a after editing the fstab thats why I was surprised to get locked out after making changes previously when I didn't get an error.

---

### Post by makem2 on 2017-11-17
> **oldfred said:**
> typos are a problem. 
But whenever you edit fstab you run this and if it remounts everything ok, you get no error messages. Otherwise you need to fix first.
sudo mount -a

This is my fstab:

```
fred@Z170N:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=5c1e1a3f-261f-4da5-a0c2-8f479b3039de /               ext4    noatime,errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=D966-440A  /boot/efi       vfat    defaults      0       1
# swap was on /dev/sdb7 during installation
UUID=3ef43e7c-8a35-4f8b-bc73-c91d6098d4cd none            swap    sw              0       0
# Entry for /dev/sdb4 :
UUID=f9537995-8b44-4abb-b5fb-ec27023f57b2 /mnt/data ext4 relatime 0 2
# Reduce SSD wear
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
UUID=D966-440A    /boot/efi    vfat    defaults    0    1

```

I have just added noatime to / mount & changed defaults to relatime.
I have mis-spelled both and the remount command saved me as it gave errors.

Thank you, mine is sorted. Except for one query: I have umask=0077 for the /boot/efi and you have defaults for both.I believe mine was made during install.

---

### Post by oldfred on 2017-11-17
Up thru at least 14.04 Ubuntu installer used defaults for mounting the ESP.

But with my 16.04 install they changed to 0077 which prevents even looking at the files from inside your install. Boot-Repair will also change to defaults so it can see & edit entries in ESP. But it probably is set to 0077 for better security as FAT32 does not have an Linux ownership nor permission settings to limit access otherwise.

---

### Post by makem2 on 2017-11-17
> **oldfred said:**
> Up thru at least 14.04 Ubuntu installer used defaults for mounting the ESP.

But with my 16.04 install they changed to 0077 which prevents even looking at the files from inside your install. Boot-Repair will also change to defaults so it can see & edit entries in ESP. But it probably is set to 0077 for better security as FAT32 does not have an Linux ownership nor permission settings to limit access otherwise.

Thank you, I will mark this thread as solved.

---

