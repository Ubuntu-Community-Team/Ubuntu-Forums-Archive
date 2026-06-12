---
title: "AV Receiver gets treated like as 2nd monitor, 'Mirror' mode crashes upon selection"
date: 2023-01-29
forum: General Help
---

### Post by xanizen on 2023-01-29
Overview schematic of the cabling setup:
nVidia 760 GeForce ports: 1 'display port', 1 HDMI, 1 DVI
12 year old BenQ monitor: 1 HDMI, 1 DVI, 1 VGA
Yamaha AV receiver: 4 HDMI input, 1 HDMI output

nVidia is connected from its HDMI to the AV's HDMI #1 Input port.
nVidia is connected from its DVI to the monitor's DVI.

AV Receiver HDMI output is not connected to anything. 

Audio (5.1 surround) functions as needed, but I must use 'join monitors'. This results in cursor leaving the screen, or moving faster when nearing the edge of the screen adjacent to the '2nd monitor'.

These are configuration of the two 'monitors':
Yamaha (Av Receiver)
Orientation: Landscape
Resolution: 1920x1080 (16:9)
Refresh Rate: 59.94 Hz
Scale: 100%

BenQ (Actual Monitor):
Orientation: Landscape
Resolution: 1920x1200 (16:10)
Refrsh rate: 59.95 Hz
Scale: 100%
Fractional Scaling: Disabled

The Yamaha Receiver has a max resolution of 2580 x 576 in the options menu, and is detected as a 32" monitor.

When I click 'Mirror' tab, 'System Settings' crashes; how do I get an error log to better determine why its crashing?

The best solution thus far, is to drag the displays and have them connect the the edge of their respective side, resembling a checker board, how black and white come in contact with each other. My concern is this uses up more graphic processing power.

---

### Post by TheFu on 2023-01-30
X/Windows or Wayland?

With X/Windows, you can run 'xrandr' to see the reported/seen monitor connections, then set the output for each to supported values.
I don't have any clue how to do things on systems running Wayland.

Anyway, have all the monitors on, and run xrandr, post the output here with all the supported modes for all the different screens/monitors.
You might also find 'lxrandr' to be a nice quick tool to test different choices, but it doesn't save the settings, so you'll either need to use xrandr or configure the xorg.conf.d/ for the specific settings you desire.

---

### Post by MAFoElffen on 2023-01-30
+1... Also curious to see what this shows...

I feel what the OP is trying to do is the correct thing, as set to Mirrored... The NVidia driver is going to check the EDID of each and set to the lowest of both. I am assuming that the OP is using the AV (with no monitor attached) for sound.

---

### Post by #&amp;thj^% on 2023-01-30
> **xanizen said:**
> Overview schematic of the cabling setup:
nVidia 760 GeForce ports: 1 'display port', 1 HDMI, 1 DVI
12 year old BenQ monitor: 1 HDMI, 1 DVI, 1 VGA
Yamaha AV receiver: 4 HDMI input, 1 HDMI output

nVidia is connected from its HDMI to the AV's HDMI #1 Input port.
nVidia is connected from its DVI to the monitor's DVI.

AV Receiver HDMI output is not connected to anything. 

Audio (5.1 surround) functions as needed, but I must use 'join monitors'. This results in cursor leaving the screen, or moving faster when nearing the edge of the screen adjacent to the '2nd monitor'.

These are configuration of the two 'monitors':
Yamaha (Av Receiver)
Orientation: Landscape
Resolution: 1920x1080 (16:9)
Refresh Rate: 59.94 Hz
Scale: 100%

BenQ (Actual Monitor):
Orientation: Landscape
Resolution: 1920x1200 (16:10)
Refrsh rate: 59.95 Hz
Scale: 100%
Fractional Scaling: Disabled

The Yamaha Receiver has a max resolution of 2580 x 576 in the options menu, and is detected as a 32" monitor.

