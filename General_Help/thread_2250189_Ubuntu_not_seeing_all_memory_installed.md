---
title: "Ubuntu not seeing all memory installed"
date: 2014-10-27
forum: General Help
---

### Post by sim085 on 2014-10-27
Hello,

I just upgraded from 2GB of ram to 4GB of ram. Before upgrade /proc/meminfo MemTotal reported "2049900 kB" which is around 2GB. After upgrade, /proc/meminfo MemTotal only reports "3340144 kB". This is only around 3.34GB. 

I have Ubuntu Server 64bit installed so I was expecting to see 4GB of ram. When I enter "uname -a" I get the following: "Linux data 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_6486_64 **x86_64** GNU/Linux"

The command "lscpu" returns that my CPU is "Architecture:          x86_64".

I cannot understand why only 3.3GB of memory is being seen by Ubuntu.

---

### Post by sim085 on 2014-10-27
When I enter the command "sudo lshw -class memory" I get the following result:

```

  *-firmware
       description: BIOS
       vendor: Award Software International, Inc.
       physical id: 0
       version: F9
       date: 12/05/2005
       size: 128KiB
       capacity: 448KiB
       capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: b
       slot: Internal Cache
       size: 128KiB
       capacity: 128KiB
       capabilities: synchronous internal write-back
  *-cache:1
       description: L2 cache
       physical id: d
       slot: External Cache
       size: 512KiB
       capacity: 512KiB
       capabilities: synchronous internal write-back
  *-cache
       description: L1 cache
       physical id: c
       slot: Internal Cache
       size: 128KiB
       capacity: 128KiB
       capabilities: synchronous internal write-back
  *-memory:0
       description: System Memory
       physical id: 1b
       slot: System board or motherboard
       size: 3261MiB
     *-bank:0
          description: DIMM 166 MHz (6.0 ns) [empty]
          physical id: 0
          slot: A0
          width: 64 bits
          clock: 166MHz (6.0ns)
     *-bank:1
          description: DIMM 166 MHz (6.0 ns) [empty]
          physical id: 1
          slot: A1
          width: 64 bits
          clock: 166MHz (6.0ns)
     *-bank:2
          description: DIMM 166 MHz (6.0 ns) [empty]
          physical id: 2
          slot: A2
          width: 64 bits
          clock: 166MHz (6.0ns)
     *-bank:3
          description: DIMM 166 MHz (6.0 ns) [empty]
          physical id: 3
          slot: A3
          width: 64 bits
          clock: 166MHz (6.0ns)
  *-memory:1 UNCLAIMED
       description: Memory controller
       product: CK804 Memory Controller
       vendor: NVIDIA Corporation
       physical id: 4
       bus info: pci@0000:00:00.0
       version: a3
       width: 32 bits
       clock: 66MHz (15.2ns)
       capabilities: ht bus_master cap_list
       configuration: latency=0

```

What does the last part mean? "*-memory:1 UNCLAIMED"?

---

### Post by Mike_Walsh on 2014-10-27
Hallo, Sim.

Have a look at this page:- 

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

It may answer your question! Apparently, Linux utilises your memory in a rather different way to Windoze...

Regards,

Mike.

---

### Post by sim085 on 2014-10-27
That article seems to speak about free memory. My problem is with total memory. When I had 2GB MemTotal reported I had 2GB. Now that I have 4GB, MemTotal reports I have 3.3GB.

---

### Post by nerdtron on 2014-10-27
I don't think this is about swap. It's about the memory reported not reaching 4GB.

Do you have a Graphics card?
Try removing it first, reboot while using the onboard video. See if memory displayed on /proc/meminfo reaches 4GB. Then try reboot again with the graphics card installed.

---

### Post by sandyd on 2014-10-27
Also, are you using some kind of Intel CPU - an amount of memory is allocated to the integrated Intel HD Graphics.

For example, on my 8G laptop,
```

MemTotal:        7895476 kB
```

---

### Post by sim085 on 2014-10-27
Yes I have a graphics card. The motherboard does not have on board video card. Wouldn't that mean that Video Card would use the memory on the video card itself?

