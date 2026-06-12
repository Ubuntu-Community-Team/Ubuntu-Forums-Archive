---
title: "System keeps freezing up"
date: 2014-12-22
forum: General Help
---

### Post by MJae on 2014-12-22
Hi all,

I don't know what's up with my Xubuntu system. It keeps freezing up. There is this thread, though: [http://ubuntuforums.org/showthread.php?t=2149104](http://ubuntuforums.org/showthread.php?t=2149104). And it seems like we have the same problem but that thread close without a solution.

And as much as I would love to give details why it happens, I can't because it seems to happen randomly. I can't give any specifics as to when it happens. It just does. Unlike the reported in that other thread, though, I don't use flash a lot on that system. Like I said, it just freezes up.

Details:
Xubuntu 12.04
IBM T40p

Thanks much. And, if there's any other information I need to provide, I'd gladly give it if I could.

---

### Post by ajgreeny on 2014-12-22
Have you searched out all the info there is on bumblebee?

It is needed for optimum performance (or maybe any performance) of the optimus graphics, which I assume you have on that machine.

It is also possible that 14.04 would give you better performance of the bumblebee graphics than 12.04, but I am not sure about that.

---

### Post by Yellow Pasque on 2014-12-22
> **ajgreeny said:**
> It is needed for optimum performance (or maybe any performance) of the optimus graphics, which I assume you have on that machine.

Bad assumption. The Thinkpad T40(p) is from 2003, which is much older than Optimus technology. From quick google, it looks a Pentium M laptop with ATI graphics from the dawn of the Radeon era.

The first thing I'd do is monitor temps to make sure it is not overheating. I would also run memtest as a RAM module might have gone bad.

---

### Post by ajgreeny on 2014-12-22
> **Temüjin said:**
> Bad assumption. The Thinkpad T40(p) is from 2003, which is much older than Optimus technology. From quick google, it looks a Pentium M laptop with ATI graphics from the dawn of the Radeon era.

The first thing I'd do is monitor temps to make sure it is not overheating. I would also run memtest as a RAM module might have gone bad.
Thanks for that info; I just assumed it was the same problem the OP linked to, ie a bumblebee/optimus problem, without going any further.

I really ought to look a bit deeper at the problem sometimes!

---

### Post by MJae on 2014-12-22
I wanted to upgrade for 14.04, as suggested, but I can't. There was this error (something about the cpu, I've forgotten what it was exactly) which makes it so that 14.04 can't be installed on it.

It is possible that the temperature might be the culprit. But it might not be all. See, sometimes, it happens when I've barely used the Thinkpad. A few minutes. It doesn't heat up that much in a short while.

I'll remember to do the memtest later and report what I get from it. (I'm using someone else's computer right now.)

Is it possible, though, that the Thinkpad is not liking the RAM that got installed on it? See, the Thinkpad was given to me by someone who didn't need it anymore. I was told that the RAM was upgraded before I got it.

---

### Post by ajgreeny on 2014-12-23
You can check your ram by running memtest86+ from the grub menu and leaving it running for as long as possible, even overnight if possible.

If any errors show along the bottom at the end there is a memory module problem.

---

### Post by MJae on 2014-12-27
So I did the memtest thing and this is what I got from it:
```

Pentium M (0.13)       1595 MHz
L1 Cache:    32K    17335 MB/s
L2 Cache:  1024K     8667 MB/s
L3 Cache: None
Memory: 1535 M    778 MB/s
Chipset: Intel 9i885PM / FSB:   99 MHz / Mobile Platform
Settings: RAM: 132 MHz (DDR264) / CAS: 2.5-3-3-

WallTime: 6:16:03
Pass: 4
Errors: 930
```

And the error summary looks like this:

```
Error Confidence Value: 127
Lowest Error Address: 000568130fc - 1384.0MB
Highest Error Address: 000568130fc - 1384.0MB
Bits in Error Mask: 00100000
Bits in Error: Total: 1
              Min: 1   Max: 1   Avg: 0
Max Contiguoug Errors: 1
ECC Correctible Errors:
Errors per Memory Slot:
 0:0  4:0  8:0 12:0
 1:0  5:0  9:0 13:0
 2:1  6:0 10:0 14:0
 3:0  7:0 11:0 15:0
```

The individual errors look like this:

```

Test               4
Pass               0
Failing Address    000568130fc - 1384.0 MB
Good               c9a20f6c
Bad                c9b20f6c
Err-bits           00100000
Count              1

```

What do I make of these? I've been reading around the memtest pages and it seems that the only solutions is to remove the faulty RAM and replace it...?

---

### Post by Yellow Pasque on 2014-12-27
> Errors per Memory Slot:
 0:0  4:0  8:0 12:0
 1:0  5:0  9:0 13:0
 **2:1**  6:0 10:0 14:0
 3:0  7:0 11:0 15:0

If all of the errors are coming from the same memory slot, then maybe you can try removing that stick and just running with one stick of RAM to see if memtest still reports errors and/or the system keeps freezing. I'm not sure which module to tell you to remove (though for your sake, I hope the fault module is the one that's easily accessible and not the one buried under the keyboard). What's your RAM setup look like?
```
sudo dmidecode -t memory
```

