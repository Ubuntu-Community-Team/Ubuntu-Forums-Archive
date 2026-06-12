---
title: "Ubuntu keeps hanging for short periods of time"
date: 2008-01-04
forum: General Help
---

### Post by sttop on 2008-01-04
I recently bought a dv2000 hp laptop and installed ubuntu 7.10 along with vista in it.

The problem is i can't watch any videos using ubuntu because from times to times it stops for a short period of time and comes back to normal.

I also found out this problem probably isn't related only to video, because sometimes it happens while i'm just typing at vim, for example.

At first I thought it could be an HD problem, so I ran fsck at my linux partition but nothing changed.

My computer is a Core Duo 2.0Ghz with 1gb of RAM memory.

Thanks for the help!

---

### Post by ukripper on 2008-01-04
Can you post your Graphics card details

---

### Post by sttop on 2008-01-04
This is what I get with lspci:

Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller

The system is using the intel driver.

---

### Post by ukripper on 2008-01-04
Did you manually install graphics drivers or  ubuntu did it for you?

---

### Post by sttop on 2008-01-04
Ubuntu did it automatically.

---

### Post by ukripper on 2008-01-04
when/ after it hangs can you post output of below commands:

```
cat /var/log/messages
```

and also :```
top
```

---

### Post by sttop on 2008-01-04
The output of top command shortly after the hang:
```
top - 11:12:57 up  1:42,  4 users,  load average: 0.22, 0.27, 0.30
Tasks: 126 total,   1 running, 125 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.3%us,  0.2%sy,  0.0%ni, 83.9%id, 10.6%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1025984k total,   985720k used,    40264k free,    36796k buffers
Swap:  1975984k total,      284k used,  1975700k free,   591656k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
16638 top       15   0 38392  15m 7156 D    9  1.6   1:23.68 mplayer            
16142 root      15   0  399m  52m 8364 S    1  5.2   0:57.00 Xorg               
16588 top       15   0  159m  48m  21m S    0  4.8   0:30.97 firefox-bin        
16673 top       15   0  2368 1172  880 R    0  0.1   0:00.51 top                
    1 root      20   0  2952 1856  532 S    0  0.2   0:01.37 init               
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.06 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.12 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.01 events/1           
   11 root      13  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   31 root      13  -5     0    0    0 S    0  0.0   0:00.02 kblockd/0          
   32 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1           

```

The last lines of the output of cat /var/log/messages:
```
Jan  4 10:36:43 top-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jan  4 10:37:05 top-laptop kernel: [ 3973.352000] audit(1199453824.530:4):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=15657 profile="/usr/sbin/cupsd"
Jan  4 10:37:08 top-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jan  4 10:37:08 top-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jan  4 10:50:45 top-laptop kernel: [ 4793.852000] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
Jan  4 10:50:45 top-laptop kernel: [ 4793.852000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
Jan  4 10:50:45 top-laptop kernel: [ 4793.856000] atkbd.c: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
Jan  4 10:50:45 top-laptop kernel: [ 4793.856000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
```

I was watching the video at 11:00AM.

---

### Post by ukripper on 2008-01-04
Can you post output of the following when it hangs again 
```
cat /var/log/Xorg.0.log
```

---

### Post by sttop on 2008-01-04
That's the output:

