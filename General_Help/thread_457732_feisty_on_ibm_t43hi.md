---
title: "feisty on ibm t43hi"
date: 2007-05-28
forum: General Help
---

### Post by dachinster on 2007-05-28
hi,
ive installed feisty successfully home with not many problems so i decided to try it out on my company laptop which is an IBM t43 since ive read all over that feisty works great out of the box on this model

i resized my windows partition using gparted and i installed feisty on a 10GB ext3 partition and a 2GB swap file.

the install went fine and it restarted ok
the bootup is really slow and it pauses on the part where it loads nautilus and stuff for about 20 seconds

also, after bootup now, everything opens slowly:
firefox, evolution, open office... even the terminal takes a shade over 10 seconds to load.
typing in commands in terminal is quick tho, and once the app is open, it is responsive and performs normally.
if i close the app and then reopen it, it is slow once more to open.

i did a sudo apt-get update and then a sudo apt-get upgrade and it upgraded everything as well as the kernel to the latest generic version and then rebooted.

no problems rebooting, but it is still really slow whereby it is almost unusable...
none of the fancy graphics are on

machine specs:
2GHZ Pentium M
1.5GB RAM
ati radeon x300
80GB HDD



what should i do?

---

### Post by mbradlcu on 2007-05-29
from what you say it seem the issue is mostly limited to data coming off the hard drive. what does 'hdparm' display? I'm guessing your drive settings here:
```
sudo /dev/hda5
```
hda5 is most likely wrong so substitute it with your root mount device.. btw here's my output:
> 
root@matt-x64:~# hdparm /dev/hdc
/dev/hdc:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 19929/255/63, sectors = 320173056, start = 0



---

### Post by dachinster on 2007-05-29
thanks for the reply
i do not know what hdparm does
im guessing it displays hard drive stats?

i did a sudo fdisk -l | less
because i was not sure where my linux partition was since this is a dual boot system

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7672    61625308+   7  HPFS/NTFS
/dev/sda2            9202        9729     4233600   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            7673        7927     2048287+   5  Extended
/dev/sda4            7928        9201    10233405   83  Linux
/dev/sda5            7673        7927     2048256   82  Linux swap / Solaris

Partition table entries are not in disk orderhere are the results of hdparm
> dachinster@Ubuntu:~$ sudo hdparm /dev/sda1
/dev/sda1:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 9729/255/63, sectors = 123250617, start = 63

dachinster@Ubuntu:~$ sudo hdparm /dev/sda2
/dev/sda2:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 9729/255/63, sectors = 8467200, start = 147828240

dachinster@Ubuntu:~$ sudo hdparm /dev/sda3
/dev/sda3:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 9729/255/63, sectors = 2, start = 123250680

dachinster@Ubuntu:~$ sudo hdparm /dev/sda4
/dev/sda4:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 9729/255/63, sectors = 20466810, start = 127347255

dachinster@Ubuntu:~$ sudo hdparm /dev/sda5
/dev/sda5:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 9729/255/63, sectors = 4096512, start = 123250743
dachinster@Ubuntu:~$ i searched around on the forums and saw people using these commands so i gathered the information for you one time:
> dachinster@Ubuntu:~$ sudo lspci |grep IDE
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)

dachinster@Ubuntu:~$ sudo hdparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   1836 MB in  2.00 seconds = 918.13 MB/sec
 Timing buffered disk reads:  106 MB in  3.05 seconds =  34.70 MB/sec

dachinster@Ubuntu:~$ sudo hdparm -i /dev/sda
/dev/sda:

 Model=HTS541080G9AT00                         , FwRev=MB4IA60A, SerialNo=      MPB4PAXKG12W3M
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=7539kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma3 udma4 *udma5 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 3a:  ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode

dachinster@Ubuntu:~$ 

---

### Post by dachinster on 2007-05-29
anyone can help me with this?
ubuntu is really slow!
i think there is definitely something wrong, because even the live cd which i tried before installing is moving faster than this

---

### Post by dachinster on 2007-05-30
anything as yet guys?

---

### Post by dachinster on 2007-05-30
ok
i figured it out... well sort of

in the beginning, i used system rescue cd to repartition my windows partition and make the ext3 and swap file (see 1st post) by using gparted since i didnt trust the options presented to me by the ubuntu installer for repartitioning an existing windows partition

since this is a fresh install and due to it being unusable, i simply popped in the ubuntu dvd and formatted the partitions i created with gparted redoing the partitions using the ubuntu partitioner since my windows partition was already safe

voila!
speed!

---

