---
title: "Intel nuc, HDMI Overscan problem"
date: 2014-05-16
forum: General Help
---

### Post by logman on 2014-05-16
Hi,

I bought Intel Nuc device, and it's connected hdmi to tv but there is really bad overscan problem

**OS**: Ubuntu 14.04 & OpenElec
**Device**: Intel NUC D54250WYKH t
**TV**: Sony Bravia 32"  (KDL-V32A11E)

Picture: [link]("https://dl.dropboxusercontent.com/u/22611414/intel/20140516_200917.jpg")

I did try openelec all works fine on there is there way take those settings to ubuntu?

xrandr verbose settings from **OpenElec** (screen scale ok).
[HTML]xrandr --current
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
HDMI1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080i    50.00 +  60.00*   59.94
   1280x720      60.00    50.00    59.94
   1440x576i     50.00
   1440x480i     60.00    59.94
   720x576       50.00
   720x480       60.00    59.94
   640x480       60.00    59.94
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

OpenELEC:~/.config # xrandr  --verbose
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
HDMI1 connected 1920x1080+0+0 (0xa9) normal (normal left inverted right x axis y axis) 160mm x 90mm
        Identifier: 0x43
        Timestamp:  103883051
        Subpixel:   unknown
        Gamma:      1.0:1.0:1.0
        Brightness: 1.0
        Clones:
        CRTC:       0
        CRTCs:      0 1 2
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter:
        EDID:
                00ffffffffffff004dd9002e00000000
                000f0103801009780aee91a3544c9926
                0f505400000001010101010101010101
                010101010101011d80d0721c1620102c
                2580a05a0000009e8c0ad08a20e02d10
                103e9600a05a00000018000000fc0053
                4f4e592054560a2020202020000000fd
                002f3d0e2e08000a2020202020200141
                02031c71499403041213050107162309
                07078301000065030c001000011d0072
                51d01e206e285500a05a0000001e8c0a
                d090204031200c405500a05a00000018
                011d00bc52d01e20b8285540a05a0000
                001e011d8018711c1620582c25001009
                0000009e000000000000000000000000
                00000000000000000000000000000014
        Broadcast RGB: Automatic
                supported: Automatic, Full, Limited 16:235
        audio: auto
                supported: force-dvi, off, auto, on
  1920x1080i (0x48) 74.250MHz +HSync +VSync Interlace +preferred
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock  28.12KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  50.00Hz
  1920x1080i (0xa9) 74.250MHz +HSync +VSync Interlace *current
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.75KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  60.00Hz
  1920x1080i (0xaa) 74.176MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.72KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  59.94Hz
  1280x720 (0xab) 74.250MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
        v: height  720 start  725 end  730 total  750           clock  60.00Hz
  1280x720 (0xac) 74.250MHz +HSync +VSync
        h: width  1280 start 1720 end 1760 total 1980 skew    0 clock  37.50KHz
        v: height  720 start  725 end  730 total  750           clock  50.00Hz
  1280x720 (0xad) 74.176MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  44.96KHz
        v: height  720 start  725 end  730 total  750           clock  59.94Hz
  1440x576i (0xae) 27.000MHz -HSync -VSync Interlace
        h: width  1440 start 1464 end 1590 total 1728 skew    0 clock  15.62KHz
        v: height  576 start  580 end  586 total  625           clock  50.00Hz
  1440x480i (0xaf) 27.027MHz -HSync -VSync Interlace
        h: width  1440 start 1478 end 1602 total 1716 skew    0 clock  15.75KHz
        v: height  480 start  488 end  494 total  525           clock  60.00Hz
  1440x480i (0xb0) 27.000MHz -HSync -VSync Interlace
        h: width  1440 start 1478 end 1602 total 1716 skew    0 clock  15.73KHz
        v: height  480 start  488 end  494 total  525           clock  59.94Hz
  720x576 (0xb1) 27.000MHz -HSync -VSync
        h: width   720 start  732 end  796 total  864 skew    0 clock  31.25KHz
        v: height  576 start  581 end  586 total  625           clock  50.00Hz
  720x480 (0xb2) 27.027MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.50KHz
        v: height  480 start  489 end  495 total  525           clock  60.00Hz
  720x480 (0xb3) 27.000MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.47KHz
        v: height  480 start  489 end  495 total  525           clock  59.94Hz
  640x480 (0xb4) 25.200MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.50KHz
        v: height  480 start  490 end  492 total  525           clock  60.00Hz
  640x480 (0xb5) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
DP1 disconnected (normal left inverted right x axis y axis)
        Identifier: 0x44
        Timestamp:  103883051
        Subpixel:   unknown
        Clones:     HDMI2
        CRTCs:      0 1 2
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter:
        Broadcast RGB: Automatic
                supported: Automatic, Full, Limited 16:235
        audio: auto
                supported: force-dvi, off, auto, on
