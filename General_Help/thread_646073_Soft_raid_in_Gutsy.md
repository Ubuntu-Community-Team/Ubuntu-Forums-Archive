---
title: "Soft raid in Gutsy"
date: 2007-12-20
forum: General Help
---

### Post by acrist on 2007-12-20
Hi body, I have some problem at new install gutsy server. 
I have 2 similarly SATA drives by 500gb,  attached it to soft raid 1(mirror).
When system booting, i have received some message
Dec 21 02:36:55 diweather kernel: [   16.836455] parport_pc 00:07: reported by Plug and Play ACPI
Dec 21 02:36:55 diweather kernel: [   16.836545] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Dec 21 02:36:55 diweather kernel: [   16.869843] NET: Registered protocol family 10
Dec 21 02:36:55 diweather kernel: [   16.869965] lo: Disabled Privacy Extensions
Dec 21 02:36:55 diweather kernel: [   16.931808] iTCO_vendor_support: vendor-support=0
Dec 21 02:36:55 diweather kernel: [   16.932549] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Dec 21 02:36:55 diweather kernel: [   16.932641] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
Dec 21 02:36:55 diweather kernel: [   16.932723] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Dec 21 02:36:55 diweather kernel: [   17.003120] md: md4 stopped.
Dec 21 02:36:55 diweather kernel: [   17.140894] md: bind<sdb6>
Dec 21 02:36:55 diweather kernel: [   17.141135] md: bind<sda6>
Dec 21 02:36:55 diweather kernel: [   17.179261] raid1: raid set md4 active with 2 out of 2 mirrors
Dec 21 02:36:55 diweather kernel: [   17.179383] md: md5 stopped.
Dec 21 02:36:55 diweather kernel: [   17.238155] md: bind<sdb7>
Dec 21 02:36:55 diweather kernel: [   17.238406] md: bind<sda7>
Dec 21 02:36:55 diweather kernel: [   17.262063] raid1: raid set md5 active with 2 out of 2 mirrors
Dec 21 02:36:55 diweather kernel: [   17.262163] md: md6 stopped.
Dec 21 02:36:55 diweather kernel: [   17.321355] md: bind<sdb8>
Dec 21 02:36:55 diweather kernel: [   17.321574] md: bind<sda8>
[B]Dec 21 02:36:55 diweather kernel: [   17.346936] raid1: raid set md6 active with 2 out of 2 mirrors
Dec 21 02:36:55 diweather kernel: [   27.258354] eth0: no IPv6 routers present
Dec 21 02:36:55 diweather kernel: [  196.736420] loop: module loaded
[/B]Dec 21 02:36:55 diweather kernel: [  196.755542] lp0: using parport0 (interrupt-driven).
Dec 21 02:36:55 diweather kernel: [  196.895570] Adding 4883640k swap on /dev/md2.  Priority:-1 extents:1 across:4883640k
Dec 21 02:36:55 diweather kernel: [  197.149523] EXT3 FS on md1, internal journal
Dec 21 02:36:55 diweather kernel: [  198.274748] kjournald starting.  Commit interval 5 seconds
Dec 21 02:36:55 diweather kernel: [  198.308388] EXT3 FS on md0, internal journal
Dec 21 02:36:55 diweather kernel: [  198.308394] EXT3-fs: mounted filesystem with ordered data mode.
Dec 21 02:36:55 diweather kernel: [  198.337129] kjournald starting.  Commit interval 5 seconds
Dec 21 02:36:55 diweather kernel: [  198.358282] EXT3 FS on md3, internal journal
Dec 21 02:36:55 diweather kernel: [  198.358286] EXT3-fs: mounted filesystem with ordered data mode.
Dec 21 02:36:55 diweather kernel: [  198.377100] kjournald starting.  Commit interval 5 seconds
Dec 21 02:36:55 diweather kernel: [  198.399753] EXT3 FS on md4, internal journal


What interested, that sleeping time is around 180 seconds(3 minutes), and it's not good for me.

My configuration is:
root#diweather~>fdisk /dev/sda

The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f0d33

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         122      979933+  fd  Linux raid autodetect
/dev/sda2             123        1095     7815622+  fd  Linux raid autodetect
/dev/sda3            1096        1703     4883760   fd  Linux raid autodetect
/dev/sda4            1704       60801   474704685    5  Extended
/dev/sda5            1704        7782    48829536   fd  Linux raid autodetect
/dev/sda6            7783       13861    48829536   fd  Linux raid autodetect
/dev/sda7           13862       38176   195310206   fd  Linux raid autodetect
/dev/sda8           38177       60801   181735281   fd  Linux raid autodetect

