---
title: "Can't get display resolution I want"
date: 2022-02-05
forum: General Help
---

### Post by lalawawa on 2022-02-05
I'm an Ubuntu 20.04.3 LTS.
    My graphics card is AMD Radeon(tm) vega 11 graphics
    I have a dual monitor system, VGA landscape on the left, HDMI portrait on the right.
    The right hand monitor has resolution going up to 1440x2560, but that resolution is not displayed when I try to change it in "Settings -> Displays".
    The menu goes up to 4096x2160, so I figure the graphics card can handle 2560x1440, it's just not giving me the choice.

    Looking at other discussion about setting resolution, the 'xandr' command is mentioned, but when I try it it's not found and I get told to
    $ sudo apt install x11-server-utils
    but when I try that install it says it already has the latest version and refuses to do anything and it still can't find 'xandr'.

---

### Post by MAFoElffen on 2022-02-06
First, xrandr only works when using Xorg XServer.It will not work with Wayland. Which are you using as a Graphics Server?
This will tell us which graphics server you are using and which vtty session it is running on...
```

ps -e | egrep -e 'tty' | egrep -e 'x11|Xorg|wayland' | awk '{print $2":" $4}'

```
This will tell you where xrandr is on your system, if it is there:
```

which xrandr
xrandr -q

```
Then to show the info on your video GPU and what drivers it is using
```

sudo lshw -c video
lsmod | grep amdgpu
dmesg | grep amdgpu

```

---

### Post by roshanmathewphilip on 2022-02-06
> **lalawawa said:**
> 
 'xandr'.
Its 'xrandr' you missed the 'r'.

---

### Post by KBar on 2022-02-06
> **MAFoElffen said:**
> First, xrandr only works when using Xorg XServer.It will not work with Wayland. Which are you using as a Graphics Server?
This will tell us which graphics server you are using and which vtty session it is running on...
```

ps -e | egrep -e 'tty' | egrep -e 'x11|Xorg|wayland' | awk '{print $2":" $4}'

```

Pardon me but I'd suggest a much simpler variation:
```
printenv XDG_SESSION_TYPE
```

---

### Post by lalawawa on 2022-02-06
OK, you're right, I misspelled 'xrandr'.  It turns out that I do have /usr/bin/xrandr.

$ sudo lshw -c video
[sudo] password for wulluw: 
  *-display
       description: VGA compatible controller
       product: Picasso
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:07:00.0
       version: c8
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix vga_controller bus_master cap_list
       configuration: driver=amdgpu latency=0
       resources: irq:53 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:f000(size=256) memory:fca00000-fca7ffff
$ set | fgrep XDG
XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/etc/xdg
XDG_CURRENT_DESKTOP=ubuntu:GNOME
XDG_DATA_DIRS=/usr/share/ubuntu:/usr/local/share/:/usr/share/:/var/lib/snapd/desktop
XDG_MENU_PREFIX=gnome-
XDG_RUNTIME_DIR=/run/user/1000
XDG_SESSION_CLASS=user
XDG_SESSION_DESKTOP=ubuntu
XDG_SESSION_TYPE=x11
$  ps -e | fgrep tty | egrep 'x11|Xorg|wayland' 
   1754 tty2     02:02:43 Xorg
$

So what should I do?

---

