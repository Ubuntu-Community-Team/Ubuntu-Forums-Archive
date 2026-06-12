---
title: "Ubuntu 18.04 sees half the RAM on three systems"
date: 2019-08-22
forum: General Help
---

### Post by rkjha1211 on 2019-08-22
Hi ajgreeny,
I am also facing same issue half of total memory. I am using Lenovo Ideapad 310-15Isk. I had installed Ubuntu 18.04.03 LTS for last 7 months and never faced this half of ram issue before. But now its creating issue several time in stating I tried to remove ram and then reinsert it and it works for sometime like this method but it works for me only 2-3 times not more that that. 

Now I am again facing this issue and I have no solution. I have 8GB of ram and bios also loading half ram (4GB) and only 3.8 GB is usable. I am sharing command output that you said to try and share.

```
command: uname -a
Output: Linux developer 5.0.0-25-generic #26~18.04.1-Ubuntu SMP Thu Aug 1 13:51:02 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux




```

```
command: free -mw
output:
              total        used        free      shared     buffers       cache   available
Mem:      3848        2414         811          91          55         567        1109
Swap:     11008         255       10753

```

```

command: cat /proc/meminfo
output:
MemTotal:        3940452 kB
MemFree:          192796 kB
MemAvailable:     523080 kB
Buffers:           57980 kB
Cached:           605456 kB
SwapCached:        14304 kB
Active:          2541928 kB
Inactive:         751716 kB
Active(anon):    2224840 kB
Inactive(anon):   560548 kB
Active(file):     317088 kB
Inactive(file):   191168 kB
Unevictable:         732 kB
Mlocked:              48 kB
SwapTotal:      11273212 kB
SwapFree:       11011580 kB
Dirty:             13220 kB
Writeback:             0 kB
AnonPages:       2621192 kB
Mapped:           393876 kB
Shmem:            155172 kB
KReclaimable:      62048 kB
Slab:             141664 kB
SReclaimable:      62048 kB
SUnreclaim:        79616 kB
KernelStack:       20048 kB
PageTables:       100280 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    13243436 kB
Committed_AS:   13916416 kB
VmallocTotal:   34359738367 kB
VmallocUsed:           0 kB
VmallocChunk:          0 kB
Percpu:             1312 kB
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
Hugetlb:               0 kB
DirectMap4k:      444816 kB
DirectMap2M:     3653632 kB
DirectMap1G:     1048576 kB

```

```

 command: sudo dmidecode --type memory
output: 
# dmidecode 3.1
Getting SMBIOS data from sysfs.
SMBIOS 2.8 present.


Handle 0x0026, DMI type 16, 23 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 32 GB
	Error Information Handle: No Error
	Number Of Devices: 2


Handle 0x0027, DMI type 17, 40 bytes
Memory Device
	Array Handle: 0x0026
	Error Information Handle: No Error
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 4096 MB
	Form Factor: SODIMM
	Set: None
	Locator: ChannelA-DIMM0
	Bank Locator: BANK 0
	Type: DDR4
	Type Detail: Synchronous
	Speed: 2133 MT/s
	Manufacturer: Samsung
	Serial Number: 00000000
	Asset Tag: 9876543210
	Part Number: M471A5244BB0-CPB    
	Rank: 1
	Configured Clock Speed: 2133 MT/s
	Minimum Voltage: 1.5 V
	Maximum Voltage: 1.5 V
	Configured Voltage: 1.2 V


Handle 0x0028, DMI type 17, 40 bytes
Memory Device
	Array Handle: 0x0026
	Error Information Handle: No Error
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: Unknown
	Set: None
	Locator: ChannelA-DIMM1
	Bank Locator: BANK 1
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified
	Rank: Unknown
	Configured Clock Speed: Unknown
	Minimum Voltage: Unknown
	Maximum Voltage: Unknown
	Configured Voltage: Unknown


Handle 0x0029, DMI type 17, 40 bytes
Memory Device
	Array Handle: 0x0026
	Error Information Handle: No Error
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: Unknown
	Set: None
	Locator: ChannelB-DIMM0
	Bank Locator: BANK 2
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified
	Rank: Unknown
	Configured Clock Speed: Unknown
	Minimum Voltage: Unknown
	Maximum Voltage: Unknown
	Configured Voltage: Unknown


Handle 0x002A, DMI type 17, 40 bytes
Memory Device
	Array Handle: 0x0026
	Error Information Handle: No Error
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: Unknown
	Set: None
	Locator: ChannelB-DIMM1
	Bank Locator: BANK 3
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified
	Rank: Unknown
	Configured Clock Speed: Unknown
	Minimum Voltage: Unknown
	Maximum Voltage: Unknown
	Configured Voltage: Unknown



```
second command also shows half ram.

---

### Post by rkjha1211 on 2019-08-22
Hi Ubuntu Experts,
I am also facing same issue half of total memory. I am using Lenovo Ideapad 310-15Isk. I had installed Ubuntu 18.04.03 LTS for last 7 months and never faced this half of ram issue before. But now its creating issue several time in stating I tried to remove ram and then reinsert it and it works for sometime like this method but it works for me only 2-3 times not more that that. 

Now I am again facing this issue and I have no solution. I have 8GB of ram and bios also loading half ram (4GB) and only 3.8 GB is usable. I am sharing command output that you said to try and share.

```
command: uname -a
Output: Linux developer 5.0.0-25-generic #26~18.04.1-Ubuntu SMP Thu Aug 1 13:51:02 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux




```

```
command: free -mw
output:
              total        used        free      shared     buffers       cache   available
Mem:      3848        2414         811          91          55         567        1109
Swap:     11008         255       10753

```

