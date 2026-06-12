---
title: "LUBUNTU HDMI not detected"
date: 2017-10-08
forum: General Help
---

### Post by nodirashidov on 2017-10-08
I am on ASUS D540S laptop
When I just installed LUBUNTU 16.04, I could not get HDMI port to work, it would not detect any monitors. After searching the web for months and trying different solutions, nothing worked for me, and I thought that the HDMI port on my laptop was broken. Then when I started feeling that the default display was too small for me, I tried again, and after I ran these commands:

sudo apt-get install xserver-xorg-video-intel
sudo apt-get install mesa-utils
sudo apt-get install compizconfig-settings-manager

And rebooted, the hdmi monitor suddenly started working. And I thought the problem was fixed.

I recently got a new monitor for lab, and the problem is back. When I connect the hdmi to my laptop a message saying "HDMI No Signal" pops up on the monitor. My laptop will refuse to detect the monitor. (I am not/cannot use the same HDMI cable as the one with the working monitor

Here is more info:


lspci -vk | grep -iA20 vga
```


00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller (rev 21) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller
        Flags: bus master, fast devsel, latency 0, IRQ 312
        Memory at 80000000 (64-bit, non-prefetchable) [size=16M]
        Memory at 90000000 (64-bit, prefetchable) [size=256M]
        I/O ports at f000 [size=64]
        [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915


00:0b.0 Signal processing controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller (rev 21)
        Subsystem: ASUSTeK Computer Inc. Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller
        Flags: bus master, fast devsel, latency 0, IRQ 314
        Memory at 8141f000 (64-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: proc_thermal
        Kernel modules: processor_thermal_device


00:13.0 SATA controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SATA Controller (rev 21) (prog-if 01 [AHCI 1.0])
        Subsystem: ASUSTeK Computer Inc. Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SATA Controller

```



xrandr
```

Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
eDP-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768      60.00*+
   1360x768      59.80    59.96  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)


```


cat /etc/default/grub
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```


sudo apt install read-edid && sudo get-edid | parse-edid
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
read-edid is already the newest version (3.0.2-1).
0 upgraded, 0 newly installed, 0 to remove and 137 not upgraded.
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 4
No EDID on bus 5
No EDID on bus 6
No EDID on bus 8
No EDID on bus 9
1 potential busses found: 7
256-byte EDID successfully retrieved from i2c bus 7
Looks like i2c was successful. Have a good day.
Checksum Correct


Section "Monitor"
    Identifier " 
                     @"
    ModelName " 
                    @"
    VendorName "CMN"
    # Monitor Manufactured week 34 of 2014
    # EDID version 1.4
    # Digital Display
    DisplaySize 340 190
    Gamma 2.20
    Option "DPMS" "false"
    Modeline     "Mode 0" 76.42 1366 1434 1479 1592 768 772 779 800 -hsync -vsync 
EndSection

```

---

### Post by mörgæs on 2017-10-11
Hi, welcome to the fora.

How does 17.10 work?

---