### Post by lalawawa on 2022-02-06
$ lsmod | grep amdgpu
amdgpu               6348800  52
iommu_v2               24576  1 amdgpu
gpu_sched              36864  1 amdgpu
drm_ttm_helper         16384  1 amdgpu
ttm                    69632  2 amdgpu,drm_ttm_helper
drm_kms_helper        253952  1 amdgpu
i2c_algo_bit           16384  1 amdgpu
drm                   557056  14 gpu_sched,drm_kms_helper,amdgpu,drm_ttm_helper,ttm
$ dmesg | grep amdgpu
[    9.180468] [drm] amdgpu kernel modesetting enabled.
[    9.181682] amdgpu: Topology: Add APU node [0x0:0x0]
[    9.181779] fb0: switching to amdgpudrmfb from EFI VGA
[    9.182103] amdgpu 0000:07:00.0: vgaarb: deactivate vga console
[    9.182182] amdgpu 0000:07:00.0: enabling device (0106 -> 0107)
[    9.182264] amdgpu 0000:07:00.0: amdgpu: Trusted Memory Zone (TMZ) feature enabled
[    9.182868] amdgpu 0000:07:00.0: amdgpu: Fetched VBIOS from VFCT
[    9.182873] amdgpu: ATOM BIOS: 113-PICASSO-115
[    9.183354] amdgpu 0000:07:00.0: amdgpu: VRAM: 2048M 0x000000F400000000 - 0x000000F47FFFFFFF (2048M used)
[    9.183357] amdgpu 0000:07:00.0: amdgpu: GART: 1024M 0x0000000000000000 - 0x000000003FFFFFFF
[    9.183360] amdgpu 0000:07:00.0: amdgpu: AGP: 267419648M 0x000000F800000000 - 0x0000FFFFFFFFFFFF
[    9.183457] [drm] amdgpu: 2048M of VRAM memory ready
[    9.183463] [drm] amdgpu: 3072M of GTT memory ready.
[    9.191452] amdgpu: hwmgr_sw_init smu backed is smu10_smu
[    9.193878] amdgpu 0000:07:00.0: amdgpu: Will use PSP to load VCN firmware
[    9.282670] amdgpu 0000:07:00.0: amdgpu: RAS: optional ras ta ucode is not available
[    9.287409] amdgpu 0000:07:00.0: amdgpu: RAP: optional rap ta ucode is not available
[    9.287414] amdgpu 0000:07:00.0: amdgpu: SECUREDISPLAY: securedisplay ta ucode is not available
[    9.333517] snd_hda_intel 0000:07:00.1: bound 0000:07:00.0 (ops amdgpu_dm_audio_component_bind_ops [amdgpu])
[    9.479234] kfd kfd: amdgpu: Allocated 3969056 bytes on gart
[    9.479491] amdgpu: Topology: Add APU node [0x15d8:0x1002]
[    9.479493] kfd kfd: amdgpu: added device 1002:15d8
[    9.479495] amdgpu 0000:07:00.0: amdgpu: SE 1, SH per SE 1, CU per SH 11, active_cu_number 11
[    9.481299] fbcon: amdgpudrmfb (fb0) is primary device
[    9.481364] amdgpu 0000:07:00.0: [drm] fb0: amdgpudrmfb frame buffer device
[    9.496131] amdgpu 0000:07:00.0: amdgpu: ring gfx uses VM inv eng 0 on hub 0
[    9.496137] amdgpu 0000:07:00.0: amdgpu: ring comp_1.0.0 uses VM inv eng 1 on hub 0
[    9.496140] amdgpu 0000:07:00.0: amdgpu: ring comp_1.1.0 uses VM inv eng 4 on hub 0
[    9.496143] amdgpu 0000:07:00.0: amdgpu: ring comp_1.2.0 uses VM inv eng 5 on hub 0
[    9.496145] amdgpu 0000:07:00.0: amdgpu: ring comp_1.3.0 uses VM inv eng 6 on hub 0
[    9.496148] amdgpu 0000:07:00.0: amdgpu: ring comp_1.0.1 uses VM inv eng 7 on hub 0
[    9.496150] amdgpu 0000:07:00.0: amdgpu: ring comp_1.1.1 uses VM inv eng 8 on hub 0
[    9.496152] amdgpu 0000:07:00.0: amdgpu: ring comp_1.2.1 uses VM inv eng 9 on hub 0
[    9.496158] amdgpu 0000:07:00.0: amdgpu: ring comp_1.3.1 uses VM inv eng 10 on hub 0
[    9.496161] amdgpu 0000:07:00.0: amdgpu: ring kiq_2.1.0 uses VM inv eng 11 on hub 0
[    9.496168] amdgpu 0000:07:00.0: amdgpu: ring sdma0 uses VM inv eng 0 on hub 1
[    9.496170] amdgpu 0000:07:00.0: amdgpu: ring vcn_dec uses VM inv eng 1 on hub 1
[    9.496173] amdgpu 0000:07:00.0: amdgpu: ring vcn_enc0 uses VM inv eng 4 on hub 1
[    9.496175] amdgpu 0000:07:00.0: amdgpu: ring vcn_enc1 uses VM inv eng 5 on hub 1
[    9.496177] amdgpu 0000:07:00.0: amdgpu: ring jpeg_dec uses VM inv eng 6 on hub 1
[    9.508651] [drm] Initialized amdgpu 3.41.0 20150101 for 0000:07:00.0 on minor 0
[795434.901076] audit: type=1400 audit(1644111606.082:222): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/usr/share/libdrm/amdgpu.ids" pid=200553 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
$

