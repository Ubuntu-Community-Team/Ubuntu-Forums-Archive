---
title: "System crashes and reboots randomly while browsing"
date: 2013-09-21
forum: General Help
---

### Post by Thunder Teaser on 2013-09-21
[SIZE=5]Please, help me finding out what's happening![/SIZE]

I'm totally clueless. I can't seem to find the cause of the reboots in dmesg or any other log. Basically, my system reboots randomly while browsing, **right after clicking on a link**. Sometimes I can browse for hours and sometimes for a few minutes. It doesn't matter which browser I'm using, that's why I ran a memtest, but my RAM is apparently good.

I haven't always had this problem. It started out some days ago (maybe almost a month ago), but I don't know exactly when because I haven't ever done anything particular to possibily damage my system. So either it was a package upgrade, or a kernel upgrade, or even nvidia drivers upgrade, I just can't tell.

Here's some info about my system: Ubuntu is installed on disk1 (SSD), its journal is on its own partition on disk4, while /var and /tmp are on disk4 as bind. A virtual swap is present too.

**lsb_release -a**

```
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 13.04
Release:        13.04
Codename:       raring
```

**/etc/fstab**

```
UUID=2b0da3e1-76d3-4dda-be4c-8dee07beb485 / ext4 discard,noatime,errors=remount-ro 0 1
UUID=68ce9c0c-d6ab-4f3a-bdfc-37e33ae8856f /media/disk2 ext4 defaults,errors=remount-ro,relatime 0 1
UUID=7071a8f4-95a1-4fc9-956f-302baf8ccbea /media/Sdisk3 ext4 defaults,errors=remount-ro,relatime 0 1
UUID=36539e72-9101-4663-a7d0-cd59098a5147 /media/disk4 ext4 defaults,errors=remount-ro,relatime 0 1
/media/disk4/var /var bind defaults,bind,noatime,mode=0755 0 0
/media/disk4/tmp /tmp bind defaults,bind,noatime,mode=1777 0 0
/media/disk4/swap/2048Mb.swap none swap sw 0 0
/dev/sr0 /media/dvd udf,iso9660 user,noauto,exec,utf8 0 0
```

**lshw -short**

```
H/W path      Device      Class       Description
=================================================
                          system      System Product Name (To Be Filled By O.E.M.)
/0                        bus         A8R-MVP
/0/0                      memory      64KiB BIOS
/0/4                      processor   AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
/0/4/5                    memory      128KiB L1 cache
/0/4/6                    memory      1MiB L2 cache
/0/36                     memory      4GiB System Memory
/0/36/0                   memory      1GiB DIMM DDR Synchronous 333 MHz (3,0 ns)
/0/36/1                   memory      1GiB DIMM DDR Synchronous 333 MHz (3,0 ns)
/0/36/2                   memory      1GiB DIMM DDR Synchronous 333 MHz (3,0 ns)
/0/36/3                   memory      1GiB DIMM DDR Synchronous 333 MHz (3,0 ns)
/0/100                    bridge      RS480/RS482/RS485 Host Bridge
/0/100/2                  bridge      RS480 PCI-X Root Port
/0/100/2/0                display     G96 [GeForce 9500 GT]
/0/100/1a                 bridge      M5249 HTT to PCI Bridge
/0/100/1a/11              multimedia  SB X-Fi
/0/100/1a/12              storage     VT6421 IDE/SATA Controller
/0/100/1a/13              bus         TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
/0/100/1a/14  eth0        network     88E8001 Gigabit Ethernet Controller
/0/100/1c                 bus         USB 1.1 Controller
/0/100/1c.1               bus         USB 1.1 Controller
/0/100/1c.2               bus         USB 1.1 Controller
/0/100/1c.3               bus         USB 2.0 Controller
/0/100/1e                 bridge      M1575 South Bridge
/0/100/1e.1               bridge      M7101 Power Management Controller [PMU]
/0/100/1f                 storage     M5229 IDE
/0/100/1f.1               storage     ULi M5288 SATA
/0/101                    bridge      K8 [Athlon64/Opteron] HyperTransport Technology Configuration
/0/102                    bridge      K8 [Athlon64/Opteron] Address Map
/0/103                    bridge      K8 [Athlon64/Opteron] DRAM Controller
/0/104                    bridge      K8 [Athlon64/Opteron] Miscellaneous Control
/0/1          scsi0       storage     
/0/1/0.0.0    /dev/sda    disk        120GB Samsung SSD 840
/0/1/0.0.0/1  /dev/sda1   volume      111GiB EXT4 volume
/0/2          scsi1       storage     
/0/2/0.0.0    /dev/sdb    disk        320GB WDC WD3200JD-22K
/0/2/0.0.0/1  /dev/sdb1   volume      10236MiB Windows NTFS volume
/0/2/0.0.0/2  /dev/sdb2   volume      288GiB EXT4 volume
/0/3          scsi2       storage     
/0/3/0.0.0    /dev/sdc    disk        500GB WDC WD5000AAKX-0
/0/3/0.0.0/1  /dev/sdc1   volume      465GiB EXT4 volume
/0/5          scsi3       storage     
/0/5/0.0.0    /dev/sdd    disk        320GB WDC WD3200JD-22K
/0/5/0.0.0/1  /dev/sdd1   volume      400MiB Linux filesystem partition
/0/5/0.0.0/2  /dev/sdd2   volume      297GiB EXT4 volume
/0/6          scsi4       storage     
/0/6/0.0.0    /dev/cdrom  disk        iHAS524   B
/0/7          scsi9       storage     
/0/7/0.0.0    /dev/sde    disk        Officejet 6500 E
/0/7/0.0.0/0  /dev/sde    disk
```

