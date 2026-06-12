---
title: "command to get monitor make"
date: 2013-06-18
forum: General Help
---

### Post by TWj2X6Ln4F on 2013-06-18
Hello!

I was curious what command I could run to get info on what make of monitors are currently connected. If I go to the displays portion of the system settings where I adjust my screen resolution, it lists accurately what the brand of the monitor's are, and how they are connected. How can I get this via the command line? I want this so that I can tell if a certian monitor is connected so I know whether or not to run my color configuration script.

All help is appreciated!

---

### Post by Cheesemill on 2013-06-18
First of all install the read-edid and edid-decode packages...
```
sudo apt-get install read-edid edid-decode
```

Then the following will give you all of the monitor information...
```
sudo get-edid | edid-decode
```

There's probably other ways of doing this but this is the only one that I've used.

---

### Post by TWj2X6Ln4F on 2013-06-19
Hmm, I tried that, and I don't think it is working. I am using a Philips external monitor right now and I don't see the brand name in there at all. In case I hadn't mentioned, I am using an Acer laptop. I am getting the following output:

```
james@jamesgq:~$ sudo get-edid
get-edid: get-edid version 2.0.0

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function unsupported
    Call failed

    VBE version 0
    VBE string at 0x0 "O"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function unsupported
    Call failed

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function unsupported
    Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
james@jamesgq:~$ sudo get-edid | edid-decode
get-edid: get-edid version 2.0.0

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function unsupported
    Call failed

    VBE version 0
    VBE string at 0x0 "O"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function unsupported
    Call failed

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function unsupported
    Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
Extracted contents:
header:          00 00 00 00 00 00 00 00
serial number:   00 00 00 00 00 00 00 00 00 00
version:         00 00
basic params:    00 00 00 00 00
chroma info:     00 00 00 00 00 00 00 00 00 00
established:     00 00 00
standard:        00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
descriptor 1:    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
descriptor 2:    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
descriptor 3:    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
descriptor 4:    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
extensions:      00
checksum:        00

No header found
Manufacturer: @@@ Model 0 Serial Number 0
EDID version: 0.0
Analog display, Input voltage level: 0.7/0.3 V
Sync: 
Image size is variable
Gamma: 1.00
Monochrome or grayscale display
Established timings supported:
Standard timings supported:
non-conformant standard timing (0 horiz)
non-conformant standard timing (0 horiz)
non-conformant standard timing (0 horiz)
non-conformant standard timing (0 horiz)
non-conformant standard timing (0 horiz)
non-conformant standard timing (0 horiz)
non-conformant standard timing (0 horiz)
non-conformant standard timing (0 horiz)
Manufacturer-specified data, tag 0
Manufacturer-specified data, tag 0
Manufacturer-specified data, tag 0
Manufacturer-specified data, tag 0
Checksum: 0x0
EDID block does not conform at all!
    Bad year of manufacture
    Manufacturer name field contains garbage
```

---

