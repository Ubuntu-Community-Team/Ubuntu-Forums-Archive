---
title: "Command to find maker of monitor"
date: 2018-02-10
forum: General Help
---

### Post by satimis on 2018-02-10
Hi all,

I have a Samsung monitor attached to this PC.  How can I find the maker with command on Terminal?

$ sudo lshw
didn't find it

&#10219; xrandr```

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080     60.00*+  50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1600x1200     60.00  
   1680x1050     59.88  
   1280x1024     60.02  
   1440x900      59.90  
   1280x960      60.00  
   1280x800      59.91  
   1280x720      60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32    56.25  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       60.00    59.94  
DVI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)

```

Please advise.  Thanks

Regards
satimis

---

### Post by #&amp;thj^% on 2018-02-10
> **satimis said:**
> Hi all,

I have a Samsung monitor attached to this PC.  How can I find the maker with command on Terminal?

$ sudo lshw
didn't find it

&#10219; xrandr```

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080     60.00*+  50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1600x1200     60.00  
   1680x1050     59.88  
   1280x1024     60.02  
   1440x900      59.90  
   1280x960      60.00  
   1280x800      59.91  
   1280x720      60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32    56.25  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       60.00    59.94  
DVI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)

```

Please advise.  Thanks

Regards
satimis

See if this meets your needs:>>>  **Nvidia only.**
```
grep "NVIDIA(GPU-0)" /var/log/Xorg.0.log |head -17| cut -d\: -f2
```
Mine:
```
grep "NVIDIA(GPU-0)" /var/log/Xorg.0.log |head -17| cut -d\: -f2
 HP w2338h (CRT-0)
 HP w2338h (CRT-0)
 
 CRT-1
 CRT-1
 
 DFP-0
 DFP-0
 DFP-0
 
 VIZ E260VA (DFP-1)
 VIZ E260VA (DFP-1)
 VIZ E260VA (DFP-1)
 
 DFP-2
 DFP-2
 DFP-2

```
Or you can use hwinfo:
```
sudo apt-get install -y hwinfo
```
Then:
```
hwinfo --monitor --short
```
Mine again:
```
hwinfo --monitor --short
monitor:                                                        
                       HP w2338h
```
Fun Stuff.:)

---

### Post by satimis on 2018-02-10
> **1fallen said:**
> See if this meets your needs:>>>  **Nvidia only.**
```
grep "NVIDIA(GPU-0)" /var/log/Xorg.0.log |head -17| cut -d\: -f2
```
Mine:
```
grep "NVIDIA(GPU-0)" /var/log/Xorg.0.log |head -17| cut -d\: -f2
 HP w2338h (CRT-0)
 HP w2338h (CRT-0)
 
 CRT-1
 CRT-1
 
 DFP-0
 DFP-0
 DFP-0
 
 VIZ E260VA (DFP-1)
 VIZ E260VA (DFP-1)
 VIZ E260VA (DFP-1)
 
 DFP-2
 DFP-2
 DFP-2

```
Or you can use hwinfo:
```
sudo apt-get install -y hwinfo
```
Then:
```
hwinfo --monitor --short
```
Mine again:
```
hwinfo --monitor --short
monitor:                                                        
                       HP w2338h
```
Fun Stuff.:)
&#10219; grep "NVIDIA(GPU-0)" /var/log/Xorg.0.log |head -17| cut -d\: -f2
No printout

&#10219; sudo apt install hwinfo

&#10219; hwinfo --monitor --short```

monitor:                                                        
                       SAMSUNG SyncMaster

```

Thanks

Regards
satimis

---

### Post by #&amp;thj^% on 2018-02-10
> **satimis said:**
> &#10219; grep "NVIDIA(GPU-0)" /var/log/Xorg.0.log |head -17| cut -d\: -f2
No printout

&#10219; sudo apt install hwinfo

&#10219; hwinfo --monitor --short```

monitor:                                                        
                       SAMSUNG SyncMaster

