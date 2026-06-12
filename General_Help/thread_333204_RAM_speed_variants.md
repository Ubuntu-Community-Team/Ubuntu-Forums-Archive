---
title: "RAM speed variants"
date: 2007-01-07
forum: General Help
---

### Post by maniacmusician on 2007-01-07
Hi,

I was wondering; when using RAM of different speeds in a computer, do all sticks default to the lowest speed? My current situation is that I have 2 sticks of RAM running at 667, but I'm about to buy a new motherboard that can do better. But I'm pretty sure that RAM can only be used at one constant speed and it would make sense that it would default to the speed of the slower RAM to accommodate it. 

So basically I don't want to spend money on faster RAM if I won't be able to use the extra speed. I don't plan on replacing all of my RAM because that'd be a tad expensive.

thanks.

edit: also, is there any way to test what speed my RAM is running at right now? I said 667, but thats actually just the fastest this motherboard can support. So I want to know what speed my RAM is running at and what its maximum speed is.

---

### Post by tommcd on 2007-01-07
AFAIK if you have RAM that runs at different speeds (eg DDR333 and DDR400) it will always run at the lower speed. Your motherboards BIOS will tell you what speed your RAM is set at. If you have a windows partition you could use CPU-Z to tell you what speed your RAM is running as well as it's timings, etc. I don't know of a similar app in linux.

[http://www.cpuid.com/](http://www.cpuid.com/)

The memory manufacture's site should tell you the specs of your RAM and what speeds it could run at.

---

### Post by maniacmusician on 2007-01-07
I've forgotten the exact model of RAM i bought back in the day so can't check that. Don't have windows so CPU-Z is out. 

I'll check my BIOS next time I reboot though, thanks for that.

If anyone knows of a program in linux that can give me this information, that would be great. 

Thanks!

---

### Post by smoker on 2007-01-07
i also think if you run memtest, should be an option on grub, it will tell you info about the speed of your ram. and cpu-z can run in wine i believe, if you have wine installed, it is only one .exe file.

a mixture of ram will always run at the speed as the slowest module (unless things have changed recently!)

and as suggested, the bios screen should be able to give you info on your ram.

---

### Post by dcstar on 2007-01-07
sudo lshw

---

### Post by smoker on 2007-01-07
> **dcstar said:**
> sudo lshw

hi, thanks, dcstar

this command will be well remembered:D

---

### Post by tommcd on 2007-01-07
> **dcstar said:**
> sudo lshw

Wow, I totally forgot about that. Thanks for mentioning it.

---

### Post by maniacmusician on 2007-01-07
awesome, you rock. but I don't see anything about speed. There's a section on memory:

>      *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 1536MB
        *-bank:0
             description: DIMM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GB
             width: 64 bits
        *-bank:1
             description: DIMM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 512MB
             width: 64 bits


---

### Post by Mike'sHardLinux on 2007-01-07
By default, your RAM will run at the slower speed. This is because your computer will read the settings from the RAM's SPD, and will use those settings. But, you can go into your BIOS setup and tell your computer to use other values. At least, this is true for every motherboard I've worked with in the past few years (even on the OEM stuff.)

If you set it to run at a faster speed, you will be overclocking your RAM, so do so at your own risk. If the RAM doesn't like being overclocked, it won't necessarily be obvious. It might seem fine, and then you might get weird stuff like when you try run a program and the program never starts up.

---

### Post by maniacmusician on 2007-01-07
> **Mike'sHardLinux said:**
> By default, your RAM will run at the slower speed. This is because your computer will read the settings from the RAM's SPD, and will use those settings. But, you can go into your BIOS setup and tell your computer to use other values. At least, this is true for every motherboard I've worked with in the past few years (even on the OEM stuff.)

If you set it to run at a faster speed, you will be overclocking your RAM, so do so at your own risk. If the RAM doesn't like being overclocked, it won't necessarily be obvious. It might seem fine, and then you might get weird stuff like when you try run a program and the program never starts up.
yes I don't even want to try overclocking. the 512 stick that's in there is probably the slower one, and it's a stock stick that came with the computer when I ordered it from HP. I'm pretty sure that it is of godawful quality so overclocking is probably not a possibility.

now, does anyone have any insight on my post # 8? How do I get lshw to display RAM speed currently being used?

---

### Post by RandomJoe on 2007-01-07
lshw only shows the memory speed when I run it as root (sudo) - just shows very basic information (less than yours even) when run as a regular user.  Did you make sure to use sudo?

First time I've heard of that command, nifty one! :)

---

### Post by maniacmusician on 2007-01-07
yes I did use sudo. What I pasted wasn't the entire output, just what was relevant to RAM. and it still shows the same thing, no speed. weird.

---

### Post by Mike'sHardLinux on 2007-01-07
Mine also does **not** show memory speed, even when run as sudo.

---

### Post by maniacmusician on 2007-01-07
phew, I'm not alone!

---

### Post by tommcd on 2007-01-07
Yeah, my lshw does not show RAM speed or timings either. Anyone know of a program similar to CPU-Z for linux? I guess CPU-Z could be run in wine as suggested.

---

### Post by maniacmusician on 2007-01-07
yeah it could, but I'd rather find a native linux solution, just out of curiosity

---

