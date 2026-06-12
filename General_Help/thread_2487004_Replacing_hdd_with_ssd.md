---
title: "Replacing hdd with ssd"
date: 2023-05-19
forum: General Help
---

### Post by grey1beard on 2023-05-19
Running 22.04 on my hp desktop, In the instructions I am following, the only question I have is where do I install gparted, ready to carry out the process ?

Do I have it on the bootable ubuntu live usb stick I've prepared, or on the old hdd, or on the new ssd ?

---

### Post by aljames2 on 2023-05-19
Gparted is on the Live USB you created.  You can boot up the Try Ubuntu and access Gparted there.  

Not knowing what steps you are following, hopefully it reminds you to have a backup of all your data somewhere else besides the HDD you are replacing.  If not, do that first.

---

### Post by grey1beard on 2023-05-19
Thanks for the quick reply.
Yes, I have done a full back up onto a separate external hdd. 
In fact that was what made me aware that my desktop hdd was on its last legs, and finally I had a good excuse to invest in ssd !
John

---

### Post by oldfred on 2023-05-19
Be sure to use gpt partitioning, particularly if UEFI system which all systems since 2012 are.
Only if installing Windows in older BIOS only system, would you use MBR(msdos) partitioning. 

You can also use gparted but must change device label to gpt or default partitioning first.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.

---

### Post by ne29914 on 2023-05-19
> **aljames2 said:**
> Gparted is on the Live USB you created.  You can boot up the Try Ubuntu and access Gparted there.  

Are you certain? On Lubuntu it isn't. Dunno about other distris.

---

### Post by oldfred on 2023-05-19
If using a flavor that does not include gparted, just add it. You will have to readd each time you reboot flash drive installer.
sudo apt install gparted

