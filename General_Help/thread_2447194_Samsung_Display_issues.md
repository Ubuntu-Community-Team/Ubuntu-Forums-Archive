---
title: "Samsung Display issues"
date: 2020-07-14
forum: General Help
---

### Post by swifty-the-kid on 2020-07-14
I have a remote computer running 16.04 we've had running as a media display for some time now. I can currently get access to it and confirm it detects the screen and is outputting, but the display has stopped picking up any output. This appears to be an ongoing issue with Samsung displays specifically. 

Output from lshw -c display: 
```
*-display       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915_bpo latency=0
       resources: irq:137 memory:de000000-deffffff memory:c0000000-cfffffff ioport:f000(size=64)
```

Output from sudo get-edid | edid-decode: 
```
This is read edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 2
No EDID on bus 3
1 potential buses found: 1
256-byte EDID successfully retrieved from i2c bus 1
Looks like i2c was successful. Have a good day. 
Extracted contents:
header:          00 ff ff ff ff ff ff 00
serial number:   4c 2d 96 0b 01 00 00 00 02 18
version:         01 03
basic params:    80 79 44 78 0a
chroma info:     ee 9d a3 54 47 99 26 0f 47 4a
established:     bd ef 80
standard:        71 4f 81 c0 81 00 81 80 95 00 a9 c0 b3 00 01 01
descriptor 1:    02 3a 80 18 71 38 2d 40 58 2c 45 00 75 f2 31 00 00 1e
descriptor 2:    66 21 56 aa 51 00 1e 30 46 8f 33 00 75 f2 31 00 00 1e
descriptor 3:    00 00 00 fd 00 18 4b 1a 51 11 00 0a 20 20 20 20 20 20
descriptor 4:    00 00 00 fc 00 53 79 6e 63 4d 61 73 74 65 72 0a 20 20
extensions:      01
checksum:        41


Manufacturer: SAM Model b96 Serial Number 1
Made week 2 of 2014
EDID version: 1.3
Digital display
Maximum image size: 121 cm x 68 cm
Gamma: 2.20
Supported color formats: RGB 4:4:4, YCrCb 4:2:2
First detailed timing is preferred timing
Established timings supported:
  720x400@70Hz
  640x480@60Hz
  640x480@67Hz
  640x480@72Hz
  640x480@75Hz
  800x600@60Hz
  800x600@72Hz
  800x600@75Hz
  832x624@75Hz
  1024x768@60Hz
  1024x768@70Hz
  1024x768@75Hz
  1280x1024@75Hz
  1152x870@75Hz
Standard timings supported:
  1152x864@75Hz
  1280x720@60Hz
  1280x800@60Hz
  1280x1024@60Hz
  1440x900@60Hz
  1600x900@60Hz
  1680x1050@60Hz
Detailed mode: Clock 148.500 MHz, 885 mm x 498 mm
               1920 2008 2052 2200 hborder 0
               1080 1084 1089 1125 vborder 0
               +hsync +vsync 
Detailed mode: Clock 85.500 MHz, 885 mm x 498 mm
               1366 1436 1579 1792 hborder 0
                768  771  774  798 vborder 0
               +hsync +vsync 
Monitor ranges (GTF): 24-75Hz V, 26-81kHz H, max dotclock 170MHz
Monitor name: SyncMaster
Has 1 extension blocks
Checksum: 0x41 (valid)


CEA extension block
Extension version: 3
34 bytes of CEA data
  Video data block
    VIC 16 1920x1080@60Hz (native)
    VIC 31 1920x1080@50Hz 
    VIC 04 1280x720@60Hz 
    VIC 19 1280x720@50Hz 
    VIC 05 1920x1080i@60Hz 
    VIC 20 1920x1080i@50Hz 
    VIC 03 720x480@60Hz 
    VIC 18 720x576@50Hz 
    VIC 32 1920x1080@24Hz 
    VIC 33 1920x1080@25Hz 
    VIC 34 1920x1080@30Hz 
  Audio data block
    Linear PCM, max channels 1
    Supported sample rates (kHz): 48 44.1 32
    Supported sample sizes (bits): 24 20 16
  Speaker allocation data block
  Extended tag: video capability data block
    YCbCr quantization: No Data (0)
    RGB quantization: No Data (0)
    PT scan behaviour: No Data (0)
    IT scan behaviour: Support both over- and underscan (3)
    CE scan behaviour: Support both over- and underscan (3)
  Extended tag: Colorimetry data block
  Vendor-specific data block, OUI 000c03 (HDMI)
    Source physical address 1.0.0.0
    Supports_AI
Underscans PC formats by default
Basic audio support
Supports YCbCr 4:4:4
Supports YCbCr 4:2:2
1 native detailed modes
Detailed mode: Clock 148.500 MHz, 885 mm x 498 mm
               1920 2448 2492 2640 hborder 0
               1080 1084 1089 1125 vborder 0
               +hsync +vsync 
Detailed mode: Clock 74.250 MHz, 885 mm x 498 mm
               1280 1390 1430 1650 hborder 0
                720  725  730  750 vborder 0
               +hsync +vsync 
Detailed mode: Clock 74.250 MHz, 885 mm x 498 mm
               1280 1720 1760 1980 hborder 0
                720  725  730  750 vborder 0
               +hsync +vsync 
Detailed mode: Clock 27.000 MHz, 885 mm x 498 mm
                720  736  798  858 hborder 0
                480  489  495  525 vborder 0
               -hsync -vsync 
Checksum: 0x92 (valid)



```

I'm not seeing anything obvious (to me) in these outputs, am I missing something that may explain why the display isn't accepting output from my computer?

---

### Post by swifty-the-kid on 2020-07-15
Closing the thread, turns out the device was outputting as expected all along, and the display settings had been dimmed to the point where they could not confirm the playback was working. Apologies for any wasted time

---