When I click 'Mirror' tab, 'System Settings' crashes; how do I get an error log to better determine why its crashing?

The best solution thus far, is to drag the displays and have them connect the the edge of their respective side, resembling a checker board, how black and white come in contact with each other. My concern is this uses up more graphic processing power.
Just my thoughts here, and more of heads up than anything else, from Nvidia:
```


    Improved the reliability of suspend and resume on UEFI systems when using certain display panels.
    Fixed a bug that prevented some controls in the nvidia-settings control panel from working when running an X server as an unprivileged user.
    Fixed a bug that could cause VK_ERROR_DEVICE_LOST when using VK_MEMORY_ALLOCATE_DEVICE_ADDRESS_CAPTURE_REPLAY_BIT to allocate memory.
    [B]Disabled Fixed Rate Link (FRL) when using passive DisplayPort to HDMI dongles, which are incompatible with FRL.
[/B]

```

---

### Post by xanizen on 2023-02-01
The system is using X11
```

vhen@vhen-az80:~$ echo $XDG_SESSION_TYPE 
x11
vhen@vhen-az80:~$ loginctl show-session $(loginctl | grep $(whoami) | awk '{print $1}') -p Type
Type=x11

```

This is my output of xrandr:
```

vhen@vhen-az80:~$ xrandr
Screen 0: minimum 8 x 8, current 3200 x 1895, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 519mm x 324mm
   1920x1200     59.95*+  59.88  
   1680x1050     59.95  
   1600x1200     60.00  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1152x720      60.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
HDMI-0 connected 1280x720+1920+1175 (normal left inverted right x axis y axis) 0mm x 0mm
   1920x1080     60.05 +  59.94    50.00    60.00    50.04  
   2880x576      50.00  
   2880x480      59.94  
   1440x576      50.00  
   1440x480      59.94  
   1280x720      59.94*   50.00  
   720x576       50.00  
   720x480       59.94  
DP-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by MAFoElffen on 2023-02-01
> **xanizen said:**
> This is my output of xrandr:
```

vhen@vhen-az80:~$ xrandr
Screen 0: minimum 8 x 8, current 3200 x 1895, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 519mm x 324mm
   1920x1200     59.95*+  59.88  
   1680x1050     59.95  
   1600x1200     60.00  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1152x720      60.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
[COLOR=#ff0000]HDMI-0 connected **1280x720+1920+1175** (normal left inverted right x axis y axis) 0mm x 0mm[/COLOR]
   1920x1080     60.05 +  59.94    50.00    60.00    50.04  
   2880x576      50.00  
   2880x480      59.94  
   1440x576      50.00  
   1440x480      59.94  
   1280x720      59.94*   50.00  
   720x576       50.00  
   720x480       59.94  
DP-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)

```
Indicated as highlighted in RED... That is not a valid mode. LOL

I would say to set that as 1920x1080 BEFORE doing anything... Then try to put it into Mirror mode.

---

### Post by xanizen on 2023-02-05
In the setting GUI, the resolution is set 1920x1080i (16:9), I forgot to point out the 'i' (interlaced) in my original post.

I tried to manually set the resolution of the AV receiver to 1920x1080, and still the resolution the remains the same as before
```

xrandr --output HDMI-0 --mode 1920x1080
xrandr --output HDMI-0  --mode 1920x1080 --rate 60.00
HDMI-0 connected 1920x1080+1920+1175 (normal left inverted right x axis y axis) 708mm x 398mm

```

I tried to define a new resolution that matches the primary monitor and xrandr rejected the configuration.
```

cvt 1920 1200 60
xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
xrandr --addmode HDMI-0 1920x1200_60.00
Error
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  41
  Current serial number in output stream:  42

```

This user supposedly encountered a similar problem and got it work with the following command, and created/updated xorg file to reflect the changes. It seems they had 4 monitors recognized.
[https://stackoverflow.com/a/67599114/1815210](https://stackoverflow.com/a/67599114/1815210)
```