Thank you so much for reading so far! If you need more info, just tell me.

---

### Post by Thunder Teaser on 2013-09-23
Is something in my sysct.conf causing these reboots?

```
$ sudo sysctl -p
net.ipv4.tcp_no_metrics_save = 1
net.ipv4.tcp_moderate_rcvbuf = 1
net.core.netdev_max_backlog = 2500
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216
net.ipv4.tcp_rmem = 4096 87380 16777216
vm.swappiness = 10
kernel.sem = 250 32000 100 128
kernel.shmall = 2097152
kernel.shmmax = 2147483648
kernel.shmmni = 4096
fs.file-max = 100000
vm.vfs_cache_pressure = 50
```

---

### Post by searchfgold6789 on 2013-09-23
Hi Thunder Teaser,

Sounds troublesome. It could be a very large number of things, so it might be good to try to narrow things down: Does the same behavior happen with a Live USB/DVD? It would be better to try it with 12.04.

 - Richard

---

### Post by Thunder Teaser on 2013-09-28
Thank you so much Richard, and sorry for being late!

I'm not experiencing this problem both on a live Ubuntu 12.04 and on a live Ubuntu 13.04. In fact, as a said earlier, this behaviour was introduced a few months ago.

Good news is I was able to narrow things down anyways: it's happening randomly (I know there's something triggering the reboots, but they're random in my point of view) when **opening/closing a tab or a window** (both on Chromium and Firefox). It happens on Gmail when **clicking on the Print email button** on the top right* even more often!*

Does this mean something to you?

Also, I should have specified that I'm using Kubuntu.

---

