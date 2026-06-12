---
title: "HDMI does not shows in xrandr"
date: 2018-08-16
forum: General Help
---

### Post by marcosrocha85 on 2018-08-16
Ubuntu 18.04
Single boot

Hello there, I'm with HDMI problems at Ubuntu 18.04 again after this week kernel's update. The last time, after update, the HDMI stopped working and I manage to back again by adding those lines to 10-amdgpu.conf on /usr/share/X11/xorg.conf.d/:
**10-amdgpu.conf**

```

Section "OutputClass"
 Identifier "DisplayLink"
 Driver "modesetting"
EndSection

Section "Monitor"
        Identifier      "MonitorTMDS1"
        Modeline        "1920x1080@60hz"    148.352  1920 1960 2016 2200  1080 1082 1088 1125  +hsync +vsync
        Option          "IgnoreEDID"        "true"
        Option          "PreferredMode"     "1920x1080@60hz"
EndSection

```

But this time stopped again and I can't be able to make work again. Can you guys guide me? I'm using Ubuntu's default interface.

**lspci:**

```

00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b) (prog-if 00 [VGA controller])
 Subsystem: Dell Haswell-ULT Integrated Graphics Controller [1028:0640]
 Flags: bus master, fast devsel, latency 0, IRQ 47
 Memory at b0400000 (64-bit, non-prefetchable) [size=4M]
 Memory at c0000000 (64-bit, prefetchable) [size=256M]
 I/O ports at 5000 [size=64]
 [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
 Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
 Capabilities: [d0] Power Management version 2
 Capabilities: [a4] PCI Advanced Features
 Kernel driver in use: i915
 Kernel modules: i915

03:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [Radeon R7 M260/M265 / M340/M360 / M440/M445] [1002:6900]
 Subsystem: Dell Radeon R7 M260/M265 [1028:0640]
 Flags: bus master, fast devsel, latency 0, IRQ 48
 Memory at a0000000 (64-bit, prefetchable) [size=256M]
 Memory at b0000000 (64-bit, prefetchable) [size=2M]
 I/O ports at 3000 [size=256]
 Memory at b0900000 (32-bit, non-prefetchable) [size=256K]
 Expansion ROM at b0940000 [disabled] [size=128K]
 Capabilities: [48] Vendor Specific Information: Len=08 <?>
 Capabilities: [50] Power Management version 3
 Capabilities: [58] Express Legacy Endpoint, MSI 00
 Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
 Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
 Capabilities: [150] Advanced Error Reporting
 Capabilities: [270] #19
 Capabilities: [2b0] Address Translation Service (ATS)
 Capabilities: [2c0] Page Request Interface (PRI)
 Capabilities: [2d0] Process Address Space ID (PASID)
 Kernel driver in use: amdgpu
 Kernel modules: amdgpu

```

**xrandr:**

```

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080     60.05*+  60.01    59.97    59.96    59.93    48.04
   1680x1050     59.95    59.88
   1600x1024     60.17
   1400x1050     59.98
   1600x900      59.99    59.94    59.95    59.82
   1280x1024     60.02
   1440x900      59.89
   1400x900      59.96    59.88
   1280x960      60.00
   1440x810      60.00    59.97
   1368x768      59.88    59.85
   1360x768      59.80    59.96
   1280x800      59.99    59.97    59.81    59.91
   1152x864      60.00
   1280x720      60.00    59.99    59.86    59.74
   1024x768      60.04    60.00
   960x720       60.00
   928x696       60.05
   896x672       60.01
   1024x576      59.95    59.96    59.90    59.82
   960x600       59.93    60.00
   960x540       59.96    59.99    59.63    59.82
   800x600       60.00    60.32    56.25
   840x525       60.01    59.88
   864x486       59.92    59.57
   800x512       60.17
   700x525       59.98
   800x450       59.95    59.82
   640x512       60.02
   720x450       59.89
   700x450       59.96    59.88
   640x480       60.00    59.94
   720x405       59.51    58.99
   684x384       59.88    59.85
   680x384       59.80    59.96
   640x400       59.88    59.98
   576x432       60.06
   640x360       59.86    59.83    59.84    59.32
   512x384       60.00
   512x288       60.00    59.92
   480x270       59.63    59.82
   400x300       60.32    56.34
   432x243       59.92    59.57
   320x240       60.05
   360x202       59.51    59.13
   320x180       59.84    59.32

```

