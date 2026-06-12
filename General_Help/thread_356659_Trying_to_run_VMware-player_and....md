---
title: "Trying to run VMware-player and..."
date: 2007-02-08
forum: General Help
---

### Post by Absurd on 2007-02-08
So I am trying to run WinXP from Ubuntu (edgy 6.10) using vmware-player and I am having some trouble.

First, I should mention that I set everything up by following the instructions [here](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html).
-------------------------------------------------------------------------------------------------------------
This is my vdmk file

```
# Disk DescriptorFile

version=1

CID=9428f535

parentCID=ffffffff

createType="fullDevice"



# Extent description

RW 63 FLAT "windowsxp.mbr" 0

RW 312387544 FLAT "/dev/sda" 63 



# The Disk Data Base 

#DDB 



ddb.toolsVersion = "6530"

ddb.adapterType = "ide"

ddb.virtualHWVersion = "4"

ddb.geometry.sectors = "63"

ddb.geometry.heads = "255"

ddb.geometry.cylinders = "19452"
```

Notes: I use "sda" instead of "hda" because I am using a sata drive. Because I obtained my pc prebuilt from dell, the first partition is some stupid FAT16 partition where an assistance app resides while my win xp partition is the second partition.
-------------------------------------------------------------------------------------------------------

When I try to run the vdmk file from vmware-player, I get the following message.

> Cannot open the disk '/home/mrmeh/RunningWindows/windows.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file.

I checked and set the owners for each file to me (mrmeh).

This is what the log says.