Or you can download a gparted live repair ISO and create a flash drive for it.
[http://gparted.org/documentation.php](http://gparted.org/documentation.php)
[https://gparted.org/news.php](https://gparted.org/news.php)

---

### Post by MAFoElffen on 2023-05-19
Just an observation... You never described the steps you plan to take to do this. Vary vague.

You may want to describe those, so that another set of eyes can tell you if they make logical sense.

For me, just speaking in the same general, vague terms, I can duplicate a disk, then use 'gparted' to change the partition sizes to my liking... That is the least amount of work.

Or by the method of Migration of what was there, to a new drive-- just create a new GPT partition table, new partitions (or other filesystem containers), then rsync the contents of each partition to the new drive into what is new. Or reorganize everything into a newer form (Like spliting out some folders into there own storage containers). That way, you can transform whatever was on the old drive, to "a new form". Example: What was stored in a flat filesystem, to LVM2, ZFS, MD Devices, BTRFS, etc...

Saying the above: What is "your plan"?

---

### Post by grey1beard on 2023-05-19
With reference to my original post, this is the source of the instructions I am about to follow.
It seems fairly straightforward to me, and I can follow the instructions with my limited knowledge.

[https://yulistic.gitlab.io/2018/03/replace-hdd-or-ssd-without-the-re-installation-of-ubuntu/](https://yulistic.gitlab.io/2018/03/replace-hdd-or-ssd-without-the-re-installation-of-ubuntu/)

For an 84 yo, the jargon that is used only confuses me, when I find the original instructions quite easy to follow.

My wife tells me not to be a crusty old fart, so thank you for your help
.
John

---

### Post by oldfred on 2023-05-19
How old is your system?
Systems since 2012 use UEFI boot with gpt partitioning.
But the link you show has the MBR(msdos) partitioning which goes back to when you were a youngster. :)
Gpt is the new fancy thing that has only actually been around for over 20 years, and used a lot in the last 10 years.

---

### Post by grey1beard on 2023-05-19
My desktop is not as old as me, and I do see that the article was written by someone who obviously had a much older system.
I guess mine, a HP ProDesk- 600-G1-SSF, is much younger, but I assumed that his instructions(written in 2018) would still be applicable.

---

### Post by mIk3_08 on 2023-05-19
For me, if you are to replace your hdd to ssd with the complete Operating System on it. You can always do the cloning. Clonezilla might be more tricky to you but I can assure you that it can give you a positive results.
I've been using it for quite a while now so far so good it never give me a headaches. But a friendly advice, always be careful when performing it. I am certain that it can help you solve your issue. 
By the way. If you don't know how to use it. [Click Here]("https://clonezilla.org/") for more info. Regards and cheers.

---

### Post by dragonfly41 on 2023-05-20
I am only reading the title of this thread.

Once you have the ancient suspect HDD pulled out (as I did with Windows internal HDD in dual boot setup) you might consider deleting its contents, placing it in a container, checking it and possibly using it as just one of n+1 backup media. This way you guard against it failing as one backup media.
I invested in StarTech USB (3.0) dual docking bay with two containers and own power supply

---

### Post by grey1beard on 2023-05-20
Hi mlk3_08
Trying out the Clonezilla route,

 [https://www.fosslinux.com/28892/how-to-create-a-clonezilla-live-usb-drive-on-linux.htm](https://www.fosslinux.com/28892/how-to-create-a-clonezilla-live-usb-drive-on-linux.htm) 

but run into a problem with the' Etcher' download. 

I'm following the FossLinux site instructions for creating a bootable Clonezilla  usb drive, and got as far as giving the Etcher downloaded file permission to run as an executable, but not found any way of launching it !

John
EDIT probably important, but the download isn't a zip file as indicated on their site - it appears as balenaEtcher-1.18.4-x64.Applmage

---

### Post by mIk3_08 on 2023-05-21
> **grey1beard said:**
> Hi mlk3_08
Trying out the Clonezilla route,
 [https://www.fosslinux.com/28892/how-to-create-a-clonezilla-live-usb-drive-on-linux.htm](https://www.fosslinux.com/28892/how-to-create-a-clonezilla-live-usb-drive-on-linux.htm) 
but run into a problem with the' Etcher' download. 
I'm following the FossLinux site instructions for creating a bootable  Clonezilla  usb drive, and got as far as giving the Etcher downloaded  file permission to run as an executable, but not found any way of  launching it !
John
EDIT probably important, but the download isn't a zip file as indicated  on their site - it appears as balenaEtcher-1.18.4-x64.Applmage

I haven't use "Etcher". Never in my entire Linux life. If you are to create Clonezilla Live on USB flash drive or USB hard drive
[Click Here]("https://clonezilla.org/liveusb.php#linux-setup") on how to create Clonezilla Live on USB flash drive or USB hard drive.
For me, this is very easy setup just follow the guide. Hope you'll be successful on this because I usually use this guide.
Just  please read carefully and follow the instructions. (Be careful on pointing your device) 
```
pmount /dev/sdg1 /media/disk/
```
If you can't be  successful in this guide. I don't know anymore how can I teach you.
Regards and cheers.

---

### Post by grey1beard on 2023-05-21
My bad. I think I misread the line **Download the amd64 (x86-64) version of Clonezilla Live zip file. ** to expect this to be a zip file, not the amd version. 
Then went off down a rabbit hole.
Regards, and thanks for your patience.
John

EDIT
Just tested my live usb stick, and it works OK. Booted up from the stick, then closed down before I plan the next move !

---

### Post by mIk3_08 on 2023-05-22
Let me see your hardware first.
Please run the command below and paste the result here in thread wrap with code.
```
sudo lshw -C cpu
```
Regards and cheers.

---

### Post by grey1beard on 2023-05-22
> *-cpu                     
       description: CPU
       product: Intel(R) Core(TM) i7-4770K CPU @ 3.50GHz
       vendor: Intel Corp.
       physical id: 9
       bus info: cpu@0
       version: 6.60.3
       slot: SOCKET 0
       size: 1795MHz
       capacity: 3900MHz
       width: 64 bits
       clock: 100MHz
       capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts md_clear flush_l1d cpufreq
       configuration: cores=4 enabledcores=4 microcode=40 threads=8


Having just discovered that my desktop has two drives, one a 1t hdd and the other a 480G ssd, I now realize that I have very little idea as to what I need to do next to find out what is where, partition-wise !
John

---

### Post by grey1beard on 2023-05-22
I've just obtained this info regarding my partitions.

---

### Post by oldfred on 2023-05-22
You can post this to see all partitions and use.Will only show mounted partitions, so if some not mounted you can mount them.
```

lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
```

---

### Post by grey1beard on 2023-05-22
As per suggestion, but I'll have to think about what it's telling me !

> lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
NAME FSTYPE   SIZE FSUSED LABEL PARTLABEL MOUNTPOINT UUID                                 PARTUUID
sda         447.1G                                                                        
&#9492;&#9472;sda1
     ext4   447.1G 215.4G                 /home      142d4978-1951-4909-91b8-096e5c8e93db 6a2a3c31-dec5-4ed5-8416-0ec0a31828ea
sdb         931.5G                                                                        
&#9500;&#9472;sdb1
&#9474;    vfat     243M     6M                 /boot/efi  7CDC-DD5C                            c84a0b01-9537-4b02-aef7-d8951c77033c
&#9500;&#9472;sdb2
&#9474;    ext4     977M 264.9M                 /boot      75115910-c4ad-4b43-ab5b-56f76e74c317 cf14aff4-04c2-499c-885d-88016cfafca6
&#9492;&#9472;sdb3
     ext4   930.3G  36.6G                 /          1308b489-462f-4afb-95e3-4b54a33452bd 98cb5f73-f581-4c93-a186-4b05ac7a383e
sr0          1024M  

---

### Post by mIk3_08 on 2023-05-22
> **grey1beard said:**
> Having just discovered that my desktop has two drives, one a 1t hdd and the other a 480G ssd, I now realize that I have very little idea as to what I need to do next to find out what is where, partition-wise !
John
The amd64 (x86-64) version of Clonezilla Live zip file for use on PCs  with AMD64 or Intel 64 processors. It supports multi-core processor, and  multiprocessor. 
> **grey1beard said:**
> As per suggestion, but I'll have to think about what it's telling me !
This is probbly your Ubuntu OS.
> sdb 931.5G
&#9500;&#9472;sdb1
&#9474; vfat 243M 6M /boot/efi 7CDC-DD5C c84a0b01-9537-4b02-aef7-d8951c77033c
&#9500;&#9472;sdb2
&#9474; ext4 977M 264.9M /boot 75115910-c4ad-4b43-ab5b-56f76e74c317 cf14aff4-04c2-499c-885d-88016cfafca6
&#9492;&#9472;sdb3
ext4 930.3G 36.6G / 1308b489-462f-4afb-95e3-4b54a33452bd 98cb5f73-f581-4c93-a186-4b05ac7a383e
sr0 1024M 
And this is your extended Storage;
> NAME FSTYPE SIZE FSUSED LABEL PARTLABEL MOUNTPOINT UUID PARTUUID
sda 447.1G
&#9492;&#9472;sda1
By the way, in cloning it is advice that destination storage is larger capacity than the source storage. I don't think you can do this by clone. 
I think we should go back to your original plan which is the "gparted" thing or gdisk a copy GPT partition scheme.

---

### Post by grey1beard on 2023-05-22
I seem to have spent most of my life going round in circles, so this seems to be no exception !
What may be an unusual partition setup is probably down to me. If I remember correctly, this desktop was bought with a windows OS, and I needed to switch to Ubuntu, as that is what was my go-to territory.
Though a little younger, I didn't have much more idea of what I was doing then as I do now. 
So lots of patience, everyone. This may be a bumpy ride !!
Regards
John
PS in some odd way, I'm enjoying the experience.
PPS Wendy, SWMBO, says she is suffering too !

---

### Post by MAFoElffen on 2023-05-22
Just an observation, which was not copied over and pointed out in mlk3_08's post:
```

NAME FSTYPE SIZE FSUSED LABEL PARTLABEL MOUNTPOINT UUID PARTUUID
sda 447.1G
&#9492;&#9472;sda1
ext4 447.1G 215.4G [COLOR=#ff0000]/home[/COLOR] 142d4978-1951-4909-91b8-096e5c8e93db 6a2a3c31-dec5-4ed5-8416-0ec0a31828ea

```
Which points out that the SSD is mounted into the system as your /home directory...

If you also do this, it will also show it:
```

grep -v '#' /etc/fstab

```
To match up that output with the previous...

<Back to observing, with interest...>

---

### Post by oldfred on 2023-05-22
Usually those with SSD & HDD, put system on SSD, maybe have /home on SSD, but for ease of configurtion have /home on HDD. 
If /home on SSD inside / or separate then use HDD for lots of data and/or backup (more of a copy) of some data. 
Real Backup still should be on other devices to be able to recover data that a copy might not have.

---

### Post by grey1beard on 2023-05-22
What was in my mind at the beginning of this process was to do just a routine back-up.
Then it occurred to me that to replace the HDD (which I thought was my only drive) with an ssd would give me not only a greatly improved performance, but enhanced storage.
It was quite a coincidence that my system warned me that the drive was overheating !
So lots of incentive to do the switch. Only when I started to explore what was involved did I learn more about my present system.
So, "onwards and upwards".
John

---

### Post by grey1beard on 2023-05-22
This may seem like throwing the towel in, but would it be a simpler process in the long run to take out both drives (hdd and ssd) , install the new 1Tb ssd, and do a completely fresh install ?
I do have a 22.04 bootable usb stick, and I do have a back up of all my data files.
Also, I have a working laptop as a link, if everything goes pear-shaped !

---

### Post by oldfred on 2023-05-22
As long as you have good backups, you can do just about anything.
I regularly install just to test latest version or a different flavor. I use grub2's loopmount, load ISO into RAM from SSD and install to HDD or another external SSD. Install then can be very fast, about 12 min. It takes longer to download list of installed apps. You do include that in your backup to make it easy to reinstall apps?

---

### Post by mIk3_08 on 2023-05-22
> **grey1beard said:**
> This may seem like throwing the towel in, but  would it be a simpler process in the long run to take out both drives  (hdd and ssd) , install the new 1Tb ssd, and do a completely fresh  install ?
I do have a 22.04 bootable usb stick, and I do have a back up of all my data files.
Also, I have a working laptop as a link, if everything goes pear-shaped !
Just curious into something...  Please run the command below. And paste the results here in thread wrap with code.
```
sudo smartctl -a /dev/sda,/dev/sdb
```
If the command above wont work please install smartmontools
```
sudo apt install smartmontools
```

---

### Post by grey1beard on 2023-05-22
> sudo smartctl -a /dev/sda,/dev/sdb
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.19.0-41-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

Smartctl open device: /dev/sda,/dev/sdb failed: No such device

??
John

---

### Post by mIk3_08 on 2023-05-23
> **grey1beard said:**
> ??
John
Try this commnd below. And paste the results here in thread wrap with code. Regards and cheers.
```
sudo smartctl -a /dev/sda
```

---

### Post by grey1beard on 2023-05-23
```
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.19.0-41-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Device Model:     BTO-480GB
Serial Number:    AA000000000000002561
Firmware Version: T0520A0
User Capacity:    480,103,981,056 bytes [480 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Form Factor:      2.5 inches
TRIM Command:     Available, deterministic, zeroed
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2 T13/2015-D revision 3
SATA Version is:  SATA 3.2, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Mon May 22 23:24:04 2023 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  120) seconds.
Offline data collection
capabilities: 			 (0x11) SMART execute Offline immediate.
					No Auto Offline data collection support.
					Suspend Offline collection upon new
					command.
					No Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					No Selective Self-test supported.
SMART capabilities:            (0x0002)	Does not save SMART data before
					entering power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  10) minutes.

SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x0032   100   100   050    Old_age   Always       -       0
  5 Reallocated_Sector_Ct   0x0032   100   100   050    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   050    Old_age   Always       -       7729
 12 Power_Cycle_Count       0x0032   100   100   050    Old_age   Always       -       1314
160 Unknown_Attribute       0x0032   100   100   050    Old_age   Always       -       0
161 Unknown_Attribute       0x0033   100   100   050    Pre-fail  Always       -       62
163 Unknown_Attribute       0x0032   100   100   050    Old_age   Always       -       192
164 Unknown_Attribute       0x0032   100   100   050    Old_age   Always       -       28704
165 Unknown_Attribute       0x0032   100   100   050    Old_age   Always       -       161
166 Unknown_Attribute       0x0032   100   100   050    Old_age   Always       -       2
167 Unknown_Attribute       0x0032   100   100   050    Old_age   Always       -       16
168 Unknown_Attribute       0x0032   100   100   050    Old_age   Always       -       5050
169 Unknown_Attribute       0x0032   100   100   050    Old_age   Always       -       100
175 Program_Fail_Count_Chip 0x0032   100   100   050    Old_age   Always       -       0
176 Erase_Fail_Count_Chip   0x0032   100   100   050    Old_age   Always       -       0
177 Wear_Leveling_Count     0x0032   100   100   050    Old_age   Always       -       0
178 Used_Rsvd_Blk_Cnt_Chip  0x0032   100   100   050    Old_age   Always       -       0
181 Program_Fail_Cnt_Total  0x0032   100   100   050    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   100   100   050    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   050    Old_age   Always       -       104
194 Temperature_Celsius     0x0022   100   100   050    Old_age   Always       -       40
195 Hardware_ECC_Recovered  0x0032   100   100   050    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   100   100   050    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   050    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0032   100   100   050    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x0032   100   100   050    Old_age   Always       -       0
232 Available_Reservd_Space 0x0032   100   100   050    Old_age   Always       -       62
241 Total_LBAs_Written      0x0030   100   100   050    Old_age   Offline      -       55671
242 Total_LBAs_Read         0x0030   100   100   050    Old_age   Offline      -       319561
245 Unknown_Attribute       0x0032   100   100   050    Old_age   Always       -       35847

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%        14         -

Selective Self-tests/Logging not supported
```

My biggest quote, I think.  Not too happy about all the 'old age' entries !

---

### Post by mIk3_08 on 2023-05-23
How about in your hdd. 
```
sudo smartctl -a /dev/sdb
```

> **grey1beard said:**
> What was in my mind at the beginning of this process was to do just a routine back-up.
Then it occurred to me that to replace the HDD (which I thought was my only drive) with an ssd would give me not only a greatly improved performance, but enhanced storage.
It was quite a coincidence that my system warned me that the drive was overheating !
So lots of incentive to do the switch. Only when I started to explore what was involved did I learn more about my present system.
So, "onwards and upwards".
John
Yes. exactly true. The performance of hdd vs ssd is quite difference. 

> **grey1beard said:**
> This may seem like throwing the towel in, but would it be a simpler process in the long run to take out both drives (hdd and ssd) , install the new 1Tb ssd, and do a completely fresh install ?
I do have a 22.04 bootable usb stick, and I do have a back up of all my data files.
Also, I have a working laptop as a link, if everything goes pear-shaped !
For me, You can still use your BTO-480GB ssd for your plan of new complete fresh install of 22.04 Ubuntu. And use your hdd as your back up. Because as far as I know, your current hdd with Ubuntu  installed on it uses only a little space of your hdd 1TB.
Which is enough to be transferred to your BTO-480GB ssd when you decide to make it as a main bootable storage system. So no need for another new 1Tb ssd.

> sdb 931.5G
&#9500;&#9472;sdb1
&#9474; vfat 243M 6M /boot/efi 7CDC-DD5C c84a0b01-9537-4b02-aef7-d8951c77033c
&#9500;&#9472;sdb2
&#9474; ext4 977M 264.9M /boot 75115910-c4ad-4b43-ab5b-56f76e74c317 cf14aff4-04c2-499c-885d-88016cfafca6
&#9492;&#9472;sdb3
ext4 930.3G 36.6G / 1308b489-462f-4afb-95e3-4b54a33452bd 98cb5f73-f581-4c93-a186-4b05ac7a383e
sr0 1024M                      

Regards and cheers.

---

### Post by HermanAB on 2023-05-23
Howdy,

My tuppence worth:
In my experience it is usually best to backup my data, then install new hardware, followed by a fresh install of Linux and then copying my data back from the backup, rather than trying to copy an old and tired version of Linux.

I’m old and tired too and a copy isn’t going to do me much good either… &#128514;

Cheers,

Herman

---

### Post by mIk3_08 on 2023-05-23
It is also safe/best if you remove your hdd when you decide install new 22.04 Ubuntu in your BTO-480GB ssd. And make it as your back-up then. 
You can use "Sata Hard Drive Enclosure" for moving your data from hdd to you new main bootable storage system. Which is the ssd BTO-480GB ssd.
Regards and cheers.

---

### Post by oldfred on 2023-05-23
I typcially only trust drives for about 5 years, used to be 3. I then get new drive and demote old drive to one of my backups or other use if still working ok.

Built this system in 2016 and it had the new (to me) M.2 connector that could use either SATA or NVMe drives. Back then NVMe was very expensive and the SATA was a bit more than a standard SSD. But now that NVMe drives are lower in cost & I wanted larger drive, I removed M.2 SATA & added new NVMe drive. Cannot say in my system NVMe is noticeable faster than SSD, but SSD is a lot faster than the HDD.

I then put SATA M.2 drive in a M.2 to USB adapter. I now will not buy any more flash drives as I have a lot. The external SSD is almost as fast as an internal drive. Writing some of my backups to flash drive is now frustratingly slow.

---

### Post by grey1beard on 2023-05-28
Just had this pop up. I was expecting the hdd to be the problem, but it turns out to be the ssd. I have found a reference to error readings of temperature if there is 'uderpopulation of ssd's in the pc. I assume that meant poor heat conduction, and that an extra ssd would change the air flow, and hence heat dissapation, But not sure.
The new caddy and cable for the 1Tb ssd(already purchased) arrives today, so it may be in the nick of time !

Havin problems uploading the screenshot  - says it's not a valid .jpg file ! Ho hum. It just said the ssd was about to fail, and gave its temperature as 40C, which is what it is when I first switch on anyway. So none the wiser.

---

### Post by grey1beard on 2023-05-29
So far, so good.
I now have installed the new 1Tb ssd, and it is recognized my the computer. Now just the courage to start re-organizing the whole system !

Am I right to plug in my bootable ubuntu stick, and take the option to install it in the new ssd ? Then re-order the boot sequence to make this  the boot disc ?

Part of my confusion comes from the current installation, where I have /boot on the 1Tb hdd, and /home on the original 480Gb ssd. 
This may have come from my initial mistake when replacing Windows with ubuntu a few years ago, but I don't remember :confused:

John

---

### Post by oldfred on 2023-05-29
If using Ubuntu's Ubiquity installer, it will want to install grub to whatever UEFI sees as first drive.
If using Ubuntu's Subquity installer with the newest versions that supposed has been fixed.
Most desktops do not need a separte /boot partition, but if UEFI, you do need the ESP - efi system partition.

---

### Post by grey1beard on 2023-06-05
It's been a 'recover a brick' route, I have to admit, but I'm now back in some sort of control !

The new ssd primary drive is giving me the improvements I hoped for, and my new, clean install is coming together.

Question.
I have attached two screen shots, one from my laptop, showing the layout I prefer, and one from the new desktop, which I don't.
I'm having trouble even identifying the search terms I need to seek help in re-creating my original ( familiar !) scheme.
I'd be grateful for some guidance.
John

---

### Post by oldfred on 2023-06-05
I never used Unity. When Ubuntu went to it, I used fallback.
Unity is back to an official flavor. So is it Unity?
[https://ubuntu.com/desktop/flavours](https://ubuntu.com/desktop/flavours)

I am using Kubuntu, you should be able to run these to see versions.
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ echo $DESKTOP_SESSION [/COLOR]
plasma 
[COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ echo $XDG_SESSION_TYPE [/COLOR]
x11
[/FONT][FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /etc/*release[/COLOR]

[/FONT]

---

### Post by grey1beard on 2023-06-06
Is it Unity ?
Looking at your link, it certainly seems like it, but I never knowingly downloaded that 'flavor'.
Checked out your Terminal entries, and posted mine, but 'in over my head' !
John

---

### Post by dragonfly41 on 2023-06-06
Replying to post #39

[https://www.omgubuntu.co.uk/2022/04/installed-ubuntu-22-04-do-these-things-next](https://www.omgubuntu.co.uk/2022/04/installed-ubuntu-22-04-do-these-things-next)

Read above and install dashtodock to enable Activities docking panel to left of main window.

I also have a docky popup panel at bottom of window which can be useful.

---

### Post by kinddolphin8827 on 2023-06-06
A few questions and suggestions

Has the original poster considered using a utility such as  dd or even clonezilla?  

I'm not sure of the OPS skill level but there are always multiple ways to kill ticks as I like to say.

I'd strongly recommend that the OP invest in a both a USB attachable hard drive and pull out their modified  configuration files in order to save themselves from losing said files if the drive copy goes boink and a whole system re-installation is required to get bac to a operational system.

---

### Post by grey1beard on 2023-06-06
**and pull out their modified configuration files**
Thanks for that particular detail. It had crossed my mind that the only way to get to where I want to be is to do another clean install, and that would save a lot of work.

However, I'm still picking up new knowledge ( or refreshing what I've forgotten !), and I've spent my life doing repair work, and learned the patience that comes with it.
Regards
John

---