xrandr --output DP-0 --off --output DP-1 --off --output HDMI-0 --mode 1920x1080 --pos 1080x170 \ 
--rotate normal --output DP-2 --primary --mode 2560x1440 --pos 1080x170 --rotate normal --output \
DP-3 --off --output DP-4 --off --output DP-5 --mode 1920x1080 --pos 0x0 --rotate left

```

---

### Post by #&amp;thj^% on 2023-02-06
Your going to be very hard pressed to make this work with a DVI connection, sorry to say...
My custom changes resides in  "/usr/share/X11/xorg.conf.d" and look like:
```
Section "OutputClass"
    Identifier "nvidia"
    MatchDriver "nvidia-drm"
    Driver "nvidia"
    Option "AllowEmptyInitialConfiguration"
    ModulePath "/usr/lib/x86_64-linux-gnu/nvidia/xorg"
EndSection

```
But the DVI port will mess it up.

---

### Post by xanizen on 2023-02-06
I was able to mirror the monitor using the 'nVidia xserver settings' app.

Before doing so, I had to connect the 2nd HDMI cable from the AV receiver's 'HDMI Out' port to the monitors HDMI port; i.e. monitor has a DVI and HDMI cable attached to it at the same time. Then press the config button on the monitor to use DVI signal not HDMI or VGA.

In nVidia x server > x server display configuration > Selection drop down menu:
3 options appeared, x screen 0, Yamaha receiver, and benq monitor

Select BenQ, use its maximum resolution of 1900x1200 (not supported in HDMI mode when connected to receiver, but 1080 is, but is distorted), select check box at bottom "Make this primary display for x screen", position is absolute, +0+0

Select Yamaha receiver in drop down menu of x server display configuration:
Press advanced button (will change to Basic...), for panning set to 1920x1200, position: absolute, +0+0, resolution at the top 2 from the drop down menu was set to 'Auto'.

I clicked apply.

In the Ubuntu system setting, I clicked display, and saw that the mirror tab was selected due to the x-server configuration.

To have 'nvidia x server' remember the settings on the next system start up, I have to click on 'Save x to configuration file' button at the bottom where the screen configuration occurred.

This required changing the permission of /usr/share/screen-resolution-extra/nvidia-polkit
```

sudo chmod  u+x  /usr/share/screen-resolution-extra/nvidia-polkit

```

You may need to run 'sudo nvidia-settings' before clicking that button.
[URL="https://i.imgur.com/dkLAhoB.jpg"]https://i.imgur.com/dkLAhoB.jpg

[/URL]Again the physical setup is precisely what I had with Windows 7.

**Edit**: Unfortunately xserver isn't remembering the settings when I restart the computer.

I pasted the contents f '/etc/X11/xorg.conf' and pasted it '/usr/share/X11/xorg.conf.d/10-nvidia.conf', after 'End Section', and x-server refuses to load/remember the settings.

```

Section "OutputClass"
    Identifier "nvidia"
    MatchDriver "nvidia-drm"
    Driver "nvidia"
    Option "AllowEmptyInitialConfiguration"
    ModulePath "/usr/lib/x86_64-linux-gnu/nvidia/xorg"
EndSection

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 470.161.03

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 510.47.03

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "BenQ G2400W"
    HorizSync       31.0 - 94.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "NVIDIA GeForce GTX 760"
    Option "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "MetaModeOrientation" "clone"
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DVI-I-1: nvidia-auto-select +0+0, HDMI-0: nvidia-auto-select @1920x1200 +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I've verified there's a checkmark next to X-server settings when viewing the 'Startup applications', with command 'gnome-session-properties'.

It possesses the following command: sh -c '/usr/bin/nvidia-settings --load-config-only'

**2nd edit**: It seems the 2nd HDMI cable isn't needed i.e. from the AV receiver to the monitor.

---

