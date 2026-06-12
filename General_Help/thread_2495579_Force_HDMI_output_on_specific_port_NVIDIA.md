---
title: "Force HDMI output on specific port NVIDIA"
date: 2024-02-23
forum: General Help
---

### Post by hdmi2csid on 2024-02-23
Installed driver: Nvidia 525.147.05 
OS: Kubuntu LTS 22.04

I am currently trying to get Ubuntu to output an HDMI signal towards a waveshare HDMI to CSI adapter.

I know the adapter works because I have recorded HDMI footage from a pi zero 2.

The Nividsa driver just for some reason does not want to send an HDMI signal to the device.

xrandr:
```

[FONT=monospace][COLOR=#000000]xrandr --verbose [/COLOR]
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767 
HDMI-0 disconnected (normal left inverted right x axis y axis) 
        Identifier: 0x1bc 
        Timestamp:  249487824 
        Subpixel:   unknown 
        Clones:     
        CRTCs:      0 1 2 3 
        Transform:  1.000000 0.000000 0.000000 
                    0.000000 1.000000 0.000000 
                    0.000000 0.000000 1.000000 
                   filter:  
        CTM: 0 1 0 0 0 0 0 0 0 1 0 0 0 0 0 0  
                0 1  
        CscMatrix: 65536 0 0 0 0 65536 0 0 0 0 65536 0  
        BorderDimensions: 4  
                supported: 4 
        Border: 0 0 0 0  
                range: (0, 65535) 
        SignalFormat: TMDS  
                supported: TMDS 
        ConnectorType: HDMI  
        ConnectorNumber: 3  
        _ConnectorLocation: 3  
        non-desktop: 0  
                supported: 0, 1 
DP-0 disconnected (normal left inverted right x axis y axis) 
...
DP-1 disconnected (normal left inverted right x axis y axis) 
...
HDMI-1 connected primary 1920x1080+0+0 (0x1c0) normal (normal left inverted right x axis y axis) 598mm x 336mm 
        Identifier: 0x1bf 
        Timestamp:  249487824 
        Subpixel:   unknown 
        Gamma:      0.37:1.0:2.2 
        Brightness: 0.64 
        Clones:     
...
This one is the other display. No Issue here. Working just fine. The output is just very long. And does not seem to be relevant to the topic.
...
  640x480 (0x1d3) 25.170MHz -HSync -VSync 
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.46KHz 
        v: height  480 start  490 end  492 total  525           clock  59.93Hz 
DP-2 disconnected (normal left inverted right x axis y axis) 
...
DP-3 disconnected (normal left inverted right x axis y axis) 
...

[/FONT]
```

The display ports are all not in use its [FONT=monospace]HDMI-0 where I want [/FONT][FONT=monospace]HDMI-1 to be mirrored too.

In case that helps:
The pi zero is set to [/FONT]
hdmi_mode=34   (1080p 30Hz)

I would be fine with 30Hz here too. the device can't capture more anyways. So a way to force the same mode would be great.

edit:
The port and cable work with the Philips display:
```

[FONT=monospace][COLOR=#000000]HDMI-0 connected 1920x1080+0+0 (0x1c0) normal (normal left inverted right x axis y axis) 597mm x 336mm [/COLOR]
        Identifier: 0x1bc 
        Timestamp:  316622749 
        Subpixel:   unknown 
        Gamma:      1.0:1.0:1.0 
        Brightness: 1.0 
        Clones:     
        CRTC:       1 
        CRTCs:      0 1 2 3 
        Transform:  1.000000 0.000000 0.000000 
                    0.000000 1.000000 0.000000 
                    0.000000 0.000000 1.000000 
                   filter:  
        EDID:  
                00ffffffffffff00410c0cc2f1120000 
                1b1e0103803c22782ae445a554529e26 
                0d5054bfef00d1c0b300950081808140 
                81c001010101565e00a0a0a029503020 
                350055502100001ea073006aa0a02950 
                0820350055502100001a000000fc0050 
                484c2032373545310a202020000000fd 
                00304b1e721e000a202020202020015c 
                020327f14b101f051404130312021101 
                230907078301000065030c001000681a 
                00000101304b00023a801871382d4058 
                2c450055502100001e8c0ad08a20e02d 
                10103e96005550210000188c0ad09020 
                4031200c405500555021000018f03c00 
                d051a0355060883a0055502100001c00 
                000000000000000000000000000000ad 
        CTM: 0 1 0 0 0 0 0 0 0 1 0 0 0 0 0 0  
                0 1  
        CscMatrix: 65536 0 0 0 0 65536 0 0 0 0 65536 0  
        BorderDimensions: 4  
                supported: 4 
        Border: 0 0 0 0  
                range: (0, 65535) 
        SignalFormat: TMDS  
                supported: TMDS 
        ConnectorType: HDMI  
        ConnectorNumber: 3  
        _ConnectorLocation: 3  
        non-desktop: 0  
                supported: 0, 1 
  2560x1440 (0xc91) 241.500MHz +HSync +VSync +preferred 
        h: width  2560 start 2608 end 2640 total 2720 skew    0 clock  88.79KHz 
        v: height 1440 start 1443 end 1448 total 1481           clock  59.95Hz 
  2560x1440 (0xc92) 296.000MHz +HSync -VSync 
        h: width  2560 start 2568 end 2600 total 2666 skew    0 clock 111.03KHz 
        v: height 1440 start 1443 end 1448 total 1481           clock  74.97Hz 
  1920x1080 (0x1c0) 148.500MHz +HSync +VSync *current 
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz 
        v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz 
...
shortened
...
  640x480 (0x1d3) 25.170MHz -HSync -VSync 
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.46KHz 
        v: height  480 start  490 end  492 total  525           clock  59.93Hz

[/FONT]

```

