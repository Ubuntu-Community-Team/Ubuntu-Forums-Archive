---
title: "Graphics Driver Issue Starting Lubuntu"
date: 2015-02-04
forum: General Help
---

### Post by aaron50 on 2015-02-04
Hello all,

I am trying to start Lubuntu on my fresh install of Ubuntu 14.04. I followed the advice of this forum post ([http://ubuntuforums.org/showthread.php?t=2222849&page=3](http://ubuntuforums.org/showthread.php?t=2222849&page=3)) and posted on it towards the end what i was doing. I will post here again for reference so that you really don't have to refer back to the other post. The individual helping me said that this may be a "lower level graphics-driver issue" and to post my graphics card specs. Here is the output from [COLOR=#000000][FONT=Ubuntu Mono]sudo lshw -C display

[/FONT][/COLOR]```
  *-display UNCLAIMED       description: VGA compatible controller
       product: CN896/VN896/P4M900 [Chrome 9 HC]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: latency=64 mingnt=2

       resources: memory:c0000000-dfffffff memory:fd000000-fdffffff memory:feaf0000-feafffff
```[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR][COLOR=#000000]Here are my steps that i took from the start:[/COLOR]

[LIST=1]
[*]installed a fresh copy of Ubuntu 14.04 trusty onto my machine
[*]ran in command line - sudo apt-get update && sudo apt-get upgrade
[*]ran in command line - sudo reboot
[*]login as the user that i created when i set up the machine
[*]ran in command line - sudo apt-get install lxde-common --no-install-recommends
[*]ran in command line - sudo apt-get install lubuntu-core --no-install-recommends
[*]ran in command line - echo 'lxsession -s Lubuntu -e LXDE' > ~/.xsession
[*]ran in command line - sudo reboot
[*]login as the user that i created when i set up the machine
[*]ran in command line - startx
[/LIST]


[COLOR=#000000]Here is where i get an error. It appears that it is trying to start up Lubuntu but cannot. I get a 30 or so "Initializing built-in" lines then "loading extension GLX". This looks like it is probably correct, but then i get some lines that start off (EE) and the last few are as follows:[/COLOR]

[COLOR=#000000]```

Fatal server error:
(EE) Caught signal 11 (Segmentation fault). Server aborting
(EE)
(EE)
Please consult the The X.Org Foundation support at [http://wiki.x.org](http://wiki.x.org)
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information
(EE)
(EE) Server terminated with error (1). Closing log file.
xinit: giving up
xinit: unable to connect to X server: connection refused
xinit: server error
```
[/COLOR]
[COLOR=#000000]I am very new to this but "giving up" never sounds good [/COLOR][IMG]http://ubuntuforums.org/images/icons/icon9.png[/IMG]

[COLOR=#000000]I looked around for the fatal service error and maybe i don't have a graphics chip or something to support Lubuntu?? I am not sure what any of this means.[/COLOR]

[COLOR=#000000]If you know why this is not working, let me know, or if you need the log information, i think i could probably figure out how to open that file and view it.[/COLOR]

[COLOR=#000000]Thank again for your help[/COLOR]

---

### Post by Bashing-om on 2015-02-04
aaron50; Hello;

I will take a stab at this.
Is this a 'Chrome' note book system ?
What results when you boot up a liveDVD(USB) ? -> all hunky dory ? else ?

longest journey begins
[INDENT][INDENT][INDENT]that 1st step
[/INDENT][/INDENT][/INDENT]

---

### Post by aaron50 on 2015-02-04
> **Bashing-om said:**
> aaron50; Hello;

I will take a stab at this.
Is this a 'Chrome' note book system ?
What results when you boot up a liveDVD(USB) ? -> all hunky dory ? else ?

longest journey begins[INDENT][INDENT][INDENT]that 1st step
[/INDENT]
[/INDENT]
[/INDENT]

Bashing,

This is not a 'Chrome' note book system as far as i know. A family member had a bunch of spare parts, not too old, laying around and i decided to build a computer and make it into a server out of them. I believe this was used as a home computer in its prior life. It used to run windows xp as its primary and on the other hard drive 95/98/me. The machine is currently running Ubuntu 14.04 on command line only. I am very new to Ubuntu and all command line, so i am trying to learn as i go, so bear with me. I am not sure what you mean by boot up a liveDVD(USB). Can you put this into more lamens terms. I am sorry for my lack of knowledge.

---

### Post by Bashing-om on 2015-02-04
aaron50; Jey;  OK


We get up and see what we can do. Builds can be fun to mess with.

Let's look at what we have to work with. Post back the outputs of terminal command:
```

cat /proc/cpuinfo

```
I have never encountered this 
> 
CN896/VN896/P4M900 [Chrome 9 HC]

chip set.
may take some time to research it.

I am confused as to what there is for a GUI ( on a server ???)
> 
installed a fresh copy of Ubuntu 14.04 trusty onto my machine

Did you install the server edition and then add the GUI components ?
-----------------------------------------
And hey, learning is a process, no one will hold it against you that you are just picking up on 'buntu. We were all new at one time.
> 
 I am not sure what you mean by boot up a liveDVD(USB). 

That is an install medium containing the desktop. If this desktop installer is on a DVD then it is a liveDVD. if on a USB it becomes a liveUSB.
-------------------

[INDENT][INDENT]anyway, let's see what we can do
[/INDENT][/INDENT]

---

### Post by steeldriver on 2015-02-04
Bashing-om I think the "Chrome" in this case refers to the [VIA S3 Chrome9]("http://en.wikipedia.org/wiki/S3_Chrome#Chrome9") graphics accelerator

aaron50can you check the following from the server command line please?

```

apt-cache policy xserver-xorg-video-openchrome

```

and also

```

lspci -vnn | grep -i vga

```

---

### Post by aaron50 on 2015-02-05
Bashing,

I will attempt to answer all of your questions first, then move onto Steeldrivers.

Here is what the output of cat /proc/cpuinfo is:
```
processor       : 0vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Genuine Intel(R) CPU            2140  @ 1.60GHz
stepping        : 2
microcode       : 0x51
cpu MHz         : 1200.000
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fdiv_bug        : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov                                                                                         pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arc                                                                                        h_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr                                                                                         pdcm lahf_lm dtherm
bogomips        : 3192.17
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:


processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Genuine Intel(R) CPU            2140  @ 1.60GHz
stepping        : 2
microcode       : 0x51
cpu MHz         : 1200.000
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fdiv_bug        : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov                                                                                         pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arc                                                                                        h_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr                                                                                         pdcm lahf_lm dtherm
bogomips        : 3192.17
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

```

to your question about the GUI and server: About 6 months ago, i downloaded Ubunutu 14.04 Server edition onto a very old laptop just to play around with it. I had no GUI on this machine because i did not think it could handle it. I was able to successfully make it into a file server using samba, and do a couple of other things on it, but now its time to move up a peg. My end goal is to build a powerful machine that can act as a file server, media server, webserver, etc., but i need to learn more first. That is why i just scrounged around at a relatives and made up a pc, this one i am hoping is faster than the laptop. Since I am not very command line savy, i would like to be able to have a very lightweight GUI on top of the server that i can boot into if i need to. MY goal is to learn more about linux and how everything is set up using the GUI then translate that into command line statements. That way when i do build my full server, i do not have to have a GUI, so i will have less security holes as i understand it. I am sorry for the drawn out explanation, but i figured i would give you the whole scoop of where i am coming from.

Steeldriver,

you are correct, i believe the Chrome is referring to the [COLOR=#000000]VIA S3 graphics accelerator, at least what i have been able to determine by googleing.[/COLOR] Here is my output to your request:

apt-cache policy xserver-xorg-video-openchrome:
```
xserver-xorg-video-openchrome:  Installed: 1:0.3.3-1build1
  Candidate: 1:0.3.3-1build1
  Version table:
 *** 1:0.3.3-1build1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status

```

Here is the output to lspci -vnn | grep -i vga:
[CODE]01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] [1106:3371] (rev 01) (prog-if 00 [VGA controller])
[CODE]

Thank you both again for any help you can provide

---

### Post by steeldriver on 2015-02-05
Unfortunately, support for those old VIA adapters is spotty at best - according to the list of [OpenChrome supported hardware]("http://www.freedesktop.org/wiki/Openchrome/SupportedHardware/") your device should be supported, with at least 2D acceleration but only software OpenGL rendering. However googling suggests that people are having little success, at least with 14.04-based distros. You might want to try a live CD/USB of Xubuntu 12.04 or Lubuntu 12.04

If you want to try diagnosing the issue further, you could pastebin the complete /var/log/Xorg.0.log

```

sudo apt get install pastebinit

pastebinit /var/log/Xorg.0.log

```

however there's no guarantee we will be able to find a solution.

---

### Post by aaron50 on 2015-02-05
Steeldriver,

Here is the output to the pastebinit command:

```
[COLOR=#000000][    24.336] [/COLOR]X.Org X Server 1.15.1
Release Date: 2014-04-13
[    24.336] X Protocol Version 11, Revision 0
[    24.336] Build Operating System: Linux 3.2.0-70-generic i686 Ubuntu
[    24.336] Current Operating System: Linux Otto-Server 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:23:46 UTC 2014 i686
[    24.336] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-44-generic root=/dev/mapper/Otto--Server--vg-root ro
[    24.336] Build Date: 10 December 2014  06:16:10PM
[    24.336] xorg-server 2:1.15.1-0ubuntu2.6 (For technical support please see http://www.ubuntu.com/support) 
[    24.336] Current version of pixman: 0.30.2
[    24.336] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    24.336] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.337] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb  5 06:56:53 2015
[    24.371] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.371] (==) No Layout section.  Using the first Screen section.
[    24.371] (==) No screen section available. Using defaults.
[    24.371] (**) |-->Screen "Default Screen Section" (0)
[    24.371] (**) |   |-->Monitor "<default monitor>"
[    24.372] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    24.372] (==) Automatically adding devices
[    24.372] (==) Automatically enabling devices
[    24.372] (==) Automatically adding GPU devices
[    24.538] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.538] 	Entry deleted from font path.
[    24.538] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.538] 	Entry deleted from font path.
[    24.538] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.538] 	Entry deleted from font path.
[    24.538] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    24.538] 	Entry deleted from font path.
[    24.539] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.539] 	Entry deleted from font path.
[    24.539] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.539] 	Entry deleted from font path.
[    24.539] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	built-ins
[    24.539] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.539] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.539] (II) Loader magic: 0xb771f6c0
[    24.539] (II) Module ABI versions:
[    24.539] 	X.Org ANSI C Emulation: 0.4
[    24.539] 	X.Org Video Driver: 15.0
[    24.539] 	X.Org XInput driver : 20.0
[    24.539] 	X.Org Server Extension : 8.0
[    24.541] (--) PCI:*(0:1:0:0) 1106:3371:1019:1b47 rev 1, Mem @ 0xc0000000/536870912, 0xfd000000/16777216, BIOS @ 0x????????/65536
[    24.541] Initializing built-in extension Generic Event Extension
[    24.541] Initializing built-in extension SHAPE
[    24.541] Initializing built-in extension MIT-SHM
[    24.541] Initializing built-in extension XInputExtension
[    24.541] Initializing built-in extension XTEST
[    24.541] Initializing built-in extension BIG-REQUESTS
[    24.541] Initializing built-in extension SYNC
[    24.541] Initializing built-in extension XKEYBOARD
[    24.541] Initializing built-in extension XC-MISC
[    24.541] Initializing built-in extension SECURITY
[    24.541] Initializing built-in extension XINERAMA
[    24.541] Initializing built-in extension XFIXES
[    24.541] Initializing built-in extension RENDER
[    24.541] Initializing built-in extension RANDR
[    24.541] Initializing built-in extension COMPOSITE
[    24.541] Initializing built-in extension DAMAGE
[    24.541] Initializing built-in extension MIT-SCREEN-SAVER
[    24.541] Initializing built-in extension DOUBLE-BUFFER
[    24.541] Initializing built-in extension RECORD
[    24.541] Initializing built-in extension DPMS
[    24.541] Initializing built-in extension Present
[    24.541] Initializing built-in extension DRI3
[    24.541] Initializing built-in extension X-Resource
[    24.541] Initializing built-in extension XVideo
[    24.542] Initializing built-in extension XVideo-MotionCompensation
[    24.542] Initializing built-in extension SELinux
[    24.542] Initializing built-in extension XFree86-VidModeExtension
[    24.542] Initializing built-in extension XFree86-DGA
[    24.542] Initializing built-in extension XFree86-DRI
[    24.542] Initializing built-in extension DRI2
[    24.542] (II) LoadModule: "glx"
[    24.610] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    24.767] (II) Module glx: vendor="X.Org Foundation"
[    24.767] 	compiled for 1.15.1, module version = 1.0.0
[    24.767] 	ABI class: X.Org Server Extension, version 8.0
[    24.767] (==) AIGLX enabled
[    24.767] Loading extension GLX
[    24.767] (==) Matched openchrome as autoconfigured driver 0
[    24.767] (==) Matched modesetting as autoconfigured driver 1
[    24.767] (==) Matched fbdev as autoconfigured driver 2
[    24.767] (==) Matched vesa as autoconfigured driver 3
[    24.767] (==) Assigned the driver to the xf86ConfigLayout
[    24.768] (II) LoadModule: "openchrome"
[    24.768] (II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
[    24.768] (II) Module openchrome: vendor="http://openchrome.org/"
[    24.768] 	compiled for 1.15.0, module version = 0.3.3
[    24.768] 	Module class: X.Org Video Driver
[    24.768] 	ABI class: X.Org Video Driver, version 15.0
[    24.768] (II) LoadModule: "modesetting"
[    24.769] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    24.769] (II) Module modesetting: vendor="X.Org Foundation"
[    24.769] 	compiled for 1.15.0, module version = 0.8.1
[    24.769] 	Module class: X.Org Video Driver
[    24.769] 	ABI class: X.Org Video Driver, version 15.0
[    24.769] (II) LoadModule: "fbdev"
[    24.769] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.769] (II) Module fbdev: vendor="X.Org Foundation"
[    24.769] 	compiled for 1.15.0, module version = 0.4.4
[    24.769] 	Module class: X.Org Video Driver
[    24.769] 	ABI class: X.Org Video Driver, version 15.0
[    24.769] (II) LoadModule: "vesa"
[    24.770] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.770] (II) Module vesa: vendor="X.Org Foundation"
[    24.770] 	compiled for 1.15.0, module version = 2.3.3
[    24.770] 	Module class: X.Org Video Driver
[    24.770] 	ABI class: X.Org Video Driver, version 15.0
[    24.770] (II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
	K8M800/K8N800, PM800/PM880/CN400, VM800/P4M800Pro/VN800/CN700,
	CX700/VX700, K8M890/K8N890, P4M890, P4M900/VN896/CN896, VX800/VX820,
	VX855/VX875, VX900
[    24.770] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    24.770] (II) FBDEV: driver for framebuffer: fbdev
[    24.770] (II) VESA: driver for VESA chipsets: vesa
[    24.770] (++) using VT number 7

