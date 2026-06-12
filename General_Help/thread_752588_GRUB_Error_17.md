---
title: "GRUB Error 17"
date: 2008-04-11
forum: General Help
---

### Post by cedge on 2008-04-11
So, short version, Ubuntu won't boot. Long version is as follows:

So, I have Ubuntu 7.10 installed on a 13.6 gig drive (currently being used as a backup OS while I'm fixing my 120 gig Windows XP drive). It ran peachy until a couple days ago, when, following a reboot, I was presented with the message:

```
GRUB Loading stage1.5
GRUB loading, please wait...

Error 17
```

I've done a lot of searching and reading about this particular error, and have found some advice, but almost everything I find regarding this problem specifically involves people who are having problems with dual-OS drives, whereas I'm using a drive with just Ubuntu.

I've found advice saying that this error can result from the partition having the wrong ID, but this isn't the case for me. Any advice, or further steps?

Here are the results of *sudo fdisk -l*, for reference:
```
Disk /dev/hda: 13.6 GB, 13601193984 bytes
255 heads, 63 sectors/track, 1653 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x242383c5

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1578    12675253+  83  Linux
/dev/hda2            1579        1653      602437+   5  Extended
/dev/hda5            1579        1653      602406   82  Linux swap / Solaris
```

GParted, however, reports that the filesystem is "unknown":
[img]http://img443.imageshack.us/img443/7163/gpartedcu3.png[/img].

Thanks in advance.

---

### Post by tvtech on 2008-04-11
is this a system that has been installed and running?  What file system did you use to format with when you set up hda1?

I got this from the grub manual which can be found [http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors]("http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors")  here

17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

---

### Post by cedge on 2008-04-11
Yes, it was up an running (been using it for a week or so). The filesystem was the default, ext3.

And yes, I've seen the GRUB manual's explaination of what the error is. As I noted, I'm somewhat confused about these reports I'm getting from fdisk (which says it sees a Linux partition) and GParted (which says the filesystem is unknown).

I'm thinking that this is damage to the partition. Any advice, or further assistance, anyone?

---

### Post by cedge on 2008-04-12
Ahem...amyone?

---

### Post by cedge on 2008-04-13
Well, if nothing else, can anyone reccommend some decent data/partition recovery tools?

---

### Post by Herman on 2008-04-13
Your installation just needs a file system check.
Boot any Linux Live CD, and open a terminal and run the following command,
```
sudo e2fsck -C0 -p -v -f /dev/hda1
```That should fix it, but in the unlikely event that it doesn't, it will tell you what to do next.
If you get some message then post it here and someone will help you more, but there's a 99.9% chance that command will do.

Regards, Herman :)

EDIT: If you use GParted Live CD, you don't need to put 'sudo' in front of that command, but if you're using Ubuntu or Knoppix you do need 'sudo'.

---

### Post by cedge on 2008-04-13
editing...

---

### Post by cedge on 2008-04-13
That command returns the following:
```
e2fsck: Bad magic number in super-block while trying to open /dev/hda1
/dev/hda1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

---

### Post by Herman on 2008-04-13
Okay, to find out where all your spare backup copies of your superblock are located, run the following command,
 ```
