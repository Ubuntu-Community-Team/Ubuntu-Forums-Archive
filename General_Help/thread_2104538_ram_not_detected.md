---
title: "ram not detected"
date: 2013-01-13
forum: General Help
---

### Post by axebill on 2013-01-13
i have a custom build with an as rock g31m-s r2.0 motherboard and core duo cpu.i installed ubuntu 12.04 64bit server os. i recently installed 8gb of ram. the bios recognizes all 8gigs but the os only shows 3.1gigs. i looked on some older threads but nothing works. any help would be appreciated.

---

### Post by Topsiho on 2013-01-13
I hate to make a stupid suggestion like this, but are you sure you installed a 64 bit version of Ubuntu, or did you by mistake install a 32 bit version?

For then it would be more clear: the hardware (BIOS) recognizes the full 8 GiB, but the software only the 3 GiB that you mention.

Topsiho

---

### Post by axebill on 2013-01-13
i'm afraid so. the bios shows "total memory at 8192mb" and on the detail section on the os it shows 3.1gb. and yes i installed 64 bit ubuntu 12.04 lts. the system previously had 32 bit 12.04 but i installed 64 in place of it. the only thing i can think of is it might have kept 32bit bit attributes but it will nit install pae either. i'm at a loss.

---

### Post by oldos2er on 2013-01-13
Can you post the output of ```
uname -a
``` ?

---

### Post by Topsiho on 2013-01-14
pae (physical address extension) is a capability of recent 32 bit processors to use more than 3 GiB of ram. So if your processor is 64 bits, it doesn't need this capability, and therefore doesn't have it.

If you installed the new os on top of the old os, then the old os is wiped into extiction. Saying this,  ==> I think of the possibility of config files that still exist on your system, and might corrupt things.

Config files for a former 32 bits os, creating their havoc on a 64 bit system :). Must be it.

Topsiho

---

### Post by axebill on 2013-01-14
linux ubuntu 3.2.0-35-generic #55-ubuntu smp wed dec 5 17:42:16 utc 2012 x86_64 x86_64 x86_64  gnu/linux
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
-64 x86
 
 
 
 
 
 
 
 
 
 
-

---

### Post by Topsiho on 2013-01-14
That's exactly the same processor as that I have in my computer.
Which uses 6 GiB without any trouble :)

Hint: Better use copy and paste in stead of retyping things :)

Linux bromo 3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Less work to do, and fewer mistakes. The lower case gnu (and other letters) betrayed you :).

It's (of course) not meant as nit picking: if you use copy and paste, helpers can be much more sure of your information, and thus how to help you.

Topsiho

---

### Post by Cheesemill on 2013-01-14
Can you post the output of...
```
sudo dmidecode -t memory
```

If you can highlight the output when replying and click the # button it will make it easier for us to read.

---

### Post by axebill on 2013-01-14
# dmidecode 2.11
SMBIOS 2.4 present.

Handle 0x0007, DMI type 5, 20 bytes
Memory Controller Information
    Error Detecting Method: 64-bit ECC
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 4096 MB
    Maximum Total Memory Size: 8192 MB
    Supported Speeds:
        Other
    Supported Memory Types:
        DIMM
        SDRAM
    Memory Module Voltage: 3.3 V
    Associated Memory Slots: 2
        0x0008
        0x0009
    Enabled Error Correcting Capabilities:
        None

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM0
    Bank Connections: 0 1
    Current Speed: Unknown
    Type: DIMM SDRAM
    Installed Size: 4096 MB (Double-bank Connection)
    Enabled Size: 4096 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM1
    Bank Connections: 4 5
    Current Speed: Unknown
    Type: DIMM SDRAM
    Installed Size: 4096 MB (Double-bank Connection)
    Enabled Size: 4096 MB (Double-bank Connection)
    Error Status: OK

Handle 0x000E, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 4 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x0010, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000E
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK0
    Type: SDRAM
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Manufacturer0
    Serial Number: SerNum0
    Asset Tag: AssetTagNum0
    Part Number: PartNum0

Handle 0x0012, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000E
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK1
    Type: SDRAM
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Manufacturer1
    Serial Number: SerNum1
    Asset Tag: AssetTagNum1
    Part Number: PartNum1

---