```
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7872 kB
(II) intel(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output TV has no monitor section
(II) intel(0): Output VGA disconnected
(II) intel(0): EDID for output VGA
(II) intel(0): Output LVDS connected
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID for output LVDS
(II) intel(0): Manufacturer: LPL  Model: e800  Serial#: 0
(II) intel(0): Year: 2007  Week: 0
(II) intel(0): EDID Version: 1.1
(II) intel(0): Digital Display Input
(II) intel(0): Max H-Image Size [cm]: horiz.: 30  vert.: 19
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.584 redY: 0.347   greenX: 0.323 greenY: 0.542
(II) intel(0): blueX: 0.157 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.0 MHz   Image Size:  304 x 190 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(II) intel(0):  LGPhilipsLCD
(II) intel(0):  LP141WX3-TLB1
(II) intel(0): EDID (in hex):
(II) intel(0):  00ffffffffffff00320c00e800000000
(II) intel(0):  00110101801e13780abf409558528a28
(II) intel(0):  25505400000001010101010101010101
(II) intel(0):  010101010101bc1b00a0502017303020
(II) intel(0):  360030be100000180000000000000000
(II) intel(0):  00000000000000000000000000fe004c
(II) intel(0):  475068696c6970734c43440a000000fe
(II) intel(0):  004c503134315758332d544c4231006e
(II) intel(0): EDID vendor "LPL", prod id 59392
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(II) intel(0): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output TV disconnected
(II) intel(0): EDID for output TV
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TV disconnected
(II) intel(0): Output LVDS using initial mode 1280x800
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xd4300000 - 0xd433ffff (0x40000) MS[B]
        [1] 0   0       0xc0000000 - 0xcfffffff (0x10000000) MS[B]
        [2] 0   0       0xd4200000 - 0xd427ffff (0x80000) MS[B]
        [3] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [4] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [5] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [6] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [7] -1  0       0xd4102400 - 0xd41024ff (0x100) MX[B]
        [8] -1  0       0xd4102000 - 0xd41020ff (0x100) MX[B]
        [9] -1  0       0xd4101c00 - 0xd4101cff (0x100) MX[B]
        [10] -1 0       0xd4101800 - 0xd41018ff (0x100) MX[B]
        [11] -1 0       0xd4101000 - 0xd41017ff (0x800) MX[B]
        [12] -1 0       0xd4100000 - 0xd4100fff (0x1000) MX[B]
        [13] -1 0       0xd4000000 - 0xd4000fff (0x1000) MX[B]
        [14] -1 0       0xd4544400 - 0xd45447ff (0x400) MX[B]
        [15] -1 0       0xd4544000 - 0xd45443ff (0x400) MX[B]
        [16] -1 0       0xd4340000 - 0xd4343fff (0x4000) MX[B]
        [17] -1 0       0xd4280000 - 0xd42fffff (0x80000) MX[B](B)
        [18] -1 0       0xd4300000 - 0xd433ffff (0x40000) MX[B](B)
        [19] -1 0       0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
        [20] -1 0       0xd4200000 - 0xd427ffff (0x80000) MX[B](B)
        [21] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [22] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [23] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [24] 0  0       0x00001800 - 0x00001807 (0x8) IS[B]
        [25] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [26] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [27] -1 0       0x00003000 - 0x0000303f (0x40) IX[B]
        [28] -1 0       0x000018e0 - 0x000018ff (0x20) IX[B]
        [29] -1 0       0x000018b0 - 0x000018bf (0x10) IX[B]
        [30] -1 0       0x000018c0 - 0x000018c3 (0x4) IX[B]
        [31] -1 0       0x000018c8 - 0x000018cf (0x8) IX[B]
        [32] -1 0       0x000018c4 - 0x000018c7 (0x4) IX[B]
        [33] -1 0       0x000018d0 - 0x000018d7 (0x8) IX[B]
        [34] -1 0       0x00001810 - 0x0000181f (0x10) IX[B]
        [35] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [36] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [37] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [38] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [39] -1 0       0x00001880 - 0x0000189f (0x20) IX[B]
        [40] -1 0       0x00001860 - 0x0000187f (0x20) IX[B]
        [41] -1 0       0x00001840 - 0x0000185f (0x20) IX[B]
        [42] -1 0       0x00001820 - 0x0000183f (0x20) IX[B]
        [43] -1 0       0x00001800 - 0x00001807 (0x8) IX[B](B)
        [44] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [45] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 238592 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 954364 kB available
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
               large DRI memory manager reservation:
(II) intel(0): Allocating 4860 scanlines for pixmap cache
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(II) intel(0): Memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB, 0x        3f820000 physical)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00032fff: overlay registers (4 kB, 0x        3f832000 physical)
(II) intel(0): 0x00040000-0x03037fff: front buffer (49120 kB)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x03038000-0x03047fff: xaa scratch (64 kB)
(II) intel(0): 0x04000000-0x04ffffff: back buffer (10240 kB)
(II) intel(0): 0x05000000-0x05ffffff: depth buffer (10240 kB)
(II) intel(0): 0x06000000-0x07ffffff: DRI memory manager (32768 kB)
(II) intel(0): 0x08000000-0x09ffffff: textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): front buffer is not tiled
(II) intel(0): back buffer is tiled
(II) intel(0): depth buffer is tiled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): [drm] DRM interface version 1.3
(II) intel(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) intel(0): [drm] added 8192 byte SAREA at 0xf8c48000
(II) intel(0): [drm] mapped SAREA 0xf8c48000 to 0xb7b03000
(II) intel(0): [drm] framebuffer handle = 0xc0040000
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): Unable to use TTM-based memory manager with DRM version 1.6
(II) intel(0): [drm] Registers = 0xd4200000
(II) intel(0): [drm] ring buffer = 0xc0000000
(II) intel(0): [drm] init sarea width,height = 1280 x 1280 (pitch 2048)
(II) intel(0): [drm] Mapping front buffer
(II) intel(0): [drm] Front Buffer = 0x28008000
(II) intel(0): [drm] Back Buffer = 0xc4000000
(II) intel(0): [drm] Depth Buffer = 0xc5000000
(II) intel(0): [drm] textures = 0xc8000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xc0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
        Solid Horizontal and Vertical Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                32 128x128 slots
                32 256x256 slots
                16 512x512 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x03038000 (pgoffset 12344)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x04000000 (pgoffset 16384)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x05000000 (pgoffset 20480)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x08000000 (pgoffset 32768)
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(**) Option "dpms"
(**) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(II) intel(0): [DRI] installation complete
(II) intel(0): [drm] dma control initialized, using IRQ 22
(II) intel(0): direct rendering: Enabled
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 304 x 190
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Synaptics Touchpad touchpad found
(II) intel(0): Output VGA disconnected
(II) intel(0): EDID for output VGA
(II) intel(0): Output LVDS connected
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID for output LVDS
(II) intel(0): Manufacturer: LPL  Model: e800  Serial#: 0
(II) intel(0): Year: 2007  Week: 0
(II) intel(0): EDID Version: 1.1
(II) intel(0): Digital Display Input
(II) intel(0): Max H-Image Size [cm]: horiz.: 30  vert.: 19
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.584 redY: 0.347   greenX: 0.323 greenY: 0.542
(II) intel(0): blueX: 0.157 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.0 MHz   Image Size:  304 x 190 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(II) intel(0):  LGPhilipsLCD
(II) intel(0):  LP141WX3-TLB1
(II) intel(0): EDID (in hex):
(II) intel(0):  00ffffffffffff00320c00e800000000
(II) intel(0):  00110101801e13780abf409558528a28
(II) intel(0):  25505400000001010101010101010101
(II) intel(0):  010101010101bc1b00a0502017303020
(II) intel(0):  360030be100000180000000000000000
(II) intel(0):  00000000000000000000000000fe004c
(II) intel(0):  475068696c6970734c43440a000000fe
(II) intel(0):  004c503134315758332d544c4231006e
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync
(II) intel(0): EDID vendor "LPL", prod id 59392
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(II) intel(0): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output TV disconnected
(II) intel(0): EDID for output TV

```

