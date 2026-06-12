---
title: "desktop keeps turning DMA off"
date: 2007-11-28
forum: General Help
---

### Post by johnnyrevell on 2007-11-28
Running Gutsy desktop as headless server

Am having real problems keeping DMA turned on for my hard drives. Computer boots OK, but then after a seemingly random amount of time, the error messages below crop up and the computer turns DMA off on the drives. Since I use this computer a mythtv backend, disk IO is VERY important!

Set up is: 2 x hard drives on each IDE channel (total of 4) on an ASUS A7V8X-MX

The problem:
/var/log/messages:
Nov 27 01:05:21 fileserver kernel: [43570.236000] hdd: dma_timer_expiry: dma status == 0x61
Nov 27 01:05:31 fileserver kernel: [43580.236000] hdd: DMA timeout error
Nov 27 01:05:31 fileserver kernel: [43580.236000] hdd: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
Nov 27 01:05:31 fileserver kernel: [43580.236000] ide: failed opcode was: unknown
Nov 27 01:05:31 fileserver kernel: [43580.236000] hdc: DMA disabled
Nov 27 01:05:31 fileserver kernel: [43580.236000] hdd: DMA disabled
Nov 27 01:05:31 fileserver kernel: [43580.428000] ide1: reset: success
Nov 27 01:05:54 fileserver kernel: [43603.404000] hdd: dma_timer_expiry: dma status == 0x41
Nov 27 01:06:04 fileserver kernel: [43613.404000] hdd: DMA timeout error
Nov 27 01:06:04 fileserver kernel: [43613.404000] hdd: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
Nov 27 01:06:04 fileserver kernel: [43613.404000] ide: failed opcode was: unknown
Nov 27 01:06:04 fileserver kernel: [43613.404000] hdd: DMA disabled
Nov 27 01:06:04 fileserver kernel: [43613.596000] ide1: reset: success
Nov 27 01:06:25 fileserver kernel: [43633.932000] hdd: dma_timer_expiry: dma status == 0x41
Nov 27 01:06:35 fileserver kernel: [43643.932000] hdd: DMA timeout error
Nov 27 01:06:35 fileserver kernel: [43643.932000] hdd: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
Nov 27 01:06:35 fileserver kernel: [43643.932000] ide: failed opcode was: unknown
Nov 27 01:06:35 fileserver kernel: [43643.932000] hdd: DMA disabled
Nov 27 01:06:35 fileserver kernel: [43644.124000] ide1: reset: success
Nov 27 01:07:04 fileserver kernel: [43673.212000] hdd: dma_timer_expiry: dma status == 0x41
Nov 27 01:07:14 fileserver kernel: [43683.212000] hdd: DMA timeout error
Nov 27 01:07:14 fileserver kernel: [43683.212000] hdd: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
Nov 27 01:07:14 fileserver kernel: [43683.212000] ide: failed opcode was: unknown
Nov 27 01:07:14 fileserver kernel: [43683.212000] hdd: DMA disabled
Nov 27 01:07:14 fileserver kernel: [43683.404000] ide1: reset: success
Nov 27 01:19:38 fileserver -- MARK --
Nov 27 01:39:39 fileserver -- MARK --
Nov 27 01:59:39 fileserver -- MARK --

...