```

command: cat /proc/meminfo
output:
MemTotal:        3940452 kB
MemFree:          192796 kB
MemAvailable:     523080 kB
Buffers:           57980 kB
Cached:           605456 kB
SwapCached:        14304 kB
Active:          2541928 kB
Inactive:         751716 kB
Active(anon):    2224840 kB
Inactive(anon):   560548 kB
Active(file):     317088 kB
Inactive(file):   191168 kB
Unevictable:         732 kB
Mlocked:              48 kB
SwapTotal:      11273212 kB
SwapFree:       11011580 kB
Dirty:             13220 kB
Writeback:             0 kB
AnonPages:       2621192 kB
Mapped:           393876 kB
Shmem:            155172 kB
KReclaimable:      62048 kB
Slab:             141664 kB
SReclaimable:      62048 kB
SUnreclaim:        79616 kB
KernelStack:       20048 kB
PageTables:       100280 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    13243436 kB
Committed_AS:   13916416 kB
VmallocTotal:   34359738367 kB
VmallocUsed:           0 kB
VmallocChunk:          0 kB
Percpu:             1312 kB
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
Hugetlb:               0 kB
DirectMap4k:      444816 kB
DirectMap2M:     3653632 kB
DirectMap1G:     1048576 kB

```

```

 command: sudo dmidecode --type memory
output: 
# dmidecode 3.1
Getting SMBIOS data from sysfs.
SMBIOS 2.8 present.


Handle 0x0026, DMI type 16, 23 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 32 GB
    Error Information Handle: No Error
    Number Of Devices: 2


Handle 0x0027, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x0026
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: SODIMM
    Set: None
    Locator: ChannelA-DIMM0
    Bank Locator: BANK 0
    Type: DDR4
    Type Detail: Synchronous
    Speed: 2133 MT/s
    Manufacturer: Samsung
    Serial Number: 00000000
    Asset Tag: 9876543210
    Part Number: M471A5244BB0-CPB    
    Rank: 1
    Configured Clock Speed: 2133 MT/s
    Minimum Voltage: 1.5 V
    Maximum Voltage: 1.5 V
    Configured Voltage: 1.2 V


Handle 0x0028, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x0026
    Error Information Handle: No Error
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: Unknown
    Set: None
    Locator: ChannelA-DIMM1
    Bank Locator: BANK 1
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified
    Rank: Unknown
    Configured Clock Speed: Unknown
    Minimum Voltage: Unknown
    Maximum Voltage: Unknown
    Configured Voltage: Unknown


Handle 0x0029, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x0026
    Error Information Handle: No Error
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: Unknown
    Set: None
    Locator: ChannelB-DIMM0
    Bank Locator: BANK 2
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified
    Rank: Unknown
    Configured Clock Speed: Unknown
    Minimum Voltage: Unknown
    Maximum Voltage: Unknown
    Configured Voltage: Unknown


Handle 0x002A, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x0026
    Error Information Handle: No Error
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: Unknown
    Set: None
    Locator: ChannelB-DIMM1
    Bank Locator: BANK 3
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified
    Rank: Unknown
    Configured Clock Speed: Unknown
    Minimum Voltage: Unknown
    Maximum Voltage: Unknown
    Configured Voltage: Unknown



```


second command also shows half ram.

---

### Post by oldfred on 2019-08-22
Many years ago Jerry Pournelle, RIP,  recommended a lubricating product for inserting memory.
It was expensive but many claimed it worked well.
[http://www.stabilant.com/Review02.html](http://www.stabilant.com/Review02.html)

Not sure what other cleaners/lubricants for electrical work well.

---

### Post by #&amp;thj^% on 2019-08-22
> **oldfred said:**
> Many years ago Jerry Pournelle, RIP,  recommended a lubricating product for inserting memory.
It was expensive but many claimed it worked well.
[http://www.stabilant.com/Review02.html](http://www.stabilant.com/Review02.html)

Not sure what other cleaners/lubricants for electrical work well.

+1 works very well.
I also use a natural gum eraser , with caution and light careful strokes. (Please be careful using the eraser not to scratch the copper)

---

### Post by MoebusNet on 2019-08-22
@rkjha - If you notice, your dmidecode command only results of 4Gb RAM in Bank 0; all the other Banks show empty. If the RAM modules are  compatible with the motherboard, then they are either defective or not making proper contact in the slots. The commercial product WD-40 was developed specifically for electrical work (the 'WD' stands for 'water displacement') and should be safe for use (disclaimer: I have not used it for this specific purpose). Ubuntu's Live-DVD has a memory test program available when booted from the Live-DVD, that may give more info.

---

### Post by lammert-nijhof on 2019-08-22
One of your memory modules is not detected by the BIOS, but it is better to check it in the BIOS screen itself.
It looks like a hardware problem, probably some contact or timing issues, if it works sometimes after re-seating the DIMM.
The first 4 GB is soldered in your laptop, so I assume you only have one location for a DIMM, so:  
- You could try some contact spray to clean the memory DIMM and socket.

Otherwise go to the place you bought the laptop or to a laptop repair shop, probably you have to replace the DIMM, I think you need probably exactly 2133 MHz DDR4 for your laptop with that soldered 4GB. 
With that soldered 4GB check carefully, which DIMM is supported using the Lenovo website for your PC.

---

### Post by coffeecat on 2019-08-22
@rkjha1211, you posted to someone else's old thread, and then posted the same request for technical help in a chat area of the forum. I have merged your two posts and all the replies to them into one thread in General Help. When using the forum, please do not post the same thing in different places, and start your own threads rather than hijacking an existing thread. The chat areas are clearly marked not for support.

---