---

### Post by ukripper on 2008-01-04
Display drivers seems to have been loaded properly. Are you playing video online or from your local HDD

---

### Post by sttop on 2008-01-04
From my local HD.

---

### Post by Junosix on 2008-01-04
Do you know if the hard disk is SATA?  There's apparently a known bug that causes a delay for a fraction of a second every now and again.  It happens on my Dell Dimension C521 desktop, which has a SATA drive.

---

### Post by ukripper on 2008-01-04
try running some video from external USB stick or drive.

---

### Post by sttop on 2008-01-04
> Do you know if the hard disk is SATA? There's apparently a known bug that causes a delay for a fraction of a second every now and again. It happens on my Dell Dimension C521 desktop, which has a SATA drive.

yeah, it's a SATA hard disk! is there a fix for this?

> try running some video from external USB stick or drive.

i'll try and post the results!

---

### Post by sttop on 2008-01-07
Could someone tell me more about this bug with the SATA drives? I've searched for it on the net but couldn't find anything useful... =/

---

### Post by ukripper on 2008-01-08
> **sttop said:**
> Could someone tell me more about this bug with the SATA drives? I've searched for it on the net but couldn't find anything useful... =/

Have you tried external disk or usb yet before concluding it is a SATA bug?

---

### Post by jeffus_il on 2008-01-08
I see firefox was running, did it have many tabs open and is it possible that it was displaying pages with heavy graphics, like flash, shockwave?