sudo dumpe2fs /dev/hda1 | grep -i superblock
```Then, run '[FONT=Bitstream Vera Sans Mono]sudo e2fsck -b 8193 /dev/hda1'[/FONT] or[FONT=Bitstream Vera Sans Mono] '[/FONT][FONT=Bitstream Vera Sans Mono]sudo e2fsck -b 32768 /dev/hda1',[/FONT]using any number that corresponds with a number from the output from your previous command.```
sudo e2fsck -b 32768 /dev/hda1
```That should fix it.

Regards, Herman :)

---

### Post by cedge on 2008-04-13
The first command returns the following:
```
dumpe2fs 1.40.2 (12-Jul-2007)
dumpe2fs: Bad magic number in super-block while trying to open /dev/hda1
Couldn't find valid filesystem superblock.
```

Thanks for your help so far...this is brutal, I know...

---

### Post by Herman on 2008-04-13
Well, if you're absolutely certain you entered that command in correctly I'm sorry to say it looks like you have something serious wrong in your hard disk.

How about checking it with smartmontools now and see if that will detect the problem, you can install smartmontools in the Ubuntu Live CD with,
```
sudo apt-get install smartmontools 
```, or use the Ubuntu Rescue Remix CD, or Knoppix or System Rescue CD or another Linux Live CD that has smartmontools in it.

---

### Post by Herman on 2008-04-13
Oh yeah, here's a link about how to run smartmontools, [Check On Your Hard Disks With Smartmontools]("http://users.bigpond.net.au/hermanzone/p20.html#Check_On_Your_Hard_Disks_With").
Good luck, I hope it passes.

If you don't want to go to that much trouble, an easier thing to do would be just to run the badblocks command from a Live CD,
```
sudo badblocks -n -v /dev/hda1
``` It will probably take a while.

Regards, Herman

---

### Post by cedge on 2008-04-13
[sudo smartctl -H /dev/hda] reports it as PASSED...

---

### Post by Herman on 2008-04-13
:) Oh, okay then, that's good, what results do the rest of the smartmontools commands report?

---

### Post by cedge on 2008-04-13
[sudo smartctl --all /dev/hda] reports, ahem:
```
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar WDxxxAA series
Device Model:     WDC WD136AA-35BAA0
Serial Number:    WD-WMA351083701
Firmware Version: 10.09K11
User Capacity:    13,601,193,984 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   4
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Apr 13 09:18:19 2008 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (  24) The self-test routine was aborted by
                                        the host.
