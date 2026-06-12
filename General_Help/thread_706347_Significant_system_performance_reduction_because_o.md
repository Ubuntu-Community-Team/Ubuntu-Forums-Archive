---
title: "Significant system performance reduction because of hdds."
date: 2008-02-24
forum: General Help
---

### Post by Joe_Bishop on 2008-02-24
First time loading takes a lot of time with the hard drive is heavily working. The whole system is also affected very much. It often takes a moment for system to response on key press, sometimes mouse cursos freezes for a moment.
I have the system:

Ubuntu 7.10 x86
```
~$ uname -a
Linux master 2.6.22-14-386 #1 Tue Feb 12 07:12:19 UTC 2008 i686 GNU/Linux

```
AXP 2500+ on nForce2 400Ultra (Gigabyte GA-7N400 motherboard),
1.0Gb + 0.5Gb Hynix memory (it works well, no errors), 
256Mb GeForce 7600gt AGP 8x (Leadtek, proprietary nVidia driver from repo, standard for Gutsy)
Realtek 8139 and 3com 3c905c-tx Fast Ethernet PCI Controllers, both working at 100Mb mode
Creative Audigy 2zs PCI Sound Card,
Beholder 507rds PCI TV-Tuner (Philips SAA7134 chipset)
```


$ lspci 
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:07.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
01:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
01:09.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev f0)
01:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 7600 GT (rev a2)
```
IDE devices:
LG GSA 4167 DVD±RW on slave 2
Maxtor 6L300R0 (16Mb, 300Gb) = /dev/hda and Western Digital WDC WD800BB (2Mb,80Gb) = /dev/hdb HDDs, both on slave 1

```
$ sudo hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   860 MB in  2.00 seconds = 429.92 MB/sec
 Timing buffered disk reads:  182 MB in  3.01 seconds =  60.50 MB/sec

```

```
$ sudo hdparm -tT /dev/hdb

/dev/hdb:
 Timing cached reads:   864 MB in  2.00 seconds = 431.11 MB/sec
 Timing buffered disk reads:  142 MB in  3.00 seconds =  47.33 MB/sec

```

Both / and /home partitions uses JFS file system, they both placed at hda (the largest) hdd
```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6              24G   16G  7.6G  68% /
varrun                760M  124K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
udev                  760M   88K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
lrm                   760M   24M  736M   4% /lib/modules/2.6.22-14-386/volatile
/dev/hda5              20G   12G  7.8G  61% /home
/dev/hdb1              75G   51G   25G  68% /media/c
/dev/hda3              71G   39G   32G  55% /media/d
/dev/hda4             165G  143G   23G  87% /media/e
tmpfs                 760M   24K  760M   1% /tmp

```

/media/c is the windows partition on the hdb and using ntfs-3g driver
/media/d and /media/c are windows partitions and using ntfs-3g too
What can I do to improve this issue?
I found [http://bbs.archlinux.org/viewtopic.php?id=35200](http://bbs.archlinux.org/viewtopic.php?id=35200), but I don't want to recompile the kernel.
And, to say, I use the same Ubuntu at work, but it works significantly better there.

---

### Post by torgrot on 2008-02-24
When you say both drives are on slave, do you mean there are CDRoms or DVDs as master on both channels?  If so, put both hard drives on one channel and the CDRoms on the other.  A hard drive and a CDRom on one channel limits the hard drive to the fastest speed of the CDRom.  

torgrot

---

### Post by Joe_Bishop on 2008-02-24
> **torgrot said:**
> When you say both drives are on slave, do you mean there are CDRoms or DVDs as master on both channels?  If so, put both hard drives on one channel and the CDRoms on the other.  A hard drive and a CDRom on one channel limits the hard drive to the fastest speed of the CDRom.  

torgrot
I meant CD-ROM on slave 2, and both HDDs on the other slave 1.

---

### Post by torgrot on 2008-02-24
You have two IDE channels.  Both hard drives are connected to one channel, on the same ribbon cable..  Is that correct?  

torgrot

---

### Post by harold4 on 2008-02-24
> **Joe_Bishop said:**
> I meant CD-ROM on slave 2, and both HDDs on the other slave 1.

So both hdd are IDE and on the primary IDE controller?  One being master and one being slave?  I'm missing how both can be on slave1

---

### Post by Joe_Bishop on 2008-02-24
Yes, both hdd are IDE and on the primary IDE controller.

---

### Post by Joe_Bishop on 2008-02-24
> **torgrot said:**
> You have two IDE channels.  Both hard drives are connected to one channel, on the same ribbon cable..  Is that correct?  

torgrot
absolutely

---

### Post by torgrot on 2008-02-24
I just looked at the specs for both of your drives, the 300GB drive is being limited by the speed of the 80GB drive.  Also it would appear that you haven't got the fastest speed selected for the 80GB drive in BIOS.  You could try selecting atuo detect for both drives in the BIOS, but first write down the values that are there now.  The 80GB drive supports up to mode 5 at 100MBs and the 300GB drive supports mode 6 at 133MBs, but connected on the same cable the best they can do is mode 5 at 100MBs.  The one other thing you could look at is the cable itself.  In order to achieve mode 5 or 6 you need to have an 80 wire cable.  If you received a cable with the 300GB drive, try using that one.

torgrot

---

