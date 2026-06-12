---
title: "asus x540sa hdmi output port"
date: 2020-06-05
forum: General Help
---

### Post by tendouser on 2020-06-05
How do I activate my hdmi output port in 20.04?

lg monitor wfhd 34bk650

Already checked in software+updates but no drivers listed there.

     *-display
                 description: VGA compatible controller
                 product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller
                 vendor: Intel Corporation
                 physical id: 2
                 bus info: pci@0000:00:02.0
                 version: 21
                 width: 64 bits
                 clock: 33MHz
                 capabilities: vga_controller bus_master cap_list rom
                 configuration: driver=i915 latency=0
                 resources: irq:126 memory:80000000-80ffffff memory:90000000-9fffffff ioport:f000(size=64) memory:c0000-dffff

---

### Post by DuckHook on 2020-06-06
How do you hook up your monitor? Is it directly from HDMI port to HDMI port? No intervening KVM switch? If so, then in almost all cases, your system should simply recognize it. The only problems tend to come from bad cables or an old video system that is too primitive to support HDMI.

The specs you list show that you have yours plugged into the VGA port. Obviously, you must plug into your GPU's HDMI port to get HDMI output.

---

### Post by tendouser on 2020-06-06
well is not connected to vga.... is from hdmi to hdmi.... what i think i need to find out is how to activate that port because i apparently is no detecting any signal.... i was reading that in windows there is a special driver to be install.... could that be the case????

---

### Post by DuckHook on 2020-06-07
> **tendouser said:**
> …what i think i need to find out is how to activate that port because i apparently is no detecting any signal…
What makes you think the port is not active? Or that there is no signal?
> …i was reading that in windows there is a special driver to be install.... could that be the case????
In Linux, for your type of GPU, the driver is already part of the kernel. On Intel GPUs, there is no external driver that needs to be installed.

Please post results of:
```
xrandr --verbose
```
```
sudo lspci -vk | grep -iA15 vga
```
```
sudo lshw
```
Output will be extensive so please post it between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

Some things to double&#8209;check:

[list=1]
[*]Monitor has proper settings (is expecting signal from proper HDMI port).
[*]Cable is a high quality cable. Does it work in Windows?
[*]System BIOS is outputting to HDMI (it isn't turned off).
[*]Is HDMI usable on a LiveUSB?
[/list]

---

### Post by tendouser on 2020-06-08
#

---

### Post by tendouser on 2020-06-08
1)Monitor has proper settings (is expecting signal from proper HDMI  port)== yes i pick the proper hdmi port in monitor using the joystick  button

2)Cable is a high quality cable==not sure if it is a high quality cable

3)Does it work in Windows==not with my win10 in my asus but my job mini-pc is working fine (win10 too)

4)System BIOS is outputting to HDMI (it isn't turned off)==no BIOS setting for HDMI

5)Is HDMI usable on a LiveUSB==not tried yet any liveusb

####################################################################