Total time to complete Offline 
data collection:                 (1040) seconds.
Offline data collection
capabilities:                    (0x1b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        No Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        No General Purpose Logging support.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  14) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   200   195   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0006   109   097   000    Old_age   Always       -       1150
  4 Start_Stop_Count        0x0012   096   096   040    Old_age   Always       -       4923
  5 Reallocated_Sector_Ct   0x0012   199   199   112    Old_age   Always       -       2
  9 Power_On_Hours          0x0012   061   061   000    Old_age   Always       -       28719
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0013   100   100   051    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0012   096   096   000    Old_age   Always       -       4720
196 Reallocated_Event_Count 0x0012   198   198   000    Old_age   Always       -       2
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0012   100   253   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       111
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 458 (device log contains only the most recent five errors)
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 458 occurred at disk power-on lifetime: 115 hours (4 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 c1 df 3b e0  Error: UNC at LBA = 0x003bdfc1 = 3923905

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 00 01 c1 df 3b e0 00      00:06:28.450  READ VERIFY SECTOR(S)
  c8 00 01 00 00 00 e0 00      00:06:28.450  READ DMA
  40 00 02 c1 df 3b e0 00      00:06:23.500  READ VERIFY SECTOR(S)
  c8 00 01 00 00 00 e0 00      00:06:23.500  READ DMA
  40 00 02 bf df 3b e0 00      00:06:23.500  READ VERIFY SECTOR(S)

Error 457 occurred at disk power-on lifetime: 115 hours (4 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 02 c1 df 3b e0  Error: UNC at LBA = 0x003bdfc1 = 3923905

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 00 02 c1 df 3b e0 00      00:06:23.500  READ VERIFY SECTOR(S)
  c8 00 01 00 00 00 e0 00      00:06:23.500  READ DMA
  40 00 02 bf df 3b e0 00      00:06:23.500  READ VERIFY SECTOR(S)
  c8 00 01 00 00 00 e0 00      00:06:23.500  READ DMA
  40 00 04 c3 df 3b e0 00      00:06:23.500  READ VERIFY SECTOR(S)

Error 456 occurred at disk power-on lifetime: 115 hours (4 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 04 c1 df 3b e0  Error: UNC at LBA = 0x003bdfc1 = 3923905

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 00 04 bf df 3b e0 00      00:06:18.650  READ VERIFY SECTOR(S)
  40 00 08 c7 df 3b e0 00      00:06:18.650  READ VERIFY SECTOR(S)
  c8 00 01 00 00 00 e0 00      00:06:18.600  READ DMA
  40 00 08 bf df 3b e0 00      00:06:13.450  READ VERIFY SECTOR(S)
  c8 00 01 00 00 00 e0 00      00:06:13.450  READ DMA

Error 455 occurred at disk power-on lifetime: 115 hours (4 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 c1 df 3b e0  Error: UNC at LBA = 0x003bdfc1 = 3923905

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 00 08 bf df 3b e0 00      00:06:13.450  READ VERIFY SECTOR(S)
  c8 00 01 00 00 00 e0 00      00:06:13.450  READ DMA
  40 00 10 cf df 3b e0 00      00:06:13.450  READ VERIFY SECTOR(S)
  c8 00 01 00 00 00 e0 00      00:06:13.450  READ DMA
  40 00 10 bf df 3b e0 00      00:06:08.200  READ VERIFY SECTOR(S)

Error 454 occurred at disk power-on lifetime: 115 hours (4 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 10 c1 df 3b e0  Error: UNC at LBA = 0x003bdfc1 = 3923905

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 00 10 bf df 3b e0 00      00:06:08.200  READ VERIFY SECTOR(S)
  40 00 20 df df 3b e0 00      00:06:08.200  READ VERIFY SECTOR(S)
  c8 00 01 00 00 00 e0 00      00:06:08.200  READ DMA
  40 00 20 bf df 3b e0 00      00:06:03.450  READ VERIFY SECTOR(S)
  c8 00 01 00 00 00 e0 00      00:06:03.450  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Aborted by host               80%       320         -
# 2  Short captive       Completed without error       00%        25         -

Device does not support Selective Self Tests/Logging
```

I'll post [sudo smartctl --test=long /dev/hda] results in a few hours (need to catch an hour or two of sleep). Thanks for your help so far.

---

### Post by Herman on 2008-04-13
:) That doesn't look too bad to me, there's a key to it here in this link, [http://en.wikipedia.org/wiki/Self-Monitoring,_Analysis,_and_Reporting_Technology](http://en.wikipedia.org/wiki/Self-Monitoring,_Analysis,_and_Reporting_Technology)

:confused: I wonder what happened to your file system then?
Did someone delete it on you? Or is it not an ext2 or ext3 file system perhaps? (Reiserfs?).

I guess the next thing to do would be to scan it with TestDisk and see what TestDisk can pick up. 
TestDisk can be installed in Ubuntu, or in Ubuntu Live CD with 'sudo apt-get install testdisk', and is found in Ubuntu Rescue Remix, System Rescue CD, Knoppix, GParted Live CD and so on.
With TestDisk you can scan your hard disk for start points of partitions and report what it can find.
Really I think it's more for the partition table, but give it a try anyway, it might help you, here's my link on that, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html").

I have to get some sleep pretty soon too, see you back here in a while.

Regards, Herman :)

---

### Post by smo0th on 2008-05-15
Seems like I have the same problem, I tried everything above and I get the same messages as cedge. It is really strange, my computer was running perfectly yesterday and this morning my keyboard fell, after few seconds the computer turned off just like that, no chance to view anything in the screen, is there a key combination that could lead to this kind of problem? Is there a way to prevent it from happening again?

Anyway, I tried testdisk and found something weird, please look at the attached screen shot. The primary bootable partition appears duplicated, however, when using quick and deeper search, partitions appear good.

I wrote again the partition information and rebooted to see if something changed but the same behavior prevails, when I try to mount the partition i get the following:

```

root@ubuntu:~# mount -t ext3 /dev/sda1 /media/ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:~# dmesg |tail
[  122.500266] NET: Registered protocol family 17
[  130.660370] NET: Registered protocol family 10
[  130.660577] lo: Disabled Privacy Extensions
[  130.661357] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  139.020251] hda-intel: Invalid position buffer, using LPIB read method instead.
[  140.889314] eth0: no IPv6 routers present
[  456.979234] cdrom: hda: mrw address space DMA selected
[ 1636.196628] VFS: Can't find ext3 filesystem on dev sda1.
[ 1646.761624] VFS: Can't find ext3 filesystem on dev sda1.
[ 2887.026893] VFS: Can't find ext3 filesystem on dev sda1.
root@ubuntu:~# 

```

And the output from fdisk is:
```

root@ubuntu:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000679c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60680   487412068+  83  Linux
/dev/sda2           60681       60801      971932+  82  Linux swap / Solaris

Disk /dev/hdb: 15.3 GB, 15367790592 bytes
255 heads, 63 sectors/track, 1868 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f1842cc

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1867    14996646    7  HPFS/NTFS
root@ubuntu:~# 

```

BTW: Yes, I have checked the BIOS settings and tried all possible configurations that may work, still nothing, besides it was working before anyway.

:confused:

---

### Post by Herman on 2008-05-18
> Seems like I have the same problem, I tried everything above and I get the same messages as cedge. It is really strange, my computer was running perfectly yesterday and this morning my keyboard fell, after few seconds the computer turned off just like that, no chance to view anything in the screen, is there a key combination that could lead to this kind of problem? Is there a way to prevent it from happening again? I think your problem would be more likely to be related to the sudden shut down that any keyboard sequence or combination.
I have seen a computer shut down suddenly from having some object  fall on the keyboard, pessing a lot of keys simultaneously. I think that probably it doesn't matter so much what the cause of the sudden shutdown is, the fact of the matter is that the kernel doesn't have time to clean up and write data that has been stored temporarily in memory to the hard disk and do whatever else it needs to do to properly unmount the file system before it shuts down.

The obvious ways to try to avoid file system damage are to try to avoid accidents with the keyboard and keep the rest of your hardware working okay, use a UPS unit in case of short power disruptions,and so on.

The best suggestions I have for fixing file systems once they are damaged is to try running e2fsck. The options I have in post               #[**6**]("http://ubuntuforums.org/showpost.php?p=4706971&postcount=6") of this thread usually work for me, and if e2fsck dosn't work with those options then I try to restore the superblock or run e2fsck with different options [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem")

I also have had two instances myself when a file system seemed to behave in a similar manner to what cedge was describing, that is, it appeared to be corrupt and neither e2fsck or attempting to restore the superblock would work, (because none could be found), and both times the problems in my case went away as suddenly and as myseriously as they appeared. One hard disk installation fixed itself the next time I ran the Alternate CD and installed in a partition beside it, and a USB flash memory device fixed itself when I tried to boot it anyway, (despite knowing there was something supposed to be wrong).
Another user ran fsck without the -a or -p options, (as advised from the output from 'sudo e2fsck -C0 -p -v -f '), and reported success. 

I'm not sure what's going on here, but maybe if we keep sharing information here someone will come up with a good solution or workaround.
Maybe try mounting and unmounting it with a different kernel even, might help, I don't know.

---

### Post by smo0th on 2008-05-18
working on it, found tons of things to fix with 'sudo e2fsck -C0 -p -v -f', I'll let you know the results later, thanx for the help :)

---

### Post by smo0th on 2008-05-18
I used ```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -f -v /dev/sda1
``` several times until I got all the problems fixed, now all seems to be ok with the disk and file structure but when I reboot I get a '1234F:' prompt which does nothing, looks like I need to fix the MBR(I screwed up). How can I do this :confused:

---

### Post by meierfra. on 2008-05-18
Did you try to fix your MBR with testdisk?

Anyway I suggest to reinstall grub. Boot from the live CD. In a terminal type

```
sudo grub
``` 

and at the grub prompt:

```
root (hd0,0)
setup (hd0)
quit
```

reboot and hopefully you'll boot into Ubuntu

---

### Post by smo0th on 2008-05-18
Thanks for the quick response, I just did that, but before establishing a root we need to get our disk configuration data using 'find /boot/grub/stage1', so in my particular case it was:

```

sudo grub
grub> find /boot/grub/stage1
grub> root (hd1,0)
grub> setup (hd1)
grub> quit

```
Then restart the computer, now I get the GRUB error 17 again but this time I'm able to enter the boot menu showing:

```

Ubuntu 7.10, kernel 2.6.22-14-generic
Windows XP Professional
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, memtest86+

```

I'm sure I've seen solutions in other threads to continue from this point, I'll search and post my results :)

---

### Post by smo0th on 2008-05-18
> **Herman said:**
> The obvious ways to try to avoid file system damage are to try to avoid accidents with the keyboard and keep the rest of your hardware working okay, use a UPS unit in case of short power disruptions,and so on.


Power disruptions are out of the list of possible root causes of the problem, I have been using a UPS since I got the computer. Still working to solve this.

---

### Post by meierfra. on 2008-05-18
Sorry about the "root (hd0,0)", I think I overlooked that you had two hard drives.

You should  be able to solve your problem by editing "/boot/grub/menu.lst". 
(change "root(hd1,0)" to "root (hd0,0)" everywhere and "#groot (hd1,0)" to "#groot (hd0,0)"

Or you could do 

sudo grub
root (hd1,0)
setup (hd0)

and change the boot order  in the bios.

Post the file "/boot/grub/menu.lst" from the ubuntu partition for more qualified help.

---

### Post by smo0th on 2008-05-18
Well, made some progress here, I did as indicated in last post, now I boot into ubuntu but right at the moment when the splash should be displayed, the screen goes blank, monitor goes to standby mode and computer seems to do nothing, the contents of my /boot/grub/menu.lst are:

```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=94fa4f81-66e2-4e75-a116-e8b81d3f8419 ro quiet splash pci=routeirq
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title Microsoft Windows XP Professional
root (hd1,0)
map (hd1,hd0)
map (hd0,hd1)
chainloader +1


title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=94fa4f81-66e2-4e75-a116-e8b81d3f8419 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

and the contents of /boot/grub/device.map are:

```
(hd0)	/dev/sda
(hd1)	/dev/hdb
```

I'll try re-checking disk for errors..

---

### Post by smo0th on 2008-05-18
Rebooted and still the same, is there a way to view the command-line progress/status in order to see where it gets stucked?

---

### Post by meierfra. on 2008-05-18
Your menu.lst looks fine. 
(although you should move the  windows item below the line "### END DEBIAN AUTOMAGIC KERNELS LIST". Otherwise it will be deleted during the next kernel update)

Just to get this straight.  The  grub menu appear at boot up, but then you select "ubuntu"  the screen goes blank after a while? Are you still getting Grub error 17?  Did you try to boot into windows? Did you try booting into recovery mode?

> is there a way to view the command-line progress/status 

Remove the "quiet" in menu.lst (although I'm not sure it will make a difference) Press "Ctr Alt F1" after you selected ubuntu in the grub.menu.

---

### Post by smo0th on 2008-05-18
Hello meierfra. Thanks for the windows item advice.

The GRUB menu appeared before, when (hd0,0) was not correctly allocated in menu.lst and when trying to boot error 17 appeared, right now I'm able to boot into ubuntu, when I try booting into windows I receive a GRUB error 11: Unrecognized string.

I removed the 'quiet' and 'splash' settings in the menu.lst section corresponding to my ubuntu boot, and system stops at 'run-init: /sbin/init: No such file or directory'.

As I'm now able to boot, although this system is still not able to properly boot, I'll perform the memory test and try to boot in recovery mode, I'll post back the results, thanks for following up :mrgreen:

---

### Post by smo0th on 2008-05-18
I selected recovery mode, the computer stops at the following lines:

```

run-init: /sbin/init: No such file or directory
[   30.117231] Kernel panic - not syncing: Attempted to kill init!

```

And that's it, I need a good fresh-brewed coffee, I'll search the forums seeking for this issue. :?

---

### Post by meierfra. on 2008-05-18
> try booting into windows I receive a GRUB error 11: Unrecognized string.


Oops. I didn't  pay much attention to your windows entry. It should be

title Microsoft Windows XP Professional
root (hd1,0)
map (hd1) (hd0)
map (hd0)  hd1)
chainloader +1


You also should check whether the "root=UUID=..." part in menu.lst is correct. You can find out the correct UUID via

```
sudo blkid
```

---

### Post by smo0th on 2008-05-18
yay! wxp is now able to boot, thanks for the support, and now I've also learned a new command(blkid)!! :D well, UUID is correct and now I booting directly to ubuntu(normal mode), the same kernel panic appears at second 24, got a great cup of coffee, next step: get rid of the kernel panic error. :mad:

---

### Post by smo0th on 2008-05-19
Well, this issue should be marked as solved, shame that I'm not the original poster. From now on this is a different problem and I'll post my findings in [this]("http://ubuntuforums.org/showthread.php?t=595421") thread.

Thanks Herman and meierfra for the help O:)

---