Nov 28 08:35:43 fileserver -- MARK --
Nov 28 08:55:43 fileserver -- MARK --
Nov 28 09:15:43 fileserver -- MARK --
Nov 28 09:35:43 fileserver -- MARK --
Nov 28 09:55:43 fileserver -- MARK --
Nov 28 10:15:43 fileserver -- MARK --
Nov 28 10:35:43 fileserver -- MARK --
Nov 28 10:51:08 fileserver kernel: [ 9355.373310] hda: status timeout: status=0x80 { Busy }
Nov 28 10:51:12 fileserver kernel: [ 9355.373318] ide: failed opcode was: unknown
Nov 28 10:51:12 fileserver kernel: [ 9355.373324] hda: DMA disabled
Nov 28 10:51:12 fileserver kernel: [ 9355.373328] hdb: DMA disabled
Nov 28 10:51:12 fileserver kernel: [ 9358.346404] ide0: reset: success
Nov 28 11:00:50 fileserver kernel: [ 9936.853148] hdc: dma_timer_expiry: dma status == 0x61
Nov 28 11:01:00 fileserver kernel: [ 9946.843726] hdc: DMA timeout error
Nov 28 11:01:00 fileserver kernel: [ 9946.843739] hdc: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
Nov 28 11:01:00 fileserver kernel: [ 9946.843744] ide: failed opcode was: unknown
Nov 28 11:01:00 fileserver kernel: [ 9946.843838] hdc: DMA disabled
Nov 28 11:01:00 fileserver kernel: [ 9946.843842] hdd: DMA disabled
Nov 28 11:01:00 fileserver kernel: [ 9947.179118] ide1: reset: success
Nov 28 11:01:20 fileserver kernel: [ 9967.179739] hdc: dma_timer_expiry: dma status == 0x21
Nov 28 11:01:30 fileserver kernel: [ 9977.169753] hdc: DMA timeout error
Nov 28 11:01:30 fileserver kernel: [ 9977.169767] hdc: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
Nov 28 11:01:30 fileserver kernel: [ 9977.169771] ide: failed opcode was: unknown
Nov 28 11:01:30 fileserver kernel: [ 9977.169860] hdc: DMA disabled
Nov 28 11:01:30 fileserver kernel: [ 9977.505428] ide1: reset: success
Nov 28 11:07:03 fileserver kernel: [10309.836704] hdc: dma_timer_expiry: dma status == 0x21
Nov 28 11:07:13 fileserver kernel: [10319.827168] hdc: DMA timeout error
Nov 28 11:07:13 fileserver kernel: [10319.827182] hdc: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
Nov 28 11:07:13 fileserver kernel: [10319.827187] ide: failed opcode was: unknown
Nov 28 11:07:13 fileserver kernel: [10319.827280] hdc: DMA disabled
Nov 28 11:07:13 fileserver kernel: [10320.162613] ide1: reset: success
Nov 28 11:07:33 fileserver kernel: [10340.171070] hdc: dma_timer_expiry: dma status == 0x21
Nov 28 11:07:43 fileserver kernel: [10350.161378] hdc: DMA timeout error
Nov 28 11:07:43 fileserver kernel: [10350.161391] hdc: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
Nov 28 11:07:43 fileserver kernel: [10350.161396] ide: failed opcode was: unknown
Nov 28 11:07:43 fileserver kernel: [10350.161490] hdc: DMA disabled
Nov 28 11:07:44 fileserver kernel: [10350.496987] ide1: reset: success
Nov 28 11:35:45 fileserver -- MARK --
Nov 28 11:55:45 fileserver -- MARK --
Nov 28 12:15:48 fileserver -- MARK --
Nov 28 12:35:48 fileserver -- MARK --
Nov 28 12:55:48 fileserver -- MARK --
Nov 28 13:15:49 fileserver -- MARK --
Nov 28 13:35:49 fileserver -- MARK --
Nov 28 13:55:49 fileserver -- MARK --
Nov 28 14:15:49 fileserver -- MARK --
Nov 28 14:35:49 fileserver -- MARK --
Nov 28 14:55:49 fileserver -- MARK --

output hdparm /dev/hdc after boot
/dev/hdc:
 multcount     =  0 (off)
 IO_support    =  1 (32-bit)
 unmaskirq     =  1 (on)
 using_dma     =  1 (on)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 24321/255/63, sectors = 390721968, start = 0

with -i
/dev/hdc:

 Model=ST3200826A, FwRev=3.03, SerialNo=4ND06EPT
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

with -tT
/dev/hdc:
 Timing cached reads:   456 MB in  2.01 seconds = 227.43 MB/sec
 Timing buffered disk reads:  178 MB in  3.00 seconds =  59.28 MB/sec



output hdparm /dev/hdc AFTER dma disabled
/dev/hdc:
 multcount     =  0 (off)
 IO_support    =  1 (32-bit)
 unmaskirq     =  1 (on)
 using_dma     =  0 (off)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 24321/255/63, sectors = 390721968, start = 0