```
Feb 08 14:48:29: vmx| Log for VMware Player pid=5651 version=1.0.3 build=build-34682 option=Release
Feb 08 14:48:29: vmx| Command line: "/usr/lib/vmware/bin/vmware-vmx" "-@" "pipe=/tmp/vmware-mrmeh/vmxc63dd2ec151736f7;vm=c63dd2ec151736f7" "/home/mrmeh/RunningWindows/windows.vmx"
Feb 08 14:48:29: vmx| UI Connecting to pipe '/tmp/vmware-mrmeh/vmxc63dd2ec151736f7' with user '(null)'
Feb 08 14:48:29: vmx| Using system libcrypto, version 9070BF
Feb 08 14:48:29: vmx| cpuids[0].id81.ecx = 0x0
Feb 08 14:48:29: vmx| cpuids[1].id81.ecx = 0x0
Feb 08 14:48:29: vmx| pcpu #0 CPUID numEntries=5 GenuntelineI
Feb 08 14:48:29: vmx| pcpu #0 CPUID version=0xf43 id1.edx=0xbfebfbff id1.ecx=0x649d id1.ebx=0x20800
Feb 08 14:48:29: vmx| pcpu #0 CPUID id80.eax=80000008 id81.edx=0x20100000 id81.ecx=0x0
Feb 08 14:48:29: vmx| pcpu #1 CPUID numEntries=5 GenuntelineI
Feb 08 14:48:29: vmx| pcpu #1 CPUID version=0xf43 id1.edx=0xbfebfbff id1.ecx=0x649d id1.ebx=0x1020800
Feb 08 14:48:29: vmx| pcpu #1 CPUID id80.eax=80000008 id81.edx=0x20100000 id81.ecx=0x0
Feb 08 14:48:29: vmx| CPUID id1.edx: 0xbfebfbff id1.ecx: 0x649d id81.edx: 0x20100000 id81.ecx: 0
Feb 08 14:48:29: vmx| CPUID id88.ecx: 0 id88.edx: 0
Feb 08 14:48:29: vmx| Setup symlink /var/run/vmware/%2fhome%2fmrmeh%2fRunningWindows%2fwindows%2evmx -> /var/run/vmware/mrmeh/5651
Feb 08 14:48:29: vmx| ACL_InitCapabilities: here 1 (bug 63252)
Feb 08 14:48:29: vmx| changing directory to /home/mrmeh/RunningWindows/.
Feb 08 14:48:29: vmx| Config file: /home/mrmeh/RunningWindows/windows.vmx
Feb 08 14:48:29: vmx| DISKLIB-FLAT  : "/dev/sda" : failed to open (38): AIOMgr_Open failed.
Feb 08 14:48:29: vmx| DISKLIB-DSCPTR: Failed to open extents for descriptor file in normal mode
Feb 08 14:48:29: vmx| DISKLIB-LINK  : "/home/mrmeh/RunningWindows/windows.vmdk" : failed to open (Insufficient permission to access file).  
Feb 08 14:48:29: vmx| DISKLIB-CHAIN : "/home/mrmeh/RunningWindows/windows.vmdk" : failed to open (Insufficient permission to access file).
Feb 08 14:48:29: vmx| DISKLIB-LIB   : Failed to open '/home/mrmeh/RunningWindows/windows.vmdk' with flags 0x17 (Insufficient permission to access file).
Feb 08 14:48:29: vmx| DISK: Cannot open disk "/home/mrmeh/RunningWindows/windows.vmdk": Insufficient permission to access file (38).
Feb 08 14:48:29: vmx| DISKUTIL: GetDevVersion: couldn't open file '/home/mrmeh/RunningWindows/windows.vmdk' : Insufficient permission to access file (38).
Feb 08 14:48:29: vmx| DISKUTIL: Could not populate version buffer.
Feb 08 14:48:29: vmx| LOG failed to remove /home/mrmeh/RunningWindows/vmware-2.log failed: No such file or directory
Feb 08 14:48:29: vmx| VMXVmdbCbVmVmxExecState: Exec state change requested to state poweredOn without reset
Feb 08 14:48:29: vmx| TOOLS delaying state change request to state 3
Feb 08 14:48:29: vmx| PowerOn
Feb 08 14:48:29: vmx| Host ACPI: can't find SRAT
Feb 08 14:48:29: vmx| HOST sysname Linux, nodename AHHHHH, release 2.6.17-10-generic, version #2 SMP Tue Dec 5 22:28:26 UTC 2006, machine i686, SMP, hz=250
Feb 08 14:48:29: vmx| DICT --- USER PREFERENCES
Feb 08 14:48:29: vmx| DICT       pref.grabOnKeyPress = FALSE
Feb 08 14:48:29: vmx| DICT       pref.eula.0.appName = VMware Player
Feb 08 14:48:29: vmx| DICT   pref.eula.0.buildNumber = 34682
Feb 08 14:48:29: vmx| DICT            pref.eula.size = 1
Feb 08 14:48:29: vmx| DICT    pref.autoFitFullScreen = fitHostToGuest
Feb 08 14:48:29: vmx| DICT     pref.view.navBar.type = favorites
Feb 08 14:48:29: vmx| DICT     pref.mruDest0.present = FALSE
Feb 08 14:48:29: vmx| DICT  pref.mruDest0.destString = 
Feb 08 14:48:29: vmx| DICT        pref.mruDest0.user = 
Feb 08 14:48:29: vmx| DICT     pref.mruDest1.present = FALSE
Feb 08 14:48:29: vmx| DICT  pref.mruDest1.destString = 
Feb 08 14:48:29: vmx| DICT        pref.mruDest1.user = 
Feb 08 14:48:29: vmx| DICT     pref.mruDest2.present = FALSE
Feb 08 14:48:29: vmx| DICT  pref.mruDest2.destString = 
Feb 08 14:48:29: vmx| DICT        pref.mruDest2.user = 
Feb 08 14:48:29: vmx| DICT     pref.mruDest3.present = FALSE
Feb 08 14:48:29: vmx| DICT  pref.mruDest3.destString = 
Feb 08 14:48:29: vmx| DICT        pref.mruDest3.user = 
Feb 08 14:48:29: vmx| DICT     pref.mruDest4.present = FALSE
Feb 08 14:48:29: vmx| DICT  pref.mruDest4.destString = 
Feb 08 14:48:29: vmx| DICT        pref.mruDest4.user = 
Feb 08 14:48:29: vmx| DICT     pref.mruDest5.present = FALSE
Feb 08 14:48:29: vmx| DICT  pref.mruDest5.destString = 
Feb 08 14:48:29: vmx| DICT        pref.mruDest5.user = 
Feb 08 14:48:29: vmx| DICT     pref.mruDest6.present = FALSE
Feb 08 14:48:29: vmx| DICT  pref.mruDest6.destString = 
Feb 08 14:48:29: vmx| DICT        pref.mruDest6.user = 
Feb 08 14:48:29: vmx| DICT     pref.mruDest7.present = FALSE
Feb 08 14:48:29: vmx| DICT  pref.mruDest7.destString = 
Feb 08 14:48:29: vmx| DICT        pref.mruDest7.user = 
Feb 08 14:48:29: vmx| DICT       webUpdate.checkLast = 1170974042
Feb 08 14:48:29: vmx| DICT --- USER DEFAULTS
Feb 08 14:48:29: vmx| DICT --- HOST DEFAULTS
Feb 08 14:48:29: vmx| DICT        vmplayer.searchbar = FALSE
Feb 08 14:48:29: vmx| DICT    vmnet1.hostonlyaddress = 192.168.177.1
Feb 08 14:48:29: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
Feb 08 14:48:29: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
Feb 08 14:48:29: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
Feb 08 14:48:29: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
Feb 08 14:48:29: vmx| DICT                    libdir = /usr/lib/vmware
Feb 08 14:48:29: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Feb 08 14:48:29: vmx| DICT --- SITE DEFAULTS
Feb 08 14:48:29: vmx| DICT                  tag.help = introduction.htm
Feb 08 14:48:29: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Feb 08 14:48:29: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Feb 08 14:48:29: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Feb 08 14:48:29: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Feb 08 14:48:29: vmx| DICT             tag.netConfig = devices_netadapter.htm
Feb 08 14:48:29: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Feb 08 14:48:29: vmx| DICT          tag.serialConfig = devices_serial.htm
Feb 08 14:48:29: vmx| DICT           tag.soundConfig = devices_sound.htm
Feb 08 14:48:29: vmx| DICT             tag.memConfig = configvm_memory.htm
Feb 08 14:48:29: vmx| DICT            tag.miscConfig = configvm.htm
Feb 08 14:48:29: vmx| DICT             tag.usbConfig = devices_usb.htm
Feb 08 14:48:29: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Feb 08 14:48:29: vmx| DICT                 tag.tools = vmtools.htm
Feb 08 14:48:29: vmx| DICT --- COMMAND LINE
Feb 08 14:48:29: vmx| DICT             gui.available = TRUE
Feb 08 14:48:29: vmx| DICT --- CONFIGURATION
Feb 08 14:48:29: vmx| DICT            config.version = 8
Feb 08 14:48:29: vmx| DICT         virtualHW.version = 4
Feb 08 14:48:29: vmx| DICT             uuid.location = 56 4d 04 2a a8 e5 93 cd-44 62 ea bc d4 7f f7 02
Feb 08 14:48:29: vmx| DICT                 uuid.bios = 56 4d 04 2a a8 e5 93 cd-44 62 ea bc d4 7f f7 02
Feb 08 14:48:29: vmx| DICT               uuid.action = create
Feb 08 14:48:29: vmx| DICT        checkpoint.vmState = 
Feb 08 14:48:29: vmx| DICT               displayName = Windows XP
Feb 08 14:48:29: vmx| DICT                annotation = 
Feb 08 14:48:29: vmx| DICT guestinfo.vmware.product.long = 
Feb 08 14:48:29: vmx| DICT guestinfo.vmware.product.url = 
Feb 08 14:48:29: vmx| DICT                   guestOS = winxppro
Feb 08 14:48:29: vmx| DICT                  numvcpus = 1
Feb 08 14:48:29: vmx| DICT                   memsize = 128
Feb 08 14:48:29: vmx| DICT                     paevm = TRUE
Feb 08 14:48:29: vmx| DICT   sched.mem.pshare.enable = TRUE
Feb 08 14:48:29: vmx| DICT     MemAllowAutoScaleDown = FALSE
Feb 08 14:48:29: vmx| DICT               MemTrimRate = -1
Feb 08 14:48:29: vmx| DICT                     nvram = WindowsXP.nvram
Feb 08 14:48:29: vmx| DICT              mks.enable3d = FALSE
Feb 08 14:48:29: vmx| DICT           vmmouse.present = FALSE
Feb 08 14:48:29: vmx| DICT          vmmouse.fileName = auto detect
Feb 08 14:48:29: vmx| DICT            tools.syncTime = TRUE
Feb 08 14:48:29: vmx| DICT       tools.remindinstall = FALSE
Feb 08 14:48:29: vmx| DICT isolation.tools.hgfs.disable = FALSE
Feb 08 14:48:29: vmx| DICT isolation.tools.dnd.disable = FALSE
Feb 08 14:48:29: vmx| DICT isolation.tools.copy.enable = TRUE
Feb 08 14:48:29: vmx| DICT isolation.tools.paste.enabled = TRUE
Feb 08 14:48:29: vmx| DICT            gui.restricted = FALSE
Feb 08 14:48:29: vmx| DICT         ethernet0.present = TRUE
Feb 08 14:48:29: vmx| DICT  ethernet0.connectionType = nat
Feb 08 14:48:29: vmx| DICT     ethernet0.addressType = generated
Feb 08 14:48:29: vmx| DICT ethernet0.generatedAddress = 00:0c:29:59:aa:eb
Feb 08 14:48:29: vmx| DICT ethernet0.generatedAddressOffset = 0
Feb 08 14:48:29: vmx| DICT               usb.present = FALSE
Feb 08 14:48:29: vmx| DICT   usb.generic.autoconnect = FALSE
Feb 08 14:48:29: vmx| DICT             sound.present = TRUE
Feb 08 14:48:29: vmx| DICT          sound.virtualdev = sb16
Feb 08 14:48:29: vmx| DICT            ide0:0.present = TRUE
Feb 08 14:48:29: vmx| DICT           ide0:0.fileName = windows.vmdk
Feb 08 14:48:29: vmx| DICT               ide0:0.mode = independent-persistent
Feb 08 14:48:29: vmx| DICT         ide0:0.deviceType = rawDisk
Feb 08 14:48:29: vmx| DICT               ide0:0.redo = 
Feb 08 14:48:29: vmx| DICT       ide0:0.writeThrough = FALSE
Feb 08 14:48:29: vmx| DICT     ide0:0.startConnected = TRUE
Feb 08 14:48:29: vmx| DICT            ide1:0.present = TRUE
Feb 08 14:48:29: vmx| DICT           ide1:0.fileName = /dev/cdrom
Feb 08 14:48:29: vmx| DICT         ide1:0.deviceType = atapi-cdrom
Feb 08 14:48:29: vmx| DICT       ide1:0.writeThrough = FALSE
Feb 08 14:48:29: vmx| DICT     ide1:0.startConnected = TRUE
Feb 08 14:48:29: vmx| DICT           floppy0.present = TRUE
Feb 08 14:48:29: vmx| DICT          floppy0.fileName = /dev/fd0
Feb 08 14:48:29: vmx| DICT    floppy0.startConnected = TRUE
Feb 08 14:48:29: vmx| DICT           serial0.present = FALSE
Feb 08 14:48:29: vmx| DICT           serial1.present = FALSE
Feb 08 14:48:29: vmx| DICT         parallel0.present = FALSE
Feb 08 14:48:29: vmx| DICT --- USER DEFAULTS
Feb 08 14:48:29: vmx| DICT --- HOST DEFAULTS
Feb 08 14:48:29: vmx| DICT        vmplayer.searchbar = FALSE
Feb 08 14:48:29: vmx| DICT    vmnet1.hostonlyaddress = 192.168.177.1
Feb 08 14:48:29: vmx| DICT    vmnet1.hostonlynetmask = 255.255.255.0
Feb 08 14:48:29: vmx| DICT          control.fullpath = /usr/bin/vmware-cmd
Feb 08 14:48:29: vmx| DICT             loop.fullpath = /usr/bin/vmware-loop
Feb 08 14:48:29: vmx| DICT            dhcpd.fullpath = /usr/bin/vmnet-dhcpd
Feb 08 14:48:29: vmx| DICT                    libdir = /usr/lib/vmware
Feb 08 14:48:29: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Feb 08 14:48:29: vmx| DICT --- SITE DEFAULTS
Feb 08 14:48:29: vmx| DICT                  tag.help = introduction.htm
Feb 08 14:48:29: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Feb 08 14:48:29: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Feb 08 14:48:29: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Feb 08 14:48:29: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Feb 08 14:48:29: vmx| DICT             tag.netConfig = devices_netadapter.htm
Feb 08 14:48:29: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Feb 08 14:48:29: vmx| DICT          tag.serialConfig = devices_serial.htm
Feb 08 14:48:29: vmx| DICT           tag.soundConfig = devices_sound.htm
Feb 08 14:48:29: vmx| DICT             tag.memConfig = configvm_memory.htm
Feb 08 14:48:29: vmx| DICT            tag.miscConfig = configvm.htm
Feb 08 14:48:29: vmx| DICT             tag.usbConfig = devices_usb.htm
Feb 08 14:48:29: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Feb 08 14:48:29: vmx| DICT                 tag.tools = vmtools.htm
Feb 08 14:48:29: vmx| DICT --- GLOBAL SETTINGS
Feb 08 14:48:29: vmx| Msg_Hint: msg.guestos.xp (shown)
Feb 08 14:48:29: vmx| WSSCAN: reserved mem (in MB) min=32 max=928 recommended=928
Feb 08 14:48:29: vmx|         hostMem=1024 maxAllowedAll=4096 maxAllowedVM=3600
Feb 08 14:48:29: vmx|         totOverhead=16
Feb 08 14:48:29: vmx| WSSCAN: used rec mem (in MB) 928
Feb 08 14:48:29: vmx| WSSCAN: Overhead 39153 paged 5278 nonpaged 4096 maxFBSize
Feb 08 14:48:29: vmx| WSSCAN 1 1 237568 -1 237568 -1 50 0
Feb 08 14:48:29: vmx| LICENSE: Running in restricted mode
Feb 08 14:48:29: vmx| STATDECLGROUP stats Root "" null
Feb 08 14:48:29: vmx| Host CPUID features: version 0xf48 id1.edx 0xbfebfbff id1.ecx 0x649d id81.edx 0x20100000 id81.ecx 0x0
Feb 08 14:48:29: vmx| CPU.cpuFeatures = 0xb9b1ff20
Feb 08 14:48:29: vmx| CPUID after masking: version 0xf48 id1.edx 0xfebfbff id1.ecx 0x15 id81.edx 0x100800 id81.ecx 0x0 id88.ecx 0x0
Feb 08 14:48:29: vmx| CPU.cpuFeatures = 0x98b1fe00
Feb 08 14:48:29: vmx| APIC: Local APIC at 0xfee00000
Feb 08 14:48:29: vmx| KHZEstimate 2992603
Feb 08 14:48:29: vmx| MHZEstimate 2993
Feb 08 14:48:29: vmx| NumVCPUs 1
Feb 08 14:48:29: vmx| UUID: location-UUID is 56 4d 04 2a a8 e5 93 cd-44 62 ea bc d4 7f f7 02
Feb 08 14:48:29: vmx| MM: Using partialmap, 32768 pages AC 0 CE 1 TM 0 DOHU 0
Feb 08 14:48:29: vmx| UUID: canonical path is /home/mrmeh/RunningWindows/windows.vmx
Feb 08 14:48:29: vmx| UUID: location-UUID is 56 4d 04 2a a8 e5 93 cd-44 62 ea bc d4 7f f7 02
Feb 08 14:48:29: vmx| MM: using fileName /home/mrmeh/RunningWindows/564d042a-a8e5-93cd-4462-eabcd47ff702.vmem for paging
Feb 08 14:48:29: vmx| Msg_Reset:
Feb 08 14:48:29: vmx| ----------------------------------------
Feb 08 14:48:29: vmx| Opened paging file /home/mrmeh/RunningWindows/564d042a-a8e5-93cd-4462-eabcd47ff702.vmem
Feb 08 14:48:29: vmx| Mapped mainmem as pageable
Feb 08 14:48:29: vmx| MStat: Creating Stat vm.uptime
Feb 08 14:48:29: vmx| DISK: OPEN ide0:0 '/home/mrmeh/RunningWindows/windows.vmdk' independent-persistent R[(null)]
Feb 08 14:48:29: vmx| AIOGNRC: Starting 4 I/O threads.
Feb 08 14:48:29: vmx| DISKLIB-DSCPTR: Opened [0]: "windowsxp.mbr" 0 (0xa)
Feb 08 14:48:29: vmx| AIOGNRC: Failed to open '/dev/sda' : Insufficient permissions to access the file (115) (0x3).
Feb 08 14:48:29: vmx| DISKLIB-FLAT  : Opening unbuffered failed; trying Simple
Feb 08 14:48:29: vmx| AIOGNRC: Failed to open '/dev/sda' : Insufficient permissions to access the file (115) (0x3).
Feb 08 14:48:29: vmx| DISKLIB-FLAT  : "/dev/sda" : failed to open (38): AIOMgr_Open failed.
Feb 08 14:48:29: vmx| DISKLIB-DSCPTR: Failed to open extents for descriptor file in normal mode
Feb 08 14:48:29: vmx| DISKLIB-LINK  : "/home/mrmeh/RunningWindows/windows.vmdk" : failed to open (Insufficient permission to access file).  
Feb 08 14:48:29: vmx| DISKLIB-CHAIN : "/home/mrmeh/RunningWindows/windows.vmdk" : failed to open (Insufficient permission to access file).
Feb 08 14:48:29: vmx| DISKLIB-LIB   : Failed to open '/home/mrmeh/RunningWindows/windows.vmdk' with flags 0xa (Insufficient permission to access file).
Feb 08 14:48:29: vmx| DISK: Cannot open disk "/home/mrmeh/RunningWindows/windows.vmdk": Insufficient permission to access file (38).
Feb 08 14:48:29: vmx| DISK: Failed to open disk '/home/mrmeh/RunningWindows/windows.vmdk' : Insufficient permission to access file (38) 3023.
Feb 08 14:48:29: vmx| Msg_Post: Error
Feb 08 14:48:29: vmx| [msg.disk.noBackEnd] Cannot open the disk '/home/mrmeh/RunningWindows/windows.vmdk' or one of the snapshot disks it depends on.
Feb 08 14:48:29: vmx| [msg.disk.configureDiskError] Reason: Insufficient permission to access file.----------------------------------------
Feb 08 14:48:31: vmx| Module DiskEarly power on failed.
Feb 08 14:48:31: vmx| VMX_PowerOn: ModuleTable_PowerOn = 0
Feb 08 14:48:31: IO#0| AIOGNRC: thread #0 exiting (0)
Feb 08 14:48:31: IO#1| AIOGNRC: thread #1 exiting (0)
Feb 08 14:48:31: IO#2| AIOGNRC: thread #2 exiting (0)
Feb 08 14:48:31: IO#3| AIOGNRC: thread #3 exiting (0)
Feb 08 14:48:31: vmx| AIOGNRC: asyncOps=0 syncOps=0 maxPending=0 maxCompleted=0
Feb 08 14:48:31: vmx| vmdbPipe_Streams Couldn't read: OVL_STATUS_EOF
Feb 08 14:48:31: vmx| VMX idle exit
Feb 08 14:48:31: vmx| Flushing VMX VMDB connections
Feb 08 14:48:31: vmx| IPC_exit: disconnecting all threads
Feb 08 14:48:31: vmx| VMX exit.
Feb 08 14:48:31: vmx| AIOMGR-S : stat o=4 r=4 w=0 i=0 br=1794 bw=0
```

