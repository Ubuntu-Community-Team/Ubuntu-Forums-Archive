---
title: "How much RAM do I have?"
date: 2021-02-12
forum: General Help
---

### Post by hauget on 2021-02-12
Hi everyone!
Newb here. I recently purchased a new computer and ran Ubuntu natively on it from the start.
Before I bought my computer I was told that it had 8 GiB of RAM. However when I checked the "about" section in the settings menu it said that it only has 5,8 GiB. I ran the command "free -m" in the terminal to double check this. The terminal said that I have a total RAM of 5954 byte, but that I also have 2047 byte of something called Swap. What does this mean? Do I have 8 GiB of RAM or not?

Thanks in advance!

---

### Post by oldfred on 2021-02-12
Sounds like 6GB being seen.
Swap is a file or partition for use when you attempt to load more programs than you have RAM, so not to crash system. Systems with 4GB or more of RAM rarely use or need swap, but swap still recommended.

What does UEFI show?

What does these show?
[FONT=monospace][COLOR=#000000]sudo dmidecode | grep Size | grep MB[/COLOR]
head /proc/meminfo


Linux ate my RAM! -  memory use cache
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)
Difference between Details screen on RAM and free command
[http://askubuntu.com/questions/743649/new-16gb-of-ram-installed-yet-i-see-15-3-on-my-system-why?noredirect=1#comment1106622_743649](http://askubuntu.com/questions/743649/new-16gb-of-ram-installed-yet-i-see-15-3-on-my-system-why?noredirect=1#comment1106622_743649) &
[https://askubuntu.com/questions/184217/why-most-people-recommend-to-reduce-swappiness-to-10-20/184221#184221](https://askubuntu.com/questions/184217/why-most-people-recommend-to-reduce-swappiness-to-10-20/184221#184221)


[/FONT]

---

### Post by deadflowr on 2021-02-12
Your system is only seeing 5.8GB of RAM,
might be a number of reasons why only that and not 8GB.
Look at dmidecode, maybe:
```
sudo dmidecode -t memory
```
As for swap see: [https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

Ninja'd.
oldfred gave some good links to review.

---

### Post by hauget on 2021-02-12
The first command wielded a whole bunch of information that I wasn`t able to comprehend.
When I launched the second command (head /proc/meminfo) the following information appeared:
MemTotal:        6097416 kB
MemFree:         3530468 kB
MemAvailable:    4554264 kB
Buffers:           58748 kB
Cached:          1142104 kB
SwapCached:            0 kB
Active:          1267328 kB
Inactive:         854036 kB
Active(anon):     918944 kB
Inactive(anon):    13808 kB

Can you translate this for me?

---

### Post by hauget on 2021-02-12
> **deadflowr said:**
> Your system is only seeing 5.8GB of RAM,
might be a number of reasons why only that and not 8GB.
Look at dmidecode, maybe:
```
sudo dmidecode -t memory
```
As for swap see: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Ninja'd.
oldfred gave some good links to review.

Yeah, so that command wielded this information. Can you tell me what it means?

Handle 0x000A, DMI type 16, 23 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 32 GB
    Error Information Handle: 0x0009
    Number Of Devices: 2

Handle 0x0011, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x000A
    Error Information Handle: 0x0010
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM 0
    Bank Locator: P0 CHANNEL A
    Type: DDR4
    Type Detail: Synchronous Unbuffered (Unregistered)
    Speed: 3200 MT/s
    Manufacturer: Hynix
    Serial Number: 00000000
    Asset Tag: Not Specified
    Part Number: HMA851S6CJR6N-XN    
    Rank: 1
    Configured Memory Speed: 2400 MT/s
    Minimum Voltage: 1.2 V
    Maximum Voltage: 1.2 V
    Configured Voltage: 1.2 V

Handle 0x0014, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x000A
    Error Information Handle: 0x0013
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM 0
    Bank Locator: P0 CHANNEL B
    Type: DDR4
    Type Detail: Synchronous Unbuffered (Unregistered)
    Speed: 3200 MT/s
    Manufacturer: Hynix
    Serial Number: 223BA59A
    Asset Tag: Not Specified
    Part Number: HMA851S6DJR6N-XN    
    Rank: 1
    Configured Memory Speed: 2400 MT/s
    Minimum Voltage: 1.2 V
    Maximum Voltage: 1.2 V
    Configured Voltage: 1.2 V

---

### Post by ajgreeny on 2021-02-12
So you do have 8G RAM (see the lines in red below) and probably the other 2G that you are not seeing in other command output  is set aside for graphics.
What graphics do you have in the system?  My betting is some form of integrated graphics system not a separate graphics card.
The command ```
sudo inxi -Fzxm
``` will show us more hardware details including RAM info again.
```
Handle 0x0011, DMI type 17, 40 bytes
Memory Device
Array Handle: 0x000A
Error Information Handle: 0x0010
Total Width: 64 bits
Data Width: 64 bits
[COLOR="#FF0000"]Size: 4096 MB[/COLOR]
Form Factor: SODIMM
Set: None
Locator: DIMM 0
Bank Locator: P0 CHANNEL A
Type: DDR4
Type Detail: Synchronous Unbuffered (Unregistered)
Speed: 3200 MT/s
Manufacturer: Hynix
Serial Number: 00000000
Asset Tag: Not Specified
Part Number: HMA851S6CJR6N-XN
Rank: 1
Configured Memory Speed: 2400 MT/s
Minimum Voltage: 1.2 V
Maximum Voltage: 1.2 V
Configured Voltage: 1.2 V

Handle 0x0014, DMI type 17, 40 bytes
Memory Device
Array Handle: 0x000A
Error Information Handle: 0x0013
Total Width: 64 bits
Data Width: 64 bits
[COLOR="#FF0000"]Size: 4096 MB[/COLOR]
Form Factor: SODIMM
Set: None
Locator: DIMM 0
Bank Locator: P0 CHANNEL B
Type: DDR4
Type Detail: Synchronous Unbuffered (Unregistered)
Speed: 3200 MT/s
Manufacturer: Hynix
Serial Number: 223BA59A
Asset Tag: Not Specified
Part Number: HMA851S6DJR6N-XN
Rank: 1
Configured Memory Speed: 2400 MT/s
Minimum Voltage: 1.2 V
Maximum Voltage: 1.2 V
Configured Voltage: 1.2 V 
```

---

### Post by hauget on 2021-02-12
I could not run the command, but yeah, the GPU is integrated in the processor. It\s probably not very good, but I`m not much of a gamer anyway. Maybe I should try and allocate less RAM to the it?

> **ajgreeny said:**
> So you do have 8G RAM (see the lines in red below) and probably the other 2G that you are not seeing in other command output  is set aside for graphics.
What graphics do you have in the system?  My betting is some form of integrated graphics system not a separate graphics card.
The command ```
sudo inxi -Fzxm
``` will show us more hardware details including RAM info again.
```
Handle 0x0011, DMI type 17, 40 bytes
Memory Device
Array Handle: 0x000A
Error Information Handle: 0x0010
Total Width: 64 bits
Data Width: 64 bits
[COLOR=#FF0000]Size: 4096 MB[/COLOR]
Form Factor: SODIMM
Set: None
Locator: DIMM 0
Bank Locator: P0 CHANNEL A
Type: DDR4
Type Detail: Synchronous Unbuffered (Unregistered)
Speed: 3200 MT/s
Manufacturer: Hynix
Serial Number: 00000000
Asset Tag: Not Specified
Part Number: HMA851S6CJR6N-XN
Rank: 1
Configured Memory Speed: 2400 MT/s
Minimum Voltage: 1.2 V
Maximum Voltage: 1.2 V
Configured Voltage: 1.2 V

Handle 0x0014, DMI type 17, 40 bytes
Memory Device
Array Handle: 0x000A
Error Information Handle: 0x0013
Total Width: 64 bits
Data Width: 64 bits
[COLOR=#FF0000]Size: 4096 MB[/COLOR]
Form Factor: SODIMM
Set: None
Locator: DIMM 0
Bank Locator: P0 CHANNEL B
Type: DDR4
Type Detail: Synchronous Unbuffered (Unregistered)
Speed: 3200 MT/s
Manufacturer: Hynix
Serial Number: 223BA59A
Asset Tag: Not Specified
Part Number: HMA851S6DJR6N-XN
Rank: 1
Configured Memory Speed: 2400 MT/s
Minimum Voltage: 1.2 V
Maximum Voltage: 1.2 V
Configured Voltage: 1.2 V 
```

---

### Post by ajgreeny on 2021-02-12
What is the output of command ```
lspci -v | grep VGA -A12 | grep Memory
``` which should show the memory use of the graphics system.

---

### Post by hauget on 2021-02-13
The output is
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=2M]
    Memory at fcc00000 (32-bit, non-prefetchable) [size=512K]





> **ajgreeny said:**
> What is the output of command ```
lspci -v | grep VGA -A12 | grep Memory
``` which should show the memory use of the graphics system.

---

### Post by ActionParsnip on 2021-02-13
I suspect onboard video is using some of the RAM unlike a dedicated video card which has it's own RAM

---

### Post by kurt18947 on 2021-02-13
I use a little app found in the repositories, htop. It's sort of a graphics top command but i find it easier to understand. It also shows how many processor cores you have and how busy they are.

---

### Post by rsteinmetz70112 on 2021-02-14
It may be possible to configure the amount of RAM used for graphics. If you provided the CPU and Computer models someone may know.

---