HDMI2 disconnected (normal left inverted right x axis y axis)
        Identifier: 0x45
        Timestamp:  103883051
        Subpixel:   unknown
        Clones:     DP1
        CRTCs:      0 1 2
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter:
        Broadcast RGB: Automatic
                supported: Automatic, Full, Limited 16:235
        audio: auto
                supported: force-dvi, off, auto, on
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
        Identifier: 0x46
        Timestamp:  103883051
        Subpixel:   no subpixels
        Clones:
        CRTCs:      3
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter:

------ Settings file: ------

    <description>HDMI1: 1920x1080i @ 30.00Hz</description>
            <subtitles>1042</subtitles>
            <pixelratio>1.000000</pixelratio>
            <refreshrate>30.000000</refreshrate>
            <output>HDMI1</output>
            <xrandrid>0xa9</xrandrid>
            <overscan>
                <left>51</left>
                <top>19</top>
                <right>1872</right>
                <bottom>1068</bottom>
            </overscan>
        </resolution>

[/HTML]


xrandr verbose settings from **ubuntu**.
[HTML]
xrandr --current
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767
HDMI1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080i     50.0*+   60.1     60.0
   1280x720       60.0     50.0     59.9
   1440x576i      50.1
   1440x480i      60.1     60.1
   720x576        50.0
   720x480        60.0     59.9
   640x480        60.0     59.9
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

-----

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767
HDMI1 connected primary 1920x1080+0+0 (0x48) normal (normal left inverted right x axis y axis) 160mm x 90mm
        Identifier: 0x43
        Timestamp:  25711
        Subpixel:   unknown
        Gamma:      1.0:1.0:1.0
        Brightness: 1.0
        Clones:
        CRTC:       0
        CRTCs:      0 1 2
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter:
        EDID:
                00ffffffffffff004dd9002e00000000
                000f0103801009780aee91a3544c9926
                0f505400000001010101010101010101
                010101010101011d80d0721c1620102c
                2580a05a0000009e8c0ad08a20e02d10
                103e9600a05a00000018000000fc0053
                4f4e592054560a2020202020000000fd
                002f3d0e2e08000a2020202020200141
                02031c71499403041213050107162309
                07078301000065030c001000011d0072
                51d01e206e285500a05a0000001e8c0a
                d090204031200c405500a05a00000018
                011d00bc52d01e20b8285540a05a0000
                001e011d8018711c1620582c25001009
                0000009e000000000000000000000000
                00000000000000000000000000000014
        Broadcast RGB: Automatic
                supported: Automatic, Full, Limited 16:235
        audio: auto
                supported: force-dvi, off, auto, on
  1920x1080i (0x48)   74.2MHz +HSync +VSync Interlace *current +preferred
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock   28.1KHz
        v: height 1080 start 1084 end 1094 total 1125           clock   50.0Hz
  1920x1080i (0xaa)   74.2MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   33.8KHz
        v: height 1080 start 1084 end 1094 total 1125           clock   60.1Hz
  1920x1080i (0xab)   74.2MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   33.7KHz
        v: height 1080 start 1084 end 1094 total 1125           clock   60.0Hz
  1280x720 (0xac)   74.2MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   60.0Hz
  1280x720 (0xad)   74.2MHz +HSync +VSync
        h: width  1280 start 1720 end 1760 total 1980 skew    0 clock   37.5KHz
        v: height  720 start  725 end  730 total  750           clock   50.0Hz
  1280x720 (0xae)   74.2MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   59.9Hz
  1440x576i (0xaf)   27.0MHz -HSync -VSync Interlace
        h: width  1440 start 1464 end 1590 total 1728 skew    0 clock   15.6KHz
        v: height  576 start  580 end  586 total  625           clock   50.1Hz
  1440x480i (0xb0)   27.0MHz -HSync -VSync Interlace
        h: width  1440 start 1478 end 1602 total 1716 skew    0 clock   15.8KHz
        v: height  480 start  488 end  494 total  525           clock   60.1Hz
  1440x480i (0xb1)   27.0MHz -HSync -VSync Interlace
        h: width  1440 start 1478 end 1602 total 1716 skew    0 clock   15.7KHz
        v: height  480 start  488 end  494 total  525           clock   60.1Hz
  720x576 (0xb2)   27.0MHz -HSync -VSync
        h: width   720 start  732 end  796 total  864 skew    0 clock   31.2KHz
        v: height  576 start  581 end  586 total  625           clock   50.0Hz
  720x480 (0xb3)   27.0MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock   31.5KHz
        v: height  480 start  489 end  495 total  525           clock   60.0Hz
  720x480 (0xb4)   27.0MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock   31.5KHz
        v: height  480 start  489 end  495 total  525           clock   59.9Hz
  640x480 (0xb5)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   60.0Hz
  640x480 (0xb6)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