---

### Post by MJae on 2014-12-31
This is what I got from dmidecode:

```

# dmidecode 2.11
SMBIOS version fixup (2.33 -> 2.3).
SMBIOS 2.3 present.

Handle 0x0007, DMI type 5, 20 bytes
Memory Controller Information
    Error Detecting Method: None
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 1024 MB
    Maximum Total Memory Size: 2048 MB
    Supported Speeds:
        Other
    Supported Memory Types:
        DIMM
        SDRAM
    Memory Module Voltage: 2.9 V
    Associated Memory Slots: 2
        0x0008
        0x0009
    Enabled Error Correcting Capabilities:
        None

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM Slot 1
    Bank Connections: 0 1
    Current Speed: Unknown
    Type: DIMM SDRAM
    Installed Size: 1024 MB (Double-bank Connection)
    Enabled Size: 1024 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM Slot 2
    Bank Connections: 2 3
    Current Speed: Unknown
    Type: DIMM SDRAM
    Installed Size: 512 MB (Double-bank Connection)
    Enabled Size: 512 MB (Double-bank Connection)
    Error Status: OK

Handle 0x002C, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 1 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x002D, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x002C
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM 1
    Bank Locator: Bank 0/1
    Type: DDR
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified

Handle 0x002E, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x002C
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 512 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM 2
    Bank Locator: Bank 2/3
    Type: DDR
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified


```

What do I make of this?

Now, I've never torn apart a laptop before because it seems like all the parts in it must be cramped together just to fit in the frame. So, thankfully, one RAM was just one screwed-in flap away. I removed that one, did the memtest again, and got this:

```

*****Pass complete, no errors, press Esc to exit*****

```

So, that means the error was coming from that RAM stick I removed right? Because, really, I don't know where the other one is. Probably buried underneath the keyboard like you said.

Now, is there no way to fix that one? And, how did this happen, in the first place?

---

### Post by Yellow Pasque on 2014-12-31
Can you run dmidecode again now that you've taken the one stick out?

> So, that means the error was coming from that RAM stick I removed right?
That would be the logical conclusion.

> Probably buried underneath the keyboard like you said. Now, is there no way to fix that one?
If that's the good stick, then you don't need to replace it. (And yes, it's buried underneath the keyboard according to the manual.)

> And, how did this happen, in the first place? 
It could have been a bad module "out of the box" or perhaps someone handled it carelessly (i.e. not by the edges) and damaged it with ESD. It could have also gone bad over time.

---

### Post by MJae on 2015-01-01
> **Temüjin said:**
> 
If that's the good stick, then you don't need to replace it. (And yes, it's buried underneath the keyboard according to the manual.)

Sorry, wrong order of words... I meant to ask, is there no way to fix that RAM module which I removed? The one that's probably causing the errors and the freezes...?

And, this is what the dmidecode result looks like now:

```

# dmidecode 2.11
SMBIOS version fixup (2.33 -> 2.3).
SMBIOS 2.3 present.

Handle 0x0007, DMI type 5, 20 bytes
Memory Controller Information
    Error Detecting Method: None
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 1024 MB
    Maximum Total Memory Size: 2048 MB
    Supported Speeds:
        Other
    Supported Memory Types:
        DIMM
        SDRAM
    Memory Module Voltage: 2.9 V
    Associated Memory Slots: 2
        0x0008
        0x0009
    Enabled Error Correcting Capabilities:
        None

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM Slot 1
    Bank Connections: 0 1
    Current Speed: Unknown
    Type: DIMM SDRAM
    Installed Size: 1024 MB (Double-bank Connection)
    Enabled Size: 1024 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM Slot 2
    Bank Connections: 2 3
    Current Speed: Unknown
    Type: DIMM SDRAM
    Installed Size: Not Installed
    Enabled Size: Not Installed
    Error Status: OK

Handle 0x002C, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 1 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x002D, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x002C
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM 1
    Bank Locator: Bank 0/1
    Type: DDR
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified

Handle 0x002E, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x002C
    Error Information Handle: No Error
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: SODIMM
    Set: None
    Locator: DIMM 2
    Bank Locator: Bank 2/3
    Type: DDR
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified


```

---

### Post by Yellow Pasque on 2015-01-01
There's no way to fix it. What you have now is 1GB of RAM. If you find that's not enough, you can always add another stick.
DDR 266 (PC2100) is what the laptop originally had. DDR 333 (PC2700) should work too if that's all you can find (though it will still run at PC2100 speed).

---

### Post by MJae on 2015-01-02
Well, that's that then.

I might not be getting another stick, though, because 1024 MB of RAM seems to be enough and it doesn't make sense to be adding more, given the CPU - which is really what I need more of most of the time, processing power not memory. But thanks for the advice. I'll be making use of it once I find that this present setup is not enough for my usual activities.

I don't mean to impose but I have some other unresolved issues here: [http://ubuntuforums.org/showthread.php?t=2252006](http://ubuntuforums.org/showthread.php?t=2252006) and here: [http://ubuntuforums.org/showthread.php?t=2065050](http://ubuntuforums.org/showthread.php?t=2065050). If you have the time, please help me out with them, too.

Thanks much for all your help!

---

