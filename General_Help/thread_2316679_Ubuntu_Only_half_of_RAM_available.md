---
title: "Ubuntu: Only half of RAM available"
date: 2016-03-10
forum: General Help
---

### Post by preston8 on 2016-03-10
Hi all. New user here, so I apologize for any ignorance. I searched and could not find an answer despite similar threads.

The problem: I have 4GB of RAM and only 2GB are available. I'm rather attached to Chrome and it fills up the 2GB quickly (..a post for another time, also not solved with the DNS fix others have reported working..). Once stuff starts going into swap, performance tanks. 

Outputs (using the full commands used, in case other new users stumble across):
"sudo lshw -c memory":
```
  *-memory       description: System Memory
       physical id: a
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: DIMM 1066 MHz (0.9 ns)
          product: M378B2873EH1-CF8
          vendor: Samsung
          physical id: 0
          serial: 4E749886
          slot: DIMM0
          size: 1GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:1
          description: DIMM 1066 MHz (0.9 ns)
          product: M378B2873EH1-CF8
          vendor: Samsung
          physical id: 1
          serial: 51749886
          slot: DIMM1
          size: 1GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:2
          description: DIMM 1066 MHz (0.9 ns)
          product: M378B2873EH1-CF8
          vendor: Samsung
          physical id: 2
          serial: 4F749886
          slot: DIMM2
          size: 1GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:3
          description: DIMM 1066 MHz (0.9 ns)
          product: M378B2873EH1-CF8
          vendor: Samsung
          physical id: 3
          serial: 2C749886
          slot: DIMM3
          size: 1GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:4
          description: DIMM SDRAM [empty]
          product: ModulePartNumber04
          vendor: Manufacturer04
          physical id: 4
          serial: SerNum04
          slot: DIMM4
     *-bank:5
          description: DIMM SDRAM [empty]
          product: ModulePartNumber05
          vendor: Manufacturer05
          physical id: 5
          serial: SerNum05
          slot: DIMM5

```

"free -m":
```
             total       used       free     shared    buffers     cached
Mem:          1991       1841        150         20         35        592
-/+ buffers/cache:       1212        778
Swap:         2036         24       2012

```

"sudo dmidecode -t memory":
```
# dmidecode 2.12SMBIOS 2.5 present.


Handle 0x000A, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 24 GB
    Error Information Handle: Not Provided
    Number Of Devices: 6


Handle 0x000C, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000A
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK0
    Type: Other
    Type Detail: None
    Speed: 1066 MHz
    Manufacturer: Samsung       
    Serial Number: 4E749886
    Asset Tag: AssetTagNum0
    Part Number: M378B2873EH1-CF8  


Handle 0x000E, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000A
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK1
    Type: Other
    Type Detail: None
    Speed: 1066 MHz
    Manufacturer: Samsung       
    Serial Number: 51749886
    Asset Tag: AssetTagNum1
    Part Number: M378B2873EH1-CF8  


Handle 0x0010, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000A
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM2
    Bank Locator: BANK2
    Type: Other
    Type Detail: None
    Speed: 1066 MHz
    Manufacturer: Samsung       
    Serial Number: 4F749886
    Asset Tag: AssetTagNum2
    Part Number: M378B2873EH1-CF8  


Handle 0x0012, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000A
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM3
    Bank Locator: BANK3
    Type: Other
    Type Detail: None
    Speed: 1066 MHz
    Manufacturer: Samsung       
    Serial Number: 2C749886
    Asset Tag: AssetTagNum3
    Part Number: M378B2873EH1-CF8  


Handle 0x0014, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000A
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM4
    Bank Locator: BANK4
    Type: SDRAM
    Type Detail: Unknown
    Speed: Unknown
    Manufacturer: Manufacturer04
    Serial Number: SerNum04
    Asset Tag: AssetTagNum4
    Part Number: ModulePartNumber04


Handle 0x0016, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000A
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM5
    Bank Locator: BANK5
    Type: SDRAM
    Type Detail: Unknown
    Speed: Unknown
    Manufacturer: Manufacturer05
    Serial Number: SerNum05
    Asset Tag: AssetTagNum5
    Part Number: ModulePartNumber05

```

I have also run memtest, which passed, and checked in both Cinnamon and Classic.
If it's pertinent, the computer is a Dell. (I noticed a Dell specific subforum and thought it may make a difference).

I have not yet reseated the RAM, nor have I looked at the BIOS for the quantity displayed.

Thanks so much in advance!

---

### Post by Bucky Ball on 2016-03-10
What machine (specifically, 'Dell' does not give enough info) are you using and is it 64bit? If so, did you install a 32bit version of Ubuntu? If this is the case, install the 64bit version.

Other than that, test the RAM. Take one stick out and put one stick in slot one. Boot the machine. All good? Take out the stick from slot one, put the other in. All good? If both are fine then the sticks themselves are fine but a slot may be shot (it happens), so repeat the process with slot two. Test stick by stick in slot two.

---

### Post by preston8 on 2016-03-10
Thanks for the reply, Bucky.
I apologize for being vague there, I didn't think it was going to have an impact so I was brief.
It's a Studio XPS 435t / 9000. Core i7 and all 'stock' internals. 
64-bit is installed.
I will take your advice right now and start swapping.

---

### Post by preston8 on 2016-03-10
Well, my friend, you honed right in on it!
Every other slot was working.
Already everything is a whole lot smoother. I think because of the discrepancies in amount of RAM seen / available the system liked to overflow the 2GB, thus overusing the swap file. 
Right in the area of the RAM I can see a bulged up capacitor. If I happen to have one of the same size lying around I'll replace it tomorrow and update the thread, but as for right now I'm going to mark this one solved!
Greatly appreciated.

---

### Post by preston8 on 2016-03-10
(I didn't actually know how to mark it solved)

---

### Post by Bucky Ball on 2016-03-10
Great news. Well, not so great about the pair being dead, but well picked up. It happens. Obviously! ;)

The first link in my signature at bottom of this post about marking thread as solved. Good luck.

---