### Post by searchfgold6789 on 2013-09-29
While this may or may not actually be the case, it does sound like a classic *memory issue*, though typically you would have problems running the Live CD, too, if that were the case. So the first thing I would do would be to [check the hard disk's health]("http://www.whileifblog.com/2011/09/15/kubuntu-how-to-test-your-hard-disk-drive/"). If that results in nothing, do run a Memtest for an extended period of time - I would give it a couple of hours, at least.

Do either of those things result in errors?

---

### Post by Thunder Teaser on 2013-10-03
Thanks, Richard.

I spent the whole day testing my hard drives and RAM. I ran the memtest for 5+ hours and it passed. I also ran smartctl long tests for every drive but they completed without errors.

At this point, I'm really out of ideas. I even checked my RAM timings (CAS latency, etc..) but they're set at a factory recommended standard. They always were, so I'm discarding this option. I used to run profile-sync-daemon, but I've removed it thinking it was the culprit, so my folder profiles are used instead, but I'm still experiencing reboots.

Last option would be my graphics card. Something might be crashing when trying to render.... something?

Do you have any more ideas?

---

### Post by searchfgold6789 on 2013-10-05
I have a ton of ideas, but I'm not sure if any of them will lead you in the right direction. Perhaps the best idea would be to attempt these in order of difficulty:

 
[LIST=1]
[*]Check the kernel logs for anything:```
dmesg
```
[*]Disable any proprietary graphics drivers; as you said, it might be a graphics issue.
[*]What's your motherboard Model Number and what's your RAM? Triple check the compatibility and check the voltage sensors with [lm-sensors]("http://www.linux.com/learn/tutorials/620416:discovering-and-monitoring-hardware-in-linux-").
[*]If you edited your [FONT=courier new]sysctl.conf[/FONT], revert it back to how it was. You may  also try to copy a new one from a Live session, since that apparently  works, backing up the old one and noting any differences. I do not know  much about [FONT=courier new]sysctl[/FONT] because I've never had to mess with it.
[*]Try several RAM configurations, trying just one RAM stick, just two, just three, whatever... you may be able to single out a specific RAM stick or find a configuration that does work.
[*]Run the Ubuntu installation entirely from the SSD or entirely from an HDD. Something about having [FONT=courier new]/tmp[/FONT] on a slower drive...
[*]I'm not going to recommend _re_installing Ubuntu because the  problem may return. If it is a hardware problem, then that wouldn't be a  real solution. However, you *could* make another Ubuntu installation on the same machine and see if the new installation doesn't have the same problem.
[*]Get a *good, new* (new model Corsair would be excellent) power supply from eBay and return it if it doesn't solve your problem or you can't afford to keep it.
[/LIST]
 
Post back when you've tried the first 4 and whatever else you have in mind.

---

### Post by Thunder Teaser on 2013-10-10
> **searchfgold6789 said:**
> I have a ton of ideas, but I'm not sure if any of them will lead you in the right direction. Perhaps the best idea would be to attempt these in order of difficulty:

 
[LIST=1]
[*]Check the kernel logs for anything:```
dmesg
```
[*]Disable any proprietary graphics drivers; as you said, it might be a graphics issue.
[*]What's your motherboard Model Number and what's your RAM? Triple check the compatibility and check the voltage sensors with [lm-sensors]("http://www.linux.com/learn/tutorials/620416:discovering-and-monitoring-hardware-in-linux-").
[*]If you edited your [FONT=courier new]sysctl.conf[/FONT], revert it back to how it was. You may  also try to copy a new one from a Live session, since that apparently  works, backing up the old one and noting any differences. I do not know  much about [FONT=courier new]sysctl[/FONT] because I've never had to mess with it.
[*]Try several RAM configurations, trying just one RAM stick, just two, just three, whatever... you may be able to single out a specific RAM stick or find a configuration that does work.
[*]Run the Ubuntu installation entirely from the SSD or entirely from an HDD. Something about having [FONT=courier new]/tmp[/FONT] on a slower drive...
[*]I'm not going to recommend _re_installing Ubuntu because the  problem may return. If it is a hardware problem, then that wouldn't be a  real solution. However, you *could* make another Ubuntu installation on the same machine and see if the new installation doesn't have the same problem.
[*]Get a *good, new* (new model Corsair would be excellent) power supply from eBay and return it if it doesn't solve your problem or you can't afford to keep it.
[/LIST]


 
Post back when you've tried the first 4 and whatever else you have in mind.

Dear Richard,
I just can't thank you enough for your precious help.

What's new is that my system rebooted in another different situation: I was scrolling a pdf when I noticed that the cursor was lagging, and after a short while it rebooted. Firefox was not running, so the problem is not in browsing only. This let me think that the problem was in my graphics card/propietary drivers, so I've disabled them. System hasn't rebooted (yet), so I'm going to test it for a week at least.

I already changed my PSU, triple checked my RAM, and switched back to default sysctl.conf too. dmesg logs don't say anything relevant.

I'm probably going to test an alternate full-SSD installation to see if it performs well.

I'll catch you later, and thanks a lot!

---

### Post by searchfgold6789 on 2013-10-10
Wow, well, if it's a bug in the graphics drivers, be sure to report it to whomever develops them!

Hopefully that solves the issue for good.

---

