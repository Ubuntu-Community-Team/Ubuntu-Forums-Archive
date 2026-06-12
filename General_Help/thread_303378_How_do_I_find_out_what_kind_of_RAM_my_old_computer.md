---
title: "How do I find out what kind of RAM my old computer uses?"
date: 2006-11-20
forum: General Help
---

### Post by megamania on 2006-11-20
I have an old P3 which I use only for downloading with aMule.

It currently has 192Mb of Ram, and I would like to take it to 256Mb or 384Mb.

Is there a way (terminal command or program in synaptic) to know the exact type of memory I should buy? What I'm looking for is something like "Everest" for Windows.

---

### Post by Wil0 on 2006-11-20
take off the cover and have a look? or in the bios...

---

### Post by zgornel on 2006-11-20
Pentium 3s used 99% SDRAM with frequencies between 100 and 133 MHz. Some odd i820 chipsets used RDRAM  but I think it is not the case. If your motherboard has a i440BX/ZX, i810/E/E2, i815E/EP/P/G chipset, gor for SDRAM PC133, it should be a bit hard to find now (new).

---

### Post by jhenager on 2006-11-20
[http://www.download.com/Faronics-System-Profiler/3000-2381_4-10427453.html](http://www.download.com/Faronics-System-Profiler/3000-2381_4-10427453.html)

You can run it from a disk or flash drive. It doesn't need to be installed. Generates a pretty comprehensive list of hardware and software on a machine.

---

### Post by AndyCooll on 2006-11-20
> **zgornel said:**
> Pentium 3s used 99% SDRAM with frequencies between 100 and 133 MHz. Some odd i820 chipsets used RDRAM  but I think it is not the case. If your motherboard has a i440BX/ZX, i810/E/E2, i815E/EP/P/G chipset, gor for SDRAM PC133, it should be a bit hard to find now (new).

You can probably get it from crucial.com

:cool:

---

### Post by megamania on 2006-11-20
> **zgornel said:**
> Pentium 3s used 99% SDRAM with frequencies between 100 and 133 MHz.

> **jhenager said:**
> [http://www.download.com/Faronics-System-Profiler/3000-2381_4-10427453.html](http://www.download.com/Faronics-System-Profiler/3000-2381_4-10427453.html)

You can run it from a disk or flash drive. 
Thanks everybody!

I'll check that program later on today.

---

### Post by jhenager on 2006-11-20
> **megamania said:**
> Thanks everybody!

I'll check that program later on today.

Forgot that Faronics is a Windows program.
Try this:
Package: lshw (02.08.01-1)
information about hardware configuration

A small tool to provide detailed information on the hardware configuration of the machine. It can report exact memory configuration, firmware version, mainboard configuration, CPU version and speed, cache configuration, bus speed, etc. on DMI-capable x86 systems, on some PowerPC machines (PowerMac G4 is known to work) and AMD64.

Information can be output in plain text, HTML or XML.

---

### Post by feign on 2006-11-20
If it's a name brand computer you can typically look up the specs on any memory manufacturer's web site (someone above suggested crucial).

---

### Post by megamania on 2006-11-21
> **jhenager said:**
> Try this:
Package: lshw (02.08.01-1)
information about hardware configuration
Just found out that lshw was already installed on both my machines!

Unfortunately, it didn't recognize the RAM model of my old computer (it does recognize the new one). Anyway, I searched for my computer brand on the net, and I'm pretty sure it uses SDRAM PC100.

My question now is: if I use faster ram (PC133) and mix it with the one that I have on board (assuming it PC100), will it work ok?

---

### Post by jhenager on 2006-11-21
> **megamania said:**
> Just found out that lshw was already installed on both my machines!

Unfortunately, it didn't recognize the RAM model of my old computer (it does recognize the new one). Anyway, I searched for my computer brand on the net, and I'm pretty sure it uses SDRAM PC100.

My question now is: if I use faster ram (PC133) and mix it with the one that I have on board (assuming it PC100), will it work ok?

I would avoid mixing PC100 with PC133. It *might*work if you have two pairs of SIMM slots, and each pair are the same speed, but I wouldn't rule out 'unexpected' results, and for sure if you try PC100 in slot 1 and PC133 in slot 2.

---

