---
title: "Trying to Speed Up Boot/Login Time - Need Help Interpreting Bootchart and dmesg"
date: 2015-03-13
forum: General Help
---

### Post by AmagicalFishy on 2015-03-13
[FONT=arial][SIZE=2][COLOR=black]I've been trying for like a week to speed up my boot and login times&#8212;but it's real difficult to find any information on how to interpret a Bootchart (in fact, I haven't found *any *general information regarding it).

Could someone give me some tips on what I should be shooting for?

Here's my Bootchart: [http://i.imgur.com/xETLuPb.png](http://i.imgur.com/xETLuPb.png)
Here's my dmesg: [http://pastebin.com/ySJK1WZV](http://pastebin.com/ySJK1WZV)

**Things I've noticed about Bootchart:**
[COLOR=#333333]Looking at the bootchart of more optimized systems, I notice that there are consistently large chunks of blue CPU usage in the first chart. I, on the other hand, have small blue spikes that are always overtaken by I/O Wait. In the 2nd chart, I notice that the Disk Utilization is always at (what seems to be) its max. Does this mean that things are utilizing the disk inefficiently?[/COLOR]
[COLOR=#333333]In which case, I think I'd like to maximize for CPU usage and minimize for disk utilization. I do not know how to do this, nor do I know if my interpretation of this chart is correct.

[B]Things I've noticed about dmesg:
[/B]Weird spikes:
[/COLOR]```
[    9.600783] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   24.800176] Adding 4881404k swap on /dev/sda6.  Priority:-1 extents:1 across:4881404k FS
```

```
[   30.365509] type=1400 audit(1426224617.008:75): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/mysqld" pid=1047 comm="apparmor_parser"[   36.636741] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   36.636783] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   39.204609] e1000e 0000:00:19.0: irq 50 for MSI/MSI-X
[   39.308572] e1000e 0000:00:19.0: irq 50 for MSI/MSI-X
[   44.601427] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   44.601463] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   45.007232] e1000e 0000:00:19.0: irq 50 for MSI/MSI-X
[   45.111174] e1000e 0000:00:19.0: irq 50 for MSI/MSI-X
[   45.328462] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   45.328497] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   49.917128] wlan0: authenticate with 88:f7:c7:2e:39:42
```

```
[   49.925544] wlan0: associated
[   51.568193] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[   57.975595] [UFW BLOCK] IN=wlan0 OUT= MAC=20:10:7a:7e:27:ca:88:f7:c7:2e:39:41:08:00 SRC=108.61.228.29 DST=10.0.0.11 LEN=97 TOS=0x00 PREC=0x20 TTL=51 ID=1167 DF PROTO=UDP SPT=8080 DPT=39605 LEN=77
[   59.301287] type=1400 audit(1426224645.912:76): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3362 comm="apparmor_parser"
[   59.301293] type=1400 audit(1426224645.912:77): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3362 comm="apparmor_parser"
[   59.301639] type=1400 audit(1426224645.912:78): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3362 comm="apparmor_parser"
[   68.193445] [UFW BLOCK] IN=wlan0 OUT= MAC=20:10:7a:7e:27:ca:88:f7:c7:2e:39:41:08:00 SRC=108.61.228.29 DST=10.0.0.11 LEN=97 TOS=0x00 PREC=0x20 TTL=51 ID=2935 DF PROTO=UDP SPT=8080 DPT=39605 LEN=77
[   71.546025] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:88:f7:c7:2e:39:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2
[   71.546959] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:88:f7:c7:2e:39:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2
[   71.547989] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:88:f7:c7:2e:39:41:08:00 SRC=172.16.12.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2
[   71.549137] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:88:f7:c7:2e:39:41:08:00 SRC=172.16.12.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2
[   71.756678] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:ac:18:26:e5:0b:f8:08:00 SRC=10.0.0.9 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2
[  197.746486] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:88:f7:c7:2e:39:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2
[  197.747538] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:88:f7:c7:2e:39:41:08:00 SRC=10.0.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2
[  198.256809] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:ac:18:26:e5:0b:f8:08:00 SRC=10.0.0.9 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2

```

I'm just not sure where to go from here. I've tried various random tweaks and such&#8212;but none of them have been specific to my computer. I'd like to be able to diagnose, specifically, this here laptop. Any help would be hugely appreciated. :)[/COLOR][/SIZE][/FONT]

---

### Post by Hulk_Joshua on 2015-03-13
Try BUM (from software center) to disable some unneeded services

---

### Post by AmagicalFishy on 2015-03-13
I have BUM, yes. (Thank you for the suggestion, anyway!)

I would really like some help dealing with Bootchart and dmesg, though.

---

### Post by oldfred on 2015-03-13
Never learned Boot chart.
But longer time stamps are an issue in dmesg.
Your drives seem to mount a little slow, but now I have an SSD so not sure what a slow laptop drive takes in time.
Booted old 2006 laptop and it takes this:
```
[    1.957000] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   21.780845] Adding 3065852k swap on /dev/sda6.  Priority:-1 extents:1 across:3065852k 

```

And you seem to be having similar issues with cups & wlan. Does wireless work once system is booted?

Another thread with cups & wlan issues:
[http://ubuntuforums.org/showthread.php?t=2268599](http://ubuntuforums.org/showthread.php?t=2268599)

---

### Post by AmagicalFishy on 2015-03-13
Huh. Wireless works excellently when my system is booted, and my printer works well, too. 

I use WICD instead of the default network manager, though&#8212;do you think that could have something to do with it?

Also, is there a way to explicitly tell Ubuntu in what order to start things? I think it's making inefficient use of my HDD. There are people with old laptops who've gotten their boot time down to 20 seconds (I don't expect nearly that fast of a boot, but I'm trying to shoot for around 40 - 50)

Edit: Apparently, my HDD during boot up is at *constant* full-capacity use. This does not seem right.

---

### Post by oldfred on 2015-03-13
What size & speed drive.?
sudo lshw -C Disk -short

sudo parted -l

Any issues with drive in Smart Data. You can see that in Disks and use icon in upper right corner.

And do you have a smaller / (root) partition so boot files are closer together on drive or one very large / so boot has to jump around entire drive to boot?

---

### Post by AmagicalFishy on 2015-03-13
My lshw output put is:
```
H/W path         Device      Class          Description=======================================================
/0/2/0.0.0       /dev/sda    disk           640GB WDC WD6400BPVT-2
/0/3/0.0.0       /dev/cdrom  disk           DVD A  DS8A8SH

```

And my parted output is:
```
Model: ATA WDC WD6400BPVT-2 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      106MB   262GB  262GB   primary   ntfs
 3      262GB   637GB  375GB   extended
 5      262GB   632GB  370GB   logical   ext4
 6      632GB   637GB  4999MB  logical   linux-swap(v1)

```

I am pretty sure I do not have a smaller root partition.  I'm going to follow this guide: [https://help.ubuntu.com/community/BootPartition]("https://help.ubuntu.com/community/CreateBootPartitionAfterInstall") &#8212; is that an ok thing to do?

Also, I dual-boot Windows 7 (which explains all of the other partitions).

By the way, oldfred, thanks so much for helping me. You have no idea how joyed I am to start making some progress. :D

---

### Post by oldfred on 2015-03-13
I once created a /boot partition and literally undid it 5 minutes later. Back then I really wanted a grub only partition as I was multi-booting several Linux partitions. But with grub2 even that is not required.

I normally just suggest a separate / (root) partition of about 25GB and either /home or /mnt/data for everything else. If a newer user the separate /home is easier to configure. I use about 11GB of my 25GB /, and that includes my /home. But all my data is really in another partition. When still booting XP I had two data partitions, one NTFS for shared data and one Linux formatted. I also had a smaller system partition for XP for the same reasons, but NTFS requires lots of unused space like 30% or it starts to slow down. Linux likes extra space also and even hides 5% when you format a Linux partition.

The separate data partition is more of a recommendation when multi-booting Linux installs. Best not to share /home, but data is easily shared. You may only need a shared NTFS partition and a somewhat larger / partition.

If you have a separate /boot partition, then you have to manage that. It used to be that kernels were not housecleaned and we have many threads with users had a full /boot where updates stop working. But now they have updated the update to only keep 2 kernels. May depend on what version your are running.

---

