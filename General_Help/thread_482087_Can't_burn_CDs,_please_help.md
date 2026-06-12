---
title: "Can't burn CDs, please help"
date: 2007-06-23
forum: General Help
---

### Post by sunshine12 on 2007-06-23
I have tried to burn .iso images, but in vain..

first I have tried brasero, but it stopped after writing about 200MB(cd image is 600MB)

then I have tried k3b, used other cd image to burn cd, but the same problem, stops at 200MB...
k3b error log is as follows:

System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-15-generic
Devices
-----------------------
HL-DT-ST RW/DVD GCC-4521B 1.05 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

Used versions
-----------------------
cdrecord: 1.1.2

cdrecord
-----------------------
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'RW/DVD GCC-4521B'
Revision       : '1.05'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009 (CD-R)
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) (current)
Profile: 0x0010 (DVD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1328096 = 1296 KB
FIFO size      : 12582912 = 12288 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Speed set to 2818 KB/s
Track 01: data   579 MB        
Total size:      665 MB (65:53.45) = 296509 sectors
Lout start:      665 MB (65:55/34) = 296509 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11607 (97:27/18)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 18
Manufacturer: Plasmon Data systems Ltd.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 63340
Starting to write CD/DVD at speed  16.0 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  579 MB written.
Track 01:    1 of  579 MB written (fifo 100%) [buf 100%]   0.7x.
Track 01:    2 of  579 MB written (fifo  96%) [buf 100%]  16.5x.
Track 01:    3 of  579 MB written (fifo  94%) [buf 100%]  17.0x.
Track 01:    4 of  579 MB written (fifo  90%) [buf 100%]  16.5x.
Track 01:    5 of  579 MB written (fifo  92%) [buf  98%]  16.7x.
Track 01:    6 of  579 MB written (fifo  90%) [buf 100%]  16.7x.
Track 01:    7 of  579 MB written (fifo  87%) [buf 100%]  16.9x.
Track 01:    8 of  579 MB written (fifo  84%) [buf 100%]  16.4x.
Track 01:    9 of  579 MB written (fifo  84%) [buf 100%]  16.9x.
Track 01:   10 of  579 MB written (fifo  83%) [buf 100%]  16.4x.
Track 01:   11 of  579 MB written (fifo  83%) [buf 100%]  16.9x.
Track 01:   12 of  579 MB written (fifo  81%) [buf 100%]  16.3x.
Track 01:   13 of  579 MB written (fifo  80%) [buf 100%]  16.8x.
Track 01:   14 of  579 MB written (fifo  79%) [buf  99%]  16.2x.
Track 01:   15 of  579 MB written (fifo  79%) [buf  99%]  16.8x.
Track 01:   16 of  579 MB written (fifo  77%) [buf 100%]  16.3x.
Track 01:   17 of  579 MB written (fifo  78%) [buf 100%]  16.8x.
Track 01:   18 of  579 MB written (fifo  79%) [buf 100%]  16.2x.
Track 01:   19 of  579 MB written (fifo  76%) [buf  99%]  16.7x.
Track 01:   20 of  579 MB written (fifo  81%) [buf  99%]  16.3x.
Track 01:   21 of  579 MB written (fifo  84%) [buf 100%]  16.8x.
Track 01:   22 of  579 MB written (fifo  85%) [buf 100%]  16.2x.
Track 01:   23 of  579 MB written (fifo  84%) [buf 100%]  16.7x.
Track 01:   24 of  579 MB written (fifo  89%) [buf 100%]  16.1x.
Track 01:   25 of  579 MB written (fifo  99%) [buf 100%]  16.7x.
Track 01:   26 of  579 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:   27 of  579 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:   28 of  579 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:   29 of  579 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:   30 of  579 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:   31 of  579 MB written (fifo 100%) [buf  98%]  16.3x.
Track 01:   32 of  579 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:   33 of  579 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:   34 of  579 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:   35 of  579 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:   36 of  579 MB written (fifo  99%) [buf 100%]  17.0x.
Track 01:   37 of  579 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:   38 of  579 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:   39 of  579 MB written (fifo  99%) [buf 100%]  16.4x.
Track 01:   40 of  579 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:   41 of  579 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:   42 of  579 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:   43 of  579 MB written (fifo  98%) [buf 100%]  16.3x.
Track 01:   44 of  579 MB written (fifo  99%) [buf 100%]  16.8x.
Track 01:   45 of  579 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:   46 of  579 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:   47 of  579 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:   48 of  579 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:   49 of  579 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:   50 of  579 MB written (fifo 100%) [buf  99%]  16.7x.
Track 01:   51 of  579 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:   52 of  579 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:   53 of  579 MB written (fifo  99%) [buf 100%]  16.2x.
Track 01:   54 of  579 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:   55 of  579 MB written (fifo 100%) [buf  99%]  16.1x.
Track 01:   56 of  579 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:   57 of  579 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:   58 of  579 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:   59 of  579 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:   60 of  579 MB written (fifo 100%) [buf  99%]  16.5x.
Track 01:   61 of  579 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:   62 of  579 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:   63 of  579 MB written (fifo 100%) [buf 100%]  16.0x.
Track 01:   64 of  579 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:   65 of  579 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:   66 of  579 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:   67 of  579 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:   68 of  579 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:   69 of  579 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:   70 of  579 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:   71 of  579 MB written (fifo  99%) [buf 100%]  16.9x.
Track 01:   72 of  579 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:   73 of  579 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:   74 of  579 MB written (fifo 100%) [buf  99%]  16.2x.
Track 01:   75 of  579 MB written (fifo 100%) [buf  99%]  16.9x.
Track 01:   76 of  579 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:   77 of  579 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:   78 of  579 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:   79 of  579 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:   80 of  579 MB written (fifo 100%) [buf  99%]  16.1x.
Track 01:   81 of  579 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:   82 of  579 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:   83 of  579 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:   84 of  579 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:   85 of  579 MB written (fifo 100%) [buf  98%]  16.4x.
Track 01:   86 of  579 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:   87 of  579 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:   88 of  579 MB written (fifo 100%) [buf  99%]  16.1x.
Track 01:   89 of  579 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:   90 of  579 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:   91 of  579 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:   92 of  579 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:   93 of  579 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:   94 of  579 MB written (fifo 100%) [buf 100%]  16.0x.
Track 01:   95 of  579 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:   96 of  579 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:   97 of  579 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:   98 of  579 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:   99 of  579 MB written (fifo 100%) [buf  99%]  16.4x.
Track 01:  100 of  579 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:  101 of  579 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  102 of  579 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  103 of  579 MB written (fifo 100%) [buf  99%]  16.2x.
Track 01:  104 of  579 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:  105 of  579 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  106 of  579 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  107 of  579 MB written (fifo 100%) [buf  99%]  16.2x.
Track 01:  108 of  579 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  109 of  579 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  110 of  579 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  111 of  579 MB written (fifo 100%) [buf  99%]  16.2x.
Track 01:  112 of  579 MB written (fifo 100%) [buf  99%]  16.7x.
Track 01:  113 of  579 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  114 of  579 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  115 of  579 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  116 of  579 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  117 of  579 MB written (fifo 100%) [buf  99%]  16.1x.
Track 01:  118 of  579 MB written (fifo 100%) [buf  99%]  16.7x.
Track 01:  119 of  579 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  120 of  579 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:  121 of  579 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  122 of  579 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:  123 of  579 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  124 of  579 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:  125 of  579 MB written (fifo 100%) [buf  99%]  15.9x.
Track 01:  126 of  579 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:  127 of  579 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:  128 of  579 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:  129 of  579 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:  130 of  579 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  131 of  579 MB written (fifo 100%) [buf  99%]  16.9x.
Track 01:  132 of  579 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:  133 of  579 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  134 of  579 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  135 of  579 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  136 of  579 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  137 of  579 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  138 of  579 MB written (fifo 100%) [buf  98%]  16.1x.
Track 01:  139 of  579 MB written (fifo 100%) [buf  99%]  17.0x.
Track 01:  140 of  579 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  141 of  579 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  142 of  579 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  143 of  579 MB written (fifo 100%) [buf  97%]  16.4x.
Track 01:  144 of  579 MB written (fifo  99%) [buf 100%]  16.6x.
Track 01:  145 of  579 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  146 of  579 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  147 of  579 MB written (fifo  99%) [buf 100%]  16.7x.
Track 01:  148 of  579 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  149 of  579 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:  150 of  579 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  151 of  579 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:  152 of  579 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  153 of  579 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:  154 of  579 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  155 of  579 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:  156 of  579 MB written (fifo 100%) [buf 100%]  16.0x.
Track 01:  157 of  579 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:  158 of  579 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:  159 of  579 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:  160 of  579 MB written (fifo 100%) [buf  98%]  16.8x.
Track 01:  161 of  579 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:  162 of  579 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  163 of  579 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  164 of  579 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  165 of  579 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  166 of  579 MB written (fifo  99%) [buf 100%]  16.9x.
Track 01:  167 of  579 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  168 of  579 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  169 of  579 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  170 of  579 MB written (fifo 100%) [buf  99%]  16.8x.
Track 01:  171 of  579 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  172 of  579 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  173 of  579 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  174 of  579 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  175 of  579 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  176 of  579 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  177 of  579 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  178 of  579 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  179 of  579 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  180 of  579 MB written (fifo 100%) [buf  99%]  16.5x.
Track 01:  181 of  579 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  182 of  579 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:  183 of  579 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  184 of  579 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:  185 of  579 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  186 of  579 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:  187 of  579 MB written (fifo 100%) [buf 100%]  16.0x.
Track 01:  188 of  579 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:  189 of  579 MB written (fifo 100%) [buf  99%]  16.9x.
Track 01:  190 of  579 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:  191 of  579 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:  192 of  579 MB written (fifo  99%) [buf 100%]  16.4x.
Track 01:  193 of  579 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  194 of  579 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  195 of  579 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  196 of  579 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  197 of  579 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  198 of  579 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  199 of  579 MB written (fifo 100%) [buf 100%]  16.8x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 01 8E 09 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 25.677s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 208685056 bytes
Writing  time:  133.437s
Average write speed  31.5x.
Min drive buffer fill was 97%
Fixating...
Fixating time:    0.007s
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=16 -dao driveropts=burnfree -eject -data -tsize=296509s - 



Now please someone can tell me what is the problem with this.. I have already wasted 2 CDs, now will burn after sorting out what is the  problem..

---

### Post by sunshine12 on 2007-06-23
kept writing spped at 16x in both of the abouve attempts..

---

### Post by Maxtorm on 2007-06-23
Looks like a hardware problem.  Do you have any problems with burning smaller files?  Could be the drive is overheating after the sustained 200 MB?  Could be a physical problem in drive when the head gets to that 200MB point on its path?

---

### Post by sunshine12 on 2007-06-23
any hint what could be the problem?
any specific changes or settings I have to make?
anybody having this kind of problem..
please help to fix it.

---

### Post by sunshine12 on 2007-06-23
> **Maxtorm said:**
> Looks like a hardware problem.  Do you have any problems with burning smaller files?  Could be the drive is overheating after the sustained 200 MB?  Could be a physical problem in drive when the head gets to that 200MB point on its path?

not tried smaller files but will check and tell you. 

any tool to check before actual burning to cd? 
thanks for reply

---

### Post by Maxtorm on 2007-06-23
> **sunshine12 said:**
> any tool to check before actual burning to cd?
In K3B, when you go to burn the disc, there is a checkbox for "**Simulate**", but I'm not sure it will be much assistance if the problem is hardware-related.  Can't hurt to try it though. 
Another thing you might want to try is to burn a 175 MB onto a disc and leave the session open.  Then try to burn 100 MB.  If the second burn fails at 25 MB (i.e. 175 MB original burn + 25 MB second burn = 200 MB overall), it would certainly seem to prove the problem is with that particular physical location of the head.

---

### Post by sunshine12 on 2007-06-23
> **Maxtorm said:**
> In K3B, when you go to burn the disc, there is a checkbox for "**Simulate**", but I'm not sure it will be much assistance if the problem is hardware-related.  Can't hurt to try it though. 
Another thing you might want to try is to burn a 175 MB onto a disc and leave the session open.  Then try to burn 100 MB.  If the second burn fails at 25 MB (i.e. 175 MB original burn + 25 MB second burn = 200 MB overall), it would certainly seem to prove the problem is with that particular physical location of the head.

Thanks Maxtorm, I will try and tell the results. thanks for the quick reply.

---

### Post by sunshine12 on 2007-06-23
Simulation test is ok, and I can write multisession: fist session 175MB and second session 100MB

now what would be the problem then.. 
please suggest
thanks

---

### Post by nutz on 2007-06-23
Check with the manufacturer of your drive for a firmware update and if that doesn't work try a different brand of media. It says above the average write speed was 31x but the log shows 16x so perhaps it is the firmware not recognizing the media properly... Firmware updates for optical drives are common now days since they are getting more complex.

Your log says you have 1.05 loaded on there now and the newest for your drive is 1.07...

Tell me how it goes...:D
[http://club.cdfreaks.com/showthread.php?t=135925](http://club.cdfreaks.com/showthread.php?t=135925)

---

### Post by sunshine12 on 2007-06-23
> **nutz said:**
> Check with the manufacturer of your drive for a firmware update and if that doesn't work try a different brand of media. It says above the average write speed was 31x but the log shows 16x so perhaps it is the firmware not recognizing the media properly... Firmware updates for optical drives are common now days since they are getting more complex.

Your log says you have 1.05 loaded on there now and the newest for your drive is 1.07...

Tell me how it goes...:D
[http://club.cdfreaks.com/showthread.php?t=135925](http://club.cdfreaks.com/showthread.php?t=135925)

Thanks for reply, I also somewhat aware of it but the problem is they provide firmware/device driver for windows and osx..... don't how to do it with Ubuntu. 
Thanks

---

### Post by nutz on 2007-06-23
```
sudo apt-get install wine
```

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by nutz on 2007-06-23
Here is the actual Version History:
101 - Fixes bug. Some Blank CD-R disc are not regonized after removing a pressed CD.
103 - Enhanced recording quality of CD-R Media.
104 - Enhanced recording quality of CD-R Media and readability 32X CD-RW media.
105 - Enhanced CD-RW Compatibility.
106 - Enhanced CD-RW & Video CD Compatibility.
107 - Enhanced CD-RW & Video CD Compatibility.

---

### Post by sunshine12 on 2007-06-23
Thank you all.
Will upgrade my firmware and let you know.
If there is any setting to be make in k3b then please let me know.
I am new to k3b, was using Nero in windows.
Thanks..

---

### Post by nutz on 2007-06-23
[http://www.nero.com/eng/NeroLINUX.html](http://www.nero.com/eng/NeroLINUX.html)

---

### Post by sunshine12 on 2007-06-24
> **nutz said:**
> [http://www.nero.com/eng/NeroLINUX.html](http://www.nero.com/eng/NeroLINUX.html)

Thanks nutz,
downloaded nerolinux. Hope this will solve the problem.:)

---

### Post by sunshine12 on 2007-06-24
Forgot One thing that when I burned first cd with brasero, it burned the cd upto 200MB and then it says that "cd is  successfully burned" no error message(isn't it strange?)...

with k3b, after burned failed at 200MB it returned with error message(obviously), the actual error message was:
"cd record returned an unknown error code:254, Sometime TAO writing mode resolve this issue"

what is the TAO mode, and that make what difference??
using k3b under ubuntu Gnome is ok??

Thanks

---

### Post by sunshine12 on 2007-06-24
Same error continues.. error code 254

Tried simulation but now it stops at 197MB..

Error log from k3b is:



System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
HL-DT-ST RW/DVD GCC-4521B 1.05 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

Used versions
-----------------------
cdrecord: 1.1.2

cdrecord
-----------------------
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'RW/DVD GCC-4521B'
Revision       : '1.05'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009 (CD-R)
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) (current)
Profile: 0x0010 (DVD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1328096 = 1296 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 2818 KB/s
Track 01: data   379 MB        
Total size:      436 MB (43:13.30) = 194498 sectors
Lout start:      436 MB (43:15/23) = 194498 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11607 (97:27/18)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 18
Manufacturer: Plasmon Data systems Ltd.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 165351
Starting to write CD/DVD at speed  16.0 in dummy TAO mode for single session.
Last chance to quit, starting dummy write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Starting new track at sector: 0
Track 01:    0 of  379 MB written.
Track 01:    1 of  379 MB written (fifo  98%) [buf  97%]   1.8x.
Track 01:    2 of  379 MB written (fifo 100%) [buf  99%]  13.2x.
Track 01:    3 of  379 MB written (fifo 100%) [buf  99%]  17.0x.
Track 01:    4 of  379 MB written (fifo  99%) [buf 100%]  16.5x.
Track 01:    5 of  379 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:    6 of  379 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:    7 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:    8 of  379 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:    9 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:   10 of  379 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:   11 of  379 MB written (fifo  99%) [buf 100%]  16.9x.
Track 01:   12 of  379 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:   13 of  379 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:   14 of  379 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:   15 of  379 MB written (fifo 100%) [buf  98%]  16.6x.
Track 01:   16 of  379 MB written (fifo  99%) [buf 100%]  16.5x.
Track 01:   17 of  379 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:   18 of  379 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:   19 of  379 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:   20 of  379 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:   21 of  379 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:   22 of  379 MB written (fifo 100%) [buf  99%]  16.1x.
Track 01:   23 of  379 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:   24 of  379 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:   25 of  379 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:   26 of  379 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:   27 of  379 MB written (fifo 100%) [buf  99%]  16.6x.
Track 01:   28 of  379 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:   29 of  379 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:   30 of  379 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:   31 of  379 MB written (fifo 100%) [buf  99%]  16.4x.
Track 01:   32 of  379 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:   33 of  379 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:   34 of  379 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:   35 of  379 MB written (fifo 100%) [buf  99%]  16.3x.
Track 01:   36 of  379 MB written (fifo 100%) [buf 100%]  17.1x.
Track 01:   37 of  379 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:   38 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:   39 of  379 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:   40 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:   41 of  379 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:   42 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:   43 of  379 MB written (fifo  99%) [buf 100%]  16.3x.
Track 01:   44 of  379 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:   45 of  379 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:   46 of  379 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:   47 of  379 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:   48 of  379 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:   49 of  379 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:   50 of  379 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:   51 of  379 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:   52 of  379 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:   53 of  379 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:   54 of  379 MB written (fifo 100%) [buf  99%]  16.6x.
Track 01:   55 of  379 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:   56 of  379 MB written (fifo 100%) [buf  99%]  16.6x.
Track 01:   57 of  379 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:   58 of  379 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:   59 of  379 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:   60 of  379 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:   61 of  379 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:   62 of  379 MB written (fifo  99%) [buf 100%]  16.5x.
Track 01:   63 of  379 MB written (fifo 100%) [buf 100%]  16.0x.
Track 01:   64 of  379 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:   65 of  379 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:   66 of  379 MB written (fifo 100%) [buf  98%]  16.4x.
Track 01:   67 of  379 MB written (fifo 100%) [buf  99%]  16.9x.
Track 01:   68 of  379 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:   69 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:   70 of  379 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:   71 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:   72 of  379 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:   73 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:   74 of  379 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:   75 of  379 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:   76 of  379 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:   77 of  379 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:   78 of  379 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:   79 of  379 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:   80 of  379 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:   81 of  379 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:   82 of  379 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:   83 of  379 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:   84 of  379 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:   85 of  379 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:   86 of  379 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:   87 of  379 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:   88 of  379 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:   89 of  379 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:   90 of  379 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:   91 of  379 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:   92 of  379 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:   93 of  379 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:   94 of  379 MB written (fifo 100%) [buf 100%]  16.0x.
Track 01:   95 of  379 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:   96 of  379 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:   97 of  379 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:   98 of  379 MB written (fifo 100%) [buf  99%]  16.9x.
Track 01:   99 of  379 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  100 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  101 of  379 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  102 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  103 of  379 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  104 of  379 MB written (fifo 100%) [buf  99%]  16.7x.
Track 01:  105 of  379 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:  106 of  379 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  107 of  379 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  108 of  379 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  109 of  379 MB written (fifo 100%) [buf  99%]  16.2x.
Track 01:  110 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  111 of  379 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  112 of  379 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  113 of  379 MB written (fifo 100%) [buf  99%]  16.2x.
Track 01:  114 of  379 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  115 of  379 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  116 of  379 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  117 of  379 MB written (fifo 100%) [buf  99%]  16.0x.
Track 01:  118 of  379 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  119 of  379 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  120 of  379 MB written (fifo  99%) [buf 100%]  16.6x.
Track 01:  121 of  379 MB written (fifo 100%) [buf  99%]  16.1x.
Track 01:  122 of  379 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:  123 of  379 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  124 of  379 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:  125 of  379 MB written (fifo 100%) [buf 100%]  16.0x.
Track 01:  126 of  379 MB written (fifo  99%) [buf 100%]  16.5x.
Track 01:  127 of  379 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:  128 of  379 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:  129 of  379 MB written (fifo 100%) [buf  98%]  16.7x.
Track 01:  130 of  379 MB written (fifo  99%) [buf 100%]  16.7x.
Track 01:  131 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  132 of  379 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  133 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  134 of  379 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  135 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  136 of  379 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  137 of  379 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  138 of  379 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  139 of  379 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  140 of  379 MB written (fifo 100%) [buf  99%]  16.2x.
Track 01:  141 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  142 of  379 MB written (fifo  99%) [buf 100%]  16.2x.
Track 01:  143 of  379 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  144 of  379 MB written (fifo 100%) [buf  99%]  16.2x.
Track 01:  145 of  379 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  146 of  379 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  147 of  379 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  148 of  379 MB written (fifo 100%) [buf  99%]  16.1x.
Track 01:  149 of  379 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  150 of  379 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  151 of  379 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:  152 of  379 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  153 of  379 MB written (fifo 100%) [buf  98%]  16.4x.
Track 01:  154 of  379 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  155 of  379 MB written (fifo  99%) [buf 100%]  16.5x.
Track 01:  156 of  379 MB written (fifo 100%) [buf 100%]  16.0x.
Track 01:  157 of  379 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:  158 of  379 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:  159 of  379 MB written (fifo  99%) [buf 100%]  16.5x.
Track 01:  160 of  379 MB written (fifo 100%) [buf  99%]  16.9x.
Track 01:  161 of  379 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  162 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  163 of  379 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  164 of  379 MB written (fifo  99%) [buf 100%]  16.9x.
Track 01:  165 of  379 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  166 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  167 of  379 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  168 of  379 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  169 of  379 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  170 of  379 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  171 of  379 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  172 of  379 MB written (fifo 100%) [buf  99%]  16.8x.
Track 01:  173 of  379 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  174 of  379 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  175 of  379 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  176 of  379 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  177 of  379 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  178 of  379 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  179 of  379 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  180 of  379 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:  181 of  379 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  182 of  379 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:  183 of  379 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  184 of  379 MB written (fifo 100%) [buf 100%]  16.6x.
Track 01:  185 of  379 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  186 of  379 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:  187 of  379 MB written (fifo  99%) [buf 100%]  16.0x.
Track 01:  188 of  379 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:  189 of  379 MB written (fifo 100%) [buf  99%]  16.9x.
Track 01:  190 of  379 MB written (fifo 100%) [buf 100%]  16.5x.
Track 01:  191 of  379 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:  192 of  379 MB written (fifo 100%) [buf  99%]  16.3x.
Track 01:  193 of  379 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:  194 of  379 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  195 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  196 of  379 MB written (fifo 100%) [buf  99%]  16.4x.
Track 01:  197 of  379 MB written (fifo 100%) [buf 100%]  16.9x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 01 8A 48 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 71 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 1.976s timeout 40s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 206716928 bytes
Writing  time:  103.638s
Average write speed  25.0x.
Min drive buffer fill was 98%
Fixating...
WARNING: Some drives don't like fixation in dummy mode.
Fixating time:    0.006s
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=16 -tao -dummy driveropts=burnfree -eject -data -tsize=194496s - 



Is it the problem with COMBO DRIVE??

---

### Post by sunshine12 on 2007-06-24
Finally after some effort I found some sucess, but have to confirm it later..

I tried to simulate in Nerolinux 3.0, and it gives me only 2 speed options, 8x and 4x.. tried 8x speed and BINGO..

I think the problem is in the speed, I tried 16x speed on the other ocassions.. but thanks to Nerolinux

Then I tried it to K3b and let it choose the speed, and guess what it started with 8x speed and sucessfull in simulation...
here is log..

System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
HL-DT-ST RW/DVD GCC-4521B 1.05 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

Used versions
-----------------------
cdrecord: 1.1.2

cdrecord
-----------------------
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'RW/DVD GCC-4521B'
Revision       : '1.05'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009 (CD-R)
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) (current)
Profile: 0x0010 (DVD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1328096 = 1296 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 1410 KB/s
Track 01: data   379 MB        
Total size:      436 MB (43:13.28) = 194496 sectors
Lout start:      436 MB (43:15/21) = 194496 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11607 (97:27/18)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 18
Manufacturer: Plasmon Data systems Ltd.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 165353
Starting to write CD/DVD at speed   8.0 in dummy SAO mode for single session.
Last chance to quit, starting dummy write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  379 MB written.
Track 01:    1 of  379 MB written (fifo 100%) [buf 100%]   0.3x.
Track 01:    2 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:    3 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:    4 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:    5 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:    6 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:    7 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:    8 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:    9 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:   10 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   11 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   12 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   13 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   14 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   15 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   16 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:   17 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   18 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:   19 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   20 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:   21 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   22 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:   23 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:   24 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:   25 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:   26 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:   27 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:   28 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:   29 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:   30 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:   31 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:   32 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:   33 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   34 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:   35 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   36 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:   37 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   38 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:   39 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   40 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:   41 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   42 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   43 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   44 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   45 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   46 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   47 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:   48 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   49 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:   50 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   51 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:   52 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   53 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:   54 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:   55 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:   56 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:   57 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:   58 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:   59 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:   60 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:   61 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:   62 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:   63 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:   64 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   65 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:   66 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   67 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:   68 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   69 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:   70 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   71 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:   72 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   73 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   74 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   75 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   76 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   77 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   78 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:   79 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   80 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:   81 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   82 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:   83 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:   84 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:   85 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:   86 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:   87 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:   88 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:   89 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:   90 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:   91 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:   92 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:   93 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:   94 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:   95 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   96 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:   97 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   98 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:   99 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  100 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  101 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  102 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  103 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  104 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  105 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  106 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  107 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  108 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  109 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  110 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  111 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  112 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  113 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  114 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  115 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  116 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  117 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  118 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  119 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  120 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  121 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  122 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  123 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  124 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  125 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  126 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  127 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  128 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  129 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  130 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  131 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  132 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  133 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  134 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  135 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  136 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  137 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  138 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  139 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  140 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  141 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  142 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  143 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  144 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  145 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  146 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  147 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  148 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  149 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  150 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  151 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  152 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  153 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  154 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  155 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  156 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  157 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  158 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  159 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  160 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  161 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  162 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  163 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  164 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  165 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  166 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  167 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  168 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  169 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  170 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  171 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  172 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  173 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  174 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  175 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  176 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  177 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  178 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  179 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  180 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  181 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  182 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  183 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  184 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  185 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  186 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  187 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  188 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  189 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  190 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  191 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  192 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  193 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  194 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  195 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  196 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  197 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  198 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  199 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  200 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  201 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  202 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  203 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  204 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  205 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  206 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  207 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  208 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  209 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  210 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  211 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  212 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  213 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  214 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  215 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  216 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  217 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  218 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  219 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  220 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  221 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  222 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  223 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  224 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  225 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  226 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  227 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  228 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  229 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  230 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  231 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  232 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  233 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  234 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  235 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  236 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  237 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  238 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  239 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  240 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  241 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  242 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  243 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  244 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  245 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  246 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  247 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  248 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  249 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  250 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  251 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  252 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  253 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  254 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  255 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  256 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  257 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  258 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  259 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  260 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  261 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  262 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  263 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  264 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  265 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  266 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  267 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  268 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  269 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  270 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  271 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  272 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  273 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  274 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  275 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  276 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  277 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  278 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  279 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  280 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  281 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  282 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  283 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  284 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  285 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  286 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  287 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  288 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  289 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  290 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  291 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  292 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  293 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  294 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  295 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  296 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  297 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  298 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  299 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  300 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  301 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  302 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  303 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  304 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  305 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  306 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  307 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  308 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  309 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  310 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  311 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  312 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  313 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  314 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  315 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  316 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  317 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  318 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  319 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  320 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  321 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  322 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  323 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  324 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  325 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  326 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  327 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  328 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  329 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  330 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  331 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  332 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  333 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  334 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  335 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  336 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  337 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  338 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  339 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  340 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  341 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  342 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  343 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  344 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  345 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  346 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  347 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  348 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  349 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  350 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  351 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  352 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  353 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  354 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  355 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  356 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  357 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  358 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  359 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  360 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  361 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  362 of  379 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:  363 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  364 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  365 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  366 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  367 of  379 MB written (fifo 100%) [buf 100%]   8.1x.
Track 01:  368 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  369 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  370 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  371 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  372 of  379 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:  373 of  379 MB written (fifo 100%) [buf 100%]   8.0x.
Track 01:  374 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  375 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  376 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  377 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:  378 of  379 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:  379 of  379 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01: Total bytes read/written: 398327808/398327808 (194496 sectors).
Writing  time:  344.302s
Average write speed   7.5x.
Min drive buffer fill was 100%
Fixating...
WARNING: Some drives don't like fixation in dummy mode.
Fixating time:   12.233s
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=8 -dao -dummy driveropts=burnfree -eject -data -tsize=194496s - 




Now I will try burning on CD.. Tell you later about the outcome.. 
Some simple solution at the end.. 

Thanks to all...

---

### Post by sunshine12 on 2007-06-24
NO, Problem not solved... it remains but this time when I burned cd with 8x in K3b, it completes burning successfully but there is some problem when I ran that CD..

After watching the surface of  cd, I have seen some strange thing, that it is not burned in between two burned portions... it is like burned portion-unburned very small portion-burned portion...

Then second CD tried on Nerolinux, that completes burning but then stuck there for 20minutes and have to cancel the burning process and after looking at the surface of the Cd, I've noticed the same thing as above... Burned portion-unburned small ring- burned portion

I think there is some problem with my Combo drive, but what it ist? can somebody help me.. Can I fix it or have to buy another one?

---

### Post by nutz on 2007-06-24
Did you do the firmware update? Your log still say the firmware is 1.05...

HL-DT-ST RW/DVD GCC-4521B **1.05** (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

---

### Post by sunshine12 on 2007-06-25
> **nutz said:**
> Did you do the firmware update? Your log still say the firmware is 1.05...

HL-DT-ST RW/DVD GCC-4521B **1.05** (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

No, I didn't. Actually I am afraid of doing  that firmware update with wine. I don't have that much experience with that and never done before. I sent an e-mail to manufacturer asking for some support but never replied!!!
Please anybody who have done it before give me some information regarding that.

or it is just ..  

wine abcdefgh.exe

and then follow the instructions?

thanks

---

### Post by nutz on 2007-06-25
> **sunshine12 said:**
> No, I didn't. Actually I am afraid of doing  that firmware update with wine. I don't have that much experience with that and never done before. I sent an e-mail to manufacturer asking for some support but never replied!!!
Please anybody who have done it before give me some information regarding that.

or it is just ..  

wine abcdefgh.exe

and then follow the instructions?

thanks

Yes.

---

### Post by thechris on 2007-06-26
I have similar issue.  If I try DAO, it gets "write error" and tells me to use TAO.  If I use TAO it is unable to fixate, and suggests DAO.

NOT a HW issue here, gentoo worked for over a year with the same drive.  as did windows.  only Ubuntu has issues.

---

### Post by sunshine12 on 2007-06-28
will burn photograph cd, let's see what happens..

About firmware update, I have bad report using wine for update.. So, If anybody having experience of doing firmware update in Linux please suggest..

thanks

---