---

### Post by sim085 on 2014-10-27
No, this is AMD. The motherboard is this one; GA-K8NXP-SLI

---

### Post by sotiris2 on 2014-10-27
What is your cpu ? It is possible that it does have integrated graphics and maybe it reserves some memory for that even though you have an discrete graphics card installed.

Modern AMD is just as likely to have graphics as Intel.

---

### Post by nerdtron on 2014-10-27
> Wouldn't that mean that Video Card would use the memory on the video card itself?
Nope, the video card will have it's own memory so all ram will be given to the OS.

you sure you don't have on board video? Most computer will have a vga, dvi o hdmi port to a monitor.

What is the specs of your server?

---

### Post by sim085 on 2014-10-27
This is a link to the motherboard:
[http://www.gigabyte.com/products/product-page.aspx?pid=1859#ov](http://www.gigabyte.com/products/product-page.aspx?pid=1859#ov)
(the motherboard does not have an onboard video card).

The CPU I have is AMD Athlon64 (1 core).

---

### Post by sim085 on 2014-10-27
Found the following note in motherboard manual:

"(Note) Due to standard PC architecture, a certain amount of memory is reserved for system usage and
therefore the actual memory size is less than the stated amount.
For example, 4 GB of memory size will instead be shown as 3.xxGB memory during system startup"

Makes no sense to me... if processor is 64bit then it should be able to see 4GB of memory!

---

### Post by sim085 on 2014-10-27
Actually the note does not say I should not be seeing 4GB of ram. Only during "during system startup" I would not see the 4GB.

---

### Post by yancek on 2014-10-27
I had one 2GB memory chip on my computer which showed as only 1.8GB.  I bought an identical 2GB memory chip from the same manufactuer which should theoretically show as 4GB, or as the previous was only showing 1.8GB it should have been 3.8GB.  It shows as 3.4GB.  Also, when I originally purchased the machine, it had a 320GB HD installed which has never shown as more than 298GB.  Not much to be done about it.  I suppose you could contact the manufacturer and see what, if anything they would do.

---

### Post by sim085 on 2014-10-27
The thing is that when I had 2GB of RAM (2x1GB) MemInfo "correctly" reported the amount of RAM I hadm i.e. - 2GB. Now that I have 4GB (4x1GB) it reports 3.3GB. However I understand your point. I will remove the old RAM I have and only leave the new RAM. After that I will check meminfo. If meminfo reports less then 2GB then the problem is with the RAM I bought. If meminfo reports I have 2GB then the problem is when I have 4GB of total ram.

---

### Post by sim085 on 2014-10-27
I Just checked; removed old ram (which reported 2GB) and left only new RAM. When switched on I got 2GB of ram reported. This means that I can see only less RAM (3.3GB) then installed only when the amount of RAM installed is 4GB.

> **yancek said:**
> I had one 2GB memory chip on my computer which showed as only 1.8GB.  I bought an identical 2GB memory chip from the same manufactuer which should theoretically show as 4GB, or as the previous was only showing 1.8GB it should have been 3.8GB.  It shows as 3.4GB.  Also, when I originally purchased the machine, it had a 320GB HD installed which has never shown as more than 298GB.  Not much to be done about it.  I suppose you could contact the manufacturer and see what, if anything they would do.

---

### Post by nerdtron on 2014-10-27
How about booting a Live USB? what would that report? Or do you have a setting in the BIOS that would limit memory usage? Look into some options there that may seem to be a possible cause.

---

### Post by sim085 on 2014-10-27
I am doing a memory test and this report 3328M which looks like the 3.3GB I see from Ubuntu ... I have looked in bios but could not see any option related to enable / disable ram.

---

### Post by nerdtron on 2014-10-27
Post #14 here? [http://forums.anandtech.com/showthread.php?t=1749145](http://forums.anandtech.com/showthread.php?t=1749145)

---

### Post by sim085 on 2014-10-27
Thank you for that. Seems to be a BIOS issue and not Ubuntu :)
I'll check what BIOS I have and see how I can upgrade with Ubuntu!

---