Anyone know what could be the real problem? (Btw, I installed vmware-player via the tarball from the vmware site.)

[edit]It's only running when I execute using root and xp is giving me a bsod :(

---

### Post by Buelldozer on 2007-02-08
[http://www.ubuntuforums.org/showthread.php?t=356603](http://www.ubuntuforums.org/showthread.php?t=356603)

I'm working with a more knowledgeable Linux guy for a FIX right now, but that post contains a work around.

---

### Post by Absurd on 2007-02-08
I found the paevm="TRUE" option, set it to FALSE and now I get this error

```
*** VMware Player internal monitor error (bug 9297) ***

The guest operating system you are running is using the Physical Address Extension (PAE) processor option.  For more information about
running PAE-enabled guest operating systems, please consult http://www.vmware.com/info?id=28
```

---

### Post by Buelldozer on 2007-02-08
set your paevm back to "TRUE", that's what you are going to need to run WinXP SP2 in VM on your machine apparently.

Here is a "band aid" to the whole permissions thing.

Make sure you have gksudo installed on your computer "sudo apt-get install gksudo" at a command line.

Then go into the application launcher for VM Player and EDIT it, adding gksudo before the word vmplayer in the command box.

In Ubuntu Feisty this is accomplished by right clicking on applications in the menu bar and selecting edit menus. From there navigate into system and then right click on VMWare Player and select properties. Now add the word gksudo ahead of vmplayer and save your changes.

The first time you launch vmware it will ask you for your su password. Once you give your password it will launch vmplayer for you with escalated permissions.

I don't know how to fix your BSD issue and if I did I'd be worth millions of dollars. :)

---

### Post by Absurd on 2007-02-08
Thanks. My only problem now is the BSOD.

Btw, the error on the BSOD is 0x0000007B

---

### Post by Buelldozer on 2007-02-09
Ouch, You can try and follow these directions: [http://support.microsoft.com/kb/324103](http://support.microsoft.com/kb/324103)

I hate the 07 stop code, it usually means that something has gone wrong with the ntfs partition, typically it happens because the drive geometry has changed when Windows didn't expect it to.

---

### Post by AC_Soaring on 2008-03-04
I'll bet you are also only getting 1 cpu in UBUNTU even though you're PC has a dual-core.  My VMplayer log looks just like this (2 cpu's showing on player start, but only 1 in the UBUNTU part of the log).

Any ideas??

- Alan

---

