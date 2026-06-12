---
title: "problems instaling 6.06 on netfinity 5000"
date: 2007-02-21
forum: General Help
---

### Post by jhonijim on 2007-02-21
i recently got a netfinity 5000 server used. when i boot of the 6.06 cd is begins loading and then the screen goes blank and i get an error on screen that says that it is working outside its maximum resolution and when i plug in a diferent monitor it does nothing just a blank screen the only way i got it to load is in safe graphics mode but after install it wont let me set my resolution higher than 640x480 is there a way to force a resoluton change? or get it to boot off the cd?

---

### Post by garrye on 2007-09-10
Presently grappling with this myself.  For you the solution could be to find an addin card with more memory.  You could also FORCE 1024X768 while using 256 colors which would be very boring.  A happier medium would be to use 800X600 and run your color depth up to 16 bits (a.k.a 65536 colors).  Now on to what brought me here in the first place.

Netfinity 5000 PCI video (no AGP) X won't start

Recently did a bit O work for a guy and took is aged but working Netfinity 5000 (Type 8659-31Y).  This thing sports a single PII-100 processor running @ 450 Mhz.  Some time ago the local retailer made me a gift of a bag full of ECC memory which somebody had ordered and never picked up.  Filled the slots up with this stuff and did a memtest on it to make sure the entire 1024 Mb of memory tested good.  This thing has an onboard SCSI controller which has five drives attached to it for a total of about 35 Gb of space.  Using the built in diagnostics all drives appear in good shape.  The installed (but very boring) NT4 works like a charm.  I poke about the RAID  volumes, do a bit o surfing and after a while decide it is time to have some real fun.

A variety of Ubuntu live CD's don't work.  Problems with X.  Elive works, but...  I try DSL a knoppix live CD and while there are problems because of the limited video memory, I am able to work with the machine, surf for info, mount and umount the drives and examine their contents.  I pull out a Ubuntu 6.10 alternate install, clean off all the drives and install.  No raid volumes, no LVM or EVMS, just format to Ext3 and pick mount points to make up a simple filesystem.

Still no worky, so I fire up the DSL again and below is the results of what I've found so far poking around the installed filesystem and the logs in the hopes of finding a clue as to what is wrong.

Here's what I have so far:

/var/log/xorg.0.log contains the following (possibly helpful) entries.  All other entries seem in order and there are NO indications of any unresolved symbols.

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4906]
1: [0xffffe420]
2: /usr/lib/xorg/modules/drivers/apm_drv.so [0x37a5c05d]
3: /usr/lib/xorg/modules/libshadowfb.so [0x379dbec3]
4: /usr/bin/X(miWindowExposures+0x1e3) [0x80ff01f]
5: /usr/bin/X [0x80c4ee9]
6: /usr/bin/X(MapWindow+0x255) [0x80738d9]
7: /usr/bin/X(InitRootWindow+0xb6) [0x8073b7f]
8: /usr/bin/X(main+0x69b) [0x806e2c7]
9: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0x37df9ea2]
10: /usr/bin/X(FontFileCompleteXLFD+0x81) [0x806d611]

Fatal server error:
Caught signal 11.  Server aborting

And finally the xorg log shows that both the onboard (and disabled) and addin video card have been detected!
(--) PCI:*(0:1:0) Alliance Semiconductor Corporation ProMotion AT3D rev 2, Mem @ 0xfd000000/24, I/O @ 0x2000/4
(--) PCI: (0:10:0) S3 Inc. 86c775/86c785 [Trio 64V2/DX or /GX] rev 22, Mem @ 0x50000000/26, BIOS @ 0x000c0000/16

Oh and here's xorg.conf:

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
EndSection

Section "Device"
    Identifier    "Alliance Semiconductor Corporation ProMotion AT3D"
    Driver        "apm"
    BusID        "PCI:0:1:0"
#    VideoRam    4096
    Option        "ShadowFB"
    Option        "SWcursor"
    Option        "noaccel"
    Option        "nolinear"
EndSection

****************************************************
note that the changes to the above section are as per instructions I found in a pdf
 ---> Information for Alliance Promotion chipset users
--->Loïc Grenié ,  Henrik Harmsen,  6 March 2000
****************************************************

Section "Monitor"
    Identifier    "DELL E156FP"
    Option        "DPMS"
    HorizSync    28-49
    VertRefresh    43-72
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Alliance Semiconductor Corporation ProMotion AT3D"
    Monitor        "DELL E156FP"
    DefaultDepth    16
    SubSection "Display"
        Depth        1
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "DRI"
    Mode    0666
EndSection

This thing has NO AGP hardware.  Although I'm surprised to see AGPGART getting in on the action, its results are not surprising:
[4294727.617000] Linux agpgart interface v0.101 (c) Dave Jones
[4294727.630000] agpgart: unable to determine aperture size.
[4294727.630000] agpgart: agp_backend_initialize() failed.
[4294727.630000] agpgart-serverworks: probe of 0000:00:00.0 failed with error -22

Here is a chunk from daemon.log in case that's useful:
Sep 10 02:53:23 finitybuntu hcid[4752]: Can't get system message bus name: Connection ":1.1" is not allowed to own the service "org.bluez" due to security policies in the configuration file
Sep 10 02:53:23 finitybuntu sdpd[4757]: Bluetooth SDP daemon
Sep 10 02:53:29 finitybuntu gdm[4659]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Sep 10 02:53:29 finitybuntu gdm[4050]: deal_with_x_crashes: Running the XKeepsCrashing script
Sep 10 03:04:01 finitybuntu init: Switching to runlevel: 0
Sep 10 03:04:02 finitybuntu gdm[4050]: Failed to start X server several times in a short time period; disabling display :0
Sep 10 03:04:13 finitybuntu sdpd[4757]: terminating...  
Sep 10 03:04:13 finitybuntu hcid[4752]: Exit.

And here is a couple of bits from dmesg.
The PnP Bios is giving trouble as show by this:
[4294671.180000] pnp: PnP ACPI init
[4294671.196000] pnp: PnP ACPI: found 15 devices
[4294671.196000] PnPBIOS: Disabled by ACPI PNP
[4294671.196000] PCI: Using ACPI for IRQ routing
[4294671.196000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

The SMBus is also misbehaving (it seems) as shown by:
[4294729.325000] piix4_smbus 0000:00:0f.0: Found 0000:00:0f.0 device
[4294729.325000] piix4_smbus 0000:00:0f.0: Unusual config register value
[4294729.325000] piix4_smbus 0000:00:0f.0: Try using fix_hstcfg=1 if you experience problems
[4294729.325000] piix4_smbus 0000:00:0f.0: Host SMBus controller not enabled!

And yes I've tried adding "pci=routeirq fix_hstcfg=1" to the boot line.

We also have to following from /var/log/messages:
Sep  9 04:19:08 finitybuntu kernel: [4294759.586000] IBM machine detected. Enabling interrupts during APM calls.
WOO HOOOOOO!!!

Anybody have an idea what's causing all this?  Is it the lack of AGP hardware to do video?  Could this be the problem?

---

