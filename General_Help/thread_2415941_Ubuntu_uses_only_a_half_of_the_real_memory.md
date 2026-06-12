---
title: "Ubuntu uses only a half of the real memory"
date: 2019-04-03
forum: General Help
---

### Post by valentin6302 on 2019-04-03
lshw -C memory shows 16Gb 
```
root@vak:~# lshw -C memory
  *-firmware              
       description: BIOS
       vendor: American Megatrends Inc.
       physical id: 0
       version: F2
       date: 12/25/2018
       size: 64KiB
       capacity: 15MiB
        capabilities: pci upgrade shadowing cdboot bootselect socketedrom  edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen  int14serial int17printer acpi usb biosbootspecification uefi
  *-memory
       description: System Memory
       physical id: 25
       [COLOR=red][B]slot: System board or motherboard
       size: 16GiB[/B][/COLOR]
     *-bank:0
           description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL  NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08  14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi  Chandler <Unknown>Language-Team: English (United Kingdom)  <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain;  charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date:  2016-06-27 17:08+0000X-Generator: Launchpad (build  18115)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME  <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08  14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi  Chandler <Unknown>Language-Team: English (United Kingdom)  <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain;  charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date:  2016-06-27 17:08+0000X-Generator: Launchpad (build 18115) [empty]
          product: Unknown
          vendor: Unknown
          physical id: 0
          serial: Unknown
          slot: DIMM 0
     *-bank:1
          description: DIMM Synchronous 2133 MHz (0,5 ns)
          product: 2800 C16 Series
          vendor: Unknown
          physical id: 1
          serial: 00000000
          slot: DIMM 1
          size: 8GiB
          width: 64 bits
          clock: 2133MHz (0.5ns)
     *-bank:2
           description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL  NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08  14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi  Chandler <Unknown>Language-Team: English (United Kingdom)  <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain;  charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date:  2016-06-27 17:08+0000X-Generator: Launchpad (build  18115)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME  <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08  14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi  Chandler <Unknown>Language-Team: English (United Kingdom)  <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain;  charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date:  2016-06-27 17:08+0000X-Generator: Launchpad (build 18115) [empty]
          product: Unknown
          vendor: Unknown
          physical id: 2
          serial: Unknown
          slot: DIMM 0
     *-bank:3
          description: DIMM Synchronous 2133 MHz (0,5 ns)
          product: 2800 C16 Series
          vendor: Unknown
          physical id: 3
          serial: 00000000
          slot: DIMM 1
          size: 8GiB
          width: 64 bits
          clock: 2133MHz (0.5ns)
  *-cache:0
       description: L1 cache
       physical id: 27
       slot: L1 - Cache
       size: 576KiB
       capacity: 576KiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
       configuration: level=1
  *-cache:1
       description: L2 cache
       physical id: 28
       slot: L2 - Cache
       size: 3MiB
       capacity: 3MiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
       configuration: level=2
  *-cache:2
       description: L3 cache
       physical id: 29
       slot: L3 - Cache
       size: 16MiB
       capacity: 16MiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
       configuration: level=3


```
and from cat /proc/meminfo I see only 8 Gb in use
```
[COLOR=red]**MemTotal:        8181628 kB**[/COLOR]
MemFree:         1133308 kB
MemAvailable:    6520380 kB
Buffers:           85956 kB
Cached:          5448992 kB
SwapCached:       108052 kB
Active:          1493376 kB
Inactive:        5094840 kB
Active(anon):     670080 kB
Inactive(anon):   475040 kB
Active(file):     823296 kB
Inactive(file):  4619800 kB
Unevictable:          16 kB
Mlocked:              16 kB
SwapTotal:       7999484 kB
SwapFree:        7731452 kB
Dirty:                44 kB
Writeback:             0 kB
AnonPages:       1009704 kB
Mapped:           348572 kB
Shmem:             91844 kB
Slab:             314948 kB
SReclaimable:     247828 kB
SUnreclaim:        67120 kB
KernelStack:       13904 kB
PageTables:        32984 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    12090296 kB
Committed_AS:    4414860 kB
VmallocTotal:   34359738367 kB
VmallocUsed:           0 kB
VmallocChunk:          0 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
ShmemHugePages:        0 kB
ShmemPmdMapped:        0 kB
CmaTotal:              0 kB
CmaFree:               0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      309832 kB
DirectMap2M:     8028160 kB
DirectMap1G:     1048576 kB


```

Who has stolen 8Gb of the memory?

P.S. Hardware Ryzen-5 1600, GA-A320M-H,2x8Gb Patriot2800
       System: Lubuntu 16.04.06

---

### Post by deadflowr on 2019-04-03
[s]duplicate thread
closed[/s]

re-opened

---