```
xrandr --verbose
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 16384 x 16384
eDP-1 connected primary 1366x768+0+0 (0x48) normal (normal left inverted right x axis y axis) 344mm x 193mm
    Identifier: 0x42
    Timestamp:  39948
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID: 
        00ffffffffffff000daeca1500000000
        221801049522137802c3c59155549428
        24505400000001010101010101010101
        010101010101da1d56e250002030442d
        470058c110000018000000fe004e3135
        364247452d4534320a20000000fe0043
        4d4e0a202020202020202020000000fe
        004e3135364247452d4534320a200055
    scaling mode: Full aspect 
        supported: Full, Full aspect
    max bpc: 10 
        range: (6, 10)
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on
    link-status: Good 
        supported: Good, Bad
    CONNECTOR_ID: 93 
        supported: 93
    non-desktop: 0 
        range: (0, 1)
  1366x768 (0x48) 76.420MHz -HSync -VSync *current +preferred
        h: width  1366 start 1434 end 1479 total 1592 skew    0 clock  48.00KHz
        v: height  768 start  772 end  779 total  800           clock  60.00Hz
  1360x768 (0x49) 84.750MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock  47.72KHz
        v: height  768 start  771 end  781 total  798           clock  59.80Hz
  1360x768 (0x4a) 72.000MHz +HSync -VSync
        h: width  1360 start 1408 end 1440 total 1520 skew    0 clock  47.37KHz
        v: height  768 start  771 end  781 total  790           clock  59.96Hz
  1280x720 (0x4b) 156.125MHz -HSync +VSync DoubleScan
        h: width  1280 start 1376 end 1512 total 1744 skew    0 clock  89.52KHz
        v: height  720 start  721 end  724 total  746           clock  60.00Hz
  1280x720 (0x4c) 120.750MHz +HSync -VSync DoubleScan
        h: width  1280 start 1304 end 1320 total 1360 skew    0 clock  88.79KHz
        v: height  720 start  721 end  724 total  740           clock  59.99Hz
  1280x720 (0x4d) 74.500MHz -HSync +VSync
        h: width  1280 start 1344 end 1472 total 1664 skew    0 clock  44.77KHz
        v: height  720 start  723 end  728 total  748           clock  59.86Hz
  1280x720 (0x4e) 63.750MHz +HSync -VSync
        h: width  1280 start 1328 end 1360 total 1440 skew    0 clock  44.27KHz
        v: height  720 start  723 end  728 total  741           clock  59.74Hz
  1024x768 (0x4f) 133.475MHz -HSync +VSync DoubleScan
        h: width  1024 start 1100 end 1212 total 1400 skew    0 clock  95.34KHz
        v: height  768 start  768 end  770 total  794           clock  60.04Hz
  1024x768 (0x50) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  960x720 (0x51) 117.000MHz -HSync +VSync DoubleScan
        h: width   960 start 1024 end 1128 total 1300 skew    0 clock  90.00KHz
        v: height  720 start  720 end  722 total  750           clock  60.00Hz
  928x696 (0x52) 109.150MHz -HSync +VSync DoubleScan
        h: width   928 start  976 end 1088 total 1264 skew    0 clock  86.35KHz
        v: height  696 start  696 end  698 total  719           clock  60.05Hz
  896x672 (0x53) 102.400MHz -HSync +VSync DoubleScan
        h: width   896 start  960 end 1060 total 1224 skew    0 clock  83.66KHz
        v: height  672 start  672 end  674 total  697           clock  60.01Hz
  1024x576 (0x54) 98.500MHz -HSync +VSync DoubleScan
        h: width  1024 start 1092 end 1200 total 1376 skew    0 clock  71.58KHz
        v: height  576 start  577 end  580 total  597           clock  59.95Hz
  1024x576 (0x55) 78.375MHz +HSync -VSync DoubleScan
        h: width  1024 start 1048 end 1064 total 1104 skew    0 clock  70.99KHz
        v: height  576 start  577 end  580 total  592           clock  59.96Hz
  1024x576 (0x56) 46.500MHz -HSync +VSync
        h: width  1024 start 1064 end 1160 total 1296 skew    0 clock  35.88KHz
        v: height  576 start  579 end  584 total  599           clock  59.90Hz
  1024x576 (0x57) 42.000MHz +HSync -VSync
        h: width  1024 start 1072 end 1104 total 1184 skew    0 clock  35.47KHz
        v: height  576 start  579 end  584 total  593           clock  59.82Hz
  960x600 (0x58) 96.625MHz -HSync +VSync DoubleScan
        h: width   960 start 1028 end 1128 total 1296 skew    0 clock  74.56KHz
        v: height  600 start  601 end  604 total  622           clock  59.93Hz
  960x600 (0x59) 77.000MHz +HSync -VSync DoubleScan
        h: width   960 start  984 end 1000 total 1040 skew    0 clock  74.04KHz
        v: height  600 start  601 end  604 total  617           clock  60.00Hz
  960x540 (0x5a) 86.500MHz -HSync +VSync DoubleScan
        h: width   960 start 1024 end 1124 total 1288 skew    0 clock  67.16KHz
        v: height  540 start  541 end  544 total  560           clock  59.96Hz
  960x540 (0x5b) 69.250MHz +HSync -VSync DoubleScan
        h: width   960 start  984 end 1000 total 1040 skew    0 clock  66.59KHz
        v: height  540 start  541 end  544 total  555           clock  59.99Hz
  960x540 (0x5c) 40.750MHz -HSync +VSync
        h: width   960 start  992 end 1088 total 1216 skew    0 clock  33.51KHz
        v: height  540 start  543 end  548 total  562           clock  59.63Hz
  960x540 (0x5d) 37.250MHz +HSync -VSync
        h: width   960 start 1008 end 1040 total 1120 skew    0 clock  33.26KHz
        v: height  540 start  543 end  548 total  556           clock  59.82Hz
  800x600 (0x5e) 81.000MHz +HSync +VSync DoubleScan
        h: width   800 start  832 end  928 total 1080 skew    0 clock  75.00KHz
        v: height  600 start  600 end  602 total  625           clock  60.00Hz
  800x600 (0x5f) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x60) 36.000MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  840x525 (0x61) 73.125MHz -HSync +VSync DoubleScan
        h: width   840 start  892 end  980 total 1120 skew    0 clock  65.29KHz
        v: height  525 start  526 end  529 total  544           clock  60.01Hz
  840x525 (0x62) 59.500MHz +HSync -VSync DoubleScan
        h: width   840 start  864 end  880 total  920 skew    0 clock  64.67KHz
        v: height  525 start  526 end  529 total  540           clock  59.88Hz
  864x486 (0x63) 32.500MHz -HSync +VSync
        h: width   864 start  888 end  968 total 1072 skew    0 clock  30.32KHz
        v: height  486 start  489 end  494 total  506           clock  59.92Hz
  864x486 (0x64) 30.500MHz +HSync -VSync
        h: width   864 start  912 end  944 total 1024 skew    0 clock  29.79KHz
        v: height  486 start  489 end  494 total  500           clock  59.57Hz
  800x512 (0x65) 51.562MHz +HSync +VSync DoubleScan
        h: width   800 start  800 end  828 total  832 skew    0 clock  61.97KHz
        v: height  512 start  512 end  514 total  515           clock  60.17Hz
  700x525 (0x66) 61.000MHz +HSync +VSync DoubleScan
        h: width   700 start  744 end  820 total  940 skew    0 clock  64.89KHz
        v: height  525 start  526 end  532 total  541           clock  59.98Hz
  800x450 (0x67) 59.125MHz -HSync +VSync DoubleScan
        h: width   800 start  848 end  928 total 1056 skew    0 clock  55.99KHz
        v: height  450 start  451 end  454 total  467           clock  59.95Hz
  800x450 (0x68) 48.750MHz +HSync -VSync DoubleScan
        h: width   800 start  824 end  840 total  880 skew    0 clock  55.40KHz
        v: height  450 start  451 end  454 total  463           clock  59.82Hz
  640x512 (0x69) 54.000MHz +HSync +VSync DoubleScan
        h: width   640 start  664 end  720 total  844 skew    0 clock  63.98KHz
        v: height  512 start  512 end  514 total  533           clock  60.02Hz
  720x450 (0x6a) 53.250MHz -HSync +VSync DoubleScan
        h: width   720 start  760 end  836 total  952 skew    0 clock  55.93KHz
        v: height  450 start  451 end  454 total  467           clock  59.89Hz
  700x450 (0x6b) 51.750MHz -HSync +VSync DoubleScan
        h: width   700 start  740 end  812 total  924 skew    0 clock  56.01KHz
        v: height  450 start  451 end  456 total  467           clock  59.96Hz
  700x450 (0x6c) 43.250MHz +HSync -VSync DoubleScan
        h: width   700 start  724 end  740 total  780 skew    0 clock  55.45KHz
        v: height  450 start  451 end  456 total  463           clock  59.88Hz
  640x480 (0x6d) 54.000MHz +HSync +VSync DoubleScan
        h: width   640 start  688 end  744 total  900 skew    0 clock  60.00KHz
        v: height  480 start  480 end  482 total  500           clock  60.00Hz
  640x480 (0x6e) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
  720x405 (0x6f) 22.500MHz -HSync +VSync
        h: width   720 start  744 end  808 total  896 skew    0 clock  25.11KHz
        v: height  405 start  408 end  413 total  422           clock  59.51Hz
  720x405 (0x70) 21.750MHz +HSync -VSync
        h: width   720 start  768 end  800 total  880 skew    0 clock  24.72KHz
        v: height  405 start  408 end  413 total  419           clock  58.99Hz
  684x384 (0x71) 42.625MHz -HSync +VSync DoubleScan
        h: width   684 start  720 end  788 total  892 skew    0 clock  47.79KHz
        v: height  384 start  385 end  390 total  399           clock  59.88Hz
  684x384 (0x72) 36.125MHz +HSync -VSync DoubleScan
        h: width   684 start  708 end  724 total  764 skew    0 clock  47.28KHz
        v: height  384 start  385 end  390 total  395           clock  59.85Hz
  680x384 (0x73) 42.375MHz -HSync +VSync DoubleScan
        h: width   680 start  716 end  784 total  888 skew    0 clock  47.72KHz
        v: height  384 start  385 end  390 total  399           clock  59.80Hz
  680x384 (0x74) 36.000MHz +HSync -VSync DoubleScan
        h: width   680 start  704 end  720 total  760 skew    0 clock  47.37KHz
        v: height  384 start  385 end  390 total  395           clock  59.96Hz
  640x400 (0x75) 41.750MHz -HSync +VSync DoubleScan
        h: width   640 start  676 end  740 total  840 skew    0 clock  49.70KHz
        v: height  400 start  401 end  404 total  415           clock  59.88Hz
  640x400 (0x76) 35.500MHz +HSync -VSync DoubleScan
        h: width   640 start  664 end  680 total  720 skew    0 clock  49.31KHz
        v: height  400 start  401 end  404 total  411           clock  59.98Hz
  576x432 (0x77) 40.810MHz -HSync +VSync DoubleScan
        h: width   576 start  608 end  668 total  760 skew    0 clock  53.70KHz
        v: height  432 start  432 end  434 total  447           clock  60.06Hz
  640x360 (0x78) 37.250MHz -HSync +VSync DoubleScan
        h: width   640 start  672 end  736 total  832 skew    0 clock  44.77KHz
        v: height  360 start  361 end  364 total  374           clock  59.86Hz
  640x360 (0x79) 31.875MHz +HSync -VSync DoubleScan
        h: width   640 start  664 end  680 total  720 skew    0 clock  44.27KHz
        v: height  360 start  361 end  364 total  370           clock  59.83Hz
  640x360 (0x7a) 18.000MHz -HSync +VSync
        h: width   640 start  664 end  720 total  800 skew    0 clock  22.50KHz
        v: height  360 start  363 end  368 total  376           clock  59.84Hz
  640x360 (0x7b) 17.750MHz +HSync -VSync
        h: width   640 start  688 end  720 total  800 skew    0 clock  22.19KHz
        v: height  360 start  363 end  368 total  374           clock  59.32Hz
  512x384 (0x7c) 32.500MHz -HSync -VSync DoubleScan
        h: width   512 start  524 end  592 total  672 skew    0 clock  48.36KHz
        v: height  384 start  385 end  388 total  403           clock  60.00Hz
  512x288 (0x7d) 23.250MHz -HSync +VSync DoubleScan
        h: width   512 start  532 end  580 total  648 skew    0 clock  35.88KHz
        v: height  288 start  289 end  292 total  299           clock  60.00Hz
  512x288 (0x7e) 21.000MHz +HSync -VSync DoubleScan
        h: width   512 start  536 end  552 total  592 skew    0 clock  35.47KHz
        v: height  288 start  289 end  292 total  296           clock  59.92Hz
  480x270 (0x7f) 20.375MHz -HSync +VSync DoubleScan
        h: width   480 start  496 end  544 total  608 skew    0 clock  33.51KHz
        v: height  270 start  271 end  274 total  281           clock  59.63Hz
  480x270 (0x80) 18.625MHz +HSync -VSync DoubleScan
        h: width   480 start  504 end  520 total  560 skew    0 clock  33.26KHz
        v: height  270 start  271 end  274 total  278           clock  59.82Hz
  400x300 (0x81) 20.000MHz +HSync +VSync DoubleScan
        h: width   400 start  420 end  484 total  528 skew    0 clock  37.88KHz
        v: height  300 start  300 end  302 total  314           clock  60.32Hz
  400x300 (0x82) 18.000MHz +HSync +VSync DoubleScan
        h: width   400 start  412 end  448 total  512 skew    0 clock  35.16KHz
        v: height  300 start  300 end  301 total  312           clock  56.34Hz
  432x243 (0x83) 16.250MHz -HSync +VSync DoubleScan
        h: width   432 start  444 end  484 total  536 skew    0 clock  30.32KHz
        v: height  243 start  244 end  247 total  253           clock  59.92Hz
  432x243 (0x84) 15.250MHz +HSync -VSync DoubleScan
        h: width   432 start  456 end  472 total  512 skew    0 clock  29.79KHz
        v: height  243 start  244 end  247 total  250           clock  59.57Hz
  320x240 (0x85) 12.587MHz -HSync -VSync DoubleScan
        h: width   320 start  328 end  376 total  400 skew    0 clock  31.47KHz
        v: height  240 start  245 end  246 total  262           clock  60.05Hz
  360x202 (0x86) 11.250MHz -HSync +VSync DoubleScan
        h: width   360 start  372 end  404 total  448 skew    0 clock  25.11KHz
        v: height  202 start  204 end  206 total  211           clock  59.51Hz
  360x202 (0x87) 10.875MHz +HSync -VSync DoubleScan
        h: width   360 start  384 end  400 total  440 skew    0 clock  24.72KHz
        v: height  202 start  204 end  206 total  209           clock  59.13Hz
  320x180 (0x88)  9.000MHz -HSync +VSync DoubleScan
        h: width   320 start  332 end  360 total  400 skew    0 clock  22.50KHz
        v: height  180 start  181 end  184 total  188           clock  59.84Hz
  320x180 (0x89)  8.875MHz +HSync -VSync DoubleScan
        h: width   320 start  344 end  360 total  400 skew    0 clock  22.19KHz
        v: height  180 start  181 end  184 total  187           clock  59.32Hz
DP-1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x43
    Timestamp:  39948
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    max bpc: 10 
        range: (6, 10)
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on
    link-status: Good 
        supported: Good, Bad
    CONNECTOR_ID: 83 
        supported: 83
    non-desktop: 0 
        range: (0, 1)
HDMI-1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x44
    Timestamp:  39948
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    content type: No Data 
        supported: No Data, Graphics, Photo, Cinema, Game
    Colorspace: Default 
         supported: Default, SMPTE_170M_YCC, BT709_YCC, XVYCC_601,  XVYCC_709, SYCC_601, opYCC_601, opRGB, BT2020_CYCC, BT2020_RGB,  BT2020_YCC, DCI-P3_RGB_D65, DCI-P3_RGB_Theater
    aspect ratio: Automatic 
        supported: Automatic, 4:3, 16:9
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on
    link-status: Good 
        supported: Good, Bad
    CONNECTOR_ID: 88 
        supported: 88
    non-desktop: 0 
        range: (0, 1)
DP-2 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x45
    Timestamp:  39948
    Subpixel:   unknown
    Clones:    
    CRTCs:      2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    max bpc: 10 
        range: (6, 10)
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on
    link-status: Good 
        supported: Good, Bad
    CONNECTOR_ID: 98 
        supported: 98
    non-desktop: 0 
        range: (0, 1)
HDMI-2 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x46
    Timestamp:  39948
    Subpixel:   unknown
    Clones:    
    CRTCs:      2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    content type: No Data 
        supported: No Data, Graphics, Photo, Cinema, Game
    Colorspace: Default 
         supported: Default, SMPTE_170M_YCC, BT709_YCC, XVYCC_601,  XVYCC_709, SYCC_601, opYCC_601, opRGB, BT2020_CYCC, BT2020_RGB,  BT2020_YCC, DCI-P3_RGB_D65, DCI-P3_RGB_Theater
    aspect ratio: Automatic 
        supported: Automatic, 4:3, 16:9
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on
    link-status: Good 
        supported: Good, Bad
    CONNECTOR_ID: 101 
        supported: 101
    non-desktop: 0 
        range: (0, 1)

####################################################################
```

