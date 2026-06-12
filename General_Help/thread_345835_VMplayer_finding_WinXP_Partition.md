---
title: "VMplayer finding WinXP Partition"
date: 2007-01-24
forum: General Help
---

### Post by mgaskell on 2007-01-24
Hello,

I'm trying to set up VMplayer to run my WindowsXP Home from my NTFS partition. I am following the directions (copying, pasting and tweaking as necessary) by Imran Nazer from the link: 

[http://rougebob.com/Running-a-Windows-Partition-in-VMware.htm](http://rougebob.com/Running-a-Windows-Partition-in-VMware.htm)

When I point VMplayer at my WindowsXP.vmx file I get the error:


"VMware Player cannot find the virtual disk "/home/mike/Desktop/WindowsXP.vmdk". Please verify the path is valid and try again.Cannot open the disk '/home/mike/Desktop/WindowsXP.vmdk' or one of the snapshot disks it depends on.
Reason: The system cannot find the file specified."


The WindowsXP.vmdk file is sitting on my desktop and here are its contents:

version=1
CID=9428f535
parentCID=ffffffff
createType="fullDevice"

# Extent description
RW 63 FLAT "WindowsXP.mbr" 0
RW 195371504 FLAT "/dev/hda" 63

# The Disk Data Base
#DDB

ddb.toolsVersion = "6530"
ddb.adapterType = "ide"
ddb.virtualHWVersion = "4"
ddb.geometry.sectors = "63"
ddb.geometry.heads = "255"
ddb.geometry.cylinders = "12161"

The rest of my VMware files reside in my home directory in the folder /VMware.

Here are the contents of my WindowsXP.vmx file:

#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4"

uuid.location = "56 4d 85 1b f3 a5 53 a8-5c 18 be ad 05 57 4a a1"
uuid.bios = "56 4d 85 1b f3 a5 53 a8-5c 18 be ad 05 57 4a a1"

uuid.action = "create"
checkpoint.vmState = ""

displayName = "Windows XP Professional"
annotation = ""
guestinfo.vmware.product.long = ""
guestinfo.vmware.product.url = ""

guestOS = "winxppro"
numvcpus = "1"
memsize = "128"
paevm = "FALSE"
sched.mem.pshare.enable = "TRUE"
MemAllowAutoScaleDown = "FALSE"

MemTrimRate = "-1"

nvram = "WindowsXP.nvram"

mks.enable3d = "FALSE"
vmmouse.present = "FALSE"
vmmouse.fileName = "auto detect"

tools.syncTime = "TRUE"
tools.remindinstall = "FALSE"

isolation.tools.hgfs.disable = "FALSE"
isolation.tools.dnd.disable = "FALSE"
isolation.tools.copy.enable = "TRUE"
isolation.tools.paste.enabled = "TRUE"
gui.restricted = "FALSE"

ethernet0.present = "TRUE"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddress = "00:0c:29:59:aa:eb"
ethernet0.generatedAddressOffset = "0"

usb.present = "TRUE"
usb.generic.autoconnect = "TRUE"

sound.present = "TRUE"
sound.virtualdev = "sb16"

ide0:0.present = "TRUE"
ide0:0.fileName = "WindowsXP.vmdk"
ide0:0.mode = "independent-persistent"
ide0:0.deviceType = "rawDisk"
ide0:0.redo = ""
ide0:0.writeThrough = "FALSE"
ide0:0.startConnected = "TRUE"

ide1:0.present = "TRUE"
ide1:0.fileName = "/dev/cdrom"
ide1:0.deviceType = "atapi-cdrom"
ide1:0.writeThrough = "FALSE"
ide1:0.startConnected = "TRUE"

floppy0.present = "TRUE"
floppy0.fileName = "/dev/fd0"
floppy0.startConnected = "TRUE"

serial0.present = "FALSE"
serial1.present = "FALSE"
parallel0.present = "FALSE"

fileSearchPath = "/home/mike/Desktop;."


Here are the contents of my latest log file:

Jan 24 00:37:47: vmx| Log for VMware Player pid=5711 version=1.0.2 build=build-29634 option=Release
Jan 24 00:37:47: vmx| Command line: "/usr/lib/vmware-player/bin/vmware-vmx" "-@" "pipe=/tmp/vmware-mike/vmx1a130c783bc786ad;vm=1a130c783bc786ad" "/home/mike/vmware/WindowsXP.vmx"
Jan 24 00:37:47: vmx| UI Connecting to pipe '/tmp/vmware-mike/vmx1a130c783bc786ad' with user '(null)'
Jan 24 00:37:47: vmx| Using system libcrypto, version 9070BF
Jan 24 00:37:47: vmx| pcpu #0 CPUID numEntries=2 GenuntelineI
Jan 24 00:37:47: vmx| pcpu #0 CPUID version=0x6d6 id1.edx=0xafe9fbbf id1.ecx=0x180 id1.ebx=0x816
Jan 24 00:37:47: vmx| pcpu #0 CPUID id80.eax=80000004 id81.edx=0x0 id81.ecx=0x0
Jan 24 00:37:47: vmx| CPUID id1.edx: 0xafe9fbbf id1.ecx: 0x180 id81.edx: 0 id81.ecx: 0
Jan 24 00:37:47: vmx| CPUID id88.ecx: 0 id88.edx: 0x2c04307d
Jan 24 00:37:47: vmx| Setup symlink /var/run/vmware/%2fhome%2fmike%2fvmware%2fWindowsXP%2evmx -> /var/run/vmware/mike/5711
Jan 24 00:37:47: vmx| ACL_InitCapabilities: here 1 (bug 63252)
Jan 24 00:37:47: vmx| changing directory to /home/mike/vmware/.
Jan 24 00:37:47: vmx| Config file: /home/mike/vmware/WindowsXP.vmx
Jan 24 00:37:47: vmx| DISKLIB-FLAT  : "/home/mike/vmware/WindowsXP.mbr" : failed to open (25): AIOMgr_Open failed.
Jan 24 00:37:47: vmx| DISKLIB-DSCPTR: Failed to open extents for descriptor file in normal mode
Jan 24 00:37:47: vmx| DISKLIB-LINK  : "/home/mike/vmware/WindowsXP.vmdk" : failed to open (The system cannot find the file specified).  
Jan 24 00:37:47: vmx| DISKLIB-CHAIN : "/home/mike/vmware/WindowsXP.vmdk" : failed to open (The system cannot find the file specified).
Jan 24 00:37:47: vmx| DISKLIB-LIB   : Failed to open '/home/mike/vmware/WindowsXP.vmdk' with flags 0x17 (The system cannot find the file specified).
Jan 24 00:37:47: vmx| DISK: Cannot open disk "/home/mike/vmware/WindowsXP.vmdk": The system cannot find the file specified (25).
Jan 24 00:37:47: vmx| DISKUTIL: GetDevVersion: couldn't open file '/home/mike/vmware/WindowsXP.vmdk' : The system cannot find the file specified (25).
Jan 24 00:37:47: vmx| DISKUTIL: Could not populate version buffer.
Jan 24 00:37:47: vmx| LOG failed to remove /home/mike/vmware/vmware-2.log failed: No such file or directory
Jan 24 00:37:47: vmx| VMXVmdbCbVmVmxExecState: Exec state change requested to state poweredOn without reset
Jan 24 00:37:47: vmx| TOOLS delaying state change request to state 3
Jan 24 00:37:47: vmx| PowerOn
Jan 24 00:37:47: vmx| Host ACPI: can't find SRAT
Jan 24 00:37:47: vmx| HOST sysname Linux, nodename mike-laptop, release 2.6.17-10-generic, version #2 SMP Tue Dec 5 22:28:26 UTC 2006, machine i686, SMP, hz=250
Jan 24 00:37:47: vmx| DICT --- USER PREFERENCES
Jan 24 00:37:47: vmx| DICT       pref.grabOnKeyPress = FALSE
Jan 24 00:37:47: vmx| DICT       pref.eula.0.appName = VMware Player
Jan 24 00:37:47: vmx| DICT   pref.eula.0.buildNumber = 29634
Jan 24 00:37:47: vmx| DICT            pref.eula.size = 1
Jan 24 00:37:47: vmx| DICT    pref.autoFitFullScreen = fitHostToGuest
Jan 24 00:37:47: vmx| DICT     pref.view.navBar.type = favorites
Jan 24 00:37:47: vmx| DICT     pref.mruDest0.present = FALSE
Jan 24 00:37:47: vmx| DICT  pref.mruDest0.destString = 
Jan 24 00:37:47: vmx| DICT        pref.mruDest0.user = 
Jan 24 00:37:47: vmx| DICT     pref.mruDest1.present = FALSE
Jan 24 00:37:47: vmx| DICT  pref.mruDest1.destString = 
Jan 24 00:37:47: vmx| DICT        pref.mruDest1.user = 
Jan 24 00:37:47: vmx| DICT     pref.mruDest2.present = FALSE
Jan 24 00:37:47: vmx| DICT  pref.mruDest2.destString = 
Jan 24 00:37:47: vmx| DICT        pref.mruDest2.user = 
Jan 24 00:37:47: vmx| DICT     pref.mruDest3.present = FALSE
Jan 24 00:37:47: vmx| DICT  pref.mruDest3.destString = 
Jan 24 00:37:47: vmx| DICT        pref.mruDest3.user = 
Jan 24 00:37:47: vmx| DICT     pref.mruDest4.present = FALSE
Jan 24 00:37:47: vmx| DICT  pref.mruDest4.destString = 
Jan 24 00:37:47: vmx| DICT        pref.mruDest4.user = 
Jan 24 00:37:47: vmx| DICT     pref.mruDest5.present = FALSE
Jan 24 00:37:47: vmx| DICT  pref.mruDest5.destString = 
Jan 24 00:37:47: vmx| DICT        pref.mruDest5.user = 
Jan 24 00:37:47: vmx| DICT     pref.mruDest6.present = FALSE
Jan 24 00:37:47: vmx| DICT  pref.mruDest6.destString = 
Jan 24 00:37:47: vmx| DICT        pref.mruDest6.user = 
Jan 24 00:37:47: vmx| DICT     pref.mruDest7.present = FALSE
Jan 24 00:37:47: vmx| DICT  pref.mruDest7.destString = 
Jan 24 00:37:47: vmx| DICT        pref.mruDest7.user = 
Jan 24 00:37:47: vmx| DICT       webUpdate.checkLast = 1169409721
Jan 24 00:37:47: vmx| DICT webUpdate.lastCheck.status = done_updates
Jan 24 00:37:47: vmx| DICT --- USER DEFAULTS
Jan 24 00:37:47: vmx| DICT --- HOST DEFAULTS
Jan 24 00:37:47: vmx| DICT    vmnet1.hostonlyaddress = 192.168.35.1
Jan 24 00:37:47: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
Jan 24 00:37:47: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
Jan 24 00:37:47: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
Jan 24 00:37:47: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
Jan 24 00:37:47: vmx| DICT                    libdir = /usr/lib/vmware-player
Jan 24 00:37:47: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Jan 24 00:37:47: vmx| DICT --- SITE DEFAULTS
Jan 24 00:37:47: vmx| DICT                  tag.help = introduction.htm
Jan 24 00:37:47: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Jan 24 00:37:47: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Jan 24 00:37:47: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Jan 24 00:37:47: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Jan 24 00:37:47: vmx| DICT             tag.netConfig = devices_netadapter.htm
Jan 24 00:37:47: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Jan 24 00:37:47: vmx| DICT          tag.serialConfig = devices_serial.htm
Jan 24 00:37:47: vmx| DICT           tag.soundConfig = devices_sound.htm
Jan 24 00:37:47: vmx| DICT             tag.memConfig = configvm_memory.htm
Jan 24 00:37:47: vmx| DICT            tag.miscConfig = configvm.htm
Jan 24 00:37:47: vmx| DICT             tag.usbConfig = devices_usb.htm
Jan 24 00:37:47: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Jan 24 00:37:47: vmx| DICT                 tag.tools = vmtools.htm
Jan 24 00:37:47: vmx| DICT --- COMMAND LINE
Jan 24 00:37:47: vmx| DICT             gui.available = TRUE
Jan 24 00:37:47: vmx| DICT --- CONFIGURATION
Jan 24 00:37:47: vmx| DICT            config.version = 8
Jan 24 00:37:47: vmx| DICT         virtualHW.version = 4
Jan 24 00:37:47: vmx| DICT             uuid.location = 56 4d 85 1b f3 a5 53 a8-5c 18 be ad 05 57 4a a1
Jan 24 00:37:47: vmx| DICT                 uuid.bios = 56 4d 85 1b f3 a5 53 a8-5c 18 be ad 05 57 4a a1
Jan 24 00:37:47: vmx| DICT               uuid.action = create
Jan 24 00:37:47: vmx| DICT        checkpoint.vmState = 
Jan 24 00:37:47: vmx| DICT               displayName = Windows XP Professional
Jan 24 00:37:47: vmx| DICT                annotation = 
Jan 24 00:37:47: vmx| DICT guestinfo.vmware.product.long = 
Jan 24 00:37:47: vmx| DICT guestinfo.vmware.product.url = 
Jan 24 00:37:47: vmx| DICT                   guestOS = winxppro
Jan 24 00:37:47: vmx| DICT                  numvcpus = 1
Jan 24 00:37:47: vmx| DICT                   memsize = 128
Jan 24 00:37:47: vmx| DICT                     paevm = FALSE
Jan 24 00:37:47: vmx| DICT   sched.mem.pshare.enable = TRUE
Jan 24 00:37:47: vmx| DICT     MemAllowAutoScaleDown = FALSE
Jan 24 00:37:47: vmx| DICT               MemTrimRate = -1
Jan 24 00:37:47: vmx| DICT                     nvram = WindowsXP.nvram
Jan 24 00:37:47: vmx| DICT              mks.enable3d = FALSE
Jan 24 00:37:47: vmx| DICT           vmmouse.present = FALSE
Jan 24 00:37:47: vmx| DICT          vmmouse.fileName = auto detect
Jan 24 00:37:47: vmx| DICT            tools.syncTime = TRUE
Jan 24 00:37:47: vmx| DICT       tools.remindinstall = FALSE
Jan 24 00:37:47: vmx| DICT isolation.tools.hgfs.disable = FALSE
Jan 24 00:37:47: vmx| DICT isolation.tools.dnd.disable = FALSE
Jan 24 00:37:47: vmx| DICT isolation.tools.copy.enable = TRUE
Jan 24 00:37:47: vmx| DICT isolation.tools.paste.enabled = TRUE
Jan 24 00:37:47: vmx| DICT            gui.restricted = FALSE
Jan 24 00:37:47: vmx| DICT         ethernet0.present = TRUE
Jan 24 00:37:47: vmx| DICT  ethernet0.connectionType = nat
Jan 24 00:37:47: vmx| DICT     ethernet0.addressType = generated
Jan 24 00:37:47: vmx| DICT ethernet0.generatedAddress = 00:0c:29:59:aa:eb
Jan 24 00:37:47: vmx| DICT ethernet0.generatedAddressOffset = 0
Jan 24 00:37:47: vmx| DICT               usb.present = TRUE
Jan 24 00:37:47: vmx| DICT   usb.generic.autoconnect = TRUE
Jan 24 00:37:47: vmx| DICT             sound.present = TRUE
Jan 24 00:37:47: vmx| DICT          sound.virtualdev = sb16
Jan 24 00:37:47: vmx| DICT            ide0:0.present = TRUE
Jan 24 00:37:47: vmx| DICT           ide0:0.fileName = WindowsXP.vmdk
Jan 24 00:37:47: vmx| DICT               ide0:0.mode = independent-persistent
Jan 24 00:37:47: vmx| DICT         ide0:0.deviceType = rawDisk
Jan 24 00:37:47: vmx| DICT               ide0:0.redo = 
Jan 24 00:37:47: vmx| DICT       ide0:0.writeThrough = FALSE
Jan 24 00:37:47: vmx| DICT     ide0:0.startConnected = TRUE
Jan 24 00:37:47: vmx| DICT            ide1:0.present = TRUE
Jan 24 00:37:47: vmx| DICT           ide1:0.fileName = /dev/cdrom
Jan 24 00:37:47: vmx| DICT         ide1:0.deviceType = atapi-cdrom
Jan 24 00:37:47: vmx| DICT       ide1:0.writeThrough = FALSE
Jan 24 00:37:47: vmx| DICT     ide1:0.startConnected = TRUE
Jan 24 00:37:47: vmx| DICT           floppy0.present = TRUE
Jan 24 00:37:47: vmx| DICT          floppy0.fileName = /dev/fd0
Jan 24 00:37:47: vmx| DICT    floppy0.startConnected = TRUE
Jan 24 00:37:47: vmx| DICT           serial0.present = FALSE
Jan 24 00:37:47: vmx| DICT           serial1.present = FALSE
Jan 24 00:37:47: vmx| DICT         parallel0.present = FALSE
Jan 24 00:37:47: vmx| DICT --- USER DEFAULTS
Jan 24 00:37:47: vmx| DICT --- HOST DEFAULTS
Jan 24 00:37:47: vmx| DICT    vmnet1.hostonlyaddress = 192.168.35.1
Jan 24 00:37:47: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
Jan 24 00:37:47: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
Jan 24 00:37:47: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
Jan 24 00:37:47: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
Jan 24 00:37:47: vmx| DICT                    libdir = /usr/lib/vmware-player
Jan 24 00:37:47: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Jan 24 00:37:47: vmx| DICT --- SITE DEFAULTS
Jan 24 00:37:47: vmx| DICT                  tag.help = introduction.htm
Jan 24 00:37:47: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Jan 24 00:37:47: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Jan 24 00:37:47: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Jan 24 00:37:47: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Jan 24 00:37:47: vmx| DICT             tag.netConfig = devices_netadapter.htm
Jan 24 00:37:47: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Jan 24 00:37:47: vmx| DICT          tag.serialConfig = devices_serial.htm
Jan 24 00:37:47: vmx| DICT           tag.soundConfig = devices_sound.htm
Jan 24 00:37:47: vmx| DICT             tag.memConfig = configvm_memory.htm
Jan 24 00:37:47: vmx| DICT            tag.miscConfig = configvm.htm
Jan 24 00:37:47: vmx| DICT             tag.usbConfig = devices_usb.htm
Jan 24 00:37:47: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Jan 24 00:37:47: vmx| DICT                 tag.tools = vmtools.htm
Jan 24 00:37:47: vmx| DICT --- GLOBAL SETTINGS
Jan 24 00:37:47: vmx| Msg_Hint: msg.guestos.xp (shown)
Jan 24 00:37:47: vmx| WSSCAN: reserved mem (in MB) min=32 max=896 recommended=896
Jan 24 00:37:47: vmx|         hostMem=992 maxAllowedAll=4096 maxAllowedVM=3600
Jan 24 00:37:47: vmx|         totOverhead=16
Jan 24 00:37:47: vmx| WSSCAN: used rec mem (in MB) 896
Jan 24 00:37:47: vmx| WSSCAN: Overhead 39153 paged 5278 nonpaged 4096 maxFBSize
Jan 24 00:37:47: vmx| WSSCAN 1 1 229376 -1 229376 -1 50 0
Jan 24 00:37:47: vmx| LICENSE: Running in restricted mode
Jan 24 00:37:47: vmx| STATDECLGROUP stats Root "" null
Jan 24 00:37:47: vmx| Host CPUID features: version 0x6d8 id1.edx 0xafe9fbbf id1.ecx 0x180 id81.edx 0x0 id81.ecx 0x0
Jan 24 00:37:47: vmx| CPU.cpuFeatures = 0x851fe02
Jan 24 00:37:47: vmx| CPUID after masking: version 0x6d8 id1.edx 0xfe9fbbf id1.ecx 0x0 id81.edx 0x800 id81.ecx 0x0 id88.ecx 0x0
Jan 24 00:37:47: vmx| CPU.cpuFeatures = 0x851fe02
Jan 24 00:37:47: vmx| APIC: Local APIC at 0xfee00000
Jan 24 00:37:47: vmx| KHZEstimate 600000
Jan 24 00:37:47: vmx| MHZEstimate 600
Jan 24 00:37:47: vmx| NumVCPUs 1
Jan 24 00:37:47: vmx| UUID: location-UUID is 56 4d 85 1b f3 a5 53 a8-5c 18 be ad 05 57 4a a1
Jan 24 00:37:47: vmx| MM: Using partialmap, 32768 pages AC 0 CE 1 TM 0 DOHU 0
Jan 24 00:37:47: vmx| UUID: canonical path is /home/mike/vmware/WindowsXP.vmx
Jan 24 00:37:47: vmx| UUID: location-UUID is 56 4d 85 1b f3 a5 53 a8-5c 18 be ad 05 57 4a a1
Jan 24 00:37:47: vmx| MM: using fileName /home/mike/vmware/564d851b-f3a5-53a8-5c18-bead05574aa1.vmem for paging
Jan 24 00:37:47: vmx| Msg_Reset:
Jan 24 00:37:47: vmx| ----------------------------------------
Jan 24 00:37:47: vmx| Opened paging file /home/mike/vmware/564d851b-f3a5-53a8-5c18-bead05574aa1.vmem
Jan 24 00:37:47: vmx| Mapped mainmem as pageable
Jan 24 00:37:47: vmx| MStat: Creating Stat vm.uptime
Jan 24 00:37:47: vmx| DISK: OPEN ide0:0 '/home/mike/vmware/WindowsXP.vmdk' independent-persistent R[(null)]
Jan 24 00:37:47: vmx| AIOGNRC: Starting 4 I/O threads.
Jan 24 00:37:47: vmx| AIOGNRC: Failed to open '/home/mike/vmware/WindowsXP.mbr' : Could not find the file (99) (0x3).
Jan 24 00:37:47: vmx| DISKLIB-FLAT  : Opening unbuffered failed; trying Simple
Jan 24 00:37:47: vmx| AIOGNRC: Failed to open '/home/mike/vmware/WindowsXP.mbr' : Could not find the file (99) (0x3).
Jan 24 00:37:47: vmx| DISKLIB-FLAT  : "/home/mike/vmware/WindowsXP.mbr" : failed to open (25): AIOMgr_Open failed.
Jan 24 00:37:47: vmx| DISKLIB-DSCPTR: Failed to open extents for descriptor file in normal mode
Jan 24 00:37:47: vmx| DISKLIB-LINK  : "/home/mike/vmware/WindowsXP.vmdk" : failed to open (The system cannot find the file specified).  
Jan 24 00:37:47: vmx| DISKLIB-CHAIN : "/home/mike/vmware/WindowsXP.vmdk" : failed to open (The system cannot find the file specified).
Jan 24 00:37:47: vmx| DISKLIB-LIB   : Failed to open '/home/mike/vmware/WindowsXP.vmdk' with flags 0xa (The system cannot find the file specified).
Jan 24 00:37:47: vmx| DISK: Failed to open disk '/home/mike/vmware/WindowsXP.vmdk' : The system cannot find the file specified (25) 3023.
Jan 24 00:37:47: vmx| Msg_Post: Error
Jan 24 00:37:47: vmx| [msg.disk.fileNotFound] VMware Player cannot find the virtual disk "/home/mike/vmware/WindowsXP.vmdk". Please verify the path is valid and try again.
Jan 24 00:37:47: vmx| [msg.disk.noBackEnd] Cannot open the disk '/home/mike/vmware/WindowsXP.vmdk' or one of the snapshot disks it depends on.
Jan 24 00:37:47: vmx| [msg.disk.configureDiskError] Reason: The system cannot find the file specified.----------------------------------------
Jan 24 00:38:08: vmx| Module DiskEarly power on failed.
Jan 24 00:38:08: vmx| VMX_PowerOn: ModuleTable_PowerOn = 0
Jan 24 00:38:08: IO#0| AIOGNRC: thread #0 exiting (0)
Jan 24 00:38:08: IO#1| AIOGNRC: thread #1 exiting (0)
Jan 24 00:38:08: IO#2| AIOGNRC: thread #2 exiting (0)
Jan 24 00:38:08: IO#3| AIOGNRC: thread #3 exiting (0)
Jan 24 00:38:08: vmx| AIOGNRC: asyncOps=0 syncOps=0 maxPending=0 maxCompleted=0
Jan 24 00:38:08: vmx| vmdbPipe_Streams Couldn't read: OVL_STATUS_EOF
Jan 24 00:38:08: vmx| VMX idle exit
Jan 24 00:38:08: vmx| Flushing VMX VMDB connections
Jan 24 00:38:08: vmx| IPC_exit: disconnecting all threads
Jan 24 00:38:08: vmx| VMX exit.
Jan 24 00:38:08: vmx| AIOMGR-S : stat o=3 r=4 w=0 i=0 br=1752 bw=0

Other pertinent facts are;

1. It should be obvious by this post that I am not a programmer!
2. I am running Ubuntu Edgy on /hda3 partition
3. I am running WindowsXP Home on /hda1 NTFS partiton


It would be great to never boot into Windows again. Any help would be greatly appreciated.

Thanks,

Mike

---

### Post by gaebriel on 2007-01-24
What are the contents of your /home/mike/vmware directory? The logs keep griping about files missing in there ... Also, did you actually create a VMWare image that you're trying to run or are you trying to point the player to your XP Home install on /dev/hda1?

---

### Post by mgaskell on 2007-01-25
Thanks,

The files in the vmware directory:

vmware.log
vmware-0.log
vmware-1.log
vmware-2.log
WindowsXP.vmsd
WindowsXP.vmx

I am trying to point it at the Windows load in /hda1

Mike

---

### Post by mgaskell on 2007-01-25
The link that I mentioned was instructions to use a virtual machine to run the install in /hda1. I'm trying to save disk space.

Thanks again.

---

### Post by mgaskell on 2007-01-25
I copied WindowsXP.vmdk to the vmware directory and VMplayer says is cannot find it there either.

---

### Post by anaconda on 2007-01-25
Cant say I know anything, but just guessing:

What version of VMWare player have you got? I think running an actual windows install is a NEW feature, and if you dont have the most recent version of VMWare it might not work...

PS. if you get it working tell us what you did. I would like to do the same with my work-machine.

---

### Post by eldragon on 2007-02-08
ive been following a damn simmilar guide to yours. and i have the exact same problem. my problem is being described here:

[http://ubuntuforums.org/showthread.php?p=2121674#post2121674](http://ubuntuforums.org/showthread.php?p=2121674#post2121674)

if anyone has a solution, please!

---

### Post by orangesmell on 2007-02-08
Hi, 

I have been following the same guide, I had the same issue which I solved by running vmplayer as root. But I now have another issue:

When I start vmplayer with this file, I have the following error in my log:

** Non relevant things before **
Feb 08 21:08:11: vmx| DISKLIB-DEVCRL: LBA IDE disk 117231408 16383(116301)/16/63
Feb 08 21:08:11: vmx| DISKLIB-DEVCRL: Facts for /dev/hda: Cap=117231408 Phys C/H/S=16383/16/63 BIOS C/H/S=1024/255/63 Adap=IDE
Feb 08 21:08:11: vmx| DISKLIB-FLAT  : "/dev/hda" : failed to open (15): Size of extent in descriptor file larger than real size.
Feb 08 21:08:11: vmx| DISKLIB-DSCPTR: Failed to open extents for descriptor file in normal mode
Feb 08 21:08:11: vmx| DISKLIB-LINK  : "/home/arno/EssaiWin/windows.vmdk" : failed to open (The file specified is not a virtual disk).  
Feb 08 21:08:11: vmx| DISKLIB-CHAIN : "/home/arno/EssaiWin/windows.vmdk" : failed to open (The file specified is not a virtual disk).
Feb 08 21:08:11: vmx| DISKLIB-LIB   : Failed to open '/home/arno/EssaiWin/windows.vmdk' with flags 0x17 (The file specified is not a virtual disk)
.
Feb 08 21:08:11: vmx| DISK: Cannot open disk "/home/arno/EssaiWin/windows.vmdk": The file specified is not a virtual disk (15).
Feb 08 21:08:11: vmx| DISKUTIL: GetDevVersion: couldn't open file '/home/arno/EssaiWin/windows.vmdk' : The file specified is not a virtual disk (1
5).
Feb 08 21:08:11: vmx| DISKUTIL: Could not populate version buffer.
** Non Relevant things after **

The above issue is solved as I had made a small mistake in the mvdk file..

---

### Post by tcashin on 2007-02-08
> **mgaskell said:**
> Thanks,

The files in the vmware directory:

vmware.log
vmware-0.log
vmware-1.log
vmware-2.log
WindowsXP.vmsd
WindowsXP.vmx

I am trying to point it at the Windows load in /hda1

Mike

Two things: 
1. where is your WindowsXP.mbr file?
2. what are the permissions for /dev/hda and WindowsXP.mbr?

In order to run from a physical/raw disk, vmware needs read and write permissions to the physical disk device (or file) for all users who run vmplayer. To get such access to /dev/hda*, try adding yourself to the disk group

```
sudo usermod -a disk username
```

Logout/login to have this take effect.  Then set similar permissions for the WindowsXP.mbr file (just make sure you have read-write access).  Also, WindowsXP.mbr should be in /home/mike/vmware along with the .vmx and .vmdk files.

---

### Post by orangesmell on 2007-02-08
Finally got it working. :popcorn: 

I had to create another vmdk file for my second disk where my linux files are so that grub could see its boot list. easily done though. Then I copied and modified the ide0.0 lines in the vmx file to ide1.0 (with obvious parameters) and it worked.

I am very surprised by the speed of Windows in this VM. It's pretty fast, and I can definitely work on it... 

However, there's a catch. When starting, Windows sees new hardware off course and wants to be reactivated... I probably can do that, but then if one day I start it from the dual boot, it's going to ask me again for the reactivation and then again after and so on... :( 

So, what can I do here ?

Any idea would be really appreciated here, and in the meantime I'll keep you informed of my progress.

---

### Post by veloce on 2007-02-08
The error:

"VMware Player cannot find the virtual disk "/home/mike/Desktop/WindowsXP.vmdk". Please verify the path is valid and try again.Cannot open the disk '/home/mike/Desktop/WindowsXP.vmdk' or one of the snapshot disks it depends on.
Reason: The system cannot find the file specified."

Is not limited to the Linux version.  I had the same issue when trying to use a VM from one windows machine on another windows machine.  (Incidentally, both using VM Server). 

The problem appeared to be with the VM itself.  The disk files are sometimes dependent on others and when you move them the dependency breaks.  Seems to only happen when a snapshot has been taken at some stage. I never got this particular VM working again.  

I would suggest:
1. use VM Server rather than player (it's also free now)
2. build a new VM on the machine you want to use.

I have Win XP running under VM Server on my Edgy laptop.  It accesses the work network (through a virtual firewall) and reads and writes to network drives without problem.

Kerry.

---

### Post by eldragon on 2007-02-09
> **tcashin said:**
> Two things: 
1. where is your WindowsXP.mbr file?
2. what are the permissions for /dev/hda and WindowsXP.mbr?

In order to run from a physical/raw disk, vmware needs read and write permissions to the physical disk device (or file) for all users who run vmplayer. To get such access to /dev/hda*, try adding yourself to the disk group

```
sudo usermod -a disk username
```

Logout/login to have this take effect.  Then set similar permissions for the WindowsXP.mbr file (just make sure you have read-write access).  Also, WindowsXP.mbr should be in /home/mike/vmware along with the .vmx and .vmdk files.

oh god, i needed to relogon so that group policies applied. thanks.

now im getting a second error in vmplayer:
> 
Cannot open the disk '/home/eldragon/Desktop/VMWARE/windows.vmdk' or one of the snapshot disks it depends on.
Reason: Inappropriate ioctl for device.


the log says:

> 
Feb 09 09:14:05: vmx| DISKLIB-FLAT  : "/dev/mapper/nvidia_geaeafee" : failed to open (1638409): Couldn't get device facts.
Feb 09 09:14:05: vmx| DISKLIB-DSCPTR: Failed to open extents for descriptor file in normal mode
Feb 09 09:14:05: vmx| DISKLIB-LINK  : "/home/eldragon/Desktop/VMWARE/windows.vmdk" : failed to open (Inappropriate ioctl for device).  
Feb 09 09:14:05: vmx| DISKLIB-CHAIN : "/home/eldragon/Desktop/VMWARE/windows.vmdk" : failed to open (Inappropriate ioctl for device).
Feb 09 09:14:05: vmx| DISKLIB-LIB   : Failed to open '/home/eldragon/Desktop/VMWARE/windows.vmdk' with flags 0xa (Inappropriate ioctl for device).
Feb 09 09:14:05: vmx| DISK: Cannot open disk "/home/eldragon/Desktop/VMWARE/windows.vmdk": Inappropriate ioctl for device (1638409).
Feb 09 09:14:05: vmx| DISK: Failed to open disk '/home/eldragon/Desktop/VMWARE/windows.vmdk' : Inappropriate ioctl for device (1638409) 3023.
Feb 09 09:14:05: vmx| Msg_Post: Error
Feb 09 09:14:05: vmx| [msg.disk.noBackEnd] Cannot open the disk '/home/eldragon/Desktop/VMWARE/windows.vmdk' or one of the snapshot disks it depends on.
Feb 09 09:14:05: vmx| [msg.disk.configureDiskError] Reason: Inappropriate ioctl for device.


any help will be really appreciated, thanks

---

### Post by ArchStanton on 2007-02-14
I followed some similar instructions, and am almost there:
[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)


I needed to run vmplayer as root (sudo vmplayer). The big issue I have now is that when it starts the GRUB boot loader comes up with an Error 21. I assume its looking for my Ubuntu install on my second hard drive. I'm not sure where to proceed from here.

---

### Post by ArchStanton on 2007-02-14
OK, so I'm getting further . . .

I modified the ide section of the windows.vmx file as follows:
```
ide0:0.present = "TRUE" 
ide0:0.fileName = "windows.vmdk" 
ide0:0.mode = "independent-persistent" 
ide0:0.deviceType = "rawDisk" 
ide0:0.redo = ""
ide0:0.writeThrough = "FALSE" 
ide0:0.startConnected = "TRUE" 

ide0:1.present = "TRUE" 
ide0:1.fileName = "linux.vmdk" 
ide0:1.mode = "independent-persistent" 
ide0:1.deviceType = "rawDisk" 
ide0:1.redo = ""
ide0:1.writeThrough = "FALSE" 
ide0:1.startConnected = "TRUE" 

ide1:0.present = "TRUE" 
ide1:0.fileName = "/dev/cdrom" 
ide1:0.deviceType = "atapi-cdrom" 
ide1:0.writeThrough = "FALSE" 
ide1:0.startConnected = "TRUE" 
```

Then I created a linux.vmdk file and a linux.mbr file exactly like I did the windows versions of those files, but with the other hard drive.

Now windows starts to boot, but crashes and this error is what I get

> Operation on file "/dev/hda" failed (Input/output error).
Choose Retry to attempt the operation again. Choose Abort to terminate this session.
Choose Continue to forward the error to the guest operating system.

Clicking the abort button gives me this error:

> VMware Player cannot sync with disk before abort. Disk /dev/hda may be inconsistent.

Gonna do some more research.

---

### Post by kevpatts on 2007-06-03
> **eldragon said:**
> oh god, i needed to relogon so that group policies applied. thanks.

now im getting a second error in vmplayer:


the log says:



any help will be really appreciated, thanks
I have this same issue, and I followed the guide linked to by ArchStanton. Anything I did wrong?? Also have to run it as root even to get that far.

---

### Post by ArchStanton on 2007-06-04
I gave up.

---

### Post by kevpatts on 2007-06-04
Has anyone got this working?

---