[    24.770] (!!) VIA Technologies does not support this driver in any way.
[    24.770] (!!) For support, please refer to http://www.openchrome.org/.
[    24.770] (!!) (openchrome 0.3.3 release)
[    24.770] (WW) Falling back to old probe method for modesetting
[    24.770] (EE) open /dev/dri/card0: No such file or directory
[    24.771] (WW) Falling back to old probe method for fbdev
[    24.771] (II) Loading sub module "fbdevhw"
[    24.771] (II) LoadModule: "fbdevhw"
[    24.771] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.771] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.771] 	compiled for 1.15.1, module version = 0.0.2
[    24.771] 	ABI class: X.Org Video Driver, version 15.0
[    24.771] (WW) Falling back to old probe method for vesa
[    24.771] (II) CHROME(0): VIAPreInit
[    24.771] (II) CHROME(0): VIAGetRec
[    24.771] (--) CHROME(0): Chipset: P4M900/VN896/CN896
[    24.772] (--) CHROME(0): Chipset revision: 0
[    24.912] (EE) CHROME(0): [drm] Failed to open DRM device for pci:0000:01:00.0: No such file or directory
[    24.912] (II) Loading sub module "vgahw"
[    24.912] (II) LoadModule: "vgahw"
[    24.912] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    24.912] (II) Module vgahw: vendor="X.Org Foundation"
[    24.912] 	compiled for 1.15.1, module version = 0.1.0
[    24.912] 	ABI class: X.Org Video Driver, version 15.0
[    24.912] (--) CHROME(0): Probed amount of VideoRAM = 65536 kB
[    24.912] (II) CHROME(0): VIAMapMMIO
[    24.912] (--) CHROME(0): mapping MMIO @ 0xfd000000 with size 0xd000
[    24.912] (--) CHROME(0): mapping BitBlt MMIO @ 0xfd200000 with size 0x200000
[    24.913] (II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0
[    24.913] (II) CHROME(0): VIAMapFB
[    24.913] (--) CHROME(0): mapping framebuffer @ 0xc0000000 with size 0x4000000
[    24.913] (--) CHROME(0): Frame buffer start: 0xb299f000, free start: 0x0 end: 0x4000000
[    24.913] (II) CHROME(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    24.913] (==) CHROME(0): Depth 24, (--) framebuffer bpp 32
[    24.913] (==) CHROME(0): RGB weight 888
[    24.913] (==) CHROME(0): Default visual is TrueColor
[    24.913] (II) CHROME(0): VIASetupDefaultOptions - Setting up default chipset options.
[    24.913] (==) CHROME(0): Shadow framebuffer is disabled.
[    24.913] (==) CHROME(0): Hardware acceleration is enabled.
[    24.913] (==) CHROME(0): Using EXA acceleration architecture.
[    24.913] (==) CHROME(0): EXA composite acceleration enabled.
[    24.913] (==) CHROME(0): EXA scratch area size is 4096 kB.
[    24.913] (==) CHROME(0): Using hardware two-color cursors and software full-color cursors.
[    24.913] (==) CHROME(0): GPU virtual command queue will be enabled.
[    24.913] (==) CHROME(0): DRI IRQ will be enabled if DRI is enabled.
[    24.913] (==) CHROME(0): AGP DMA will be disabled if DRI is enabled.
[    24.913] (==) CHROME(0): PCI DMA will not be used for XV image transfer if DRI is enabled.
[    24.913] (==) CHROME(0): Will not enable VBE modes.
[    24.913] (==) CHROME(0): VBE VGA register save & restore will not be used
	if VBE modes are enabled.
[    24.913] (==) CHROME(0): Xv Bandwidth check is enabled.
[    24.913] (==) CHROME(0): Will not impose a limit on video RAM reserved for DRI.
[    24.913] (==) CHROME(0): Will try to allocate 32768 kB of AGP memory.
[    24.913] (==) CHROME(0): TV dotCrawl is disabled.
[    24.913] (==) CHROME(0): TV deflicker is set to 0.
[    24.913] (==) CHROME(0): No default TV type is set.
[    24.913] (==) CHROME(0): No default TV output signal type is set.
[    24.913] (==) CHROME(0): No default TV output port is set.
[    24.913] (==) CHROME(0): Will not print VGA registers.
[    24.913] (==) CHROME(0): Will not scan I2C buses.
[    24.913] (II) CHROME(0): ...Finished parsing config file options.
[    24.913] (EE) CHROME(0): Unknown Card-Ids (3371|1019|1B47), Chipset: P4M900/VN896/CN896; please report to openchrome-users@lists.freedesktop.org
[    24.913] (EE) 
[    24.914] (EE) Backtrace:
[    24.914] (EE) 0: /usr/bin/X (xorg_backtrace+0x4f) [0xb769810f]
[    24.914] (EE) 1: /usr/bin/X (0xb74ef000+0x1acef4) [0xb769bef4]
[    24.914] (EE) 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb74cc40c]
[    24.914] (EE) 3: /usr/lib/xorg/modules/drivers/openchrome_drv.so (0xb6bce000+0x13c9c) [0xb6be1c9c]
[    24.914] (EE) 4: /usr/bin/X (InitOutput+0xb43) [0xb7572343]
[    24.914] (EE) 5: /usr/bin/X (0xb74ef000+0x40de7) [0xb752fde7]
[    24.914] (EE) 6: /usr/bin/X (0xb74ef000+0x2ab4e) [0xb7519b4e]
[    24.914] (EE) 7: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xf3) [0xb70dfa83]
[    24.914] (EE) 8: /usr/bin/X (0xb74ef000+0x2ab84) [0xb7519b84]
[    24.914] (EE) 
[    24.914] (EE) Segmentation fault at address 0x0
[    24.914] (EE) 
Fatal server error:
[    24.915] (EE) Caught signal 11 (Segmentation fault). Server aborting
[    24.915] (EE) 
[    24.915] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    24.915] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    24.915] (EE)  [COLOR=#000000][    24.956] (EE) Server terminated with error (1). Closing log file.[/COLOR]
```

I would like to try to get this working if i can. I am only looking for the GUI to provide me with a way to become familiar to the system, not so much the graphics that it can offer me. My other two options are as follows, let me know if you have any suggestions:
[LIST=1]
[*]between my relatives and I, we have about 4 other computers lying around, pretty old. I could try to take a graphics card out of them and put it into this machine, no guarantee that it would work better than this one.
[*]Is there another, possibly better, very lightweight GUI that goes well with Ubuntu 14.04 that i could install instead. I am open to anything that you think would help me learn, but i would like to keep it as lightweight as possible as most of the time i would like to boot into command line only then go into the GUI when i am stuck.
[/LIST]
Thanks again for all your help.

---

### Post by steeldriver on 2015-02-05
Sorry to say it looks like an openchrome driver bug - in spite of what the supported hardware list says, the driver itself says

```

[    24.913] (EE) CHROME(0): **[COLOR=#ff0000]Unknown Card-Ids (3371[/COLOR]**|1019|1B47), Chipset: P4M900/VN896/CN896; **please report to openchrome-users@lists.freedesktop.org**

```

Changing to a lighter-weight GUI won't help if the basic driver layer is not operable. You *might *be able to force the system to use a generic VGA driver - I'm not a graphics hardware specialist, but yes scavenging a different graphics card sounds like a better way forward at this point.

---

### Post by aaron50 on 2015-02-05
> **steeldriver said:**
> 
Changing to a lighter-weight GUI won't help if the basic driver layer is not operable. You *might *be able to force the system to use a generic VGA driver - I'm not a graphics hardware specialist, but yes scavenging a different graphics card sounds like a better way forward at this point.

I will probably be able to scavenge one up this weekend. In the meantime i will try to force the system to use a generic VGA driver as you mentioned. I will try looking online for how to do this. I have no experience with graphics hardware, so if you know of anything else please let me know. In the meantime i will report back to this thread when i have a different graphics card installed.

---

### Post by steeldriver on 2015-02-05
Sorry I meant to say generic ***VESA*** driver.

If your system created a /etc/X11/xorg.conf.failsafe file, you could try forcing it to use that e.g.

```

sudo cp /etc/X11/xorg.conf{,_05FEB15}

sudo cp /etc/X11/xorg.conf{.failsafe,}

startx

```

---

### Post by aaron50 on 2015-02-05
> **steeldriver said:**
> 

```

sudo cp /etc/X11/xorg.conf{,_05FEB15}


```
after i tried this if said cannot start... : No such file or directory

i tried ls /etc/X11/ and the xorg.conf file is not listed

---

### Post by steeldriver on 2015-02-05
That first command was just to create a backup of the xorg.conf file if it existed (the error is likely "cannot stat" rather than "cannot start" - you can ignore it). The more important question is whether /etc/X11/xorg.conf*.failsafe* exists or not. It should contain something like

```

Section "Device"
    Identifier    "Configured Video Device"
    **Driver        "vesa"**
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

which might let you run at least in reduced-graphics mode (I'm clutching at straws here really).

---

### Post by aaron50 on 2015-02-05
sorry, yes it is cannot stat. I just typed that line since it was so short.

here is what i show when i double tap tab on this statement

```
ls /etc/X11/x
```

xinit/ xkb/ xsm

---

### Post by aaron50 on 2015-02-05
Do you think i should follow what is being said on this [post]("http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there") and create the xorg.conf file??

---

### Post by aaron50 on 2015-02-05
Steeldriver,

Your genius! I was able to get it to work!!! at least i think... What i did was create my own xorg.conf file because through further research Ubuntu 14.04 does not have a xorg.conf file. here were my steps:

```
sudo X -configure
sudo mv xorg.conf.new /etc/X11/xorg.conf
sudo vim /etc/X11/xorg.conf

```

In the text editor i just changed what was currently in the screen section driver to vesa, like you said. Rebooted the machine and boom, it booted right into a gui. Now i have a couple of questions...(you thought i was done)[IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG]

[LIST=1]
[*]is there a way that i can boot into the command line instead of the GUI? then start the GUI on command. I really don't want to be dependent on the GUI and booting into command line will force me to learn some things.
[*]The GIU's screen says LXDE on it, i know that somehow Lubuntu is like LXDE, but did i do everything right in my install? Is this the best lightweight GUI that you know of, or is there something more lightweight that i can use to learn from?
[/LIST]

---

### Post by steeldriver on 2015-02-05
Sounds like you've made good progress! 

It shouldn't boot right to the GUI if you just installed the packages described in the other thread (i.e. no display manager such as lightdm or gdm). If you ***have*** installed a display manager, then you can either:
[LIST=1]
[*]remove it
[*]override it e.g. for lightdm, create a 'lightdm.override' file in the /etc/init directory containing the single line ```
manual
```
[*]modify your grub configuration, adding the word [FONT=courier new]text[/FONT] to the boot options - you should be able to find step-by-step instructions here on ubuntuforums or elsewhere
[/LIST]

Lubuntu is really just a "themed" version of LXDE plus various desktop packages. You should have got the "theme" part if you installed the lubuntu-core package and configured your ~/.xsession file as described in the previous thread (i.e. with lxsession **-s Lubuntu **-e LXDE)

---

### Post by aaron50 on 2015-02-05
Thank you so much for all of your help. I went back to that other thread and was able to understand it a little more and got everything to work. I'm learning already! I appretiate all of your help.

---

### Post by steeldriver on 2015-02-05
Happy to help - have fun with the server

---