---

### Post by lalawawa on 2022-02-06
No, I don't understand what I should do to add 2560x1440 to the list of resolutions I can choose.

---

### Post by lalawawa on 2022-02-06
```
$ xrandr --prop
Screen 0: minimum 320 x 200, current 3000 x 1920, maximum 16384 x 16384
HDMI-A-0 connected 1080x1920+1920+0 left (normal left inverted right x axis y axis) 708mm x 398mm
	_MUTTER_PRESENTATION_OUTPUT: 0 
	EDID: 
		00ffffffffffff0061a44a0001000000
		061c0103807341780acf74a3574cb023
		09484c21080081804540614095000101
		010101010101023a801871382d40582c
		4500c48e2100001e662150b051001b30
		40703600c48e2100001e000000fc004d
		692054560a20202020202020000000fd
		00324b1e5017000a20202020202001e6
		02033cf24f010304050790121314161f
		606165662c0907071117505107003d07
		c0830100006e030c002000b83c208080
		01020304e30f0078e3060501011d00bc
		52d01e20b8285540c48e2100001e011d
		80d0721c1620102c2580c48e2100009e
		00000000000000000000000000000000
		000000000000000000000000000000cd
	GAMMA_LUT_SIZE: 4096 
		range: (0, -1)
	DEGAMMA_LUT_SIZE: 4096 
		range: (0, -1)
	GAMMA_LUT: 0 
		range: (0, 65535)
	CTM: 0 1 0 0 0 0 0 0 0 1 0 0 0 0 0 0 
		0 1 
	DEGAMMA_LUT: 0 
		range: (0, 65535)
	TearFree: auto 
		supported: off, on, auto
	HDCP Content Type: HDCP Type0 
		supported: HDCP Type0, HDCP Type1
	Content Protection: Undesired 
		supported: Undesired, Desired, Enabled
	vrr_capable: 0 
		range: (0, 1)
	max bpc: 8 
		range: (8, 16)
	underscan vborder: 0 
		range: (0, 128)
	underscan hborder: 0 
		range: (0, 128)
	underscan: off 
		supported: off, on, auto
	scaling mode: None 
		supported: None, Full, Center, Full aspect
	link-status: Good 
		supported: Good, Bad
	CONNECTOR_ID: 78 
		supported: 78
	non-desktop: 0 
		range: (0, 1)
   1920x1080     60.00 +  50.00    59.94* 
   4096x2160     24.00    23.98  
   3840x2160     30.00    25.00    24.00    29.97    23.98  
   1680x1050     60.00  
   1280x1024     60.02  
   1440x900      59.90  
   1360x768      60.02  
   1280x800      60.00  
   1280x720      60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       60.00    59.94  
DisplayPort-0 connected primary 1920x1080+0+419 (normal left inverted right x axis y axis) 256mm x 192mm
	_MUTTER_PRESENTATION_OUTPUT: 0 
	EDID: 
		00ffffffffffff002685166500000000
		03190104003c22780a3d25a35951a025
		0f505421080081c08180a940d1c0b300
		90409500a9c064190040410026301888
		360000c010000018662156aa51001e30
		468f330055c01000001e000000fc0044
		503256474120563232360a20302a0008
		52c028306070130040f01000001e00e8
	GAMMA_LUT_SIZE: 4096 
		range: (0, -1)
	DEGAMMA_LUT_SIZE: 4096 
		range: (0, -1)
	GAMMA_LUT: 0 
		range: (0, 65535)
	CTM: 0 1 0 0 0 0 0 0 0 1 0 0 0 0 0 0 
		0 1 
	DEGAMMA_LUT: 0 
		range: (0, 65535)
	TearFree: auto 
		supported: off, on, auto
	subconnector: VGA 
		supported: Unknown, VGA, DVI-D, HDMI, DP, Wireless, Native
	HDCP Content Type: HDCP Type0 
		supported: HDCP Type0, HDCP Type1
	Content Protection: Undesired 
		supported: Undesired, Desired, Enabled
	vrr_capable: 0 
		range: (0, 1)
	max bpc: 8 
		range: (8, 16)
	underscan vborder: 0 
		range: (0, 128)
	underscan hborder: 0 
		range: (0, 128)
	underscan: off 
		supported: off, on, auto
	scaling mode: None 
		supported: None, Full, Center, Full aspect
	link-status: Good 
		supported: Good, Bad
	CONNECTOR_ID: 85 
		supported: 85
	non-desktop: 0 
		range: (0, 1)
   1024x768      60.00 +
   1920x1080     60.00* 
   1600x1200     60.00  
   1680x1050     59.95  
   1400x1050     59.98  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1366x768      59.79  
   1280x720      60.00  
   800x600       60.32  
   640x480       59.94  
$
```

