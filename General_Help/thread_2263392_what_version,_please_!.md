---
title: "what version, please !"
date: 2015-01-31
forum: General Help
---

### Post by ondalin on 2015-01-31
hello. i want to know  **what xubuntu/lubuntu version can run decent**  on this laptop: **cpu intel celeron 1.73 ghz, 2gb ram, 120gb hdd, sata chipset, video card intel 965 express family**. thanks.

---

### Post by ajgreeny on 2015-01-31
I would suggest you try Xubuntu first and if that is still too slow for you go to Lubuntu.  Stick with 14.04 as it is an LTS version.

However it is not only the DE you use that makes a difference, because once started it will just be a vessel for your applications and they will vary in speed a lot , eg, Libreoffice will always be a lot slower than Abiword and Gnumeric, so choose both the DE and your apps with care.

---

### Post by sudodus on 2015-01-31
Welcome to the Ubuntu Forums :-)

- Please tell us the computer's brand name and model too.

- And there are so many celeron processors, can specify it with more details.

It will make it possible to give more detailed advice.

Without knowing more details I would say that both of Lubuntu and Xubuntu should work fairly well. Start trying version 14.04 LTS. So download both 32-bit desktop iso files and [try them live before deciding what to install]("http://ubuntuforums.org/showthread.php?t=2230389").

---

### Post by grahammechanical on 2015-01-31
Whatever member of the Ubuntu family we use it is always best to install a version that still has support for security fixes. And the best version at the moment is 14.04 LTS. Apart from 12.04 LTS any version older than 14.04 has now reached end of life. The software repositories of those older versions are now closed. We cannot install applications or receive security updates for end of life versions.

Regards.

---

### Post by ondalin on 2015-01-31
first, thanks to everyone for quick replies.
second, system info:

