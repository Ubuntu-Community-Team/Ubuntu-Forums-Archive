---
title: "Problem with TV overscan"
date: 2015-09-24
forum: General Help
---

### Post by germ65 on 2015-09-24
I have an old projection TV (Sony KDF-E50A10) connected to an i3 Gigabyte Brix running Ubuntu 14.04.3 LTS Desktop (was running OS X Mavericks in a previous life). The HDTV is connected to the computer via its HDMI input (this is the easiest because the mini-PC has mini-DP and HDMI ports, and also the HDMI port carries audio, which works beautifully in Ubuntu. I do not with to change the way the computer is connected to the TV). The problem is that I cannot find a good setting so that I don't cut off pixels at the right and bottom edge of the screen. I have already spent a few hours doing research and trying to fix this problem, but I have not found a good solution yet. 

The overscan cannot be fixed at the TV. I have tried all the settings and read the manual. So it needs to be fixed with tweaking of xrandr and/or creating new modes. The problem is, how exactly to do this and achieve perfect results. Here is the output of xrandr -q --verbose:

```
Screen 0: minimum 320 x 200, current 1332 x 768, maximum 32767 x 32767
HDMI1 connected primary 1319x778+0+0 (0xaa) normal (normal left inverted right x axis y axis) 16mm x 9mm
	Identifier: 0x43
	Timestamp:  4112051
	Subpixel:   unknown
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       0
	CRTCs:      0 1 2
	Transform:  1.029999 0.000000 -28.000000
	            0.000000 1.079987 -18.000000
	            0.000000 0.000000 1.000000
	           filter: bilinear
	EDID: 
		00ffffffffffff004dd9f80101010101
		000e0103800000780a0dc9a057479827
		12484c20000001010101010101010101
		010101010101011d8018711c1620582c
		250010090000009e8c0ad08a20e02d10
		103e9600040300000018000000fc0053
		4f4e592054560a2020202020000000fd
		003b3d0f2e08000a20202020202001df
		02031a76478502030406070123090707
		8301000065030c001000011d007251d0
		1e206e28550010090000001e8c0aa014
		51f01600267c43000403000000988c0a
		d08a20e02d10103e9600100900000018
		8c0aa01451f01600267c430010090000
		00980000000000000000000000000000
		00000000000000000000000000000097
	aspect ratio: Automatic 
		supported: Automatic, 4:3, 16:9
	Broadcast RGB: Automatic 
		supported: Automatic, Full, Limited 16:235
	audio: auto 
		supported: force-dvi, off, auto, on
  1920x1080i (0x48)   74.2MHz +HSync +VSync Interlace +preferred
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   33.8KHz
        v: height 1080 start 1084 end 1094 total 1125           clock   60.1Hz
  1920x1080i (0xa9)   74.2MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   33.7KHz
        v: height 1080 start 1084 end 1094 total 1125           clock   60.0Hz
  1280x720 (0xaa)   74.2MHz +HSync +VSync *current
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   60.0Hz
  1280x720 (0xab)   74.2MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   59.9Hz
  1440x480i (0xac)   27.0MHz -HSync -VSync Interlace
        h: width  1440 start 1478 end 1602 total 1716 skew    0 clock   15.7KHz
        v: height  480 start  488 end  494 total  525           clock   60.1Hz
  720x480 (0xad)   27.0MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock   31.5KHz
        v: height  480 start  489 end  495 total  525           clock   60.0Hz
  720x480 (0xae)   27.0MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock   31.5KHz
        v: height  480 start  489 end  495 total  525           clock   59.9Hz
  720x480i (0xaf)   13.5MHz -HSync -VSync Interlace
        h: width   720 start  739 end  801 total  858 skew    0 clock   15.7KHz
        v: height  480 start  488 end  494 total  525           clock   60.1Hz
  720x480i (0xb0)   13.5MHz -HSync -VSync Interlace
        h: width   720 start  739 end  801 total  858 skew    0 clock   15.7KHz
        v: height  480 start  488 end  494 total  525           clock   60.1Hz
  640x480 (0xb1)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   60.0Hz
  640x480 (0xb2)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
DP1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x44
	Timestamp:  4112051
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
	Timestamp:  4112051
	Subpixel:   unknown
	Clones:     DP1
	CRTCs:      0 1 2
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	aspect ratio: Automatic 
		supported: Automatic, 4:3, 16:9
	Broadcast RGB: Automatic 
		supported: Automatic, Full, Limited 16:235
	audio: auto 
		supported: force-dvi, off, auto, on
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x46
	Timestamp:  4112051
	Subpixel:   no subpixels
	Clones:    
	CRTCs:      3
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 

```

As you can see, the system offers two main modes: 1920x1080i (preferred by default) and 1280x720. I was surprised to see the first mode. I do not like it because everything is way too small. So what I did is to select 1280x720 and start tweaking with xrandr settings. After much trial and error I found that this command would give me a reasonable result:

```
xrandr --output HDMI1 --fb 1332x768 --transform 1.03,0,-28,0,1.08,-18,0,0,1
```

So I saved it into ~/.xprofile to make it permanent. 

I now have two issues:
1. The rightmost ~30 pixels and bottommost ~? pixels are cut off
2. At booting, I am greeted with an error message that "the screen is too large to fit in the given space" (I am paraphrasing). Clicking OK with the mouse dismisses the dialog box and boot proceeds. This is very annoying. 

One thing I have noticed is that I cannot simply enlarge the frame buffer past 1332 horizontal pixels (for example using --fb 1352x768): The TV stops showing me more of the desktop above 1332. WHY?

It seems to me that this TV needs a resolution in the neighborhood of 1366x768, a mode that is however not offered by default. So I read about using cvt to create a new mode and adding it. I was able to do that, but when I switched to it, I just got a black screen. Maybe I made a rookie mistake at some step, maybe not. 

So the question is now, how to proceed?

(The irony is OS X has a simple checkbox "Overscan" in the Display Preferences that fixed the problem with one click. Don't flame me, just saying...)

---

