---
title: "HELP Need to force DVI output trhought HDMI."
date: 2018-11-13
forum: General Help
---

### Post by soul7aker on 2018-11-13
Hi people of Ubuntu and Linux, I'm new to Linux, just started today, and I'm facing the problem that I knew that I will have to face, and that is my TV monitor, long story short, I cant connect my TV to a PC using HDMI because the image looks fuzzy and ugly, It has been that way since I've bought it, I managed to get around the problem using an edid override in the .inf files for the Windows drivers, and force the PC to output a DVI signal, and everything looks amazing.

But this is Ubuntu, and I'm very very new to Linux, (but not to read and try to fix it myself) I've been searching for the past 6 hours around the web and the forums, but I haven't found the solution, or cant get a way to fix it.

I've tried different combinations with xrandr and have even got the EDID with the get-edid thats built in Ubuntu

In windows I used a program to get my TV edid, another program to edit its last 2 bits, change a 1 for a 0, convert it to an .inf file and change the monitor's drivers in windows, and that fix it, I do the same thing for every GPU update. 

But I cant seem to find a way to do something like that in Ubuntu.

So TLDR; how do I override the EDID of my TV monitor in Ubuntu drivers, or how do I make Ubuntu to output a DVI signal, even when its plugged with a HDMI cable?

---

### Post by marcelof01 on 2018-11-14
I suggest you play with `xrandr`

[https://github.com/NicoHood/NicoHood.github.io/wiki/Fix-blurry-HDMI-output-with-DVI-mode#ubuntulinux-fix](https://github.com/NicoHood/NicoHood.github.io/wiki/Fix-blurry-HDMI-output-with-DVI-mode#ubuntulinux-fix)

List your devices to know the exact name
```

$> xrandr 
Screen 0: minimum 320 x 200, current 5120 x 1440, maximum 16384 x 16384
DVI-D-1 disconnected primary (normal left inverted right x axis y axis)
DP-1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024     60.02*+  75.02  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
   720x400       70.08  
DP-2 connected 1280x1024+3840+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024     60.02*+  75.02  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
   720x400       70.08  
HDMI-1 connected 2560x1440+1280+0 (normal left inverted right x axis y axis) 597mm x 336mm
   2560x1440     59.95*+
   1920x1080     60.00    50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1280x1024     75.02    60.02  
   1152x864      75.00  
   1280x768      59.87  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  
DP-3 disconnected (normal left inverted right x axis y axis)

```

Replace YOUR_DEVICE_NAME_HERE with DP-1 or HDMI-1 or whatever your device is named (and also replace with your preferred mode).
```

$> xrandr --output YOUR_DEVICE_NAME_HERE --set audio force-dvi --mode 1920x1080 

```

Use this setting for every startup
```

$> vim ~/.xprofile
```

You can even configure multi-monitor with xrandr.

This is my setup at office:
```

~ $ cat .xinitrc 
...
xrandr --output HDMI-1 --right-of DP-1
xrandr --output DP-2 --right-of HDMI-1
...

```

---

### Post by soul7aker on 2018-11-14
Thanks for your reply, here what I get from this steps:

first when I run xrandr 
```
soul7aker@soul7aker-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
HDMI-A-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 885mm x 498mm
   1920x1080     60.00*+  50.00    59.94    30.00    25.00    24.00    29.97    23.98  
   1680x1050     60.00  
   1280x1024     75.02    60.02  
   1440x900      60.00  
   1360x768      59.95  
   1280x800      59.91  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  
HDMI-A-1 disconnected (normal left inverted right x axis y axis)
```

then I try to use the command:

```
soul7aker@soul7aker-desktop:~$ xrandr --output HDMI-A-0 --set audio force-dvi --mode 1920x1080
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  32
  Current serial number in output stream:  32
```

This is the xrandr --prop

```
xrandr --prop
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
    TearFree: auto 
        supported: off, on, auto
    freesync_capable: 0 
        range: (0, 1)
    freesync: 0 
        range: (0, 1)
    underscan vborder: 0 
        range: (0, 128)
    underscan hborder: 0 
        range: (0, 128)
    underscan: off 
        supported: off, on, auto
    scaling mode: None 
        supported: None, Full, Center, Full aspect
    non-desktop: 0 
        range: (0, 1)
    link-status: Good 
        supported: Good, Bad
HDMI-A-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 885mm x 498mm
    EDID: 
        00ffffffffffff004d79010001010101
        01160103805932780a0dc9a057479827
        12484cbfef0031404540614081008bc0
        8180d1c00101023a801871382d40582c
        450075f23100001e662150b051001b30
        4070360075f23100009e000000fc0054
        56206d6f6e69746f720a2020000000fd
        00314c0f500e000a2020202020200103
        020330745102041113202210211f0615
        03071216051423090f00830100007103
        0c001000b82de00c0c0c0ca002014100
        011d00bc52d01e20b828554075f23100
        001e011d80d0721c1620102c258075f2
        3100009f8c0ad08a20e02d10103e9600
        75f2310000198c0ad090204031200c40
        550075f2310000180000000000000053
    _MUTTER_PRESENTATION_OUTPUT: 0 
    TearFree: auto 
        supported: off, on, auto
    freesync_capable: 0 
        range: (0, 1)
    freesync: 0 
        range: (0, 1)
    underscan vborder: 54 
        range: (0, 128)
    underscan hborder: 96 
        range: (0, 128)
    underscan: on 
        supported: off, on, auto
    scaling mode: None 
        supported: None, Full, Center, Full aspect
    non-desktop: 0 
        range: (0, 1)
    link-status: Good 
        supported: Good, Bad
   1920x1080     60.00*+  50.00    59.94    30.00    25.00    24.00    29.97    23.98  
   1680x1050     60.00  
   1280x1024     75.02    60.02  
   1440x900      60.00  
   1360x768      59.95  
   1280x800      59.91  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  
HDMI-A-1 disconnected (normal left inverted right x axis y axis)
    TearFree: auto 
        supported: off, on, auto
    freesync_capable: 0 
        range: (0, 1)
    freesync: 0 
        range: (0, 1)
    underscan vborder: 0 
        range: (0, 128)
    underscan hborder: 0 
        range: (0, 128)
    underscan: off 
        supported: off, on, auto
    scaling mode: None 
        supported: None, Full, Center, Full aspect
    non-desktop: 0 
        range: (0, 1)
    link-status: Good 
        supported: Good, Bad

```

---

### Post by marcelof01 on 2018-11-14
Check out this post, sounds like your problem too: [https://bbs.archlinux.org/viewtopic.php?pid=1408081#p1408081](https://bbs.archlinux.org/viewtopic.php?pid=1408081#p1408081)

---