Command (m for help): 

root#diweather~>fdisk /dev/sdb

The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000c2c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         122      979933+  fd  Linux raid autodetect
/dev/sdb2             123        1095     7815622+  fd  Linux raid autodetect
/dev/sdb3            1096        1703     4883760   fd  Linux raid autodetect
/dev/sdb4            1704       60801   474704685    5  Extended
/dev/sdb5            1704        7782    48829536   fd  Linux raid autodetect
/dev/sdb6            7783       13861    48829536   fd  Linux raid autodetect
/dev/sdb7           13862       38176   195310206   fd  Linux raid autodetect
/dev/sdb8           38177       60801   181735281   fd  Linux raid autodetect

Command (m for help):

root#diweather~>cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
#ARRAY /dev/md0 level=raid1 num-devices=2 UUID=e0e37ba3:c1b56cdc:cf23be8e:87e4e138
#ARRAY /dev/md1 level=raid1 num-devices=2 UUID=a7eb5ecd:f97f9315:f49b4728:a6da7e87
#ARRAY /dev/md2 level=raid1 num-devices=2 UUID=907c27bf:53f8b316:740dd672:8a38450e
#ARRAY /dev/md3 level=raid1 num-devices=2 UUID=55f295b0:ceb66103:d7cf9b46:1d9de7c1
#ARRAY /dev/md4 level=raid1 num-devices=2 UUID=3e9e6d62:efd00863:b89dc9c6:85bc3b94
#ARRAY /dev/md5 level=raid1 num-devices=2 UUID=81e58e6d:98a872f0:c1e21f6a:77a39dad
#ARRAY /dev/md6 level=raid1 num-devices=2 UUID=7ba9fec3:e8effc16:03410ea9:4f68a151
ARRAY /dev/md0 level=raid1 num-devices=2 devices=/dev/sda1,/dev/sdb1
ARRAY /dev/md1 level=raid1 num-devices=2 devices=/dev/sda2,/dev/sdb2
ARRAY /dev/md2 level=raid1 num-devices=2 devices=/dev/sda3,/dev/sdb3
ARRAY /dev/md3 level=raid1 num-devices=2 devices=/dev/sda5,/dev/sdb5
ARRAY /dev/md4 level=raid1 num-devices=2 devices=/dev/sda6,/dev/sdb6
ARRAY /dev/md5 level=raid1 num-devices=2 devices=/dev/sda7,/dev/sdb7
ARRAY /dev/md6 level=raid1 num-devices=2 devices=/dev/sda8,/dev/sdb8

# This file was auto-generated on Fri, 21 Dec 2007 03:18:27 +0000
# by mkconf $Id: mkconf 324 2007-05-05 18:49:44Z madduck $
root#diweather~>

root#diweather~>cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md6 : active raid1 sda8[0] sdb8[1]
      181735168 blocks [2/2] [UU]
      
md5 : active raid1 sda7[0] sdb7[1]
      195310080 blocks [2/2] [UU]
      
md4 : active raid1 sda6[0] sdb6[1]
      48829440 blocks [2/2] [UU]
      
md3 : active raid1 sda5[0] sdb5[1]
      48829440 blocks [2/2] [UU]
      
md2 : active raid1 sda3[0] sdb3[1]
      4883648 blocks [2/2] [UU]
      
md1 : active raid1 sda2[0] sdb2[1]
      7815552 blocks [2/2] [UU]
      
md0 : active raid1 sda1[0] sdb1[1]
      979840 blocks [2/2] [UU]
      
unused devices: <none>
root#diweather~>

All drives is absalutly new, and smart can't find any defection.

Any body can explain this, and talk me to repair my "spleeply" server??

---

### Post by gagatz on 2008-01-20
sorry, that i can't help, but you might ask for help in the
hardware & laptops
forum and rather not put all your infos into the first post, cos it might frighten off people who want to help.

---

### Post by dgray_from_dc on 2008-01-23
I don't understand the purpose of your set up.  Why do you have 16 separate partitions across two drives making 8 arrays?  That configuration will create a tremendous performance lag.

---