```
sudo lspci -vk | grep -iA15 vga
[sudo] password for user: 
00:02.0  VGA compatible controller: Intel Corporation Atom/Celeron/Pentium  Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller (rev 21)  (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller
    Flags: bus master, fast devsel, latency 0, IRQ 126
    Memory at 80000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 90000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
    Capabilities: [d0] Power Management version 2
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Vendor Specific Information: Len=07 <?>
    Kernel driver in use: i915
    Kernel modules: i915

00:0b.0  Signal processing controller: Intel Corporation Atom/Celeron/Pentium  Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller (rev  21)
    Subsystem: ASUSTeK Computer Inc. Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller
    Flags: bus master, fast devsel, latency 0, IRQ 124

####################################################################

```
```
sudo lshw
user-x540sa                 
    description: Notebook
    product: X540SA (ASUS-NotebookSKU)
    vendor: ASUSTeK COMPUTER INC.
    version: 1.0
    serial: G1N0GR02P71902A
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 smp vsyscall32
    configuration: boot=normal chassis=notebook family=X sku=ASUS-NotebookSKU uuid=62FE4629-8B13-4CB2-9F80-53F7248FF85B
  *-core
       description: Motherboard
       product: X540SA
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: X540SA.304
          date: 01/20/2017
          size: 64KiB
          capacity: 6MiB
           capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd  int13floppy1200 int13floppy720 int13floppy2880 int5printscreen  int9keyboard int14serial int17printer acpi usb smartbattery  biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR3 1600 MHz (0.6 ns)
             product: HMT451S6CFR6A-PB
             vendor: Hynix Semiconduc
             physical id: 0
             serial: 00000000
             slot: A1_DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM [empty]
             product: Array1_PartNumber1
             vendor: A1_Manufacturer1
             physical id: 1
             serial: A1_SerNum1
             slot: A1_DIMM1
     *-cache:0
          description: L1 cache
          physical id: 11
          slot: CPU Internal L1
          size: 112KiB
          capacity: 112KiB
          capabilities: internal write-back
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 12
          slot: CPU Internal L2
          size: 2MiB
          capacity: 2MiB
          capabilities: internal write-back unified
          configuration: level=2
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU  N3050  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 13
          bus info: cpu@0
          version: Intel(R) Celeron(R) CPU N3050 @ 1.60GHz
          slot: SOCKET 0
          size: 926MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 80MHz
           capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8  apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2  ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts  rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid aperfmperf  tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3  cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes rdrand  lahf_lm 3dnowprefetch epb pti ibrs ibpb stibp tpr_shadow vnmi  flexpriority ept vpid tsc_adjust smep erms dtherm ida arat md_clear  cpufreq
          configuration: cores=2 enabledcores=2 threads=2
     *-pci
          description: Host bridge
          product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 21
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:126 memory:80000000-80ffffff memory:90000000-9fffffff ioport:f000(size=64) memory:c0000-dffff
        *-generic:0
             description: Signal processing controller
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller
             vendor: Intel Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:124 memory:81421000-81421fff
        *-sata
             description: SATA controller
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SATA Controller
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             logical name: scsi0
             logical name: scsi1
             version: 21
             width: 32 bits
             clock: 66MHz
             capabilities: sata msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:120 ioport:f060(size=32) memory:8141e000-8141e7ff
           *-disk
                description: ATA Disk
                product: ST500LT012-1DG14
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SDM1
                serial: SBY3F5Z8
                size: 465GiB (500GB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: ansiversion=5 guid=c8745393-564a-4fe5-af66-fedd73af9759 logicalsectorsize=512 sectorsize=4096
              *-volume:0 UNCLAIMED
                   description: Windows FAT volume
                   vendor: MSDOS5.0
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   version: FAT32
                   serial: 2802-a880
                   size: 255MiB
                   capacity: 259MiB
                   capabilities: boot fat initialized
                   configuration: FATs=2 filesystem=fat label=SYSTEM name=EFI system partition
              *-volume:1
                   description: reserved partition
                   vendor: Windows
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   serial: 1b1110a3-c044-4047-90d1-f0cbab0a1941
                   capacity: 15MiB
                   capabilities: nofs
                   configuration: name=Microsoft reserved partition
              *-volume:2
                   description: Windows NTFS volume
                   vendor: Windows
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 5a28a834-610f-dc49-9029-835550fc8e76
                   size: 240GiB
                   capacity: 240GiB
                   capabilities: ntfs initialized
                    configuration: clustersize=4096 created=2016-01-15 04:13:37  filesystem=ntfs label=OS name=Basic data partition state=clean
              *-volume:3
                   description: Windows NTFS volume
                   vendor: Windows
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   version: 3.1
                   serial: 2cd2-a5a1
                   size: 473MiB
                   capacity: 498MiB
                   capabilities: boot precious ntfs initialized
                    configuration: clustersize=4096 created=2019-09-04 23:10:16  filesystem=ntfs name=Basic data partition state=clean
              *-volume:4
                   description: Linux swap volume
                   vendor: Linux
                   physical id: 5
                   bus info: scsi@0:0.0.0,5
                   logical name: /dev/sda5
                   version: 1
                   serial: 5ce80477-93c6-404f-acae-f29a6d8c6678
                   size: 3814MiB
                   capacity: 3814MiB
                   capabilities: nofs swap initialized
                   configuration: filesystem=swap pagesize=4095
              *-volume:5
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 6
                   bus info: scsi@0:0.0.0,6
                   logical name: /dev/sda6
                   logical name: /
                   version: 1.0
                   serial: 0d365288-3db1-44f3-aa60-33c5eedf4e3f
                   size: 186GiB
                    capabilities: journaled extended_attributes large_files huge_files  dir_nlink recover 64bit extents ext4 ext2 initialized
                    configuration: created=2019-06-23 10:02:40 filesystem=ext4  lastmountpoint=/ modified=2020-06-08 15:57:37 mount.fstype=ext4  mount.options=rw,relatime,errors=remount-ro mounted=2020-06-08 15:57:43  state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GUE1N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: AS00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb
             description: USB controller
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:118 memory:81400000-8140ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.4.0-33-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.04
                capabilities: usb-2.00
                configuration: driver=hub slots=7 speed=480Mbit/s
              *-usb:0
                   description: Keyboard
                   product: ActiveJet K-2024 Multimedia Keyboard
                   vendor: Elan Microelectronics Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.07
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
              *-usb:1
                   description: Mouse
                   product: Wireless Mouse
                   vendor: KYE
                   physical id: 2
                   bus info: usb@1:2
                   version: 0.01
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=2Mbit/s
              *-usb:2
                   description: Bluetooth wireless interface
                   product: Bluetooth Radio
                   vendor: Realtek
                   physical id: 3
                   bus info: usb@1:3
                   version: 2.00
                   serial: 00e04c000001
                   capabilities: bluetooth usb-2.10
                   configuration: driver=btusb maxpower=500mA speed=12Mbit/s
              *-usb:3
                   description: Video
                   product: USB2.0 VGA UVC WebCam
                   vendor: Chicony Electronics Co.,Ltd.
                   physical id: 4
                   bus info: usb@1:4
                   version: 95.52
                   serial: 0x0001
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.4.0-33-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.04
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
        *-generic:1
             description: Encryption controller
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:125 memory:81100000-811fffff memory:81000000-810fffff
        *-multimedia
             description: Audio device
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:127 memory:81410000-81413fff
        *-pci:0
             description: PCI bridge
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:115 ioport:1000(size=4096) memory:81500000-816fffff ioport:81700000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:116 ioport:e000(size=4096) memory:81300000-813fffff ioport:a0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL810xE PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0
                version: 07
                serial: 9c:5c:8e:d5:5a:98
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                 capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet  physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                 configuration: autonegotiation=on broadcast=yes driver=r8169  firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes  port=MII
                resources: irq:18 ioport:e000(size=256) memory:81300000-81300fff memory:a0000000-a0003fff
        *-pci:2
             description: PCI bridge
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:117 ioport:d000(size=4096) memory:81200000-812fffff
           *-network
                description: Wireless interface
                product: RTL8723BE PCIe Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 00
                serial: c8:ff:28:af:38:cd
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                 configuration: broadcast=yes driver=rtl8723be  driverversion=5.4.0-33-generic firmware=N/A ip=192.168.0.9 latency=0  link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:19 ioport:d000(size=256) memory:81200000-81203fff
        *-isa
             description: ISA bridge
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-serial
             description: SMBus
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=i801_smbus latency=0
             resources: irq:18 memory:81418000-8141801f ioport:f040(size=32)
     *-pnp00:00
          product: PnP device PNP0b00
          physical id: 1
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:01
          product: PnP device PNP0c02
          physical id: 2
          capabilities: pnp
          configuration: driver=system
     *-pnp00:02
          product: PnP device PNP0c02
          physical id: 3
          capabilities: pnp
          configuration: driver=system
     *-pnp00:03
          product: PnP device ATK3001
          physical id: 4
          capabilities: pnp
          configuration: driver=i8042 kbd
     *-pnp00:04
          product: PnP device PNP0c02
          physical id: 5
          capabilities: pnp
          configuration: driver=system
     *-pnp00:05
          product: PnP device PNP0c02
          physical id: 6
          capabilities: pnp
          configuration: driver=system
```

