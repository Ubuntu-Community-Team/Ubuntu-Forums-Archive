---
title: "CD/DVD Not recognizing."
date: 2012-12-23
forum: General Help
---

### Post by NenadSpaske on 2012-12-23
Hi, well i'm new to ubuntu.
So, here is the problem.I put my CD-RW into the drive, the little green light is flashing, but there is no respoce on my home directory on the left side, where the divices are located.I've seen some other threads, and here is the proof that drive is detected : i typed in sudo hdparm -I /dev/sr0  here's what i get : ```
ATAPI CD-ROM, with removable media
    Model Number:       PIONEER DVD-RW  DVR-112D                
    Serial Number:      GEDP670352WL       
    Firmware Revision:  1.21    
Standards:
    Likely used CD-ROM ATAPI-1
Configuration:
    DRQ response: 50us.
    Packet size: 12 bytes
    cache/buffer size  = unknown
Capabilities:
    LBA, IORDY(can be disabled)
    Buffer size: 64.0kB
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 *udma4 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    Power Management feature set
       *    PACKET command feature set
       *    DEVICE_RESET command
HW reset results:
    CBLID- above Vih
    Device num = 1 determined by the jumper
```.
I have some CDW program installed, and when i try to read the actual CD-RW here is what i get :  CD/DVD drive doesn't respond (timeout). 
 Try again?           , and after that.
 Cannot get basic information about disc.
Now the important note: Before all of this i have burned something to this CD, it took my computer a while to recognize it, but it did.Now it isn't recognizing it at all.Also i tried many times to reboot the computer.Oh, and my ubuntu version is 12.10 .
Please help. :)

---

### Post by NenadSpaske on 2012-12-23
I have put a DVD in the drive, and it read.Though i still need help, because this CD has some important information that i erased from computer, beliving it will work.;)

---