```

Thanks

Regards
satimis

Your Welcome.
You can get even more Information if needed with:
```
hwinfo --monitor 
18: None 00.0: 10002 LCD Monitor                                
  [Created at monitor.125]
  Unique ID: rdCR.uwSPF29WQb1
  Parent ID: _Znp.ErZiNuX2U1C
  Hardware Class: monitor
  Model: "HP w2338h"
  Vendor: HWP "HP"
  Device: eisa 0x281c "HP w2338h"
  Serial ID: "CNCXXXXX" (Sniped by OP)
  Resolution: 720x400@70Hz
  Resolution: 640x480@60Hz
  Resolution: 800x600@60Hz
  Resolution: 832x624@75Hz
  Resolution: 1024x768@60Hz
  Resolution: 1024x768@75Hz
  Resolution: 1280x1024@75Hz
  Resolution: 1280x960@60Hz
  Resolution: 1280x1024@60Hz
  Resolution: 1280x720@60Hz
  Resolution: 1920x1080@60Hz
  Size: 509x286 mm
  Year of Manufacture: 2009
  Week of Manufacture: 31
  Detailed Timings #0:
     Resolution: 1920x1080
     Horizontal: 1920 2008 2052 2200 (+88 +132 +280) +hsync
       Vertical: 1080 1084 1089 1125 (+4 +9 +45) +vsync
    Frequencies: 148.50 MHz, 67.50 kHz, 60.00 Hz
  Driver Info #0:
    Max. Resolution: 1920x1080
    Vert. Sync Range: 48-76 Hz
    Hor. Sync Range: 24-83 kHz
    Bandwidth: 148 MHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #6 (Display controller)

```

---

### Post by satimis on 2018-02-10
> **1fallen said:**
> Your Welcome.
You can get even more Information if needed with:
```
hwinfo --monitor 
18: None 00.0: 10002 LCD Monitor                                
  [Created at monitor.125]
  Unique ID: rdCR.uwSPF29WQb1
  Parent ID: _Znp.ErZiNuX2U1C
  Hardware Class: monitor
  Model: "HP w2338h"
  Vendor: HWP "HP"
  Device: eisa 0x281c "HP w2338h"
  Serial ID: "CNCXXXXX" (Sniped by OP)
  Resolution: 720x400@70Hz
  Resolution: 640x480@60Hz
  Resolution: 800x600@60Hz
  Resolution: 832x624@75Hz
  Resolution: 1024x768@60Hz
  Resolution: 1024x768@75Hz
  Resolution: 1280x1024@75Hz
  Resolution: 1280x960@60Hz
  Resolution: 1280x1024@60Hz
  Resolution: 1280x720@60Hz
  Resolution: 1920x1080@60Hz
  Size: 509x286 mm
  Year of Manufacture: 2009
  Week of Manufacture: 31
  Detailed Timings #0:
     Resolution: 1920x1080
     Horizontal: 1920 2008 2052 2200 (+88 +132 +280) +hsync
       Vertical: 1080 1084 1089 1125 (+4 +9 +45) +vsync
    Frequencies: 148.50 MHz, 67.50 kHz, 60.00 Hz
  Driver Info #0:
    Max. Resolution: 1920x1080
    Vert. Sync Range: 48-76 Hz
    Hor. Sync Range: 24-83 kHz
    Bandwidth: 148 MHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #6 (Display controller)

```
Noted and thanks

satimis

---

### Post by satimis on 2018-02-10
Hi  1fallen's

Something strange found on my daily working PC.  A Dell 25" monitor is connected to this PC via HDMI

&#10219; hwinfo --monitor
No printout

&#10219; hwinfo --monitor --short
no printout

&#10219; hwinfo --monitor -short ```

