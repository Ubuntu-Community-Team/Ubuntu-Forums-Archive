---
title: "Xrandr twitches when using DVI-VGA adapter"
date: 2013-07-09
forum: General Help
---

### Post by BruCry on 2013-07-09
Hello all,

I have a problem with xrandr, or at least with my video cards, now I'm using the ubuntu 13.04 live DVD, but if I use an up-to-date ubuntu server installation with x.org installed, the same problem occurs.
I have three video cards, one IGP, one PCI-e and one PCI, in that order:
```
root@ubuntu:~# lspci | grep VGA
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880 [Radeon HD 4250]
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV610 [Radeon HD 2400 PRO]
06:06.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV250/M9 GL [Mobility FireGL 9000/Radeon 9000] (rev 02)
```
The IGP is connected via DVI to a 24" monitor and via VGA to a 17" monitor, all good so far.
Then I have three monitors left, two 15" VGA and one 17" vga, so to use all monitors, I have to use one DVI-VGA adapter.
No matter in what order/combination I connect the monitors to the video cards, the monitor that is connected via the adapter always flickers along with the other monitor on that same card (does not matter which card).
It seems like the two monitors have two sperate framebuffers, but by default they both show the framebuffer for the monitor with adapter, but when I move the mouse they switch rapidly from that framebuffer to the other and back.
It's hard to explain, but here are three video's showing the problem:
[http://www.youtube.com/watch?v=tQiJADHGuZg](http://www.youtube.com/watch?v=tQiJADHGuZg) (Top-Right monitor connected via adapter, in the same card as Bottom-Right)
[http://www.youtube.com/watch?v=lk9muK8f06c](http://www.youtube.com/watch?v=lk9muK8f06c) (Top-Left monitor connected via adapter, in the same card as Bottom-Right)
[http://www.youtube.com/watch?v=6Ses1jUcu2k](http://www.youtube.com/watch?v=6Ses1jUcu2k) (Top-Left monitor connected via adapter, in the same card as Top-Right)
They're recorded with my phone, so I hope they're clear enough to see the problem.
Now I hear you ask, why do I think it's a xrandr problem, well I have the exact same setup used with zaphodhead mode and xinerama, it works but its EXTREMELY slow.

I have already tried another DVI-VGA adapter, but with the same results.
Another strange thing is that xrandr seems to think that two monitors are clones (one of which not connected):
```
ubuntu@ubuntu:~$ xrandr --verbose
Screen 0: minimum 320 x 200, current 6528 x 1295, maximum 8192 x 8192
VGA-0 connected 1280x1024+0+56 (0x50) normal (normal left inverted right x axis y axis) 340mm x 270mm
    Identifier: 0xab
    Timestamp:  326178
    Subpixel:   no subpixels
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
        00ffffffffffff0022f05c2601010101
        1e0f010368221b8cee5e50a6544c9926
        145054adef8081800101010101010101
        010101010101302a009851002a403070
        1300540e1100001e000000fd00324c1e
        530e000a202020202020000000fc0048
        50204c313730360a20202020000000ff
        00434e43353330315957590a2020008c
    load detection: 1 (0x00000001)    range:  (0,1)
  1280x1024 (0x50)  108.0MHz +HSync +VSync *current +preferred
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
</snip>
HDMI-0 connected 1920x1080+1280+0 (0xaf) normal (normal left inverted right x axis y axis) 521mm x 293mm
    Identifier: 0xac
    Timestamp:  326178
    Subpixel:   horizontal rgb
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       1
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID:
        00ffffffffffff0026cd0d5601010101
        2b14010381341e782aeed5a555489b26
        125054bfef80b300a9409500818f8180
        950f714f81c0023a801871382d40582c
        450009252100001e000000ff00313130
        30313034333030393834000000fd0037
        4c1d5111000a202020202020000000fc
        00504c45323430374844530a20200019
    underscan vborder: 0 (0x00000000)    range:  (0,128)
    underscan hborder: 0 (0x00000000)    range:  (0,128)
    underscan:    off
        supported: off          on           auto        
    coherent: 1 (0x00000001)    range:  (0,1)
  1920x1080 (0xaf)  148.5MHz +HSync +VSync *current +preferred
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.5KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   60.0Hz
</snip>
VGA-2 connected 1024x768+3200+312 (0x45) normal (normal left inverted right x axis y axis) 300mm x 230mm
    Identifier: 0x74
    Timestamp:  326178
    Subpixel:   no subpixels
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:     DVI-1
    CRTC:       2
    CRTCs:      2 3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID:
        00ffffffffffff00225402152d080000
        100c0101081e1700e8d1eca05a4a9824
        164d53bfee0031404540614001010101
        010101010101000000fc004865726375
        6c65730a20202020000000fd00374b1e
        3d08000a202020202020000000fc0020
        50726f70686574766965770a000000fc
        00203732300a20202020202020200051
    load detection: 1 (0x00000001)    range:  (0,1)
  1024x768 (0x45)   78.8MHz +HSync +VSync *current
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.1KHz
        v: height  768 start  769 end  772 total  800           clock   75.1Hz
</snip>
DVI-1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x75
    Timestamp:  326178
    Subpixel:   horizontal rgb
    Clones:     VGA-2
    CRTCs:      2 3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    load detection: 1 (0x00000001)    range:  (0,1)
VGA-1 connected 1024x768+4224+312 (0x45) normal (normal left inverted right x axis y axis) 30mm x 22mm
    Identifier: 0x41
    Timestamp:  326178
    Subpixel:   no subpixels
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       4
    CRTCs:      4 5
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID:
        00ffffffffffff0009ad370245e80100
        210c0101081e1864e81726a061589a2e
        275439adce0000000000000000000000
        000000000000c31e0020410020301060
        13001e1600000000000000fc00353637
        00000031354c000a2000000000fd003c
        4b1f3c0800001e1600000000000000fe
        00465a574a32383031323439393700ac
    load detection: 1 (0x00000001)    range:  (0,1)
  1024x768 (0x45)   78.8MHz +HSync +VSync *current
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.1KHz
        v: height  768 start  769 end  772 total  800           clock   75.1Hz
</snip>
DIN disconnected (normal left inverted right x axis y axis)
    Identifier: 0x42
    Timestamp:  326178
    Subpixel:   no subpixels
    Clones:    
    CRTCs:      4 5
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    tv standard:    ntsc
        supported: ntsc         pal          pal-m        pal-60      
                   ntsc-j       scart-pal    pal-cn       secam       
    load detection: 1 (0x00000001)    range:  (0,1)
DVI-0 connected 1280x1024+5248+271 (0x51) normal (normal left inverted right x axis y axis) 338mm x 270mm
    Identifier: 0x43
    Timestamp:  326178
    Subpixel:   horizontal rgb
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       5
    CRTCs:      4 5
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID:
        00ffffffffffff003aac010001000000
        0610010308221b00ca0b329c5a4d8c26
        204e57afcf0081800101010101010101
        010101010101302a009851002a403070
        1300520e1100001e000000fe000a2020
        20202020202020202020000000fe000a
        202020202020202020202020000000fc
        000a20202020202020202020202000ec
    load detection: 1 (0x00000001)    range:  (0,1)
    underscan vborder: 0 (0x00000000)    range:  (0,128)
    underscan hborder: 0 (0x00000000)    range:  (0,128)
    underscan:    off
        supported: off          on           auto        
    coherent: 1 (0x00000001)    range:  (0,1)
  1280x1024 (0x50)  108.0MHz +HSync +VSync +preferred
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1280x1024 (0x51)  135.0MHz +HSync +VSync *current
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
</snip>
```
I have cut out the various supported modes, the full xrandr --verbose output is attached (in a zip, because I can only attach up to 19 KB...)
As you see, VGA-2 and DVI-1 apparantly are clones, but in this case only VGA-2 is connected, I don't know if that is normal.
I will try another configuration later and edit in the xrandr output.

Furthermore there are two reasons why I'm asking in the ubuntu forums first:
1. Xrandr 1.4 which first brougth support for multi-gpu only works in ubuntu, in other distributions there is no multi-gpu support although xrandr is at version 1.4.
2. I do not know where to file a bug report for xrandr (or x.org in general...)

Has anyone ever experienced something like this, or can anyone shed some light on the problem?
I hope this is enough information, but if anyone wants to know anything else, please ask.

With kind regards,
Robke Geenen


EDIT:
I now have connected two monitors (both 15") to VGA-2 and DVI-1, and the xrandr output has not changed, it still shows VGA-2 and DVI-1 as cloned, but the two displays still twitch as in the video's...
This is not getting any clearer...

---

