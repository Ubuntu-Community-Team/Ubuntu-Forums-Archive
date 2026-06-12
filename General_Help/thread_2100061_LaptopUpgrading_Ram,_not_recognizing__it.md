---
title: "Laptop/Upgrading Ram, not recognizing  it"
date: 2012-12-31
forum: General Help
---

### Post by BuntuLife on 2012-12-31
ive tried to search all around, usually dont have to do any forum help but this time i couldt find the answer :frown:

i had 2gb of ram and trying to upgrade it with 2gb more, but only 1.8 shows in the system monitor:-?

laptop: Lenovo Thinkpad L412
OS: Ubuntu 12.10 64bit

[-o<

---

### Post by Cheesemill on 2012-12-31
Can you post the output of:
```
sudo dmidecode -t 6
```

---

### Post by BuntuLife on 2012-12-31
> **Cheesemill said:**
> Can you post the output of:
```
sudo dmidecode -t 6
```


# dmidecode 2.11
SMBIOS 2.6 present.

--------

i was wondering if its possible that Ubuntu is reading only the Ram that was installed when i installed Ubuntu, therefore i have to reinstall Ubuntu  :???:

---

### Post by haqking on 2012-12-31
You sure you have 64 bit installed ?

post

```
uname -m
```

And is the memory seen i the bios ? is it seated correctly and the same type as original memory installed

---

### Post by Cheesemill on 2012-12-31
> **BuntuLife said:**
> # dmidecode 2.11
SMBIOS 2.6 present.

--------

i was wondering if its possible that Ubuntu is reading only the Ram that was installed when i installed Ubuntu, therefore i have to reinstall Ubuntu  :???:
Are you sure thats all you get? It should return a detailed memory description like this:
```
rob@arch:~$ sudo dmidecode -t 6
# dmidecode 2.11
SMBIOS 2.4 present.

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A0
    Bank Connections: 1
    Current Speed: Unknown
    Type: Other
    Installed Size: 4096 MB (Single-bank Connection)
    Enabled Size: 4096 MB (Single-bank Connection)
    Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A1
    Bank Connections: 2
    Current Speed: Unknown
    Type: Other
    Installed Size: 2048 MB (Single-bank Connection)
    Enabled Size: 2048 MB (Single-bank Connection)
    Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A2
    Bank Connections: 3
    Current Speed: Unknown
    Type: Unknown
    Installed Size: Not Installed
    Enabled Size: Not Installed
    Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A3
    Bank Connections: 4
    Current Speed: Unknown
    Type: Other
    Installed Size: 2048 MB (Single-bank Connection)
    Enabled Size: 2048 MB (Single-bank Connection)
    Error Status: OK
```

If your not getting all this information try the following instead;
```
sudo dmidecode -t memory
```

---

### Post by Luigi2012SM64DS on 2012-12-31
When you have 1gb ram does it recognize 1.0gb or 0.8 gb? That would probably mean you are sharing memory with your video card( if you have one).

---

### Post by BuntuLife on 2012-12-31
> **haqking said:**
> You sure you have 64 bit installed ?

post

```
uname -m
```And is the memory seen i the bios ? is it seated correctly and the same type as original memory installed


```
 x86_64
```

by the same type do you mean same brand?..they are both DDR3

but cut the story short...i think the 2nd DIM is not working right, its not holding the Ram, after i read you guy comments i did another check to find that it was loose :frown:

Also Cheesemill i tried again and it gave me the same output, just said it was present..

is there a command or something i could do to see if maybe its the DIM spot that is not working or holding the ram steady? 

i guess my other option would be to get one 4gb stick of Ram and use that #-o

---

### Post by Cheesemill on 2012-12-31
Have you tried:
```
sudo dmidecode -t memory
```

---

### Post by BuntuLife on 2012-12-31
> **Cheesemill said:**
> Have you tried:
```
sudo dmidecode -t memory
```


```
# dmidecode 2.11
SMBIOS 2.6 present.

Handle 0x001B, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 16 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x001C, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x001B
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: SODIMM
    Set: 1
    Locator: M1
    Bank Locator: Bank 0
    Type: DDR3
    Type Detail: Synchronous
    Speed: 667 MHz
    Manufacturer: 0198            
    Serial Number: 431026D1        
    Asset Tag: 1123
    Part Number: 9904342-002.A00G  
    Rank: Unknown

Handle 0x001D, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x001B
    Error Information Handle: No Error
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: SODIMM
    Set: 1
    Locator: M2
    Bank Locator: Bank 1
    Type: Unknown
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer:                 
    Serial Number:                 
    Asset Tag:     
    Part Number:                   
    Rank: Unknown

```

---

### Post by haqking on 2012-12-31
> **BuntuLife said:**
> ```
# dmidecode 2.11
SMBIOS 2.6 present.

Handle 0x001B, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 16 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x001C, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x001B
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: SODIMM
    Set: 1
    Locator: M1
    Bank Locator: Bank 0
    Type: DDR3
    Type Detail: Synchronous
    Speed: 667 MHz
    Manufacturer: 0198            
    Serial Number: 431026D1        
    Asset Tag: 1123
    Part Number: 9904342-002.A00G  
    Rank: Unknown

Handle 0x001D, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x001B
    Error Information Handle: No Error
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: SODIMM
    Set: 1
    Locator: M2
    Bank Locator: Bank 1
    Type: Unknown
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer:                 
    Serial Number:                 
    Asset Tag:     
    Part Number:                   
    Rank: Unknown

```

Looks like a dodgy second DIMM, is it seen in the BIOS ? I doubt it is as it says no DIMM is installed

---

### Post by BuntuLife on 2012-12-31
> **haqking said:**
> Looks like a dodgy second DIMM, is it seen in the BIOS ? I doubt it is as it says no DIMM is installed


yup...i think so as well, not much i can do about it, and negative on the BIOS


thanks for all your help everyone.much much appreciated the awesome community is part of th reason i love Ubuntu :p again thanks...problem solved, Bad DIMM socket

---

### Post by haqking on 2012-12-31
> **BuntuLife said:**
> yup...i think so as well, not much i can do about it, and negative on the BIOS


thanks for all your help everyone.much much appreciated the awesome community is part of th reason i love Ubuntu :p again thanks...problem solved, Bad DIMM socket

Bad DIMM socket, have you put your known working DIMM into the socket to see ?

I suspect it is a bad SODIMM itself, though it may be the socket ?

---

### Post by BuntuLife on 2012-12-31
> **haqking said:**
> Bad DIMM socket, have you put your known working DIMM into the socket to see ?

I suspect it is a bad SODIMM itself, though it may be the socket ?


i tried, it works as normal, so im thinking its just the socket....im trying to find on google  if i can even replace it, its a laptop so no clue how or if i can replace it...the simplest solution would be to get a 4gb and stick it in the working socket, i did want 8gb but i guess 4gb will do for now

---