Usage: hwinfo [OPTIONS]
Probe for hardware.
Options:
    --<HARDWARE_ITEM>
        This option can be given more than once. Probe for a particular
        HARDWARE_ITEM. Available hardware items are:
        all, arch, bios, block, bluetooth, braille, bridge, camera,
        cdrom, chipcard, cpu, disk, dsl, dvb, fingerprint, floppy,
        framebuffer, gfxcard, hub, ide, isapnp, isdn, joystick, keyboard,
        memory, modem, monitor, mouse, netcard, network, partition,
        pci, pcmcia, pcmcia-ctrl, pppoe, printer, redasd,
        reallyall, scanner, scsi, smp, sound, storage-ctrl, sys, tape,
        tv, uml, usb, usb-ctrl, vbe, wlan, xen, zip
    --short
        Show only a summary. Use this option in addition to a hardware
        probing option.
    --listmd
        Normally hwinfo does not report RAID devices. Add this option to
        see them.
    --only DEVNAME
        This option can be given more than once. If you add this option,
        only data about devices with DEVNAME will be shown.
    --save-config SPEC
        Store config  for a particular device below /var/lib/hardware.
        SPEC can be a device name, an UDI, or 'all'. This option must be
        given in addition to a hardware probing option.
    --show-config UDI
        Show saved config data for a particular device.
    --map
        If disk names have  changed (e.g. after a kernel update) this
        prints a list of disk name mappings. Note  that  you must have
        used --save-config at some point before for this can work.
    --debug N
        Set debug level to N. The debug info is shown only in the log
        file. If you specify a log file, the debug level is implicitly
        set to a reasonable value.
    --verbose
        Increase verbosity. Only together with --map.
    --log FILE
        Write log info to FILE.
    --dump-db N
        Dump hardware data base. N is either 0 for the external data
        base in /var/lib/hardware, or 1 for the internal data base.
    --version
        Print libhd version.
    --help
        Print usage.

```

&#10219; hwinfo --cpu --short```

cpu:                                                            
                       AMD FX(tm)-8320 Eight-Core Processor, 3500 MHz
                       AMD FX(tm)-8320 Eight-Core Processor, 1700 MHz
                       AMD FX(tm)-8320 Eight-Core Processor, 1400 MHz
                       AMD FX(tm)-8320 Eight-Core Processor, 1400 MHz
                       AMD FX(tm)-8320 Eight-Core Processor, 1400 MHz
                       AMD FX(tm)-8320 Eight-Core Processor, 1400 MHz
                       AMD FX(tm)-8320 Eight-Core Processor, 1400 MHz
                       AMD FX(tm)-8320 Eight-Core Processor, 1400 MHz

```

&#10219; hwinfo --disk --short```

disk:                                                           
  /dev/sda             TS1TSSD370
  /dev/sdb             SanDisk SDSSDH32


  /dev/sdc             WDC WD1502FAEX-0
  /dev/sdd             WDC WD2005VBYZ-0

```

&#10219; hwinfo --display --short ```
        
graphics card:                                                  
                       nVidia GK208 [GeForce GT 730]

Primary display adapter: #28

```

&#10219; xrandr```

Screen 0: minimum 8 x 8, current 2560 x 1440, maximum 16384 x 16384
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 2560x1440+0+0 (normal left inverted right x axis y axis) 553mm x 311mm
   2560x1440     59.95*+
   2048x1152     60.00  
   1920x1200     59.88  
   1920x1080     60.00    59.94    50.00    29.97    25.00    23.97    60.05    60.00    50.04  
   1680x1050     59.95  
   1600x1200     60.00  
   1280x1024     75.02    60.02  
   1280x720      60.00    59.94    50.00  
   1200x960      60.00  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00    50.08  
   720x480       59.94    60.05  
   640x480       75.00    59.94    59.93  

```

Any advice?  Thanks

Remark:
I have reinstalled hwinfo twice without result

&#10219; lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:        16.04
Codename:       xenial
```


Regards
satimis

---

### Post by #&amp;thj^% on 2018-02-11
I have not seen this myself so not a lot of help from me I'm afraid:
About the only suggestion I have is try different cables, and make sure there no bent pins in the connectors. And all connections are tight.
This is not the same computer as the first post you list here, is it? (With the SAMSUNG SyncMaster)

---

### Post by satimis on 2018-02-11
> **1fallen said:**
> I have not seen this myself so not a lot of help from me I'm afraid:
About the only suggestion I have is try different cables, and make sure there no bent pins in the connectors. And all connections are tight.
This is not the same computer as the first post you list here, is it? (With the SAMSUNG SyncMaster)
Hi,

This is another computer;
AMD 8-core
RAM 32G (previous computer 8G)

The Dell monitor is working.

&#10219; xrandr```