DP1 disconnected (normal left inverted right x axis y axis)
        Identifier: 0x44
        Timestamp:  25711
        Subpixel:   unknown
        Clones:     HDMI2
        CRTCs:      0 1 2
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter:
        Broadcast RGB: Automatic
                supported: Automatic, Full, Limited 16:235
        audio: auto
                supported: force-dvi, off, auto, on
HDMI2 disconnected (normal left inverted right x axis y axis)
        Identifier: 0x45
        Timestamp:  25711
        Subpixel:   unknown
        Clones:     DP1
        CRTCs:      0 1 2
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter:
        Broadcast RGB: Automatic
                supported: Automatic, Full, Limited 16:235
        audio: auto
                supported: force-dvi, off, auto, on
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
        Identifier: 0x46
        Timestamp:  25711
        Subpixel:   no subpixels
        Clones:
        CRTCs:      3
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter:

[/HTML]

---

### Post by papibe on 2014-05-16
Hi logman.

It is usually the TV's fault, and you can solve it using your remote.

In my Sony Bravia, you select your Menu ('Home' button) and go to
```
Screen -> Display Area
```
there you set the field to 'Full Pixel'

Hope it helps. Let us know how it goes.
Regards.

---

### Post by logman on 2014-05-16
There is no home button Tv from 2005 :(  and did look all settings from tv..

---

### Post by papibe on 2014-05-16
Let's try adjusting the viewing area, and the position of the screen using xrandr.

Since the resolution is 1920x1080, let's assume that the overscan is 'eating' 16 pixels from every side, and 20 from top and bottom. Then, at most viewing are should be:
```
(1920-16-16)x(1080-20-20) =  1888x1040
```
Then adjusting the screen size with xrandr would be:
```
xrandr --output HDMI1 --fb 1888x1040
```
Now you would have to move the initial position where the screen is display:
```
xrandr --output HDMI1 --pos 20x16
```
Hope that helps. Let us know how it goes.
Regards.

---

### Post by logman on 2014-05-16
Got error: xrandr: specified screen 1888x1040 not large enough for output HDMI1 (1920x1080+0+0)

---

### Post by tragicallyhip on 2014-05-16
There is no software solution, Intel nuc can only broadcast a limited number of resolutions over HDMI, and your monitor can only receive  limited number of Resolutions over HDMI. They don't have a common resolution hence the over/under scanning. the solution is to add an HDMI/VGA signal converter. Attach the converter to your HDMI cable, sound will still work over HDMI however the HDMI video signal is captured and converted to VGA on it's way to your monitor. All you will have to do is set your monitor to receive VGA signals and it will automatically default to it's native resolution (1368x768) or something like that.
good luck
tragic

---

### Post by logman on 2014-05-19
> **tragicallyhip said:**
> There is no software solution, Intel nuc can only broadcast a limited number of resolutions over HDMI, and your monitor can only receive  limited number of Resolutions over HDMI. They don't have a common resolution hence the over/under scanning. the solution is to add an HDMI/VGA signal converter. Attach the converter to your HDMI cable, sound will still work over HDMI however the HDMI video signal is captured and converted to VGA on it's way to your monitor. All you will have to do is set your monitor to receive VGA signals and it will automatically default to it's native resolution (1368x768) or something like that.
good luck
tragic

Why OpenElec works just fine and ubuntu not

---

### Post by matt_symes on 2014-05-20
Hi

I think you may be able to fix it using xrandr.

Can you post the output of

xrandr --prop

Your looking for an underscan entry under the hdmi entry.

If you have that, this may be fixable.

Kind regards

---

### Post by mcduck on 2014-05-21
I'd be really, really surprised if a Sony Bravia with a HDMI connector wouldn't have option for pixel-per-pixel mode.

The names and locations of all settings of course depend on manufacturer and model, so not having a "home" button doesn't mean you wouldn't have the option. I recommend checkign it's manual, or if you can give the exact model number I can always try to find the manual and check what the option is called and where to find it in the menu.

Overscan on a TV with HDMI connector is pretty much always a problem best solved on the TV itself. Anything you could do on the computer end is just applying duct tape to work around the issue, and will also result in lower quality picture (since you'll end sending lower resolution  picture to the display, which then needs to scale it up again to fit the panel's actual resolution. Just sending the exactly correct resolution in the fist palce and telling the display to render it as it is without overscan or scaling will give much sharper image).

Edit: Also looking at the picture of the display in your first post, it has the HD-Ready sticker on it. That means even if might accept 1080p (1920x1080), the display panel  itself is lower resolution.  Interestingly, while HD-Ready defines the resolution to be 720p (1280x720),  for manufacturing reasons pretty much all HD-Ready display panels are actually 1366x768 resolution. So if possible, you'd really want to set your computer to run either at 1366x768 or 1360x768 to get best quality image. Especially if you plan on using it for actual desktop tasks and not just for watching movies (where blurriness caused by image scaling might not be us noticeable)

---

