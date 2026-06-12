---
title: "&quot;Overclocking failed!&quot; - BIOS or motherboard?"
date: 2008-05-22
forum: General Help
---

### Post by ricardisimo on 2008-05-22
Every other boot-up one thing or another happens (and these two things alternately precisely every other time):
[LIST=1]
[*]I get no display at all; the monitor is on with a completely black screen; or...
[*]I get that warning about overclocking before the kernel loads, specifically:
[/LIST]
```
Overclocking failed! Please enter Setup to reconfigure your system.
Press F1 to run SETUP
Press F2 to load default values and continue
```
I had a question about this exact problem in what are now the archives, and the response there was that it had to be my CMOS battery gone or going out. Well, I checked that out, and the battery is fine. The guy at the shop, who knows only Windows, seemed certain that I need to flash my BIOS, and suggested that it was the easiest thing in the world. If that doesn't work, he said, it's a bad motherboard.

I looked into flashing BIOS, and it is indeed very simple to do... if you run Windows. I was hoping someone who had already succeeded in this endeavor could point me to the appropriate HOWTO or other thread or web link.

I can deal with rebooting every time. The bigger problem is that I can't seem to install or upgrade past Feisty Fawn (Ubuntu or Kubuntu) on this comp, and I'm assuming it's a related issue. Doesn't seem a stretch, really. I can't get the "Install" icon to appear on the desktop of the LiveCD installer, and upgrade announces all sorts of failures after it's way too late to stop it (like when the process is over) and then freezes. I went through each option at least twice, sadly.

My motherboard and BIOS are American Megatrends, as I gather most people's are. I'd post other system info, but I'll wait to see if anyone asks specifics instead. And, just in case anyone is interested, no, I'm not actually overclocking.

---

### Post by sdennie on 2008-05-22
Are you actually overclocking the machine via BIOS?  If not, it does actually sound like a motherboard issue.  I had a machine where I had to reseat the DIMMS every time I powered it on or it wouldn't boot (seems very similar to what you describe in #1 in your post).  Nothing at all to do with linux; the motherboard was just a piece of garbage.

Edit:

Thinking about this a bit more, it could actually be a power supply issue as well.

---

### Post by hardyn on 2008-05-22
or ram speed

---

### Post by bigken on 2008-05-22
try shorting the cmos or remove the battery see if this resets the mobo

---

### Post by ricardisimo on 2008-05-31
> **bigken said:**
> try shorting the cmos or remove the battery see if this resets the mobo

No luck. I just had to endure being scolded by the check disk utility for mounting 8,437,702 times without checking for errors... check forced... well, maybe not that many times, but...

The RAM sounds more likely at this point. I recall having a problem with where the chips had to go. If I placed them in one slot, something that closely resembled short-circuiting was happening. Very scary. Is the problem the RAM chips, the DIMM slots, the motherboard, or something else? Any idea how to proceed? Thanks a gajillion.

Here's my lshw (at least, the motherboard and memory):
```
    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: P4P8X
       vendor: ASUSTek Computer Inc.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
       slot: 
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1006.007 (05/13/2003)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: CPU 1
          size: 2400MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 8KB
             capacity: 8KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KB
             capacity: 512KB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 35
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 256MB
             width: 64 bits
        *-bank:2
             description: DIMM SDRAM Synchronous
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 256MB
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
```

---

### Post by bigken on 2008-05-31
well it sounds like your board has gone bad I had a one which went crazy on me so I replaced the mobo and the same thing happed with the new board it turned out to be the case the mounts were touching something to make the mobo  short personally I would remove all the cards and ram chips and try each ram chip in each slot good luck

---

### Post by ricardisimo on 2008-06-24
I tried moving all of the RAM chips around, which only subtracted or added memory. Now I'm back up to the full 1Gig of RAM, but no luck on the "overclocking", and still having to power up twice every time.

Before I go buy a new motherboard, what are the odds of my graphics card being the culprit? When i run "sudo lshw", the video card shows twice; once normally and once as "unclaimed", like so:
```
 *-display:0
                description: VGA compatible controller
                product: RV280 [Radeon 9200 SE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: iomemory:e8000000-efffffff ioport:c000-c0ff iomemory:fe9f0000-fe9fffff irq:17
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV280 [Radeon 9200 SE] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@01:00.1
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: iomemory:e0000000-e7ffffff iomemory:fe9e0000-fe9effff
```
Thanks again for any help.

---

### Post by mc4man on 2008-06-24
I wouldn't worry about having the card show twice, typical of ati cards . You'd also see that in windows in device manager, the display adapter listed twice -  primary and secondary

---

### Post by WRDN on 2008-06-24
For commands used in the terminal, you may find [this]("http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/") useful.

---

### Post by ricardisimo on 2008-06-25
> **WRDN said:**
> For commands used in the terminal, you may find [this]("http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/") useful.

Thank you, but this is in reference to what, exactly? Is there a link on these pages referring to my rebooting problem?

---

### Post by Lord Quinny on 2009-04-02
Possibly a bit too late for this thread but maybe helpful to someone else, I have also had this problem.

I have an ASUS P4P800 Deluxe motherboard and this overclocking message has come up for me before but I have managed to get rid of it.

The first time I managed to resolve this by setting the BIOS "Performance Mode" to Standard (the Default is Auto).

I caused this error to happen again by moving one of the 2-wire molex fan plugs to a full power (4-wire) molex power cable. Changing the fan plug back to the 2-wire "Fan only" power cable resolved the issue.

Hope that helps.

---