---

### Post by julian67 on 2008-01-08
This is unlikely to be a problem in the Intel Graphics which are extremely reliable.  A lot of system freezes are due to a firmware bug in the optical drive. This can affect the whole system because the kernel hangs. If you google or search Launchpad for TSST you'll see more. Here's a quote from [https://bugs.launchpad.net/linux/+bug/75295/comments/97]("https://bugs.launchpad.net/linux/+bug/75295/comments/97")> Background:
TSST stands for "Toshiba Samsung Storage Technology". Samsung provides these drives in their own laptops but they also provide them to other laptop companies such as Asus, Acer, HP and others. If you have a Samsung laptop your firmware version will likely begin with SC (however other possibilities exist). I have an ASUS so the firmware has been labeled ASxx. More on this if you goto [http://www.samsungodd.com](http://www.samsungodd.com) and then FIRMWARE->Check F/W VERSION. Samsung appears to provide a customised firmware product to other laptop companies. However, Samsung only supports their drives in their laptops. Other laptop companies must pass on firmware upgrades independently, which in the case of ASUS doesn't appear to be happening. Some other laptop companies may do this- you'll have to check.

A quick web search shows that these drives are causing trouble for numerous OS platforms including MSwindows (although the problem manifests itself a little differently on MSWindows). I'll assert at this point that I think this bug is not an Ubuntu bug nor is it a Linux kernel bug: it is a manufacturer firmware bug. However, having said that, I am very grateful that this did exist as a bug in Ubuntu's Launchpad because world-wide, Launchpad has been the best source of information about this problem with some excellent discussion and ideas.

For me the only solution available was to cross-flash with SCxx firmware to replace my buggy AS05 firmware and hope that the differences between the custom AS05 and SCxx are negligible. It seems that in the case of the A6Rp the differences are indeed negligible or perhaps non-existent.

You can check your drive and firmware version in Ubuntu by going: System>Preferences>Hardware Information ; Now look for your drive. Under the "advanced" tab you will find > 'info.product' & also 'storage.product' which will say something like "TSSTcorpCD/DVD TS-L632D" ; and, 'storage.firmware_version' which may say "AS05". Alternatively, you can download "WININQUIRY.EXE" from [http://www.samsungodd.com](http://www.samsungodd.com) and then FIRMWARE>Check F/W VERSION and run this in MSWindows or run it in Ubuntu using wine (It works perfectly with wine in Ubuntu feisty).

Note that some laptops that have Samsung drives which are not model TS-L632D are reported to have been successfully flashed with the SCxx firmware for the TS-L632D drive (see Andreas on 2007-08-04 above in this bug commentary).

Below I outline my solution and I also provide reference to a solution if you don't have an MSwindows partition.

I'm not sure this is your difficulty but it is far more lilely than buggy Intel GMA firmware or drivers, which are open source, extremely widely used and well proven.

---

### Post by ukripper on 2008-01-08
We should proceed through the process of eliminiation while troubleshooting, rather than just hitting in the dark.

Could you try using USB disk or drive first before we proceed and posts the results whether it still hangs?

---

### Post by julian67 on 2008-01-08
> **ukripper said:**
> We should proceed through the process of eliminiation while troubleshooting, rather than just hitting in the dark.

Could you try using USB disk or drive first before we proceed and posts the results whether it still hangs?

Yes, but Intel GMA is probably the least likely source of the problem, whereas this is a common problem with a known cause and a possible fix (firmware upgrade), so my inclination would be to look at the common and well known causes first and if that draws a blank then start looking at the less likely ones. But I'll leave this thread alone now, you have it in hand.

---

### Post by ukripper on 2008-01-08
> **julian67 said:**
> Yes, but Intel GMA is probably the least likely source of the problem, whereas this is a common problem with a known cause and a possible fix (firmware upgrade), so my inclination would be to look at the common and well known causes first and if that draws a blank then start looking at the less likely ones. But I'll leave this thread alone now, you have it in hand.

Do you know firmware upgrade can cripple system if it goes wrong.i would choose it as last resort.

---

### Post by dark_harmonics on 2008-01-08
> **ukripper said:**
> Do you know firmware upgrade can cripple system if it goes wrong.i would choose it as last resort.

I agree except when I'm wrong! HAHA!
 It has happened to me only a few times over the years where it was needed, but most of the time I don't run firmware upgrades. There are several reasons for this that don't really relate to this subject.  

I have had my Ubuntu hang like this before, and it was related to the fact that i was running "big desktop" on my ATI video card (macbook pro which has a radeon x1600). The system would just randomly hang for 5-10 seconds. There wasn't any catalyst that I could tell other than the video driver. I switched back to single screen as a test for a day, and it ran without error. 

Based on my experience then, I would support the graphics theory.

---

### Post by sttop on 2008-01-08
hey guys, i just tested watching a video file stored at my iPod and it seemed to work preety well. I watched it for, like, 10 minutes and the system didn't hang once. I'll try to watch it any longer and see what happens later.

For now, is my problem really this SATA bug or should I run more tests?

---

### Post by julian67 on 2008-01-08
> **ukripper said:**
> Do you know firmware upgrade can cripple system if it goes wrong.i would choose it as last resort.

Well, a firmware upgrade to an optical device firmware could potentially brick that particular device, not the system as a whole.  Firmware upgrades are always a *potential* problem;  I'd never upgrade a firmware unless certain that the updated firmware addresses a specific problem I actually have or implements a feature I need.  Having said that, I've never crippled any device this way, probably because I follow the vendor's instructions and have never had a power outage during an upgrade.

---

### Post by ukripper on 2008-01-08
> **sttop said:**
> hey guys, i just tested watching a video file stored at my iPod and it seemed to work preety well. I watched it for, like, 10 minutes and the system didn't hang once. I'll try to watch it any longer and see what happens later.

For now, is my problem really this SATA bug or should I run more tests?

Now lets concentrate on resolving your disk  problem atleast now we have isolated the problem area component that is your internal drive

---

### Post by ukripper on 2008-01-08
> **julian67 said:**
> Well, a firmware upgrade to an optical device firmware could potentially brick that particular device, not the system as a whole.  Firmware upgrades are always a *potential* problem;  I'd never upgrade a firmware unless certain that the updated firmware addresses a specific problem I actually have or implements a feature I need.  Having said that, I've never crippled any device this way, probably because I follow the vendor's instructions and have never had a power outage during an upgrade.

I bricked many PICs while  programming them in assembly, I guess I would still consider firmware upgrade  as a last resort.

---

### Post by sttop on 2008-01-09
I just tried watching a video file stored at my iPod for more time and no hangs happened. is there anything i could do to fix this SATA bug?

---

