---
title: "Long Boot and Display resolution/detection problems"
date: 2016-02-11
forum: General Help
---

### Post by pawelma on 2016-02-11
Hi.

Firstly I want to apologize for my poor English.

Recently I decided to fully switch on my home computer from windows to Ubuntu.

I installed Ubuntu (14.04 LTS) it worked to first boot but then it doesn't want to boot so I decided to install 15.05 version with Gnome3 desktop environment. Installation went flawlessly and during installation a I experienced decent display quality. After reboot things doesn't look so bright. For now there are to major problems:
[LIST=1]
[*]Very long boot time (osculates between 3 and 4 minutes), 
[*]Too low detected resolution. 
[/LIST]

Firstly I installed Ubuntu in BIOS mode because my Windows was also installed in this mode, system was clumsy (expirienced same problems like now) so I decided to wipe disk and install in UEFI mode - unfortunately with same results.

My Hardware is following:
Processor: i5-4690K
Motherboard: AsRock Z97 Extreme 4
Graphic card: NVidia GTX970
Disk: SSD Crucial CT250MX

Ad.1.
I tried to install bootchart but it doesn't work on my machine. 
While booting there are several messages which may impact so long boot time (but there are not logged to boot.log, syslog nor dmesg):
```
buffer i/o error on dev sr0
```
```
A start job is running for Wait for Playmuth Boot Screen to Quit (XXs / no limit)        # where xx is increased every second
```
and other longer errors with some hex values which I didn't manage to remember from boot screen

Ad.2.
I'm using LG FLATRON 2550D monitor which is connected via HDMI cable. Display was OK with live CD and during installation. After boot resolution was lower than expected (i manage to set it to 1360x768). I installed some drivers from graphic-drivers ppa. Firstly it was recommended `nvidia-352` after reboot it doesn't change anything. I tried every driver from ppa list and none helped with issue. So I downloaded .run file from nvidia page but same result. I updated kernel to 4.3 but no result also. I tried to add new display mode via xrandr but ended with error. I also tried another HDMI calble (I have no DVI cable to check it out and in my card there is no VGA output; but anyway I want to use HDMI connection because I have speakers in my monitor).

Try to add new HD display mode.
```

$ xrandr
Screen 0: minimum 8 x 8, current 1360 x 768, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00 +
   1360x768      59.96*   59.80  
   1152x864      60.00  
   800x600       72.19    60.32    56.25  
   680x384       59.96    59.80  
   640x480       59.94  
   512x384       60.00  
   400x300       72.19  
   320x240       60.05  
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
  1920x1080_60.00 (0x1ee) 173.000MHz
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock  67.16KHz
        v: height 1080 start 1083 end 1088 total 1120           clock  59.96Hz


$ xrandr --addmode HDMI-0 1920x1080_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  39
  Current serial number in output stream:  40

```

I also tried to add new mode in xorg.conf and during boot using .xprofile file - no changes

It's weird that when I use read-edid it return different output than xrandr and displays gui (in gui there is an unknown display with 4:3 aspect ratio)
```

$ sudo get-edid  | parse-edid
[sudo] password for pawel: 
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 2
No EDID on bus 4
No EDID on bus 5
1 potential busses found: 3
256-byte EDID successfully retrieved from i2c bus 3
Looks like i2c was successful. Have a good day.
Checksum Correct

Section "Monitor"
    Identifier "M2550D"
    ModelName "M2550D"
    VendorName "GSM"
    # Monitor Manufactured week 4 of 2010
    # EDID version 1.3
    # Digital Display
    DisplaySize 550 310
    Gamma 2.20
    Option "DPMS" "false"
    Horizsync 30-83
    VertRefresh 56-75
    # Maximum pixel clock is 150MHz
    #Not giving standard mode: 1152x864, 75Hz
    #Not giving standard mode: 1280x720, 60Hz
    #Not giving standard mode: 1280x800, 60Hz
    #Not giving standard mode: 1280x1024, 60Hz
    #Not giving standard mode: 1440x900, 60Hz
    #Not giving standard mode: 1400x1050, 60Hz
    #Not giving standard mode: 1600x900, 60Hz
    #Not giving standard mode: 1680x1050, 60Hz

    #Extension block found. Parsing...
Extension block checksum failed

```

Is there any possibility to increase performance of boot time and fix graphics?


I cleared syslog before boot and here are some results:
[http://pastebin.com/hSucYs9R](http://pastebin.com/hSucYs9R)

---

