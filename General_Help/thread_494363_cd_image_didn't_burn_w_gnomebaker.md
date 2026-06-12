---
title: "cd image didn't burn w/ gnomebaker"
date: 2007-07-06
forum: General Help
---

### Post by nae5 on 2007-07-06
i have 7.04 

i tried to burn an iso of 6.06 server edition to a blank cd -r which is supposed to be supported by the burn drive.

i tried to right click write to disc first after the dl finished but it said to use a blank disc, it was blank and i got one i am positive was blank

same thing 

then i installed gnomebaker and it failed with this error output:

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '0,1,0'
scsibus: 0 target: 1 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
wodim: Cannot do inquiry for CD/DVD-Recorder.
Errno: 5 (Input/output error), test unit ready scsi sendcmd: fatal error
CDB:  00 00 00 00 00 00
cmd finished after 0.000s timeout 40s
TOC Type: 3 = CD-ROM XA mode 2
atapi: 1

i tried it with all the modes and it didn't work... ??

any ideas most of this stuff means nothing to me, im still noob

thanks in advance for any help

---

### Post by phidia on 2007-07-06
To start with you can type > cdrecord -scanbus in a shell/terminal and post or search the output.

A good read for the commandline tool cdrecord is [http://www.linuxquestions.org/questions/showthread.php?t=565194](http://www.linuxquestions.org/questions/showthread.php?t=565194) (which is what's behind all the gui frontends)

---

### Post by nae5 on 2007-07-06
naes@naes2:~$ cdrecord -scanbus
scsibus0:
        0,0,0     0) 'PIONEER ' 'DVD-ROM DVD-115 ' '1.22' Removable CD-ROM
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *


thnx for ur reply ill read that link this is the output you requested

---

### Post by nae5 on 2007-07-07
i dont know what i did but cdrecord -scanbus came up with the drive later

naes@naes2:~$ cdrecord -scanbus
scsibus0:
        0,0,0     0) 'PIONEER ' 'DVD-ROM DVD-115 ' '1.22' Removable CD-ROM
        0,1,0     1) 'LG      ' 'CD-RW CED-8120B ' '1.03' Removable CD-ROM
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
naes@naes2:~$ ls

i tried following the directions for a dummy burn of the iso image on the page [http://howto-pages.org/cdwriting/07.php](http://howto-pages.org/cdwriting/07.php)

but this happened

naes@naes2:~$ cdrecord dev=0,1,0 speed=4 fs=16m -v -eject -dummy /naes/ubuntu-6.06.1-server-i386.iso
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
scsidev: '0,1,0'
scsibus: 0 target: 1 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'LG      '
Identification : 'CD-RW CED-8120B '
Revision       : '1.03'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 5185536 = 5064 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 16777216 = 16384 KB
wodim: No such file or directory. Cannot open '/naes/ubuntu-6.06.1-server-i386.iso'.
naes@naes2:~$ 

i have used ubuntu before to make iso's right out of the box i m too noob to know how to fix this even tho there are small parts i undeerstand,
any help would be greatly appreciated

---

### Post by Ripfox on 2007-07-07
Brasero!!

---

### Post by phidia on 2007-07-07
> wodim: No such file or directory. Cannot open '/naes/ubuntu-6.06.1-server-i386.iso'.

That line seems significant-what are the permissions on that iso file or is it on a drive/partition that can't be read by cdrecord?
I would check obvious things like file permissions first.

---

### Post by nae5 on 2007-07-07
i have never done anything with file permissions before... but all i did was dl it w/out changing anything and it doesn't seem to work.. ?? is there something specific i should try?

---

### Post by Ripfox on 2007-07-07
I would try Brasero it's in the repos, and it works better imho.

---

### Post by nae5 on 2007-07-07
thnx for the opinion im gonna check brasero out, i am actually interested in using the CLI as often as possible although im still really new at it... but i don't understand why cdrecord doesn't work or gnomebaker.. ?? is there a package of codecs or some such thing im missing?  

thank  you guys for your help.

---

### Post by nae5 on 2007-07-07
brasero gives me the same answer as gnomebaker, it says to put a blank disc in there. im absolutely positive that the disc is blank...

---

### Post by Wiebelhaus on 2007-07-07
> **ripfox said:**
> ***_Brasero!!_***


word to yo mother , gnomebaker always crashes on me.

---

### Post by phidia on 2007-07-08
Experiances like opinions differ. I've never had problems with gnomebaker at all. I've been using it for at least three or four years.
Anyway all these gui frontends are running on cli cdrecord and if that isn't finding the device the chances of a gui app working are zero.
I recommend taking a look at man cdrecord. It isn't that difficult to figure out. If there's a specific problem using cdrecord give the output and we'll try and help from there.

---

### Post by nae5 on 2007-07-10
Quote:
wodim: No such file or directory. Cannot open '/naes/ubuntu-6.06.1-server-i386.iso'.
That line seems significant-what are the permissions on that iso file or is it on a drive/partition that can't be read by cdrecord?
I would check obvious things like file permissions first.

it wasn't file permissions it was the directory location should have been /home/naes/ubuntu...

after i tried it again with that i get this 

naes@naes2:~$ cdrecord -scanbus
scsibus0:
        0,0,0     0) 'PIONEER ' 'DVD-ROM DVD-115 ' '1.22' Removable CD-ROM
        0,1,0     1) 'LG      ' 'CD-RW CED-8120B ' '1.03' Removable CD-ROM
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
naes@naes2:~$ cdrecord dev=0,1,0 speed=4 fs=16m -v -eject -dummy /home/naes/ubuntu-6.06.1-server-i386.iso
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
scsidev: '0,1,0'
scsibus: 0 target: 1 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'LG      '
Identification : 'CD-RW CED-8120B '
Revision       : '1.03'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 5185536 = 5064 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 16777216 = 16384 KB
Track 01: data   432 MB        
Total size:      496 MB (49:10.10) = 221258 sectors
Lout start:      496 MB (49:12/08) = 221258 sectors
wodim: Cannot load media.
wodim: Cannot eject media.
naes@naes2:~$

it didn't work w/ right filepath...

---

### Post by nae5 on 2007-07-10
without "-dummy" command

naes@naes2:~$ cdrecord dev=0,1,0 speed=4 fs=16m -v -eject /home/naes/ubuntu-6.06.1-server-i386.iso
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
scsidev: '0,1,0'
scsibus: 0 target: 1 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
atapi: 1
wodim: Cannot do inquiry for CD/DVD-Recorder.
Errno: 5 (Input/output error), test unit ready scsi sendcmd: fatal error
CDB:  00 00 00 00 00 00
cmd finished after 0.000s timeout 40s
naes@naes2:~$

---