---

### Post by DuckHook on 2020-06-08
I have already edited your post so that it is readable, but remember to post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by tendouser on 2020-06-08
i did but was prompted with a error when tried to save!

---

### Post by DuckHook on 2020-06-09
> **tendouser said:**
> …3)Does it work in Windows==not with my win10 in my asus…
In other words, you get no output in either Ubuntu or Windows on the problem machine.

Let's start with the simplest attempt. With the HDMI cable connected to laptop and monitor, open a terminal and type: ```
xrandr --output HDMI-1 --auto
```
If this works, then you must have a LiveUSB for the next steps, but let's try the above first.

---

### Post by tendouser on 2020-06-09
not even a single output on that xrandr command fellow!

i did downloaded the latest win10 64 bit driver from asus repository but the issue persist!

even tried the hdmi cable provided with my job mini-pc! 

remember is working on that win10 but not in my asus!

---

### Post by DuckHook on 2020-06-10
The fact that Windows displays no output even with the right driver is not at all promising. Frankly, I'm pessimistic and suspect a dead HDMI subsystem. A hardware issue would be the only reason that neither OS can display.

I'm afraid I'm out of ideas.

---

### Post by CelticWarrior on 2020-06-11
I would start by updating UEFI.

There are some reports of problem with the HDMI output in that family of Asus models. If the problem persists with an updated UEFI then (some users have suggested) to disable the graphics in Windows device manager and re-enable it. If it then starts working in Windows, disable Fast Startup and shutdown Windows before trying to boot Ubuntu.

---

### Post by tendouser on 2020-07-09
solution is a big joke believe or not==alcohol+toothbrush+original-hdmi-cable jajajaja!!!!!!!

cheers guys!!!!!! is working now!!!!!

---

