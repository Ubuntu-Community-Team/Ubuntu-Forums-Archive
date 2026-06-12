---
title: "Can't identify problem - stutters from time to time: java(PHPStorm)/SSHFS"
date: 2015-12-16
forum: General Help
---

### Post by jan62 on 2015-12-16
Can't identify problem - stutters from time to time: java(PHPStorm)/SSHFS

Hi,

I cannot identify my problem. 
Stutter means my system is going almost unresponsive - for few seconds to one-two minutes. Killing PHPstorm from xkill/killing java from cmdline helps almost immediately. But I don't think it's PHPstorm/java related - it happens also when my PHPstorm is closed, but then that lag is much shorter, but then I cannot close Java/PHPStorm, because these programs are not running. 

I bet that's SSHFS related. 




I'm using PHPStorm, working on remote system using SSHFS (mounted frm fstab), I'm using Oracle java, x64 (checked in PHPStorm).
IO think problem is java/PHPstorm related - when I'm killing PHPStorm immediately after stuttering happens, system is goin responsive again.


Every step I made is getting my system more robust and fast, that's advantage. But main problem remains unresolved.

I've disabled ext4 journaling. Added some strange options to primary hdd fstab entry: commit=60,noatime
I've been adding some options to my grub. Nothing helps.
I've tried to set some options with xdiagnose. Without luck.
I've tried to close as many services/apps using bootupmanager.
Tried new kernels. No effect.
Tried to use new libfuse. It limited my problems with SSHFS disconnecting from time to time (now I don't have that problem, so it helped with some SSHFS problem).
Of course, I've made extensive tuning of my Java - set many, many options in my  phpstorm64.vmoptions. 
I've disabled chrome 3d acceleration
I have newest XFCE. 
I've disabled inspections, lot of plugins in PHPStorm.

I've tried to check in  htop - my java process (I'm using tuxjdk, but same story happens when using pure Oracle JDK, tuxjdk is a must, because I want to have clean and properly rendered fonts in my IDE). I'm using also infinality patch.

Please, help me. That's computer in my job. I'm spending more and more time in my work time trying to reach level of usability adequate for WORK. Noone have such problems with lagging environment.
That's not normal behaviour. I have such problems few times a day. Sometimes I must react immediately at work, and change something, and just have full control over my computer. 

Someone could give me some direction to check/what to do? 
I'm pasting information I think are relevant. I'll provide all information needed. 

Thanks!

my etc/fstab entry:
```

[EMAIL="jdanielewicz@devel-01.gratka.pl"]jdanielewicz@devel-01.gratka.pl[/EMAIL]:/home/xxxxxxlogin/ /mnt/xxx/ fuse.sshfs _netdev,user,idmap=user,transform_symlinks,identityfile=/home/xxxxxx/.ssh/id_rsa,allow_other,default_permissions,auto,reconnect,uid=1000,gid=1000 0 0

```

```

uname -a
Linux xxxxxxxxxxxxx 3.19.0-39-generic #44-Ubuntu SMP Tue Dec 1 14:39:05 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

My phpstorm64.vmoptions file:
```

-Xss2m
-Xms32m 
-Xmx512m
-XX:PermSize=32m 
-XX:MaxPermSize=200m
-XX:ReservedCodeCacheSize=225m
-ea
-Dsun.io.useCanonCaches=false
-Djava.net.preferIPv4Stack=true
-Djsse.enableSNIExtension=false
-XX:+UseConcMarkSweepGC
-XX:MinHeapFreeRatio=15
-XX:SoftRefLRUPolicyMSPerMB=50
-XX:+UseCodeCacheFlushing
-Dawt.useSystemAAFontSettings=lcd
-Dsun.java2d.xrender=true
-Dsun.java2d.opengl=true
-Dsun.java2d.noddraw=true 
-Dsun.java2d.d3d=false

```

```
java -version|awk '{print$3}'  

java version "1.8.0_66"
Java(TM) SE Runtime Environment (build 1.8.0_66-b17)
Java HotSpot(TM) 64-Bit Server VM (build 25.66-b17, mixed mode)