```
System Information report written at: 01/31/15 23:07:43

[System Summary]

Item    Value    
OS Name    Microsoft Windows 7 Professional    
Version    6.1.7600 Build 7600    
Other OS Description     Not Available    
OS Manufacturer    Microsoft Corporation    
System Manufacturer    TOSHIBA    
**System Model**    **T20    **(*on the back of the laptop is says L40-14B, don't know why here states T20*)
System Type    X86-based PC    
Processor    Intel(R) Celeron(R) CPU          530  @ 1.73GHz, 1729 Mhz, 1 Core(s), 1 Logical Processor(s)    
BIOS Version/Date    American Megatrends Inc. V5.50, 5/14/2008    
SMBIOS Version    2.4    
    
Installed Physical Memory (RAM)    2.00 GB    
Total Physical Memory    1.99 GB    
Available Physical Memory    1.16 GB    
Total Virtual Memory    3.98 GB    
Available Virtual Memory    3.19 GB    
Page File Space    1.99 GB    

[Display]

Item    Value    
Name    Mobile Intel(R) 965 Express Chipset Family    
PNP Device ID    PCI\VEN_8086&DEV_2A03&SUBSYS_FF401179&REV_03\3&11583659&0&11    
Adapter Type    Not Available, Intel Corporation compatible    
Adapter Description    Mobile Intel(R) 965 Express Chipset Family    
Adapter RAM    Not Available    
Installed Drivers    igdumdx32.dll,igd10umd32.dll    
Driver Version    8.15.10.1825    
INF File    oem2.inf (i965GM1 section)    
Color Planes    Not Available    
Color Table Entries    4294967296    
Resolution    1280 x 800 x 59 hertz    
Bits/Pixel    32    

        
Name    Mobile Intel(R) 965 Express Chipset Family    
PNP Device ID    PCI\VEN_8086&DEV_2A02&SUBSYS_FF401179&REV_03\3&11583659&0&10    
Adapter Type    Mobile Intel(R) 965 Express Chipset Family, Intel Corporation compatible    
Adapter Description    Mobile Intel(R) 965 Express Chipset Family    
Adapter RAM    384.00 MB (402,653,184 bytes)    
Installed Drivers    igdumdx32.dll,igd10umd32.dll    
Driver Version    8.15.10.1825    
INF File    oem2.inf (i965GM0 section)    
Color Planes    Not Available    
Color Table Entries    Not Available    
Resolution    Not Available    
Bits/Pixel    Not Available    
Memory Address    0xFEB00000-0xFEBFFFFF    
Memory Address    0xD0000000-0xDFFFFFFF    
I/O Port    0x0000EC00-0x0000EC07    
IRQ Channel    IRQ 16    
I/O Port    0x000003B0-0x000003BB    
I/O Port    0x000003C0-0x000003DF    
Memory Address    0xA0000-0xBFFFF    
Driver    c:\windows\system32\drivers\igdkmd32.sys (8.15.10.1825, 4.54 MB (4,756,992 bytes), 1/8/2015 7:48 PM)    



[Disks]

Item    Value    
Description    Disk drive    
Manufacturer    (Standard disk drives)    
Model    FUJITSU MHY2120BH ATA Device    
Bytes/Sector    512    
Media Loaded    Yes    
Media Type    Fixed hard disk    
Partitions    3    
SCSI Bus    0    
SCSI Logical Unit    0    
SCSI Port    1    
SCSI Target ID    0    
Sectors/Track    63    
Size    111.79 GB (120,031,511,040 bytes)    
Total Cylinders    14,593    
Total Sectors    234,436,545    
Total Tracks    3,721,215    
Tracks/Cylinder    255    
Partition    Disk #0, Partition #0    
Partition Size    100.00 MB (104,857,600 bytes)    
Partition Starting Offset    1,048,576 bytes    
Partition    Disk #0, Partition #1    
Partition Size    48.73 GB (52,321,845,248 bytes)    
Partition Starting Offset    105,906,176 bytes    
Partition    Disk #0, Partition #2    
Partition Size    62.95 GB (67,595,351,040 bytes)    
Partition Starting Offset    52,427,934,720 bytes    


[IDE]

Item    Value    
Name    Intel(R) ICH8M SATA AHCI Controller - 2829    
Manufacturer    Intel    
Status    OK    
PNP Device ID    PCI\VEN_8086&DEV_2829&SUBSYS_FF401179&REV_03\3&11583659&0&FA    
I/O Port    0x0000E880-0x0000E887    
I/O Port    0x0000E800-0x0000E803    
I/O Port    0x0000E480-0x0000E487    
I/O Port    0x0000E400-0x0000E403    
I/O Port    0x0000E080-0x0000E09F    
Memory Address    0xFEAFF800-0xFEAFFFFF    
IRQ Channel    IRQ 20    
Driver    c:\windows\system32\drivers\msahci.sys (6.1.7600.16385, 27.06 KB (27,712 bytes), 7/14/2009 2:45 AM)    
        
Name    ATA Channel 0    
Manufacturer    (Standard IDE ATA/ATAPI controllers)    
Status    OK    
PNP Device ID    PCIIDE\IDECHANNEL\4&189D71C&0&0    
I/O Port    0x000001F0-0x000001F7    
I/O Port    0x000003F6-0x000003F6    
IRQ Channel    IRQ 14    
Driver    c:\windows\system32\drivers\atapi.sys (6.1.7600.16385, 21.08 KB (21,584 bytes), 7/14/2009 2:11 AM)    
        
Name    ATA Channel 0    
Manufacturer    (Standard IDE ATA/ATAPI controllers)    
Status    OK    
PNP Device ID    PCIIDE\IDECHANNEL\4&18A8A25F&0&0    
Driver    c:\windows\system32\drivers\atapi.sys (6.1.7600.16385, 21.08 KB (21,584 bytes), 7/14/2009 2:11 AM)    
        
Name    ATA Channel 1    
Manufacturer    (Standard IDE ATA/ATAPI controllers)    
Status    OK    
PNP Device ID    PCIIDE\IDECHANNEL\4&18A8A25F&0&1    
Driver    c:\windows\system32\drivers\atapi.sys (6.1.7600.16385, 21.08 KB (21,584 bytes), 7/14/2009 2:11 AM)    
        
Name    ATA Channel 2    
Manufacturer    (Standard IDE ATA/ATAPI controllers)    
Status    OK    
PNP Device ID    PCIIDE\IDECHANNEL\4&18A8A25F&0&2    
Driver    c:\windows\system32\drivers\atapi.sys (6.1.7600.16385, 21.08 KB (21,584 bytes), 7/14/2009 2:11 AM)    
        
Name    Intel(R) ICH8M Ultra ATA Storage Controllers - 2850    
Manufacturer    Intel    
Status    OK    
PNP Device ID    PCI\VEN_8086&DEV_2850&SUBSYS_FF401179&REV_03\3&11583659&0&F9    
I/O Port    0x0000FFA0-0x0000FFAF    
Driver    c:\windows\system32\drivers\intelide.sys (6.1.7600.16385, 15.06 KB (15,424 bytes), 7/14/2009 2:11 AM)    
```

thanks again.

---

### Post by sudodus on 2015-01-31
Thanks for all these details. I think you can run both ***Lubuntu and Xubuntu***. Lubuntu with a lighter desktop environment will be better for playing video, but Xubuntu has other advantages. It is a matter of preferences and how you intend to use the computer.

So I still suggest that you download both 32-bit desktop iso files (version 14.04.1 LTS) and ***try*** them live (booted from the install CD/DVD/USB drive) before starting to install.

---

### Post by ondalin on 2015-01-31
ok, thanks again. we'll try.

---

### Post by flaymond on 2015-02-01
I'm using a pc with 1gb ram and 1.73ghz processor, run great with Xubuntu(slightly heavy than Lubuntu) and Lubuntu(It's faster, but lack of beautiful features)

---