Screen 0: minimum 8 x 8, current 2560 x 1440, maximum 16384 x 16384
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 2560x1440+0+0 (normal left inverted right x axis y axis) 553mm x 311mm
   2560x1440     59.95*+
   2048x1152     60.00  
   1920x1200     59.88  
   1920x1080     60.00    59.94    50.00    29.97    25.00    23.97    60.05    60.00    50.04  
   1680x1050     59.95  
   1600x1200     60.00  
   1280x1024     75.02    60.02  
   1280x720      60.00    59.94    50.00  
   1200x960      60.00  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00    50.08  
   720x480       59.94    60.05  
   640x480       75.00    59.94    59.93  

```

&#10219; xrandr --listmonitors```

Monitors: 1
 0: +*HDMI-0 2560/553x1440/311+0+0  HDMI-0

```

&#10219; xrandr --listproviders```

Providers: number : 1
Provider 0: id: 0x279 cap: 0x1, Source Output crtcs: 4 outputs: 3 associated providers: 0 name:NVIDIA-0

```

satimis

---

### Post by #&amp;thj^% on 2018-02-12
> **satimis said:**
> Hi,

This is another computer;
AMD 8-core
RAM 32G (previous computer 8G)

The Dell monitor is working.

satimis
I have to plead ignorance here believe it or not I have never used Dell Products, so this may be a big guessing game for me here.
But I don't quit.
This will give you a long list for all video related questions:

```
xrandr -q --verbose | less

```
Look for EDID string for the monitor you want,** and copy/paste it to a file** I named mine **"monitor.txt"** and just saved it to my home (maybe there is a better way but this is all I know.)
You will need edid-decode installed.

```
sudo apt install edid-decode
```

Then use:

```
edid-decode monitor.txt
```

to get all the info about your monitor from EDID string.
Mine for just the second Monitor.
```
EDID version: 1.3
Manufacturer: VIZ Model 67 Serial Number 1XXXXXX(Removed by OP)
Made in year 2011
Digital display
Maximum image size: 58 cm x 32 cm
Gamma: 2.20
DPMS levels: Off
RGB color display
First detailed timing is preferred timing

```
I'm sure you know this already but all monitors must be "ON" and connected first.;)
Now if this don't work then there is something different about Dell Monitors.

---

### Post by gordintoronto on 2018-02-12
Running Xubuntu 17.10, hwinfo --monitor 
shows me nothing, but NVIDIA X Server Settings, under the X Server Display Configuration, correctly identifies my Dell U2412M.

---

### Post by #&amp;thj^% on 2018-02-12
> **gordintoronto said:**
> Running Xubuntu 17.10, hwinfo --monitor 
shows me nothing, but NVIDIA X Server Settings, under the X Server Display Configuration, correctly identifies my Dell U2412M.

@gordintoronto give this a try if you would please.;)
```
grep "NVIDIA(GPU-0)" /var/log/Xorg.0.log |head -17| cut -d\: -f2
```
I'm just curious if it shows your Dell Monitor.

---

### Post by gordintoronto on 2018-02-12
Yup, among other things, it says:
 CRT-1
 DELL U2412M (DFP-0)

---

### Post by #&amp;thj^% on 2018-02-12
> **gordintoronto said:**
> Yup, among other things, it says:
 CRT-1
 DELL U2412M (DFP-0)
Great Thanks for checking that for me.:)

---

### Post by satimis on 2018-02-12
Hi all,

I got it.  Thanks

&#10219; grep "NVIDIA(GPU-0)" /var/log/Xorg.0.log |head -17| cut -d\: -f2```

 Found DRM driver nvidia-drm (20150116)
 CRT-0
 DFP-0
 DELL U2515H (DFP-1)
 The EDID for DELL U2515H (DFP-1) contradicts itself
     "720x480" is specified in the EDID; however, the EDID's
     valid HorizSync range (30.000-113.000 kHz) would exclude
     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
     for mode "720x480".
 The EDID for DELL U2515H (DFP-1) contradicts itself
     "720x576" is specified in the EDID; however, the EDID's
     valid HorizSync range (30.000-113.000 kHz) would exclude
     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
     for mode "720x576".
 The EDID for DELL U2515H (DFP-1) contradicts itself
     "720x576" is specified in the EDID; however, the EDID's
     valid VertRefresh range (56.000-86.000 Hz) would exclude

```

CRT-0
DFP-0
DELL U2515H (DFP-1)

satimis

---

