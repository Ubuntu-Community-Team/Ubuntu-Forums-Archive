---
title: "Shared Graphics Memory Issue"
date: 2013-08-16
forum: General Help
---

### Post by YxF4zb3 on 2013-08-16
I had recently dual booted Windows 8 and Ubuntu 13.04. It seems that under ubuntu I have 512MB total graphics memory and under windows 8 I have 3022MB. I'm unsure how to fix this, as I would like to play some games, but I'm unsure if it will run with the same amount of graphics memory for games as under windows.

Relevant Dxdiag info:
```
Card name: AMD Radeon HD 7660G       Manufacturer: Advanced Micro Devices, Inc.
          Chip type: AMD Radeon HD 7660G (0x9900)
           DAC type: Internal DAC(400MHz)
        Device Type: Full Device
         Device Key: Enum\PCI\VEN_1002&DEV_9900&SUBSYS_18A6103C&REV_00
     Display Memory: 3022 MB
   Dedicated Memory: 480 MB
      Shared Memory: 2542 MB
```

"lspci -v | less" displays this for my graphics card:
```
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9900 (prog-if 00 [VGA controller])        Subsystem: Hewlett-Packard Company Device 18a6
        Flags: bus master, fast devsel, latency 0, IRQ 54
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 3000 [size=256]
        Memory at f0300000 (32-bit, non-prefetchable) [size=256K]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: fglrx_pci

```

---

### Post by mastablasta on 2013-08-16
are the drivers installed? how did you install them? 

hwo doyou know it's using only 512 MB graphics memorry? in windows that memorry is GPU+your RAM. in linux it will use the ram as well if it needs it.  i don't think the card has 3GB or am i wrong here? i see that AMD Radeon HD 7660G  is dual graphics. is this supported in linux by AMD?

---

### Post by YxF4zb3 on 2013-08-16
To install drivers  I went here:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Step one: APU
Step two: Mobile APU
Three: A series
Four: Linux x86_64

I unzipped the download, and followed this official pdf:
[http://www2.ati.com/relnotes/catalyst_linux_installer.pdf](http://www2.ati.com/relnotes/catalyst_linux_installer.pdf)

Catalyst Control Center says as well that there's only 512. I googled that command I posted trying to figure out how to display graphics memory and posted that command because it showed 256 prefetchable and  256 non prefetchable = 512.

According to windows' dxdiag, the card has 480MB of dedicated memory. If Ubuntu is only displaying dedicated memory, then I'm baffled.

Windows is showing 2542MB shared memory which indeed would take from the total of  6GB of RAM from the computer.

Play with Linux's install for world of Tanks requests for the amount of graphics memory, and I'm really unsure what to put in it.

---

### Post by mastablasta on 2013-08-16
wiki says memory = system for this chip. hmm... are you sure it's not suing more memorry if it needs it? i think there is benchmakring suite Phronix suite. that one should show you how much mem is being used and all other data.

is that the A10 APU?

how about changing something in aticonfig. : [http://devgurus.amd.com/thread/159201](http://devgurus.amd.com/thread/159201)

---

### Post by YxF4zb3 on 2013-08-16
I'm not 100% sure. That benchmarking suite is quite advanced, I took a look at the "gpu-test" or something of the sort, but it didn't reveal much. This is the AMD A10-4600M APU.

It looked to me like that thread you posted was a dual graphics card setup. I only have one integrated graphics card, I don't believe I can do those steps on the thread.
Here's the laptop I'm using: [COLOR=#000000][FONT=helvetica]http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03610937&lc=en

EDIT: It seems none of the memory shown is dedicated,
[/FONT][/COLOR]> The AMD Radeon HD 7660G or HD7660G is a processor graphics card in the Trinity APUs from AMD. It is the fastest version and is featured only in the A10 series. It is based on the VLIW4 architecture of the Radeon HD 6900 desktop series and doesn't offer a dedicated graphics memory.

So, If that's the case, how come windows is able to access a whopping 3GB, Ubuntu a mere 512MB.

---