---

### Post by MAFoElffen on 2024-02-26
You can specify output to a specific port in the xorg.conf file, Monitor Section, Identifier entry:
> 
The Identifier entry specifies the unique name for this monitor. The Monitor section may be used to provide information about the specifications of the monitor, monitor-specific Options, and information about the video modes to use with the monitor.

[COLOR=#ff0000]With RandR 1.2-enabled drivers, monitor sections may be tied to specific outputs of the video card. Using the name of the output defined by the video driver plus the identifier of a monitor section, one associates a monitor section with an output by adding an option to the Device section in the following format:[/COLOR]

[COLOR=#ff0000]Option "Monitor-outputname" "monitorsection"

(for example, Option "Monitor-VGA" "VGA monitor" for a VGA output)
[/COLOR]
In the absence of specific association of monitor sections to outputs, if a monitor section is present the server will associate it with an output to preserve compatibility for previous single-head configurations.

But it needs to see it is connected to something and see an EDID from a display. There are ways around that, so it overrides and ignores that. That is what you would do for a KVM swith or Dolby Theater Switch. For that in DEVICE section, use: Option  "UseEDID"  "FALSE"

---

### Post by hdmi2csid on 2024-02-26
Thanks!
That sounds very promising.

But I need a verified example. As my entries are verified false (at least the parts I understand for sure) due to a previous graphics card that had to be replaced. I did not know that this operation left stuff like that behind until now.

Example:
```

[FONT=monospace][COLOR=#000000]Section "Monitor" [/COLOR]
    Identifier     "Monitor0" 
    VendorName     "Unknown" 
    ModelName      "Unknown" 
    Option         "DPMS" 
EndSection 

Section "Device" 
    Identifier     "Device0" 
    Driver         "nvidia" 
    VendorName     "NVIDIA Corporation" 
    BoardName      "GeForce RTX 2070" 
EndSection 

Section "Screen" 
    Identifier     "Screen0" 
    Device         "Device0" 
    Monitor        "Monitor0" 
    DefaultDepth    24 
    Option         "AllowEmptyInitialConfiguration" "True" 
    Option         "Coolbits" "28" 
    SubSection     "Display" 
        Depth       24 
    EndSubSection 
EndSection

[/FONT]

```

file [FONT=monospace][COLOR=#000000]/etc/X11/xorg.conf

> 
[/COLOR][/FONT]> [FONT=monospace][COLOR=#000000]grep "Using config" /var/log/Xorg.0.log [/COLOR]
[    14.979] (==) [COLOR=#ff5454]**Using config**[/COLOR][COLOR=#000000] file: "/etc/X11/xorg.conf"[/COLOR]

[/FONT]
[FONT=monospace]
[/FONT]

[FONT=monospace]'BoardName      "GeForce RTX 2070"' 
is the old card that broke it has been replaced by a 3070. The old one is definitely not in the computer anymore.[/FONT]
And the other numbers don't match my xrandr output either. So I assume there is something weird going on here. Even if it's the fact that I am getting a display signal at all. My best guess is that this file is not used anymore. How could that happen? What is going on here?

But yes, setting:
"UseEDID"  "FALSE"

for HDMI-0 seems pretty much exactly what I want. Ideally I would also set a fixed resolution and refresh rate (1080p 30Hz).

---

