---
title: "Vmware crash"
date: 2007-03-15
forum: General Help
---

### Post by leona on 2007-03-15
Hi there

I've put up this as a vmware crash, but I don't think its vmware at fault here.

I have an vmware image of XP.

I was originally on an FAT32 drive, but it got to big >4gb and then wouldn't load anymore.  So I've moved it to my other computer which has more space and its on NTFS.

It loads fine when I use it via my windows VM player (ya I know windows running windows, but I had to test it! :) ).

But Linux refuses to load it.

The image is stored as I say on another computer so I use SMB to mount that network drive and read the file.

So my guess is that there is some sort of limit on SMB / Linux Mount that is preventing VMplayer from reading / writing to this image.

The errors I get are.

```

Mar 15 20:25:06: vmx| Log for VMware Player pid=10300 version=1.0.1 build=build-19317 option=Release
Mar 15 20:25:06: vmx| Command line: "/usr/lib/vmware-player/bin/vmware-vmx" "-@" "pipe=/tmp/vmware-leona/vmx8a65ca2e99a0f97c;vm=8a65ca2e99a0f97c" "/home/leona/network/Windows XP Professional/Windows XP Professional.vmx"
Mar 15 20:25:06: vmx| UI Connecting to pipe '/tmp/vmware-leona/vmx8a65ca2e99a0f97c' with user '(null)'
Mar 15 20:25:06: vmx| Using system libcrypto, version 90703F
Mar 15 20:25:06: vmx| pcpu #0 CPUID numEntries=1 AuthcAMDenti
Mar 15 20:25:06: vmx| pcpu #0 CPUID version=0x20ff0 id1.edx=0x78bfbff id1.ecx=0x1 id1.ebx=0x800
Mar 15 20:25:06: vmx| pcpu #0 CPUID id80.eax=80000018 id81.edx=0xe3d3fbff id81.ecx=0x1
Mar 15 20:25:06: vmx| CPUID id1.edx: 0x78bfbff id1.ecx: 0x1 id81.edx: 0xe3d3fbff id81.ecx: 0x1
Mar 15 20:25:06: vmx| CPUID id88.ecx: 0 id88.edx: 0
Mar 15 20:25:06: vmx| Setup symlink /var/run/vmware/%2fhome%2fleona%2fnetwork%2fWindows%20XP%20Professional%2fWindows%20XP%20Professional%2evmx -> /var/run/vmware/leona/10300
Mar 15 20:25:06: vmx| ACL_InitCapabilities: here 1 (bug 63252)
Mar 15 20:25:06: vmx| changing directory to /home/leona/network/Windows XP Professional/.
Mar 15 20:25:06: vmx| Config file: /home/leona/network/Windows XP Professional/Windows XP Professional.vmx
Mar 15 20:25:06: vmx| VMXVmdbCbVmVmxExecState: Exec state change requested to state poweredOn without reset
Mar 15 20:25:06: vmx| TOOLS delaying state change request to state 3
Mar 15 20:25:06: vmx| PowerOn
Mar 15 20:25:06: vmx| Host ACPI: can't find SRAT
Mar 15 20:25:06: vmx| HOST sysname Linux, nodename leona-amd64-3Ghz, release 2.6.15-27-amd64-generic, version #1 SMP PREEMPT Fri Dec 8 17:50:54 UTC 2006, machine x86_64, SMP, hz=250
Mar 15 20:25:06: vmx| DICT --- USER PREFERENCES
Mar 15 20:25:06: vmx| DICT       pref.grabOnKeyPress = FALSE
Mar 15 20:25:06: vmx| DICT    pref.autoFitFullScreen = fitHostToGuest
Mar 15 20:25:06: vmx| DICT     pref.view.navBar.type = favorites
Mar 15 20:25:06: vmx| DICT     pref.mruDest0.present = FALSE
Mar 15 20:25:06: vmx| DICT  pref.mruDest0.destString = 
Mar 15 20:25:06: vmx| DICT        pref.mruDest0.user = 
Mar 15 20:25:06: vmx| DICT     pref.mruDest1.present = FALSE
Mar 15 20:25:06: vmx| DICT  pref.mruDest1.destString = 
Mar 15 20:25:06: vmx| DICT        pref.mruDest1.user = 
Mar 15 20:25:06: vmx| DICT     pref.mruDest2.present = FALSE
Mar 15 20:25:06: vmx| DICT  pref.mruDest2.destString = 
Mar 15 20:25:06: vmx| DICT        pref.mruDest2.user = 
Mar 15 20:25:06: vmx| DICT     pref.mruDest3.present = FALSE
Mar 15 20:25:06: vmx| DICT  pref.mruDest3.destString = 
Mar 15 20:25:06: vmx| DICT        pref.mruDest3.user = 
Mar 15 20:25:06: vmx| DICT     pref.mruDest4.present = FALSE
Mar 15 20:25:06: vmx| DICT  pref.mruDest4.destString = 
Mar 15 20:25:06: vmx| DICT        pref.mruDest4.user = 
Mar 15 20:25:06: vmx| DICT     pref.mruDest5.present = FALSE
Mar 15 20:25:06: vmx| DICT  pref.mruDest5.destString = 
Mar 15 20:25:06: vmx| DICT        pref.mruDest5.user = 
Mar 15 20:25:06: vmx| DICT     pref.mruDest6.present = FALSE
Mar 15 20:25:06: vmx| DICT  pref.mruDest6.destString = 
Mar 15 20:25:06: vmx| DICT        pref.mruDest6.user = 
Mar 15 20:25:06: vmx| DICT     pref.mruDest7.present = FALSE
Mar 15 20:25:06: vmx| DICT  pref.mruDest7.destString = 
Mar 15 20:25:06: vmx| DICT        pref.mruDest7.user = 
Mar 15 20:25:06: vmx| DICT       webUpdate.checkLast = 1165596620
Mar 15 20:25:06: vmx| DICT webUpdate.lastCheck.status = done_updates
Mar 15 20:25:06: vmx| DICT pref.vmplayer.confirmOnExit = TRUE
Mar 15 20:25:06: vmx| DICT pref.vmplayer.fullscreen.autohide = TRUE
Mar 15 20:25:06: vmx| DICT pref.vmplayer.deviceBarToplevel = TRUE
Mar 15 20:25:06: vmx| DICT pref.vmplayer.vmPos0.index = 2
Mar 15 20:25:06: vmx| DICT pref.vmplayer.vmPos0.vmPath = /vm/#b1c3f31da01b2540/
Mar 15 20:25:06: vmx| DICT pref.vmplayer.vmPos0.geometry = 1012x666+1+31
Mar 15 20:25:06: vmx| DICT pref.vmplayer.exit.vmAction = poweroff
Mar 15 20:25:06: vmx| DICT pref.vmplayer.webUpdateOnStartup = FALSE
Mar 15 20:25:06: vmx| DICT pref.vmplayer.vmPos1.index = 1
Mar 15 20:25:06: vmx| DICT pref.vmplayer.vmPos1.vmPath = /vm/#6cb43d17da636202/
Mar 15 20:25:06: vmx| DICT pref.vmplayer.vmPos1.geometry = 646x550+170+66
Mar 15 20:25:06: vmx| DICT pref.vmplayer.vmPos2.index = 0
Mar 15 20:25:06: vmx| DICT pref.vmplayer.vmPos2.vmPath = /vm/#1e147ca0326ea29e/
Mar 15 20:25:06: vmx| DICT pref.vmplayer.vmPos2.geometry = 646x550+200+76
Mar 15 20:25:06: vmx| DICT --- USER DEFAULTS
Mar 15 20:25:06: vmx| DICT --- HOST DEFAULTS
Mar 15 20:25:06: vmx| DICT    vmnet1.hostonlyaddress = 192.168.166.1
Mar 15 20:25:06: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
Mar 15 20:25:06: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
Mar 15 20:25:06: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
Mar 15 20:25:06: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
Mar 15 20:25:06: vmx| DICT                    libdir = /usr/lib/vmware-player
Mar 15 20:25:06: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Mar 15 20:25:06: vmx| DICT --- SITE DEFAULTS
Mar 15 20:25:06: vmx| DICT                  tag.help = introduction.htm
Mar 15 20:25:06: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Mar 15 20:25:06: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Mar 15 20:25:06: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Mar 15 20:25:06: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Mar 15 20:25:06: vmx| DICT             tag.netConfig = devices_netadapter.htm
Mar 15 20:25:06: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Mar 15 20:25:06: vmx| DICT          tag.serialConfig = devices_serial.htm
Mar 15 20:25:06: vmx| DICT           tag.soundConfig = devices_sound.htm
Mar 15 20:25:06: vmx| DICT             tag.memConfig = configvm_memory.htm
Mar 15 20:25:06: vmx| DICT            tag.miscConfig = configvm.htm
Mar 15 20:25:06: vmx| DICT             tag.usbConfig = devices_usb.htm
Mar 15 20:25:06: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Mar 15 20:25:06: vmx| DICT                 tag.tools = vmtools.htm
Mar 15 20:25:06: vmx| DICT --- COMMAND LINE
Mar 15 20:25:06: vmx| DICT             gui.available = TRUE
Mar 15 20:25:06: vmx| DICT --- CONFIGURATION
Mar 15 20:25:06: vmx| DICT            config.version = 8
Mar 15 20:25:06: vmx| DICT         virtualHW.version = 4
Mar 15 20:25:06: vmx| DICT             scsi0.present = TRUE
Mar 15 20:25:06: vmx| DICT                   memsize = 256
Mar 15 20:25:06: vmx| DICT     MemAllowAutoScaleDown = FALSE
Mar 15 20:25:06: vmx| DICT            ide0:0.present = TRUE
Mar 15 20:25:06: vmx| DICT           ide0:0.fileName = Windows XP Professional.vmdk
Mar 15 20:25:06: vmx| DICT            ide1:0.present = TRUE
Mar 15 20:25:06: vmx| DICT           ide1:0.fileName = D:\Files\build\WinLite.iso
Mar 15 20:25:06: vmx| DICT         ide1:0.deviceType = cdrom-image
Mar 15 20:25:06: vmx| DICT          floppy0.fileName = A:
Mar 15 20:25:06: vmx| DICT         ethernet0.present = TRUE
Mar 15 20:25:06: vmx| DICT               usb.present = TRUE
Mar 15 20:25:06: vmx| DICT             sound.present = TRUE
Mar 15 20:25:06: vmx| DICT          sound.virtualDev = es1371
Mar 15 20:25:06: vmx| DICT            sound.fileName = -1
Mar 15 20:25:06: vmx| DICT          sound.autodetect = TRUE
Mar 15 20:25:06: vmx| DICT               displayName = Windows XP Professional
Mar 15 20:25:06: vmx| DICT                   guestOS = winxppro
Mar 15 20:25:06: vmx| DICT                     nvram = Windows XP Professional.nvram
Mar 15 20:25:06: vmx| DICT               ide0:0.redo = 
Mar 15 20:25:06: vmx| DICT     ide1:0.startConnected = TRUE
Mar 15 20:25:06: vmx| DICT     ethernet0.addressType = generated
Mar 15 20:25:06: vmx| DICT             uuid.location = 56 4d 67 c5 fc e9 98 ae-fe dd 05 62 42 da e3 95
Mar 15 20:25:06: vmx| DICT                 uuid.bios = 56 4d 67 c5 fc e9 98 ae-fe dd 05 62 42 da e3 95
Mar 15 20:25:06: vmx| DICT ethernet0.generatedAddress = 00:0c:29:d4:00:18
Mar 15 20:25:06: vmx| DICT ethernet0.generatedAddressOffset = 0
Mar 15 20:25:06: vmx| DICT            tools.syncTime = FALSE
Mar 15 20:25:06: vmx| DICT   usb.autoConnect.device0 = 
Mar 15 20:25:06: vmx| DICT   usb.autoConnect.device1 = 
Mar 15 20:25:06: vmx| DICT --- USER DEFAULTS
Mar 15 20:25:06: vmx| DICT --- HOST DEFAULTS
Mar 15 20:25:06: vmx| DICT    vmnet1.hostonlyaddress = 192.168.166.1
Mar 15 20:25:06: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
Mar 15 20:25:06: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
Mar 15 20:25:06: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
Mar 15 20:25:06: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
Mar 15 20:25:06: vmx| DICT                    libdir = /usr/lib/vmware-player
Mar 15 20:25:06: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Mar 15 20:25:06: vmx| DICT --- SITE DEFAULTS
Mar 15 20:25:06: vmx| DICT                  tag.help = introduction.htm
Mar 15 20:25:06: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Mar 15 20:25:06: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Mar 15 20:25:06: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Mar 15 20:25:06: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Mar 15 20:25:06: vmx| DICT             tag.netConfig = devices_netadapter.htm
Mar 15 20:25:06: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Mar 15 20:25:06: vmx| DICT          tag.serialConfig = devices_serial.htm
Mar 15 20:25:06: vmx| DICT           tag.soundConfig = devices_sound.htm
Mar 15 20:25:06: vmx| DICT             tag.memConfig = configvm_memory.htm
Mar 15 20:25:06: vmx| DICT            tag.miscConfig = configvm.htm
Mar 15 20:25:06: vmx| DICT             tag.usbConfig = devices_usb.htm
Mar 15 20:25:06: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Mar 15 20:25:06: vmx| DICT                 tag.tools = vmtools.htm
Mar 15 20:25:06: vmx| DICT --- GLOBAL SETTINGS
Mar 15 20:25:06: vmx| Msg_Hint: msg.guestos.xp (shown)
Mar 15 20:25:06: vmx| WSSCAN: reserved mem (in MB) min=32 max=928 recommended=928
Mar 15 20:25:06: vmx|         hostMem=1024 maxAllowedAll=4096 maxAllowedVM=3600
Mar 15 20:25:06: vmx|         totOverhead=16
Mar 15 20:25:06: vmx| WSSCAN: used rec mem (in MB) 928
Mar 15 20:25:06: vmx| WSSCAN: Overhead 71921 paged 5534 nonpaged 4096 maxFBSize
Mar 15 20:25:06: vmx| WSSCAN 1 1 237568 -1 237568 -1 50 0
Mar 15 20:25:06: vmx| LICENSE: Running in restricted mode
Mar 15 20:25:06: vmx| STATDECLGROUP stats Root "" null
Mar 15 20:25:06: vmx| Host CPUID features: version 0x20ff0 id1.edx 0x78bfbff id1.ecx 0x1 id81.edx 0xe3d3fbff id81.ecx 0x1
Mar 15 20:25:06: vmx| CPU.cpuFeatures = 0xd83dffd0
Mar 15 20:25:06: vmx| CPUID after masking: version 0x20ff0 id1.edx 0x78bfbff id1.ecx 0x1 id81.edx 0xe3d3fbff id81.ecx 0x1 id88.ecx 0x0
Mar 15 20:25:06: vmx| CPU.cpuFeatures = 0xd83dffd0
Mar 15 20:25:06: vmx| APIC: Local APIC at 0xfee00000
Mar 15 20:25:06: vmx| KHZEstimate 1802365
Mar 15 20:25:06: vmx| MHZEstimate 1802
Mar 15 20:25:06: vmx| NumVCPUs 1
Mar 15 20:25:06: vmx| UUID: location-UUID is 56 4d 67 c5 fc e9 98 ae-fe dd 05 62 42 da e3 95
Mar 15 20:25:06: vmx| MM: Using partialmap, 65536 pages AC 0 CE 1 TM 0 DOHU 0
Mar 15 20:25:06: vmx| UUID: canonical path is /home/leona/network/Windows XP Professional/Windows XP Professional.vmx
Mar 15 20:25:06: vmx| UUID: location-UUID is 56 4d 67 c5 fc e9 98 ae-fe dd 05 62 42 da e3 95
Mar 15 20:25:06: vmx| Msg_Reset:
Mar 15 20:25:06: vmx| ----------------------------------------
Mar 15 20:25:06: vmx| Opened paging file anon
Mar 15 20:25:06: vmx| Mapped mainmem as pageable
Mar 15 20:25:06: vmx| MStat: Creating Stat vm.uptime
Mar 15 20:25:06: vmx| DISK: OPEN ide0:0 '/home/leona/network/Windows XP Professional/Windows XP Professional.vmdk' persistent R[(null)]
Mar 15 20:25:06: vmx| AIOGNRC: Starting 4 I/O threads.
Mar 15 20:25:07: vmx| DISKLIB-DSCPTR: Opened [0]: "Windows XP Professional.vmdk" (0xa)
Mar 15 20:25:07: vmx| DISKLIB-LINK  : Opened '/home/leona/network/Windows XP Professional/Windows XP Professional.vmdk' (0xa): monolithicSparse, 16777216 sectors / 8192 Mb.
Mar 15 20:25:07: vmx| DISKLIB-LIB   : Opened "/home/leona/network/Windows XP Professional/Windows XP Professional.vmdk" (flags 0xa).
Mar 15 20:25:07: vmx| DISK: OPEN '/home/leona/network/Windows XP Professional/Windows XP Professional.vmdk' Geo (16383/16/63) BIOS Geo (0/0/0) freeSpace=23547Mb
Mar 15 20:25:07: vmx| Msg_Hint: msg.nfsmounted.persistent (shown)
Mar 15 20:25:07: vmx| TimeTracker host to guest rate conversion 13451924237447 @ 1802365000Hz -> 13451924237447 @ 1802365000Hz
Mar 15 20:25:07: vmx| TimeTracker host to guest rate conversion ((x * 2147483648) >> 31) + 0
Mar 15 20:25:07: vmx| SCSI0: UNTAGGED commands will be converted to ORDER tags.
Mar 15 20:25:07: vmx| MStat: Creating Stat vm.heartbeat
Mar 15 20:25:07: vmx| DISKUTIL: ide0:0 : toolsVersion = 6404
Mar 15 20:25:07: vmx| TOOLS INSTALL initializing state to IDLE on power on.
Mar 15 20:25:07: vmx| XINFO X fd is 46
Mar 15 20:25:07: vmx| XINFO depth 24 bpp 32 class 4
Mar 15 20:25:07: vmx| XINFO WARNING: XF86MISC version 0.9
Mar 15 20:25:07: vmx| VT redirected kernel output to /dev/tty1
Mar 15 20:25:07: vmx| USB: Initializing UHCI host controller
Mar 15 20:25:07: vmx| USB: Initializing USB Generic backend
Mar 15 20:25:07: vmx| VMMon_GetkHzEstimate: Calculated 1802291 kHz
Mar 15 20:25:07: vmx| VLANCE: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks
Mar 15 20:25:07: vmx| Ethernet0 MAC Address: 00:0c:29:da:e3:95
Mar 15 20:25:07: vmx| VMXNET: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks, dontClusterSize is 128
Mar 15 20:25:07: vmx| E1000: checksum cycles/kB: C=902 asm=292
Mar 15 20:25:07: vmx| VMX_PowerOn: ModuleTable_PowerOn = 1
Mar 15 20:25:07: mks| Async MKS thread is alive
Mar 15 20:25:07: mks| Connecting to window system.
Mar 15 20:25:07: mks| XINFO X fd is 46
Mar 15 20:25:07: mks| XINFO depth 24 bpp 32 class 4
Mar 15 20:25:07: mks| XINFO WARNING: XF86MISC version 0.9
Mar 15 20:25:07: mks| VT redirected kernel output to /dev/tty1
Mar 15 20:25:07: mks| rasterops MMXEXT accelerations enabled
Mar 15 20:25:07: mks| XINFO unsupported XF86VidMode version: 2.2
Mar 15 20:25:07: vcpu-0| APIC: version = 0x10, max LVT = 5
Mar 15 20:25:07: vcpu-0| APIC: LDR = 0x1000000, DFR = 0xffffffff
Mar 15 20:25:07: mks| XINFO XFree86 VidMode 0: 1024x768 flags: 0xa
Mar 15 20:25:07: mks| XINFO XFree86 VidMode 1: 800x600 flags: 0x5
Mar 15 20:25:07: mks| XINFO XFree86 VidMode 2: 640x480 flags: 0xa
Mar 15 20:25:07: mks| KHBKL: Unable to parse keystring at: ''
Mar 15 20:25:07: vcpu-0| PShare: enabled 1, scanRate 32, checkRate 16
Mar 15 20:25:07: vcpu-0| guestCpuFeatures = 0xd83dffd0
Mar 15 20:25:07: vcpu-0| Init modules.
Mar 15 20:25:07: vcpu-0| DISKUTIL: ide0:0 : capacity=16777216
Mar 15 20:25:07: vcpu-0| CPU reset: hard
Mar 15 20:25:07: vmx| VNET: Notification enabled for Ethernet0
Mar 15 20:25:07: vmx| Msg_Question:
Mar 15 20:25:07: vmx| [msg.floppy.changeName] The path to floppy drive 0 ("A:") appears to be incorrect. Would you like to change it to "/dev/fd0"?----------------------------------------
Mar 15 20:25:12: vmx| FLOPPYLIB-LIB  : GenIoctl: syserror Invalid argument.
Mar 15 20:25:12: vmx| CDROM: Failed to connect 'D:\Files\build\WinLite.iso'.
Mar 15 20:25:12: vmx| Msg_Post: Warning
Mar 15 20:25:12: vmx| [msg.cdromImage.nofile] File "D:\Files\build\WinLite.iso" does not exist and therefore cannot be connected as a CD-ROM image.
Mar 15 20:25:12: vmx| [msg.device.startdisconnected] Virtual device ide1:0 will start disconnected.
Mar 15 20:25:12: vmx| ----------------------------------------
Mar 15 20:25:14: vmx| USB: Found device [name:Neodio\ Technologies\ USB\ device vid:0aec pid:3260 path:5/4]
Mar 15 20:25:14: vmx| VMXVmdbLoadUsbDevices: New set of 1 USB devices
Mar 15 20:25:14: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 15 20:25:14: vcpu-0| sz=3112288
Mar 15 20:25:14: vcpu-0| vmm32 initialized: Releasebuild-19317. cflags: 0x00000002.01803000.00000054
Mar 15 20:25:14: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 15 20:25:14: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0x0) and 0xec000000(0x0)
Mar 15 20:25:14: vcpu-0| PCI OPROM: Asked to map the VBIOS OPROM at 0xfe800000 (size 32768 bytes)
Mar 15 20:25:14: vcpu-0| PCI OPROM: Asked to unmap the VBIOS OPROM
Mar 15 20:25:14: vcpu-0| SVGA: Unregistering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Mar 15 20:25:14: vcpu-0| PCI OPROM: Asked to map the SBIOS OPROM at 0xfe800000 (size 16384 bytes)
Mar 15 20:25:14: vcpu-0| PCI OPROM: Asked to unmap the SBIOS OPROM
Mar 15 20:25:14: vcpu-0| PCI OPROM: Asked to map the VLANCE OPROM at 0xfe800000 (size 65536 bytes)
Mar 15 20:25:14: vcpu-0| PCI OPROM: Asked to unmap the VLANCE OPROM
Mar 15 20:25:14: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Mar 15 20:25:14: vcpu-0| PCI OPROM: Asked to map the VBIOS OPROM at 0xfe800000 (size 32768 bytes)
Mar 15 20:25:14: vcpu-0| PCI OPROM: Asked to unmap the VBIOS OPROM
Mar 15 20:25:14: vcpu-0| SVGA: Unregistering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Mar 15 20:25:14: vcpu-0| SVGA: Registering IOSpace at 0x1460 (0x0)
Mar 15 20:25:14: vcpu-0| SVGA: Registering MemSpace at 0xf0000000(0xf0000000) and 0xec000000(0xec000000)
Mar 15 20:25:14: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 15 20:25:14: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 15 20:25:14: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 15 20:25:14: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 15 20:25:14: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 15 20:25:15: vcpu-0| UHCI: Global Reset
Mar 15 20:25:15: vcpu-0| UHCI: HCReset
Mar 15 20:25:15: vcpu-0| UHCI: HCReset
Mar 15 20:25:16: vcpu-0| PCI OPROM: Asked to map the SBIOS OPROM at 0xfe800000 (size 16384 bytes)
Mar 15 20:25:16: vcpu-0| PCI OPROM: Asked to unmap the SBIOS OPROM
Mar 15 20:25:16: vcpu-0| PCI OPROM: Asked to map the VLANCE OPROM at 0xfe800000 (size 65536 bytes)
Mar 15 20:25:16: vcpu-0| PCI OPROM: Asked to map the VLANCE OPROM at 0xfe800000 (size 65536 bytes)
Mar 15 20:25:16: vcpu-0| PCI OPROM: Asked to unmap the VLANCE OPROM
Mar 15 20:25:16: vcpu-0| VIDE: Curr CHS info cyls: 17475 heads: 15 sects: 63 lba_cap: 16777216
Mar 15 20:25:17: vcpu-0| BIOS-UUID is 56 4d 67 c5 fc e9 98 ae-fe dd 05 62 42 da e3 95
Mar 15 20:25:17: vcpu-0| DISKUTIL: ide0:0 : toolsVersion = 6404
Mar 15 20:25:17: vcpu-0| DISKUTIL: ide0:0 : toolsVersion = 6404
Mar 15 20:25:17: mks| Ignoring update request in VGA_Expose (mode change pending).
Mar 15 20:25:17: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 15 20:25:17: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 15 20:25:17: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 15 20:25:17: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 15 20:25:17: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 15 20:25:18: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 15 20:25:18: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 15 20:25:18: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 15 20:25:18: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 15 20:25:18: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 15 20:25:18: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 15 20:25:18: vcpu-0| FLOPPYLIB-LIB  : read: syserror Input/output error.
Mar 15 20:25:18: vcpu-0| Unknown int 10h func 0x2000
Mar 15 20:25:21: IO#2| Caught signal 25 -- tid 10303
Mar 15 20:25:21: IO#2| SIGNAL: eip 0xffffe405 esp 0x5746e2dc ebp 0x5a0ad000
Mar 15 20:25:21: IO#2| SIGNAL: eax 0xffffffe5 ebx 0x79 ecx 0x5a0ad000 edx 0x200 esi 0xdcbf9e00 edi 0x0
Mar 15 20:25:21: IO#2| SIGNAL: stack 0x5746e2dc : 0x5746e308 0x555ad275 0x00001000 0x00000000
Mar 15 20:25:21: IO#2| SIGNAL: stack 0x5746e2ec : 0x00000000 0x00000000 0x555b13d4 0x016e5008
Mar 15 20:25:21: IO#2| SIGNAL: stack 0x5746e2fc : 0xdcbf9e00 0x00000000 0x085c6170 0x5746e358
Mar 15 20:25:21: IO#2| SIGNAL: stack 0x5746e30c : 0x08074392 0x00000079 0x5a0ad000 0x00000200
Mar 15 20:25:21: IO#2| SIGNAL: stack 0x5746e31c : 0xdcbf9e00 0x00000000 0x5746e340 0x5746e358
Mar 15 20:25:21: IO#2| SIGNAL: stack 0x5746e32c : 0x0806878e 0x00000002 0x00000000 0x00000001
Mar 15 20:25:21: IO#2| SIGNAL: stack 0x5746e33c : 0x0080fbd9 0x55861adc 0x5746e358 0x08567df8
Mar 15 20:25:21: IO#2| SIGNAL: stack 0x5746e34c : 0x085c6140 0x0856c464 0x085c6140 0x5746e398
Mar 15 20:25:21: IO#2| Backtrace:
Mar 15 20:25:21: IO#2| Backtrace[0] 0x5746deb8 eip 0x805a500 
Mar 15 20:25:21: IO#2| Backtrace[1] 0x5746df88 eip 0x80e999a 
Mar 15 20:25:21: IO#2| Backtrace[2] 0x5746dff8 eip 0x80e972a 
Mar 15 20:25:21: IO#2| Backtrace[3] 0x5a0ad000 eip 0xffffe500 
Mar 15 20:25:21: IO#2| Unexpected signal: 25.
Mar 15 20:25:21: IO#2| Backtrace:
Mar 15 20:25:21: IO#2| Backtrace[0] 0x5746da98 eip 0x805a500 
Mar 15 20:25:21: IO#2| Backtrace[1] 0x5746deb8 eip 0x80bc23b 
Mar 15 20:25:21: IO#2| Backtrace[2] 0x5746df88 eip 0x80e99fd 
Mar 15 20:25:21: IO#2| Backtrace[3] 0x5746dff8 eip 0x80e972a 
Mar 15 20:25:21: IO#2| Backtrace[4] 0x5a0ad000 eip 0xffffe500 
Mar 15 20:25:21: IO#2| Core dump limit is 0 kb.
Mar 15 20:25:21: IO#2| Attempting to dump core...
Mar 15 20:25:22: IO#2| Child process 10318 failed to dump core (status 0x6).
Mar 15 20:25:22: IO#2| Msg_Post: Error
Mar 15 20:25:22: IO#2| [msg.log.error.unrecoverable] VMware Player unrecoverable error: (IO#2)
Mar 15 20:25:22: IO#2| Unexpected signal: 25.
Mar 15 20:25:22: IO#2| [msg.panic.haveLog] A log file is available in "/home/leona/network/Windows XP Professional/vmware.log".  [msg.panic.requestSupport.withLog] Please request support and include the contents of the log file.  [msg.panic.requestSupport.linux] 
Mar 15 20:25:22: IO#2| To collect files to submit to VMware support, run vm-support.
Mar 15 20:25:22: IO#2| [msg.panic.response] We will respond on the basis of your support entitlement.
Mar 15 20:25:22: IO#2| ----------------------------------------
Mar 15 20:25:48: vmx| VTHREAD watched thread 7 "IO#2" died
Mar 15 20:25:48: IO#0| VTHREAD watched thread 0 "vmx" died
Mar 15 20:25:48: IO#3| VTHREAD watched thread 0 "vmx" died
Mar 15 20:25:48: IO#1| VTHREAD watched thread 0 "vmx" died
Mar 15 20:25:48: vcpu-0| VTHREAD watched thread 0 "vmx" died
Mar 15 20:25:48: mks| VTHREAD watched thread 0 "vmx" died

```

So what can I do to repair this, I can't have it on my Linux drive, because I don't have enough space hard drive space :)

So is this VMPlayer, playing up, or some sort of file size limitiation?

Thanks

Leona.

---