```

```
> sudo lshw
    description: Computer
    width: 64 bits
    capabilities: smbios-2.6 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3908MiB
     *-cpu
          product: Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2022MHz
          capacity: 3100MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer xsave avx lahf_lm arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid xsaveopt cpufreq
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=snb_uncore
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:3000(size=4096) memory:e1400000-e14fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:29 memory:d0000000-dfffffff memory:e1420000-e143ffff ioport:3000(size=256) memory:e1400000-e141ffff
           *-multimedia
                description: Audio device
                product: Caicos HDMI Audio [Radeon HD 6400 Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:28 memory:e1440000-e1443fff
        *-communication:0
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:26 memory:e15a0000-e15a000f
        *-communication:1
             description: Serial controller
             product: 6 Series/C200 Series Chipset Family KT Controller
             vendor: Intel Corporation
             physical id: 16.3
             bus info: pci@0000:00:16.3
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi 16550 bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:17 ioport:4100(size=8) memory:e1580000-e1580fff
        *-network
             description: Ethernet interface
             product: 82579LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 04
             serial: 18:03:73:c6:6f:42
             size: 100Mbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.13-4 ip=172.17.2.13 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:25 memory:e1500000-e151ffff memory:e1570000-e1570fff ioport:4020(size=32)
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:e1560000-e15603ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 3.19.0-39-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 3.19
                capabilities: usb-2.00
                configuration: driver=hub slots=3 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:27 memory:e1550000-e1553fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:2000(size=4096) memory:e0a00000-e13fffff ioport:e0000000(size=10485760)
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:17 memory:e1540000-e15403ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 3.19.0-39-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 3.19
                capabilities: usb-2.00
                configuration: driver=hub slots=3 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
                 *-usb:0
                      description: Keyboard
                      product: USB Keyboard
                      physical id: 1
                      bus info: usb@2:1.1
                      version: 1.01
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
                 *-usb:1
                      description: Mouse
                      product: HP USB Laser Mouse
                      vendor: HP
                      physical id: 2
                      bus info: usb@2:1.2
                      version: 31.00
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=98mA speed=1Mbit/s
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Q65 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:40f0(size=8) ioport:40e0(size=4) ioport:40d0(size=8) ioport:40c0(size=4) ioport:40b0(size=16) ioport:40a0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:e1530000-e15300ff ioport:4000(size=32)
        *-ide:1
             description: IDE interface
             product: 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:4090(size=8) ioport:4080(size=4) ioport:4070(size=8) ioport:4060(size=4) ioport:4050(size=16) ioport:4040(size=16)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3250312AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: JC47
             serial: 9VYDVXN6
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=6dc639ca
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: ebddeb29-f8bb-43c4-8f4f-3d716e833b72
                size: 228GiB
                capacity: 228GiB
                capabilities: primary bootable extended_attributes large_files huge_files dir_nlink extents ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/ modified=2015-12-16 15:19:30 mount.fstype=ext4 mount.options=rw,noatime,commit=60 mounted=2015-12-16 15:41:18 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 4051MiB
                capacity: 4051MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 4051MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: DVD-ROM DH-16D5S
             vendor: PLDS
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: VD15
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=nodisc

```

```

$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_SGI_swap_control
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_buffer_age, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD CAICOS (DRM 2.40.0, LLVM 3.6.0)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 11.0.4
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
```

---

### Post by dragonfly41 on 2015-12-16
A lot of information to wade through ..

Let's try a process of elimination ..

Can you logout from this session and login as guest user?
 Any problems seen in guest account?

[Later edit]

Other things to try ..

PHPStorm - disable indexing by enabling power saving mode.

[https://devnet.jetbrains.com/message/5544942](https://devnet.jetbrains.com/message/5544942)

...

I've tried PHPStorm (didn't like Java framework) and Aptana Studio 3 but decided to use Sublime Text 3 plus some added packages for PHP development.

---

### Post by jan62 on 2015-12-17
I'll try on another WM, also another/guest profile.

---

### Post by jan62 on 2015-12-21
That's not xubuntu related - same story with fluxbox same with guest profile.

---

### Post by dragonfly41 on 2015-12-21
Why is this not "xubuntu related". Why can't you create a fresh user account/profile in xubuntu?
You are not alone with PHPStorm problems ..
read here .. [http://stackoverflow.com/questions/12455277/phpstorm-exceptionally-slow-while-editing-javascript](http://stackoverflow.com/questions/12455277/phpstorm-exceptionally-slow-while-editing-javascript)

perhaps try tweaking Java vmoptions to give more memory?

I don't understand your reference to fluxbox (not mentioned earlier).

---

### Post by jan62 on 2015-12-21
I've tried on another WM. Same result - perhaps that's something related to SSHFS and JAVA, between them.

---

### Post by matt_symes on 2015-12-21
Hi

I edited your first post to make it readable by adding [noparse]```

```[/noparse] tags. Please use them.

Have you identified whether it's CPU, I/O or memory bound ? Is it paging out memory to the drive ? Are you network bound ?

If you have not identified where exactly the problem is then you are just speculating at what the problem maybe.

You'll want tools beyond just htop to see where the problem is.

Some of the tools i use:

vmstat
dstat
top
iostat
iotop
free
iftop
nethogs

The information in your first post is a great software and hardware audit of your system but if you want to know why it's stuttering then you need to use the tools that'll show you is happening to your system.

If you think it may be sshfs then what encryption cipher are you using ?  

Kind regards

---

### Post by dragonfly41 on 2015-12-22
If you narrow your google search to "SSHFS NEAR stuttering" this comes up ..
[http://forum.kodi.tv/showthread.php?tid=197949](http://forum.kodi.tv/showthread.php?tid=197949)

but remember that the description "stuttering" also refers to audio problems.

---

### Post by jan62 on 2015-12-28
Unfortunately, changing from SSHFS is not possible in my case. 
I'm working on +10 up to 20 mounted directories. I'm switching beetween them in my ID E(PHPStorm) to have responsive and fast environment. Working on samba is too slow - after i. e. pulling files from git repository i have to wait much more time using Samba than on SSHFS - everyone in my company on Linuxes use SSHFS.

I'll concentrate on SSHFS errors (I've used debug params - debug,sshfs_debug,loglevel=debug, in my fstab)

---