with -i flag
/dev/hdc:

 Model=ST3200826A, FwRev=3.03, SerialNo=4ND06EPT
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

with -tT
/dev/hdc:
 Timing cached reads:   494 MB in  2.00 seconds = 246.69 MB/sec
 Timing buffered disk reads:   16 MB in  3.27 seconds =   4.89 MB/sec


however, if I run sudo hdparm -d1 /dev/hdc:
/dev/hdc:
 setting using_dma to 1 (on)
 using_dma     =  1 (on)

DMA is turned back on and then disk throughput is
/dev/hdc:
 Timing cached reads:   402 MB in  2.00 seconds = 200.64 MB/sec
 Timing buffered disk reads:  170 MB in  3.03 seconds =  56.17 MB/sec


I have tried reducing the udma to udma2 and set acpi=off in the menu.lst. Makes no difference

Other info of use
john@fileserver:~$ lspci | grep IDE
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)

Disk info:
/dev/hda
=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda ATA IV family
Device Model:     ST380021A
Serial Number:    3HV0H8QX
Firmware Version: 3.10
User Capacity:    80,026,361,856 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   5
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Nov 28 14:56:16 2007 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Disabled

/dev/hdc hdc and hdd
=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.8 family
Device Model:     ST3200826A
Serial Number:    4ND06EPT
Firmware Version: 3.03
User Capacity:    200,049,647,616 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Nov 28 14:57:03 2007 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Disabled


Someone please help as I am completely stuck!

Regards

John

---

### Post by johnnyrevell on 2007-12-04
I think this may be due to the southbridge Via chipset the motherboard has (VIA VT8235)
I've tried setting pci=noapic in menu.lst, taking the top off the computer and aiming a fan at the hard drives (hddtemp reports temps of 40deg C or so) and set the drives to master/slave rather than cable select; all to no avail.
I've compiled the via driver into a stripped down kernel and also loaded it as a module into the stock gutsy installation; again no joy

The only thing that's solved the problem is to disconnect hdd. The problem seemed especially bad during heavy read/write sessions on that channel so I wonder if there is a problem with the chipset driver coordinating i/o to the disks

Will experiment with putting the now disconnected disk in an external box and hooking up via USB

John

---

### Post by zazuge on 2008-02-01
Hello sorry for the late reply but I think a have the same problem
[  147.340373] hdb: dma_intr: status=0x7f { DriveReady DeviceFault SeekComplete DataRequest CorrectedError Index Error }
[  147.340399] hdb: dma_intr: error=0x7f { DriveStatusError UncorrectableError SectorIdNotFound TrackZeroNotFound AddrMarkNotFound }, LBAsect=260013951, sector=40966241
[  147.340417] ide: failed opcode was: unknown
[  147.340537] hda: DMA disabled
[  147.340543] hdb: DMA disabled
[  151.126735] ide0: reset: success
[  153.187407] hdb: status error: status=0x7f { DriveReady DeviceFault SeekComplete DataRequest CorrectedError Index Error }
[  153.187431] hdb: status error: error=0x7f { DriveStatusError UncorrectableError SectorIdNotFound TrackZeroNotFound AddrMarkNotFound }, LBAsect=260013951, sector=2927
[  153.187447] ide: failed opcode was: unknown
[  153.187563] hdb: drive not ready for command
[  156.975445] ide0: reset: success

It happens at random sometimes even on boot time
generaly my PC goes crazzy one time to 4 time in a period of 1 to 2 days in a month :-)
And upluging the powercable for hours seems help it to calme.
a the beginning I supspected the hard drive but it even happens to the my DVDrom 
then I suspeded my IDE-cable so I changed it ,no good.
I supected my RAM (because bad  RAMs can cause file system corruption and OS crash)
I tested It and changed it ,nothing.
In the end a friend told me that it's the IDE-controller in the mothercard ,especialy because it's a VIA matsonic mothercard ,And it's known to have to cause alot of problems.
so ther's just one solution buy a new one, but I don't have the money to, maybe you can do it, And get rid of the problem altogother.

so good luck with your problem, hope you can solve it.

---