---

### Post by MAFoElffen on 2022-02-06
> **KBar said:**
> Pardon me but I'd suggest a much simpler variation:
```
printenv XDG_SESSION_TYPE
```

True, I am aware of that, but... 

Having written System  Admin applications and scripts for Ubuntu Support, not all editions, configurations, flavors and derivatives of Ubuntu populate that Graphics Layer ENV Variable. In my own scripting, I use that code as a fall back condition, to $XDG_SESSION_TYPE.

In the UbuntuForums 'system-info' script, linked in my signature line, you can see that I use $XDG_SESSION_TYPE as the primary, then fall back to other conditions in case that is not populated... I support the Linux Graphics Layer. I know there are 'variations', where the fall back is needed.

@[**[COLOR=#000000]lalawawa[/COLOR]**]("https://ubuntuforums.org/member.php?u=708587")

Please go back to your last posts and edit them... To wrap your output within CODE tags... Raw posted output does strange things to the Forums system, and is very hard to read. 

If you EDIT Post, then select Go Advanced... Then select the output with left press-mouse, then select the "#" icon, it will wrap that out put with CODE Tags.

You can alternatively manually do it by adding them in manually like this: 
[noparse]```

Put all your output here

```[/noparse]

---

### Post by MAFoElffen on 2022-02-06
I can see where your ports are connected to Displays and that they support the resolutions you want to do... I can see that you are using the amdgpu driver, and using Xorg XServer. I can see where the ports are ID'ed as HDMI-A-0 and DisplayPort-0, and both Displays have a preferred mode of 1920x1080.

You want to create and set a resolution for each, then rotate the output of one of them from portrait to landscape... Your plan should be to create modelines for each (Using CVT), that are not supported (and or get the supported resolutions listed in your Display Settings). Test them. Create a rotate command to change the orientation of the one you want to rotate. Then when you have that working, via commands, add all those to a script that you can call via $HOME/.bashrc... (or in /etc/bash.bashrc if you want the whole system to respect that for all users...)

Why create a script if you go with 'xrandr'? Because the command 'xrandr' is not a persistent solution, and you don't want to have to type in those every time you boot or reboot. Each time the system goes down, it will forget anything 'xrandr' has changed.

OR... You can create a User xorg.conf file to set what you want... The recommendation with that, is that when you get it working, keep a backup of that xorg.conf file somewhere safe, because sometimes that gets removed or changed during updates... Either way will work. 

Each display has pre-defined resolutions that you can set to (stored in their EDID), or you can define your own. The trick is the orientation of. The 'orientation' of used to be a Setting in Settings > Displays, but was removed in about 18.04 or later. (Because of a Bug in some of the Linux Kernel versions).

---

### Post by lalawawa on 2022-02-06
$ find / 2>/dev/null -iname '*xorg.conf*'
/usr/share/X11/xorg.conf.d
/usr/share/doc/xserver-xorg-video-intel/xorg.conf
/usr/share/man/man5/xorg.conf.5.gz
/usr/share/man/man5/xorg.conf.d.5.gz
$
$
$n
$ cat /usr/share/doc/xserver-xorg-video-intel/xorg.conf
Section "Device"
	Identifier "Intel"
	Driver "intel"
#	Option "AccelMethod" "uxa"
EndSection
$ 
$
$
$ cvt 1440 2560
# 1440x2560 59.98 Hz (CVT) hsync: 159.00 kHz; pclk: 318.00 MHz
Modeline "1440x2560_60.00"  318.00  1440 1568 1720 2000  2560 2563 2573 2651 -hsync +vsync
$ 

Do I put the "Modeline" into the xorg.conf?  If so, how do I specify which of the 2 monitors I'm talking about (the monitors have different max resolutions)?

---

### Post by lalawawa on 2022-02-06
$ cd /usr/share/X11/xorg.conf.d
$ ls -aCF
./   10-amdgpu.conf  10-radeon.conf    70-wacom.conf
../  10-quirks.conf  40-libinput.conf
$ cat 10-amdgpu.conf 
Section "OutputClass"
	Identifier "AMDgpu"
	MatchDriver "amdgpu"
	Driver "amdgpu"
EndSection
$

---

### Post by MAFoElffen on 2022-02-07
What the heck are you talking about? This is what I see from your output, at what things are set to at the moment... Both displays have a preferred mode of 1920x1080. That is also what the max res of the Display that is connected to your DisplayPort-0 port. 

The Display that is connected to HDMI-A-0 is a 4K display (4096x2160 DCI)... which has a n Aspect Ratio of 1:1.90. 

Where are you getting 2560x1440 <-- Notice I have the widest first, as this is how your display is when it is in portrait/normal. Saying 1440x2560, if your display 'could' show that as a resolution (it cannot), it will set 1440 across by 2560 high, when the display is turned in a normal orientation, with blank margins on both sides of it. But it cannot display that, as your display is only 2160 high. You have sort of a misunderstanding somewhere.

4k DIC is 4096x2160, which is an Aspect Ratio of 1:1.90.
4k UHD is 3840x2160, which is an AspectRatios of 1:78 (16:9)
1920x1080 or 1080p is an aspect ratios of 1:1.78 (16:9)

That display has no preset resolution between 1080p and 4K... If you were to try to create one, I would keep to an aspect ratio of 16.9, which the one you said you want fro some reason is not even close. (Sorry).

I would say 2048x1152 (2K, 16:9), 2880 x 1620 (3K UHD, 16:9), and/or 3072x1728 (3K, 16:9).... Which anything above 1920x1080 on your display seems to use a refresh rate of 24... But thatis outside of the CVT standard, so I would also try a refresh rate of 60...

```

#!/bin/bash
## Script to add resolution modelines to X using xrandr
## MAFoElffen, 2022.02.06
#  Called by $HOME/.bashrc or by /etc/bash.bashrc

xrandr --newmode "2048x1152_24.00"   71.75  2048 2104 2304 2560  1152 1155 1160 1171 -hsync +vsync
xrandr --newmode "2880x1620_24.00"  145.75  2880 3000 3288 3696  1620 1623 1628 1645 -hsync +vsync
xrandr --newmode "3072x1728_24.00"  167.00  3072 3208 3520 3968  1728 1731 1736 1755 -hsync +vsync
xrandr --newmode "2048x1152_60.00"  197.00  2048 2184 2400 2752  1152 1155 1160 1195 -hsync +vsync
xrandr --newmode "2880x1620_60.00"  396.25  2880 3096 3408 3936  1620 1623 1628 1679 -hsync +vsync
xrandr --newmode "3072x1728_60.00"  451.75  3072 3312 3640 4208  1728 1731 1736 1791 -hsync +vsync
xrandr --newmode "4096x2160_60.00"  760.00  4096 4432 4880 5664  2160 2163 2173 2237 -hsync +vsync

# Add the new mode to the table list of modes of certain output:
# Valid the Mode Names that are above between the quotation marks.
xrandr --addmode HDMI-A-0 2048x1152_24.00
xrandr --addmode HDMI-A-0 2880x1620_24.00
xrandr --addmode HDMI-A-0 3072x1728_24.00
xrandr --addmode HDMI-A-0 2048x1152_60.00
xrandr --addmode HDMI-A-0 2880x1620_60.00
xrandr --addmode HDMI-A-0 3072x1728_60.00
xrandr --addmode HDMI-A-0 4096x2160_60.00

# Set one of the new modes as current for the certain output on a port: 
xrandr --output HDMI-A-0 --mode 2880x1620_60.00

# Valid orientation rotation commands are normal, inverted, right or left.
xrandr --output HDMA-A-0 --rotate left

```
Test each above manually first...

Or in /etc/X11/xorg.conf, but would need some time to work on that for you... If you wanted to go that way... Each above would still need to be tested by you first, before any of that.

BUT-- There used to be an open bug, if tried from xorg.conf, with it crashing... What you used to do was in the Monitor Section for the Display you wanted to rotate, you used "Option Rotate Left"... and for that Bug, using 'xrandr to do the rotate was the work-around.

---

### Post by lalawawa on 2022-02-07
2560x1440 is the resolution of the monitor that I bought.

If I set the resolution about that, the monitor goes blank.

So I tried your script verbatim, and the monitor went blank until I reset it to 1920x1080.

I tried adding 2560x1440 to the list of resolutions, but I get
xrandr: cannot find mode "2560x1440_24.00"
xrandr: cannot find mode 2560x1440_24.00
warning: output HDMA-A-0 not found; ignoring

The thing is, I can easily set the resolution to any of the choices in your script with the "Display" menu from the desktop.  I just want to somehow ad 2560x1440 to the list of choices.

---

### Post by lalawawa on 2022-02-07
If I set the resolution to 2880x1620, the monitor goes blank.

---

### Post by MAFoElffen on 2022-02-07
According to your output from xrandr, xrandr sees that monitor as having these as presets:
```

1920x1080     60.00 +  50.00    59.94* 
   4096x2160     24.00    23.98  
   3840x2160     30.00    25.00    24.00    29.97    23.98  
   1680x1050     60.00  s
   1280x1024     60.02  
   1440x900      59.90  
   1360x768      60.02  
   1280x800      60.00  
   1280x720      60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       60.00    59.94  
```
If I decode your Display's EDID table, here is what it says it is and can do:
```

mafoelffen@Mikes-ThinkPad-T520:~$ edid-decode < /home/mafoelffen/EDID-Test01.bin
edid-decode (hex):

00 ff ff ff ff ff ff 00 61 a4 4a 00 01 00 00 00 
06 1c 01 03 80 73 41 78 0a cf 74 a3 57 4c b0 23 
09 48 4c 21 08 00 81 80 45 40 61 40 95 00 01 01 
01 01 01 01 01 01 02 3a 80 18 71 38 2d 40 58 2c 
45 00 c4 8e 21 00 00 1e 66 21 50 b0 51 00 1b 30 
40 70 36 00 c4 8e 21 00 00 1e 00 00 00 fc 00 4d 
69 20 54 56 0a 20 20 20 20 20 20 20 00 00 00 fd 
00 32 4b 1e 50 17 00 0a 20 20 20 20 20 20 01 e6 

02 03 3c f2 4f 01 03 04 05 07 90 12 13 14 16 1f 
60 61 65 66 2c 09 07 07 11 17 50 51 07 00 3d 07 
c0 83 01 00 00 6e 03 0c 00 20 00 b8 3c 20 80 80 
01 02 03 04 e3 0f 00 78 e3 06 05 01 01 1d 00 bc 
52 d0 1e 20 b8 28 55 40 c4 8e 21 00 00 1e 01 1d 
80 d0 72 1c 16 20 10 2c 25 80 c4 8e 21 00 00 9e 
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 cd 

----------------

EDID version: 1.3
Manufacturer: XMD Model 74 Serial Number 1
Made in week 6 of 2018
Digital display
Maximum image size: 115 cm x 65 cm
Gamma: 2.20
RGB color display
First detailed timing is preferred timing
Color Characteristics
  Red:   0.6396, 0.3398
  Green: 0.2998, 0.6904
  Blue:  0.1376, 0.0380
  White: 0.2822, 0.2968
Established Timings I & II
    640x480    59.940 Hz   4:3    31.469 kHz  25.175 MHz (DMT)
    800x600    60.317 Hz   4:3    37.879 kHz  40.000 MHz (DMT)
   1024x768    60.004 Hz   4:3    48.363 kHz  65.000 MHz (DMT)
Standard Timings
   1280x1024   60.020 Hz   5:4    63.981 kHz 108.000 MHz (DMT)
    800x600    60.317 Hz   4:3    37.879 kHz  40.000 MHz (DMT)
   1024x768    60.004 Hz   4:3    48.363 kHz  65.000 MHz (DMT)
   1440x900    59.887 Hz  16:10   55.935 kHz 106.500 MHz (DMT)
Detailed mode: Clock 148.500 MHz, 708 mm x 398 mm
               1920 2008 2052 2200 ( 88  44 148)
               1080 1084 1089 1125 (  4   5  36)
               +hsync +vsync
               VertFreq: 60.000 Hz, HorFreq: 67.500 kHz
Detailed mode: Clock 85.500 MHz, 708 mm x 398 mm
               1360 1424 1536 1792 ( 64 112 256)
                768  771  777  795 (  3   6  18)
               +hsync +vsync
               VertFreq: 60.015 Hz, HorFreq: 47.712 kHz
Display Product Name: Mi TV
Display Range Limits
  Monitor ranges (GTF): 50-75 Hz V, 30-80 kHz H, max dotclock 230 MHz
Has 1 extension block
Checksum: 0xe6

----------------

CTA-861 Extension Block Revision 3
Underscans PC formats by default
Basic audio support
Supports YCbCr 4:4:4
Supports YCbCr 4:2:2
2 native detailed modes
56 bytes of CTA data blocks
  Video Data Block
      640x480    59.940 Hz   4:3    31.469 kHz  25.175 MHz (VIC   1)
      720x480    59.940 Hz  16:9    31.469 kHz  27.000 MHz (VIC   3)
     1280x720    60.000 Hz  16:9    45.000 kHz  74.250 MHz (VIC   4)
     1920x1080i  60.000 Hz  16:9    33.750 kHz  74.250 MHz (VIC   5)
     1440x480i   59.940 Hz  16:9    15.734 kHz  27.000 MHz (VIC   7)
     1920x1080   60.000 Hz  16:9    67.500 kHz 148.500 MHz (VIC  16, native)
      720x576    50.000 Hz  16:9    31.250 kHz  27.000 MHz (VIC  18)
     1280x720    50.000 Hz  16:9    37.500 kHz  74.250 MHz (VIC  19)
     1920x1080i  50.000 Hz  16:9    28.125 kHz  74.250 MHz (VIC  20)
     1440x576i   50.000 Hz  16:9    15.625 kHz  27.000 MHz (VIC  22)
     1920x1080   50.000 Hz  16:9    56.250 kHz 148.500 MHz (VIC  31)
     3840x2160   50.000 Hz  16:9   112.500 kHz 594.000 MHz (VIC  96)
     3840x2160   60.000 Hz  16:9   135.000 kHz 594.000 MHz (VIC  97)
     4096x2160   50.000 Hz 256:135 112.500 kHz 594.000 MHz (VIC 101)
     4096x2160   60.000 Hz 256:135 135.000 kHz 594.000 MHz (VIC 102)
  Audio Data Block
    Linear PCM, max channels 2
      Supported sample rates (kHz): 48 44.1 32
      Supported sample sizes (bits): 24 20 16
    AC-3, max channels 2
      Supported sample rates (kHz): 96 48 44.1 32
      Maximum bit rate: 640 kb/s
    Dolby Digital+, max channels 2
      Supported sample rates (kHz): 48 44.1 32
    DTS, max channels 6
      Supported sample rates (kHz): 48 44.1 32
      Maximum bit rate: 1536 kb/s
  Speaker Allocation Data Block
    Speaker map:
      FL/FR - Front Left/Right
  Vendor-Specific Data Block, OUI 0x000c03 (HDMI)
    Source physical address 2.0.0.0
    Supports_AI
    DC_36bit
    DC_30bit
    DC_Y444
    Maximum TMDS clock: 300 MHz
    Extended HDMI video details:
      3D present
      HDMI VICs:
         3840x2160   30.000 Hz  16:9    67.500 kHz 297.000 MHz (HDMI VIC 1)
         3840x2160   25.000 Hz  16:9    56.250 kHz 297.000 MHz (HDMI VIC 2)
         3840x2160   24.000 Hz  16:9    54.000 kHz 297.000 MHz (HDMI VIC 3)
         4096x2160   24.000 Hz 256:135  54.000 kHz 297.000 MHz (HDMI VIC 4)
  Extended tag: YCbCr 4:2:0 Capability Map Data Block
     3840x2160   50.000 Hz  16:9   112.500 kHz 594.000 MHz (VIC  96)
     3840x2160   60.000 Hz  16:9   135.000 kHz 594.000 MHz (VIC  97)
     4096x2160   50.000 Hz 256:135 112.500 kHz 594.000 MHz (VIC 101)
     4096x2160   60.000 Hz 256:135 135.000 kHz 594.000 MHz (VIC 102)
  Extended tag: HDR Static Metadata Data Block
    Electro optical transfer functions:
      Traditional gamma - SDR luminance range
      SMPTE ST2084
    Supported static metadata descriptors:
      Static metadata type 1
Detailed mode: Clock 74.250 MHz, 708 mm x 398 mm
               1280 1720 1760 1980 (440  40 220)
                720  725  730  750 (  5   5  20)
               +hsync +vsync
               VertFreq: 50.000 Hz, HorFreq: 37.500 kHz
Detailed mode: Clock 74.250 MHz, 708 mm x 398 mm
               1920 2448 2492 2640 (528  44 148)
                540  542  547  562 (  2   5  15)
               +hsync +vsync
               VertFreq: 50.000i Hz, HorFreq: 28.125 kHz

```
So, ignore the modelines I calc'ed with 24Mhz as he refresh rate...

*** And again... I am not clairvoyant. I cannot quess what display you  have, and you have not said what make and model it is... But from the output of what it say it is and what it's presets are, I still do not see where you are thinking that 2560x1440 is a preferred native resolution of that display. It says/reports that it's preferred is 1920x1080@60Mhz...

2560x1440 is 560 × 1440 (QHD) QHD (Quad HD), WQHD (Wide Quad HD), or 1440p, is a display resolution of 2560 × 1440 pixels in a **16:9** aspect ratio. Your display's EDID table does not mention that it has that as being native... or as a preset. Just saying what I see.

No opinion. No guess. Just the facts from the data you provided...

---

