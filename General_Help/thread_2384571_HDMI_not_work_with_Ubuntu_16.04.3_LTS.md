---
title: "HDMI not work with Ubuntu 16.04.3 LTS"
date: 2018-02-08
forum: General Help
---

### Post by alaasamameer on 2018-02-08
Hello
I tried to make HDMI working on my Ubuntu laptop,but it doesn't, 
note that it works when my laptop was Windows.
please provide me with step by step solution
please, below find my system information

lsb_release -a
```

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

```

inxi -MCG
```

Machine:   System: LENOVO (portable) product: 20405 v: Lenovo Flex 2-15
           Mobo: LENOVO model: Lenovo Flex 2-15 Bios: LENOVO v: A0CN21WW date: 03/21/2014
CPU:       Dual core Intel Core i5-4210U (-HT-MCP-) cache: 3072 KB 
           clock speeds: max: 2700 MHz 1: 2578 MHz 2: 2427 MHz 3: 2239 MHz 4: 1244 MHz
Graphics:  Card-1: Intel Haswell-ULT Integrated Graphics Controller
           Card-2: NVIDIA GM108M [GeForce 840M]
           Display Server: X.Org 1.19.5 driver: nvidia Resolution: 1920x1080@60.02hz
           GLX Renderer: GeForce 840M/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 384.111

```

xrandr --prop
```

Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
eDP-1-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
    EDID: 
        00ffffffffffff0030e44f0400000000
        0018010495231378ea0cf5a05b559226
        0c505400000001010101010101010101
        0101010101012e3680a070381f403020
        350059c2100000190000000000000000
        00000000000000000000000000fe004c
        4720446973706c61790a2020000000fe
        004c503135365746342d53504c310013
    PRIME Synchronization: 0 
        supported: 0, 1
    scaling mode: Full aspect 
        supported: None, Full, Center, Full aspect
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on
   1920x1080     60.02*+  59.93  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
HDMI-1-1 disconnected (normal left inverted right x axis y axis)
    PRIME Synchronization: 1 
        supported: 0, 1
    aspect ratio: Automatic 
        supported: Automatic, 4:3, 16:9
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on

```

---