**/etc/default/grub:**

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
#  radeon.cik_support=0 radeon.si_support=0 amdgpu.si_support=1 amdgpu.cik_support=1 amdgpu.dc=0 amdgpu.dpm=0 i915.alpha_support=1

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
# GRUB_GFXMODE=1920x1080x32

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

**parse-edid:**

```

This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 4
No EDID on bus 6
No EDID on bus 8
2 potential busses found: 5 7
Will scan through until the first EDID is found.
Pass a bus number as an option to this program to go only for that one.
256-byte EDID successfully retrieved from i2c bus 5
Looks like i2c was successful. Have a good day.
Checksum Correct

Section "Monitor"
 Identifier "22MP55"
 ModelName "22MP55"
 VendorName "GSM"
 # Monitor Manufactured week 8 of 2014
 # EDID version 1.3
 # Digital Display
 DisplaySize 480 270
 Gamma 2.20
 Option "DPMS" "true"
 Horizsync 30-83
 VertRefresh 56-61
 # Maximum pixel clock is 150MHz
 #Not giving standard mode: 1152x864, 60Hz
 #Not giving standard mode: 1280x720, 60Hz
 #Not giving standard mode: 1280x800, 60Hz
 #Not giving standard mode: 1280x1024, 60Hz
 #Not giving standard mode: 1440x900, 60Hz
 #Not giving standard mode: 1400x1050, 60Hz
 #Not giving standard mode: 1600x900, 60Hz
 #Not giving standard mode: 1680x1050, 60Hz

 #Extension block found. Parsing...
 Modeline  "Mode 11" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
 Modeline  "Mode 0" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
 Modeline  "Mode 1" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
 Modeline  "Mode 2" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
 Modeline  "Mode 3" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
 Modeline  "Mode 4" 25.200 640 656 752 800 480 490 492 525 -hsync -vsync
 Modeline  "Mode 5" 74.250 1920 2448 2492 2640 1080 1082 1089 1125 +hsync +vsync interlace
 Modeline  "Mode 6" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
 Modeline  "Mode 7" 74.250 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync interlace
 Modeline  "Mode 8" 148.500 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
 Modeline  "Mode 9" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
 Modeline  "Mode 10" 74.250 1280 1720 1760 1980 720 725 730 750 +hsync +vsync
 Modeline  "Mode 12" 74.25 1920 2008 2052 2200 540 542 547 562 +hsync +vsync interlace
 Modeline  "Mode 13" 74.25 1280 1390 1430 1650 720 725 730 750 +hsync +vsync
 Modeline  "Mode 14" 27.00 720 736 798 858 480 489 495 525 -hsync -vsync
 Option "PreferredMode" "Mode 11"
EndSection

```

**lshw -C display**

```

  *-display                
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       manufacturer: Intel Corporation
       Physical ID: 2
       BUS information: pci@0000:00:02.0
       version: 0b
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:b0400000-b07fffff memory:c0000000-cfffffff porta de E/S:5000(tamanho=64) memory:c0000-dffff
  *-display
       description: Display controller
       product: Topaz XT [Radeon R7 M260/M265 / M340/M360 / M440/M445]
       manufacturer: Advanced Micro Devices, Inc. [AMD/ATI]
       Physical ID: 0
       BUS information: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=amdgpu latency=0
       resources: irq:48 memory:a0000000-afffffff memory:b0000000-b01fffff porta de E/S:3000(tamanho=256) memory:b0900000-b093ffff memory:b0940000-b095ffff

```

[B]-- Update --
[/B]After turn off/on my Dell notebook and use it without HDMI connected, turn off/on with HDMI connected magically it back to work. I don't know why, but it worked.

---

