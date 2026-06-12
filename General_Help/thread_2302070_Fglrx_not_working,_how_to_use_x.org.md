---
title: "Fglrx not working, how to use x.org ?"
date: 2015-11-07
forum: General Help
---

### Post by stefanoskikristijan on 2015-11-07
Hey i just installed kubuntu 14.04 and tried if i can configure the Fglrx driver but again without success as i tried many times on Ubuntu 15.04 and 14.04...  The first time i booitiated i tried to instal fglrx but again i cant initialise because i get **"No supported graphic card found" i **dont know why but i tried every single method and it doesnt work i always run into low graphic mode... So i can use X.ORG driver from Addition Drivers in kubuntu, but my question is how will i configure the card after that ? I dont see any changes after installing X.ORG driver, i think my Radeon isnt running but the situation is like before i use the Intel 4000.

---

### Post by Bashing-om on 2015-11-07
stefanoskikristijan; Hello;

We need to know what graphic's card(s) (GPU) we are working with.
Post back the outputs - Between Code Tags - of terminal commands:
```

lspci | grep "VGA\|3D"
sudo ubuntu-drivers devices
sudo ubuntu-drivers list
sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We see what tale gets told, and what can be done.

[INDENT][INDENT]it is what it is
[/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-07
> **Bashing-om said:**
> stefanoskikristijan; Hello;

We need to know what graphic's card(s) (GPU) we are working with.
Post back the outputs - Between Code Tags - of terminal commands:
```

lspci | grep "VGA\|3D"
sudo ubuntu-drivers devices
sudo ubuntu-drivers list
sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We see what tale gets told, and what can be done.
[INDENT][INDENT]it is what it is
[/INDENT]
[/INDENT]



First i have hybrid graphics Intel4000 + AMD Raden HD8500
Here are the outputs of the comands you asked for:
```

***~$ lspci | grep "VGA\|3D"***
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)

```

```

***sudo ubuntu-drivers devices***
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
model    : Sun PRO [Radeon HD 8500M Series]
modalias : pci:v00001002d00006663sv000017AAsd00003800bc03sc80i00
vendor   : Advanced Micro Devices, Inc. [AMD/ATI]
driver   : fglrx-updates - distro non-free
driver   : xserver-xorg-video-ati - distro free builtin recommended
driver   : fglrx - distro non-free

```

```

***sudo ubuntu-drivers list***
fglrx
fglrx-updates

```

```

***sudo lshw -C display***
 *-display               
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:27 memory:d8000000-d83fffff memory:c0000000-cfffffff ioport:4000(size=64)


```

---

### Post by Bashing-om on 2015-11-07
stefanoskikristijan; Welll ..

OK; switchable graphics can have it's issues .
What driver is presently installed ?

```

dpkg -l | grep fglrx

```

Maybe all we have to do is initialize the GPUs ?


[INDENT][INDENT]it is a thing
[/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-08
> **Bashing-om said:**
> stefanoskikristijan; Welll ..

OK; switchable graphics can have it's issues .
What driver is presently installed ?

```

dpkg -l | grep fglrx

```

Maybe all we have to do is initialize the GPUs ?

[INDENT][INDENT]it is a thing
[/INDENT]
[/INDENT]


Here is what i get when i enter that but i have to say that when i try to initialise it doesnt recognize the card "No supported graphic card detected" also there is no AMD Catalyst
```

dpkg -l | grep fglrx
rc  fglrx                                      2:15.200-0ubuntu0.5                     amd64        Video driver for the AMD graphics accelerators
rc  fglrx-core                                 2:15.200-0ubuntu0.5                     amd64        Minimal video driver for the AMD graphics accelerators

```

---

### Post by Bashing-om on 2015-11-08
stefanoskikristijan; Nope;

That last says we have no graphic's driver installed.

So, what will it take to install one ?

Got to make sure the old stuff is cleaned out, and groundwork laid for a new install .
```

dpkg -l  linux-headers-generic 
dkms status
ls -al /usr/share/ati/
ls -al /usr/X11R6/lib64/modules/dri

```

In this new driver install .. do you want to go with the open source driver - or for gaming - the FGLRX proprietary driver ?

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-08
> **Bashing-om said:**
> stefanoskikristijan; Nope;

That last says we have no graphic's driver installed.

So, what will it take to install one ?

Got to make sure the old stuff is cleaned out, and groundwork laid for a new install .
```

dpkg -l  linux-headers-generic 
dkms status
ls -al /usr/share/ati/
ls -al /usr/X11R6/lib64/modules/dri

```

In this new driver install .. do you want to go with the open source driver - or for gaming - the FGLRX proprietary driver ?
[INDENT][INDENT]we can do that
[/INDENT]
[/INDENT]


Yeah i want to go with the FGLRX because i also run games on my laptop, here is what i got with those last lines:
```

dpkg -l  linux-headers-generic
dpkg-query: no packages found matching linux-headers-generic

```
```

dkms status

ls -al /usr/share/ati/
ls: cannot access /usr/share/ati/: No such file or directory

```

```

ls -al /usr/X11R6/lib64/modules/dri
ls: cannot access /usr/X11R6/lib64/modules/dri: No such file or directory

```

---

### Post by Bashing-om on 2015-11-08
stefanoskikristijan; Hey, Hey ...

We are closer to knowing the why FGLRX has it's problems installing.

Let's install the ground work:
```

sudo apt-get install linux-headers-generic
sudo apt-get install dkms

```

And next is a bit of cleanup:
As you have not resorted to OEM this should be good enough:
```

sudo apt-get purge fglrx fglrx-amdcccle

```

And now install the driver from our repo:
```

sudo apt-get install fglrx-updates
sudo amdconfig --initial

```

Reboot the system to see the effect.

IF all appears now good, there is a bit of cleanup yet to be done. We do that finally.

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-08
> **Bashing-om said:**
> stefanoskikristijan; Hey, Hey ...

We are closer to knowing the why FGLRX has it's problems installing.

Let's install the ground work:
```

sudo apt-get install linux-headers-generic
sudo apt-get install dkms

```

And next is a bit of cleanup:
As you have not resorted to OEM this should be good enough:
```

sudo apt-get purge fglrx fglrx-amdcccle

```

And now install the driver from our repo:
```

sudo apt-get install fglrx-updates
sudo amdconfig --initial

```

Reboot the system to see the effect.

IF all appears now good, there is a bit of cleanup yet to be done. We do that finally.
[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]
[/INDENT]


Everything went without problem but when i try to initialise:
```

sudo amdconfig --initial
amdconfig: No supported adapters detected

```

Should i try to reboot ?

---

### Post by Bashing-om on 2015-11-08
stefanoskikristijan; Humm ...

maybe we best be looking at the log file, see what is going on.

1st however, is Catalyst Control Center installed ? It should have by default when installing the FGLRX driver:
```

dpkg -l fglrx-amdcccle

```
If it is not installed I can see why the initialization step fails.

[INDENT][INDENT]gotts be a reason
[/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-08
> **Bashing-om said:**
> stefanoskikristijan; Humm ...

maybe we best be looking at the log file, see what is going on.

1st however, is Catalyst Control Center installed ? It should have by default when installing the FGLRX driver:
```

dpkg -l fglrx-amdcccle

```
If it is not installed I can see why the initialization step fails.
[INDENT][INDENT]gotts be a reason
[/INDENT]
[/INDENT]


Here:
```

dpkg -l fglrx-amdcccle
Desired=Unknown/Install/Remove/Purge/Hold| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                    Version          Architecture     Description
+++-=======================-================-================-===================================================
un  fglrx-amdcccle          <none>           <none>           (no description available)



```

I remember in a month ago i used to initialise after i woke up the card using DRI_PRIME=1 glxgears or something like that and it initialised well but again i run in low graphic mode... :(

---

### Post by Bashing-om on 2015-11-08
stefanoskikristijan; Errhhmmm ..

I be guilty of not thinking things through .. we want - updates ! -
How about:
```

dpkg -l fglrx-amdcccle-updates

```

[INDENT][INDENT]to err is human
[INDENT][INDENT][INDENT]but I can really foul things up, sometimes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-08
> **Bashing-om said:**
> stefanoskikristijan; Errhhmmm ..

I be guilty of not thinking things through .. we want - updates ! -
How about:
```

dpkg -l fglrx-amdcccle-updates

```
[INDENT][INDENT]to err is human[INDENT][INDENT][INDENT]but I can really foul things up, sometimes
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


```
Desired=Unknown/Install/Remove/Purge/Hold| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                    Version          Architecture     Description
+++-=======================-================-================-===================================================
ii  fglrx-amdcccle-updates  2:15.200-0ubuntu amd64            Catalyst Control Center for the AMD graphics accele

```

Yeah, here you go.. :)

---

### Post by Bashing-om on 2015-11-08
stefanoskikristijan; Yeah !

So much for that thought .. we are good .

OK, when all else fails read the instructions:
```

cat /var/log/Xorg.0.log

```

let's see if we can see what is not going on here .

[INDENT][INDENT]look'n for the cause
[/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-08
> **Bashing-om said:**
> stefanoskikristijan; Yeah !

So much for that thought .. we are good .

OK, when all else fails read the instructions:
```

cat /var/log/Xorg.0.log

```

let's see if we can see what is not going on here .
[INDENT][INDENT]look'n for the cause
[/INDENT]
[/INDENT]


I really dont know what should i look for in the file so here i copy all from it:

```

[    18.440] 
X.Org X Server 1.17.1
Release Date: 2015-02-10
[    18.440] X Protocol Version 11, Revision 0
[    18.440] Build Operating System: Linux 3.19.0-28-generic x86_64 Ubuntu
[    18.440] Current Operating System: Linux Kristijan1999 3.19.0-32-generic #37~14.04.1-Ubuntu SMP Thu Oct 22 09:41:40 UTC 2015 x86_64
[    18.440] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-32-generic.efi.signed root=UUID=e55fcb5a-5900-4293-af60-6d6a5f503798 ro quiet splash vt.handoff=7
[    18.440] Build Date: 11 September 2015  10:33:14AM
[    18.440] xorg-server 2:1.17.1-0ubuntu3.1~trusty1 (For technical support please see http://www.ubuntu.com/support) 
[    18.440] Current version of pixman: 0.30.2
[    18.440] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    18.440] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.440] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov  8 14:17:30 2015
[    18.463] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.463] (==) No Layout section.  Using the first Screen section.
[    18.463] (==) No screen section available. Using defaults.
[    18.463] (**) |-->Screen "Default Screen Section" (0)
[    18.463] (**) |   |-->Monitor "<default monitor>"
[    18.464] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    18.464] (==) Automatically adding devices
[    18.464] (==) Automatically enabling devices
[    18.464] (==) Automatically adding GPU devices
[    18.464] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.464] 	Entry deleted from font path.
[    18.464] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.464] 	Entry deleted from font path.
[    18.464] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.464] 	Entry deleted from font path.
[    18.464] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.464] 	Entry deleted from font path.
[    18.464] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.464] 	Entry deleted from font path.
[    18.464] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    18.464] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.464] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.464] (II) Loader magic: 0x7fe1fcc60c60
[    18.464] (II) Module ABI versions:
[    18.464] 	X.Org ANSI C Emulation: 0.4
[    18.464] 	X.Org Video Driver: 19.0
[    18.464] 	X.Org XInput driver : 21.0
[    18.464] 	X.Org Server Extension : 9.0
[    18.464] (II) xfree86: Adding drm device (/dev/dri/card1)
[    18.464] (II) xfree86: Adding drm device (/dev/dri/card0)
[    18.466] (--) PCI:*(0:0:2:0) 8086:0166:17aa:3800 rev 9, Mem @ 0xd8000000/4194304, 0xc0000000/268435456, I/O @ 0x00004000/64
[    18.466] (--) PCI: (0:1:0:0) 1002:6663:17aa:3800 rev 0, Mem @ 0xd0000000/134217728, 0xd8600000/262144, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[    18.466] (II) LoadModule: "glx"
[    18.467] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.778] (II) Module glx: vendor="X.Org Foundation"
[    18.778] 	compiled for 1.17.1, module version = 1.0.0
[    18.778] 	ABI class: X.Org Server Extension, version 9.0
[    18.778] (==) AIGLX enabled
[    18.778] (==) Matched intel as autoconfigured driver 0
[    18.778] (==) Matched fglrx as autoconfigured driver 1
[    18.778] (==) Matched ati as autoconfigured driver 2
[    18.778] (==) Matched intel as autoconfigured driver 3
[    18.778] (==) Matched modesetting as autoconfigured driver 4
[    18.778] (==) Matched fbdev as autoconfigured driver 5
[    18.778] (==) Matched vesa as autoconfigured driver 6
[    18.778] (==) Assigned the driver to the xf86ConfigLayout
[    18.778] (II) LoadModule: "intel"
[    18.779] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    18.800] (II) Module intel: vendor="X.Org Foundation"
[    18.800] 	compiled for 1.17.1, module version = 2.99.917
[    18.800] 	Module class: X.Org Video Driver
[    18.800] 	ABI class: X.Org Video Driver, version 19.0
[    18.800] (II) LoadModule: "fglrx"
[    18.801] (WW) Warning, couldn't open module fglrx
[    18.801] (II) UnloadModule: "fglrx"
[    18.801] (II) Unloading fglrx
[    18.801] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    18.801] (II) LoadModule: "ati"
[    18.801] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    18.801] (II) Module ati: vendor="X.Org Foundation"
[    18.801] 	compiled for 1.17.1, module version = 7.5.0
[    18.801] 	Module class: X.Org Video Driver
[    18.801] 	ABI class: X.Org Video Driver, version 19.0
[    18.801] (II) LoadModule: "radeon"
[    18.801] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    18.802] (II) Module radeon: vendor="X.Org Foundation"
[    18.802] 	compiled for 1.17.1, module version = 7.5.0
[    18.802] 	Module class: X.Org Video Driver
[    18.802] 	ABI class: X.Org Video Driver, version 19.0
[    18.802] (II) LoadModule: "modesetting"
[    18.802] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    18.802] (II) Module modesetting: vendor="X.Org Foundation"
[    18.802] 	compiled for 1.17.1, module version = 1.17.1
[    18.802] 	Module class: X.Org Video Driver
[    18.802] 	ABI class: X.Org Video Driver, version 19.0
[    18.802] (II) LoadModule: "fbdev"
[    18.802] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.802] (II) Module fbdev: vendor="X.Org Foundation"
[    18.802] 	compiled for 1.17.1, module version = 0.4.4
[    18.802] 	Module class: X.Org Video Driver
[    18.802] 	ABI class: X.Org Video Driver, version 19.0
[    18.802] (II) LoadModule: "vesa"
[    18.802] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.802] (II) Module vesa: vendor="X.Org Foundation"
[    18.802] 	compiled for 1.17.1, module version = 2.3.3
[    18.802] 	Module class: X.Org Video Driver
[    18.802] 	ABI class: X.Org Video Driver, version 19.0
[    18.802] (==) Matched intel as autoconfigured driver 0
[    18.802] (==) Matched fglrx as autoconfigured driver 1
[    18.802] (==) Matched ati as autoconfigured driver 2
[    18.802] (==) Matched intel as autoconfigured driver 3
[    18.802] (==) Matched modesetting as autoconfigured driver 4
[    18.802] (==) Matched fbdev as autoconfigured driver 5
[    18.802] (==) Matched vesa as autoconfigured driver 6
[    18.802] (==) Assigned the driver to the xf86ConfigLayout
[    18.802] (II) LoadModule: "intel"
[    18.802] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    18.802] (II) Module intel: vendor="X.Org Foundation"
[    18.802] 	compiled for 1.17.1, module version = 2.99.917
[    18.802] 	Module class: X.Org Video Driver
[    18.802] 	ABI class: X.Org Video Driver, version 19.0
[    18.802] (II) UnloadModule: "intel"
[    18.802] (II) Unloading intel
[    18.802] (II) Failed to load module "intel" (already loaded, 32737)
[    18.802] (II) LoadModule: "fglrx"
[    18.803] (WW) Warning, couldn't open module fglrx
[    18.803] (II) UnloadModule: "fglrx"
[    18.803] (II) Unloading fglrx
[    18.803] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    18.803] (II) LoadModule: "ati"
[    18.803] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    18.803] (II) Module ati: vendor="X.Org Foundation"
[    18.803] 	compiled for 1.17.1, module version = 7.5.0
[    18.803] 	Module class: X.Org Video Driver
[    18.803] 	ABI class: X.Org Video Driver, version 19.0
[    18.803] (II) LoadModule: "modesetting"
[    18.803] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    18.803] (II) Module modesetting: vendor="X.Org Foundation"
[    18.803] 	compiled for 1.17.1, module version = 1.17.1
[    18.803] 	Module class: X.Org Video Driver
[    18.803] 	ABI class: X.Org Video Driver, version 19.0
[    18.803] (II) UnloadModule: "modesetting"
[    18.803] (II) Unloading modesetting
[    18.803] (II) Failed to load module "modesetting" (already loaded, 0)
[    18.803] (II) LoadModule: "fbdev"
[    18.803] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.803] (II) Module fbdev: vendor="X.Org Foundation"
[    18.803] 	compiled for 1.17.1, module version = 0.4.4
[    18.803] 	Module class: X.Org Video Driver
[    18.803] 	ABI class: X.Org Video Driver, version 19.0
[    18.803] (II) UnloadModule: "fbdev"
[    18.803] (II) Unloading fbdev
[    18.803] (II) Failed to load module "fbdev" (already loaded, 0)
[    18.803] (II) LoadModule: "vesa"
[    18.803] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.803] (II) Module vesa: vendor="X.Org Foundation"
[    18.803] 	compiled for 1.17.1, module version = 2.3.3
[    18.803] 	Module class: X.Org Video Driver
[    18.803] 	ABI class: X.Org Video Driver, version 19.0
[    18.803] (II) UnloadModule: "vesa"
[    18.803] (II) Unloading vesa
[    18.803] (II) Failed to load module "vesa" (already loaded, 0)
[    18.803] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    18.803] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    18.803] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    18.803] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    18.803] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
	ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
	ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
	OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
	HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE,
	BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
	BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
	MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
	MULLINS, MULLINS, MULLINS, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
	HAWAII, HAWAII, HAWAII, HAWAII, HAWAII
[    18.808] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    18.808] (II) FBDEV: driver for framebuffer: fbdev
[    18.808] (II) VESA: driver for VESA chipsets: vesa
[    18.808] (++) using VT number 7


[    18.808] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20141121
[    18.808] (II) intel(0): SNA compiled: xserver-xorg-video-intel-lts-vivid 2:2.99.917-1~exp1ubuntu2.2~trusty1 (Timo Aaltonen <tjaalton@debian.org>)
[    18.808] (II) intel(0): SNA compiled for use with valgrind
[    18.808] (II) [KMS] Kernel modesetting enabled.
[    18.808] (WW) Falling back to old probe method for modesetting
[    18.808] (WW) Falling back to old probe method for fbdev
[    18.808] (II) Loading sub module "fbdevhw"
[    18.808] (II) LoadModule: "fbdevhw"
[    18.809] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    18.809] (II) Module fbdevhw: vendor="X.Org Foundation"
[    18.809] 	compiled for 1.17.1, module version = 0.0.2
[    18.809] 	ABI class: X.Org Video Driver, version 19.0
[    18.809] (WW) Falling back to old probe method for vesa
[    18.809] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4000
[    18.809] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[    18.809] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    18.809] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    18.809] (==) intel(0): RGB weight 888
[    18.809] (==) intel(0): Default visual is TrueColor
[    18.809] (II) intel(0): Output LVDS1 has no monitor section
[    18.809] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output LVDS1
[    18.809] (II) intel(0): Enabled output LVDS1
[    18.809] (II) intel(0): Output VGA1 has no monitor section
[    18.809] (II) intel(0): Enabled output VGA1
[    18.809] (II) intel(0): Output HDMI1 has no monitor section
[    18.809] (II) intel(0): Enabled output HDMI1
[    18.809] (II) intel(0): Output DP1 has no monitor section
[    18.809] (II) intel(0): Enabled output DP1
[    18.809] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    18.809] (II) intel(0): Output VIRTUAL1 has no monitor section
[    18.809] (II) intel(0): Enabled output VIRTUAL1
[    18.809] (--) intel(0): Output LVDS1 using initial mode 1366x768 on pipe 0
[    18.809] (==) intel(0): TearFree disabled
[    18.809] (==) intel(0): DPI set to (96, 96)
[    18.809] (II) Loading sub module "dri2"
[    18.809] (II) LoadModule: "dri2"
[    18.809] (II) Module "dri2" already built-in
[    18.809] (II) Loading sub module "present"
[    18.810] (II) LoadModule: "present"
[    18.810] (II) Module "present" already built-in
[    18.810] (==) RADEON(G0): Depth 24, (--) framebuffer bpp 32
[    18.810] (II) RADEON(G0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    18.810] (==) RADEON(G0): Default visual is TrueColor
[    18.810] (==) RADEON(G0): RGB weight 888
[    18.810] (II) RADEON(G0): Using 8 bits per RGB (8 bit DAC)
[    18.810] (--) RADEON(G0): Chipset: "HAINAN" (ChipID = 0x6663)
[    18.810] (II) Loading sub module "dri2"
[    18.810] (II) LoadModule: "dri2"
[    18.810] (II) Module "dri2" already built-in
[    18.810] (II) Loading sub module "glamoregl"
[    18.810] (II) LoadModule: "glamoregl"
[    18.810] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    18.835] (II) Module glamoregl: vendor="X.Org Foundation"
[    18.835] 	compiled for 1.17.1, module version = 1.0.0
[    18.835] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.835] (II) glamor: OpenGL accelerated X.org driver based.
[    18.938] (II) glamor: EGL version 1.4 (DRI2):
[    18.940] (II) RADEON(G0): glamor detected, initialising EGL layer.
[    18.940] (II) RADEON(G0): KMS Color Tiling: enabled
[    18.940] (II) RADEON(G0): KMS Color Tiling 2D: enabled
[    18.940] (II) RADEON(G0): KMS Pageflipping: enabled
[    18.940] (II) RADEON(G0): SwapBuffers wait for vsync: enabled
[    18.940] (II) RADEON(G0): mem size init: gart size :3fbcf000 vram size: s:80000000 visible:7fabe000
[    18.940] (==) RADEON(G0): DPI set to (96, 96)
[    18.940] (II) Loading sub module "fb"
[    18.940] (II) LoadModule: "fb"
[    18.940] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.940] (II) Module fb: vendor="X.Org Foundation"
[    18.940] 	compiled for 1.17.1, module version = 1.0.0
[    18.940] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.940] (==) RADEON(G0): Using gamma correction (1.0, 1.0, 1.0)
[    18.940] (II) Loading sub module "ramdac"
[    18.940] (II) LoadModule: "ramdac"
[    18.940] (II) Module "ramdac" already built-in
[    18.940] (II) UnloadModule: "modesetting"
[    18.940] (II) Unloading modesetting
[    18.940] (II) UnloadModule: "fbdev"
[    18.940] (II) Unloading fbdev
[    18.940] (II) UnloadSubModule: "fbdevhw"
[    18.940] (II) Unloading fbdevhw
[    18.940] (II) UnloadModule: "vesa"
[    18.940] (II) Unloading vesa
[    18.940] (==) Depth 24 pixmap format is 32 bpp
[    18.940] (II) RADEON(G0): [DRI2] Setup complete
[    18.940] (II) RADEON(G0): [DRI2]   DRI driver: radeonsi
[    18.940] (II) RADEON(G0): [DRI2]   VDPAU driver: radeonsi
[    18.940] (II) RADEON(G0): Front buffer size: 3072K
[    18.940] (II) RADEON(G0): VRAM usage limit set to 1879826K
[    18.940] (==) RADEON(G0): Backing store enabled
[    18.940] (II) RADEON(G0): Direct rendering enabled
[    19.001] (II) RADEON(G0): Use GLAMOR acceleration.
[    19.001] (II) RADEON(G0): Acceleration enabled
[    19.001] (==) RADEON(G0): DPMS enabled
[    19.001] (==) RADEON(G0): Silken mouse enabled
[    19.001] (II) RADEON(G0): Set up textured video (glamor)
[    19.001] (II) RADEON(G0): [XvMC] Associated with GLAMOR Textured Video.
[    19.001] (EE) RADEON(G0): [XvMC] Failed to initialize extension.
[    19.001] (II) RADEON(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    19.001] (II) intel(0): SNA initialized with Ivybridge (gen7, gt2) backend
[    19.001] (==) intel(0): Backing store enabled
[    19.001] (==) intel(0): Silken mouse enabled
[    19.001] (II) intel(0): HW Cursor enabled
[    19.001] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    19.002] (==) intel(0): DPMS enabled
[    19.002] (==) intel(0): display hotplug detection enabled
[    19.002] (II) intel(0): [DRI2] Setup complete
[    19.002] (II) intel(0): [DRI2]   DRI driver: i965
[    19.002] (II) intel(0): [DRI2]   VDPAU driver: i965
[    19.002] (II) intel(0): direct rendering: DRI2 enabled
[    19.002] (II) intel(0): hardware support for Present enabled
[    19.002] (--) RandR disabled
[    19.029] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    19.029] (II) AIGLX: enabled GLX_ARB_create_context
[    19.029] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    19.029] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    19.029] (II) AIGLX: enabled GLX_INTEL_swap_event
[    19.029] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    19.029] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    19.029] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    19.029] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    19.029] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    19.029] (II) AIGLX: Loaded and initialized i965
[    19.029] (II) GLX: Initialized DRI2 GL provider for screen 0
[    19.042] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    19.057] (II) intel(0): Setting screen physical size to 361 x 203
[    19.064] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.066] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    19.066] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.066] (II) LoadModule: "evdev"
[    19.066] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.080] (II) Module evdev: vendor="X.Org Foundation"
[    19.081] 	compiled for 1.17.1, module version = 2.9.0
[    19.081] 	Module class: X.Org XInput Driver
[    19.081] 	ABI class: X.Org XInput driver, version 21.0
[    19.081] (II) Using input driver 'evdev' for 'Power Button'
[    19.081] (**) Power Button: always reports core events
[    19.081] (**) evdev: Power Button: Device: "/dev/input/event2"
[    19.081] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.081] (--) evdev: Power Button: Found keys
[    19.081] (II) evdev: Power Button: Configuring as keyboard
[    19.081] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    19.081] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    19.081] (**) Option "xkb_rules" "evdev"
[    19.081] (**) Option "xkb_model" "pc105"
[    19.081] (**) Option "xkb_layout" "gb"
[    19.083] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    19.084] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    19.084] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    19.084] (II) Using input driver 'evdev' for 'Video Bus'
[    19.084] (**) Video Bus: always reports core events
[    19.084] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    19.084] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    19.084] (--) evdev: Video Bus: Found keys
[    19.084] (II) evdev: Video Bus: Configuring as keyboard
[    19.084] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:03/input/input8/event5"
[    19.084] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    19.084] (**) Option "xkb_rules" "evdev"
[    19.084] (**) Option "xkb_model" "pc105"
[    19.084] (**) Option "xkb_layout" "gb"
[    19.084] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    19.084] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.084] (II) Using input driver 'evdev' for 'Power Button'
[    19.084] (**) Power Button: always reports core events
[    19.084] (**) evdev: Power Button: Device: "/dev/input/event0"
[    19.084] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.084] (--) evdev: Power Button: Found keys
[    19.084] (II) evdev: Power Button: Configuring as keyboard
[    19.084] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0/event0"
[    19.084] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    19.084] (**) Option "xkb_rules" "evdev"
[    19.084] (**) Option "xkb_model" "pc105"
[    19.084] (**) Option "xkb_layout" "gb"
[    19.085] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    19.085] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    19.085] (II) Using input driver 'evdev' for 'Video Bus'
[    19.085] (**) Video Bus: always reports core events
[    19.085] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    19.085] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    19.085] (--) evdev: Video Bus: Found keys
[    19.085] (II) evdev: Video Bus: Configuring as keyboard
[    19.085] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:35/LNXVIDEO:00/input/input7/event4"
[    19.085] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 9)
[    19.085] (**) Option "xkb_rules" "evdev"
[    19.085] (**) Option "xkb_model" "pc105"
[    19.085] (**) Option "xkb_layout" "gb"
[    19.085] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    19.085] (II) No input driver specified, ignoring this device.
[    19.085] (II) This device may have been added with another device file.
[    19.086] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/event6)
[    19.086] (**) A4TECH USB Device: Applying InputClass "evdev keyboard catchall"
[    19.086] (II) Using input driver 'evdev' for 'A4TECH USB Device'
[    19.086] (**) A4TECH USB Device: always reports core events
[    19.086] (**) evdev: A4TECH USB Device: Device: "/dev/input/event6"
[    19.086] (--) evdev: A4TECH USB Device: Vendor 0x9da Product 0x9090
[    19.086] (--) evdev: A4TECH USB Device: Found 1 mouse buttons
[    19.086] (--) evdev: A4TECH USB Device: Found scroll wheel(s)
[    19.086] (--) evdev: A4TECH USB Device: Found relative axes
[    19.086] (--) evdev: A4TECH USB Device: Found absolute axes
[    19.086] (--) evdev: A4TECH USB Device: Found absolute multitouch axes
[    19.086] (--) evdev: A4TECH USB Device: Found x and y absolute axes
[    19.086] (--) evdev: A4TECH USB Device: Found keys
[    19.086] (II) evdev: A4TECH USB Device: Forcing relative x/y axes to exist.
[    19.086] (II) evdev: A4TECH USB Device: Configuring as mouse
[    19.086] (II) evdev: A4TECH USB Device: Configuring as keyboard
[    19.086] (II) evdev: A4TECH USB Device: Adding scrollwheel support
[    19.086] (**) evdev: A4TECH USB Device: YAxisMapping: buttons 4 and 5
[    19.086] (**) evdev: A4TECH USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.086] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/0003:09DA:9090.0001/input/input9/event6"
[    19.086] (II) XINPUT: Adding extended input device "A4TECH USB Device" (type: KEYBOARD, id 10)
[    19.086] (**) Option "xkb_rules" "evdev"
[    19.086] (**) Option "xkb_model" "pc105"
[    19.086] (**) Option "xkb_layout" "gb"
[    19.086] (II) evdev: A4TECH USB Device: initialized for relative axes.
[    19.086] (WW) evdev: A4TECH USB Device: ignoring absolute axes.
[    19.087] (**) A4TECH USB Device: (accel) keeping acceleration scheme 1
[    19.087] (**) A4TECH USB Device: (accel) acceleration profile 0
[    19.087] (**) A4TECH USB Device: (accel) acceleration factor: 2.000
[    19.087] (**) A4TECH USB Device: (accel) acceleration threshold: 4
[    19.087] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/js0)
[    19.087] (II) No input driver specified, ignoring this device.
[    19.087] (II) This device may have been added with another device file.
[    19.087] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/event7)
[    19.087] (**) A4TECH USB Device: Applying InputClass "evdev pointer catchall"
[    19.087] (II) Using input driver 'evdev' for 'A4TECH USB Device'
[    19.087] (**) A4TECH USB Device: always reports core events
[    19.087] (**) evdev: A4TECH USB Device: Device: "/dev/input/event7"
[    19.140] (--) evdev: A4TECH USB Device: Vendor 0x9da Product 0x9090
[    19.140] (--) evdev: A4TECH USB Device: Found 20 mouse buttons
[    19.140] (--) evdev: A4TECH USB Device: Found scroll wheel(s)
[    19.140] (--) evdev: A4TECH USB Device: Found relative axes
[    19.140] (--) evdev: A4TECH USB Device: Found x and y relative axes
[    19.140] (II) evdev: A4TECH USB Device: Configuring as mouse
[    19.140] (II) evdev: A4TECH USB Device: Adding scrollwheel support
[    19.140] (**) evdev: A4TECH USB Device: YAxisMapping: buttons 4 and 5
[    19.140] (**) evdev: A4TECH USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.140] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.1/0003:09DA:9090.0002/input/input10/event7"
[    19.140] (II) XINPUT: Adding extended input device "A4TECH USB Device" (type: MOUSE, id 11)
[    19.140] (II) evdev: A4TECH USB Device: initialized for relative axes.
[    19.140] (**) A4TECH USB Device: (accel) keeping acceleration scheme 1
[    19.140] (**) A4TECH USB Device: (accel) acceleration profile 0
[    19.140] (**) A4TECH USB Device: (accel) acceleration factor: 2.000
[    19.140] (**) A4TECH USB Device: (accel) acceleration threshold: 4
[    19.141] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/mouse0)
[    19.141] (II) No input driver specified, ignoring this device.
[    19.141] (II) This device may have been added with another device file.
[    19.141] (II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event13)
[    19.141] (**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
[    19.141] (II) Using input driver 'evdev' for 'Lenovo EasyCamera'
[    19.141] (**) Lenovo EasyCamera: always reports core events
[    19.141] (**) evdev: Lenovo EasyCamera: Device: "/dev/input/event13"
[    19.141] (--) evdev: Lenovo EasyCamera: Vendor 0xbda Product 0x5728
[    19.141] (--) evdev: Lenovo EasyCamera: Found keys
[    19.141] (II) evdev: Lenovo EasyCamera: Configuring as keyboard
[    19.141] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/input/input15/event13"
[    19.141] (II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 12)
[    19.141] (**) Option "xkb_rules" "evdev"
[    19.141] (**) Option "xkb_model" "pc105"
[    19.141] (**) Option "xkb_layout" "gb"
[    19.141] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    19.141] (II) No input driver specified, ignoring this device.
[    19.141] (II) This device may have been added with another device file.
[    19.142] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    19.142] (II) No input driver specified, ignoring this device.
[    19.142] (II) This device may have been added with another device file.
[    19.142] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[    19.142] (II) No input driver specified, ignoring this device.
[    19.142] (II) This device may have been added with another device file.
[    19.142] (II) config/udev: Adding input device Ideapad extra buttons (/dev/input/event9)
[    19.142] (**) Ideapad extra buttons: Applying InputClass "evdev keyboard catchall"
[    19.142] (II) Using input driver 'evdev' for 'Ideapad extra buttons'
[    19.142] (**) Ideapad extra buttons: always reports core events
[    19.142] (**) evdev: Ideapad extra buttons: Device: "/dev/input/event9"
[    19.142] (--) evdev: Ideapad extra buttons: Vendor 0 Product 0
[    19.142] (--) evdev: Ideapad extra buttons: Found keys
[    19.142] (II) evdev: Ideapad extra buttons: Configuring as keyboard
[    19.142] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1f.0/PNP0C09:00/VPC2004:00/input/input11/event9"
[    19.142] (II) XINPUT: Adding extended input device "Ideapad extra buttons" (type: KEYBOARD, id 13)
[    19.142] (**) Option "xkb_rules" "evdev"
[    19.142] (**) Option "xkb_model" "pc105"
[    19.142] (**) Option "xkb_layout" "gb"
[    19.143] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    19.143] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    19.143] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    19.143] (**) AT Translated Set 2 keyboard: always reports core events
[    19.143] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    19.143] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    19.143] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    19.143] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    19.143] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    19.143] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 14)
[    19.143] (**) Option "xkb_rules" "evdev"
[    19.143] (**) Option "xkb_model" "pc105"
[    19.143] (**) Option "xkb_layout" "gb"
[    19.143] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event8)
[    19.143] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    19.143] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    19.143] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    19.143] (II) LoadModule: "synaptics"
[    19.143] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    19.143] (II) Module synaptics: vendor="X.Org Foundation"
[    19.143] 	compiled for 1.17.1, module version = 1.8.99
[    19.143] 	Module class: X.Org XInput Driver
[    19.143] 	ABI class: X.Org XInput driver, version 21.0
[    19.143] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    19.143] (**) ETPS/2 Elantech Touchpad: always reports core events
[    19.143] (**) Option "Device" "/dev/input/event8"
[    19.156] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2940 (res 0)
[    19.156] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1260 (res 0)
[    19.156] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    19.156] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    19.156] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    19.156] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    19.156] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    19.156] (**) ETPS/2 Elantech Touchpad: always reports core events
[    19.168] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event8"
[    19.168] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 15)
[    19.168] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    19.168] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    19.168] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.063
[    19.168] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    19.168] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    19.168] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    19.168] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    19.168] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    19.169] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    19.169] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    49.369] reporting 4 5 1 8
[    53.256] (II) intel(0): EDID vendor "LGD", prod id 826
[    53.256] (II) intel(0): Printing DDC gathered Modelines:
[    53.256] (II) intel(0): Modeline "1366x768"x0.0   70.00  1366 1402 1450 1492  768 771 776 782 -hsync -vsync (46.9 kHz eP)
[    53.259] reporting 4 5 7 53
[    53.361] reporting 4 5 7 53
[    53.361] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.643] reporting 4 5 7 53
[    53.643] reporting 4 5 7 53
[    53.643] reporting 4 5 7 53
[    53.643] reporting 4 5 7 53
[    53.643] reporting 4 5 7 53
[    53.643] reporting 4 5 7 53
[    53.643] reporting 4 5 7 53
[    54.213] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AA2FC318445DE966DF48706BBC15B7668547E20.xkm
[    55.502] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.995] reporting 4 5 7 53
[    56.040] reporting 4 5 7 53
[    56.040] reporting 4 5 7 53
[    56.041] reporting 4 5 7 53
[    56.041] reporting 4 5 7 53
[    56.041] reporting 4 5 7 53
[    56.041] reporting 4 5 7 53
[    56.041] reporting 4 5 7 53
[    56.054] reporting 4 5 7 53
[    56.054] reporting 4 5 7 53
[    56.054] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.085] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.088] reporting 4 5 7 53
[    56.107] reporting 4 5 7 53
[    56.107] reporting 4 5 7 53
[   114.208] reporting 4 5 7 53
[   128.100] reporting 4 5 7 53
[   339.790] reporting 4 5 7 53
[   530.263] reporting 4 5 7 53
[   530.263] reporting 4 5 7 53
[   530.263] reporting 4 5 7 53
[   530.575] reporting 4 5 7 53
[   530.673] reporting 4 5 7 53
[   531.861] reporting 4 5 7 53
[   596.488] reporting 4 5 7 53
[   596.533] reporting 4 5 7 53
[   596.584] reporting 4 5 7 53
[   596.615] reporting 4 5 7 53
[   596.624] reporting 4 5 7 53
[   596.656] reporting 4 5 7 53
[   597.360] reporting 4 5 7 53
[   600.105] reporting 4 5 7 53
[   600.913] reporting 4 5 7 53
[   600.933] reporting 4 5 7 53
[   600.933] (II) intel(0): switch to mode 640x480@59.9 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   601.686] reporting 4 5 7 53
[   601.689] reporting 4 5 7 53
[   601.726] reporting 4 5 7 53
[   601.726] reporting 4 5 7 53
[   601.726] reporting 4 5 7 53
[   602.026] reporting 4 5 7 53
[   602.026] reporting 4 5 7 53
[   602.026] reporting 4 5 7 53
[   602.026] reporting 4 5 7 53
[   602.027] reporting 4 5 7 53
[   602.027] reporting 4 5 7 53
[   602.027] reporting 4 5 7 53
[   602.027] reporting 4 5 7 53
[   602.027] reporting 4 5 7 53
[   602.028] reporting 4 5 7 53
[   602.028] reporting 4 5 7 53
[   602.028] reporting 4 5 7 53
[   602.028] reporting 4 5 7 53
[   602.028] reporting 4 5 7 53
[   609.124] reporting 4 5 7 53
[   609.124] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   609.885] reporting 4 5 7 53
[   609.889] reporting 4 5 7 53
[   609.947] reporting 4 5 7 53
[   609.947] reporting 4 5 7 53
[   609.947] reporting 4 5 7 53
[   610.247] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.249] reporting 4 5 7 53
[   610.249] reporting 4 5 7 53
[   610.249] reporting 4 5 7 53
[   610.355] reporting 4 5 7 53
[   610.387] reporting 4 5 7 53
[   610.387] (II) intel(0): switch to mode 1024x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   611.189] reporting 4 5 7 53
[   611.194] reporting 4 5 7 53
[   611.228] reporting 4 5 7 53
[   611.228] reporting 4 5 7 53
[   611.229] reporting 4 5 7 53
[   611.529] reporting 4 5 7 53
[   611.529] reporting 4 5 7 53
[   611.529] reporting 4 5 7 53
[   611.529] reporting 4 5 7 53
[   611.529] reporting 4 5 7 53
[   611.530] reporting 4 5 7 53
[   611.530] reporting 4 5 7 53
[   611.530] reporting 4 5 7 53
[   611.530] reporting 4 5 7 53
[   611.530] reporting 4 5 7 53
[   611.530] reporting 4 5 7 53
[   611.530] reporting 4 5 7 53
[   611.530] reporting 4 5 7 53
[   611.530] reporting 4 5 7 53
[   653.793] reporting 4 5 7 53
[   653.793] (II) intel(0): switch to mode 640x480@59.9 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   654.546] reporting 4 5 7 53
[   654.549] reporting 4 5 7 53
[   654.587] reporting 4 5 7 53
[   654.587] reporting 4 5 7 53
[   654.587] reporting 4 5 7 53
[   654.887] reporting 4 5 7 53
[   654.888] reporting 4 5 7 53
[   654.888] reporting 4 5 7 53
[   654.888] reporting 4 5 7 53
[   654.888] reporting 4 5 7 53
[   654.888] reporting 4 5 7 53
[   654.888] reporting 4 5 7 53
[   654.889] reporting 4 5 7 53
[   654.889] reporting 4 5 7 53
[   654.889] reporting 4 5 7 53
[   654.889] reporting 4 5 7 53
[   654.889] reporting 4 5 7 53
[   654.889] reporting 4 5 7 53
[   654.890] reporting 4 5 7 53
[   663.532] reporting 4 5 7 53
[   663.532] (II) intel(0): switch to mode 1024x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   664.357] reporting 4 5 7 53
[   664.362] reporting 4 5 7 53
[   664.395] reporting 4 5 7 53
[   664.399] reporting 4 5 7 53
[   664.400] reporting 4 5 7 53
[   664.700] reporting 4 5 7 53
[   664.700] reporting 4 5 7 53
[   664.701] reporting 4 5 7 53
[   664.701] reporting 4 5 7 53
[   664.701] reporting 4 5 7 53
[   664.701] reporting 4 5 7 53
[   664.701] reporting 4 5 7 53
[   664.702] reporting 4 5 7 53
[   664.702] reporting 4 5 7 53
[   664.702] reporting 4 5 7 53
[   664.702] reporting 4 5 7 53
[   664.702] reporting 4 5 7 53
[   664.703] reporting 4 5 7 53
[   664.703] reporting 4 5 7 53
[   665.862] reporting 4 5 7 53
[   665.862] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   666.657] reporting 4 5 7 53
[   666.660] reporting 4 5 7 53
[   666.697] reporting 4 5 7 53
[   666.697] reporting 4 5 7 53
[   666.697] reporting 4 5 7 53
[   666.998] reporting 4 5 7 53
[   666.998] reporting 4 5 7 53
[   666.998] reporting 4 5 7 53
[   666.998] reporting 4 5 7 53
[   666.998] reporting 4 5 7 53
[   666.998] reporting 4 5 7 53
[   666.998] reporting 4 5 7 53
[   666.999] reporting 4 5 7 53
[   666.999] reporting 4 5 7 53
[   666.999] reporting 4 5 7 53
[   666.999] reporting 4 5 7 53
[   666.999] reporting 4 5 7 53
[   666.999] reporting 4 5 7 53
[   666.999] reporting 4 5 7 53
[  1747.830] reporting 4 5 7 53
[  1822.830] reporting 4 5 7 53
[  1897.829] reporting 4 5 7 53
[  2594.471] reporting 4 5 7 53
[  6680.609] reporting 4 5 7 53
[  6687.046] reporting 4 5 7 53
[  6846.392] reporting 4 5 7 53
[  7187.062] reporting 4 5 7 53
[  7231.844] reporting 4 5 7 53
[  7283.000] reporting 4 5 7 53
[  7306.398] reporting 4 5 7 53
[  7434.616] reporting 4 5 7 53
[  7637.434] reporting 4 5 7 53
[  7665.531] reporting 4 5 7 53
[  7810.771] reporting 4 5 7 53
[  8000.544] reporting 4 5 7 53
[  8000.548] reporting 4 5 7 53
[  8040.983] reporting 4 5 7 53
[  8040.984] reporting 4 5 7 53
[  8225.499] reporting 4 5 7 53
[  8827.271] reporting 4 5 7 53
[  8899.741] reporting 4 5 7 53
[  9146.910] reporting 4 5 7 53
[  9150.502] reporting 4 5 7 53
[  9374.923] reporting 4 5 7 53
[  9419.409] reporting 4 5 7 53
[  9586.987] reporting 4 5 7 53
[  9791.290] reporting 4 5 7 53
[  9952.420] reporting 4 5 7 53
[ 10189.686] reporting 4 5 7 53
[ 10191.814] reporting 4 5 7 53
[ 11003.526] reporting 4 5 7 53
[ 11013.383] reporting 4 5 7 53
[ 11029.386] reporting 4 5 7 53
[ 11112.675] reporting 4 5 7 53
[ 11223.046] reporting 4 5 7 53
[ 11230.545] reporting 4 5 7 53
[ 11646.462] reporting 4 5 7 53
[ 11948.050] reporting 4 5 7 53
[ 11950.287] reporting 4 5 7 53
[ 12100.385] reporting 4 5 7 53
[ 12175.384] reporting 4 5 7 53
[ 12220.970] reporting 4 5 7 53
[ 12251.827] reporting 4 5 7 53
[ 12772.535] reporting 4 5 7 53
[ 12791.910] reporting 4 5 7 53
[ 12791.910] reporting 4 5 7 53
[ 12791.910] reporting 4 5 7 53
[ 12792.521] reporting 4 5 7 53
[ 12792.728] reporting 4 5 7 53
[ 12794.422] reporting 4 5 7 53
[ 12795.098] reporting 4 5 7 53
[ 12795.675] reporting 4 5 7 53
[ 12969.346] reporting 4 5 7 53
[ 12973.860] reporting 4 5 7 53
[ 13123.905] reporting 4 5 7 53
[ 13125.597] reporting 4 5 7 53
[ 13184.975] reporting 4 5 7 53
[ 13184.985] reporting 4 5 7 53
[ 13184.985] reporting 4 5 7 53
[ 13184.985] reporting 4 5 7 53
[ 13184.985] reporting 4 5 7 53
[ 13184.985] reporting 4 5 7 53
[ 13184.985] reporting 4 5 7 53
[ 13184.986] reporting 4 5 7 53
[ 13185.651] reporting 4 5 7 53
[ 13185.699] reporting 4 5 7 53
[ 13187.087] reporting 4 5 7 53
[ 13203.661] reporting 4 5 7 53
[ 13203.854] reporting 4 5 7 53
[ 13216.494] reporting 4 5 7 53
[ 13282.153] reporting 4 5 7 53
[ 13282.188] reporting 4 5 7 53
[ 13282.230] reporting 4 5 7 53
[ 13282.275] reporting 4 5 7 53
[ 13282.317] reporting 4 5 7 53
[ 13282.324] reporting 4 5 7 53
[ 13282.880] reporting 4 5 7 53
[ 13285.920] reporting 4 5 7 53
[ 13289.444] reporting 4 5 7 53
[ 13289.465] (II) intel(0): switch to mode 1024x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 13290.312] reporting 4 5 7 53
[ 13290.316] reporting 4 5 7 53
[ 13290.487] reporting 4 5 7 53
[ 13290.531] reporting 4 5 7 53
[ 13290.531] reporting 4 5 7 53
[ 13290.900] reporting 4 5 7 53
[ 13290.900] reporting 4 5 7 53
[ 13290.901] reporting 4 5 7 53
[ 13290.901] reporting 4 5 7 53
[ 13290.901] reporting 4 5 7 53
[ 13290.901] reporting 4 5 7 53
[ 13290.901] reporting 4 5 7 53
[ 13290.901] reporting 4 5 7 53
[ 13290.902] reporting 4 5 7 53
[ 13290.902] reporting 4 5 7 53
[ 13290.902] reporting 4 5 7 53
[ 13290.902] reporting 4 5 7 53
[ 13290.902] reporting 4 5 7 53
[ 13290.902] reporting 4 5 7 53
[ 13291.422] reporting 4 5 7 53
[ 13291.422] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 13292.189] reporting 4 5 7 53
[ 13292.192] reporting 4 5 7 53
[ 13292.204] reporting 4 5 7 53
[ 13292.210] (II) intel(0): switch to mode 1024x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 13292.703] reporting 4 5 7 53
[ 13292.706] reporting 4 5 7 53
[ 13292.711] reporting 4 5 7 53
[ 13292.712] reporting 4 5 7 53
[ 13292.712] reporting 4 5 7 53
[ 13292.733] reporting 4 5 7 53
[ 13292.733] reporting 4 5 7 53
[ 13292.734] reporting 4 5 7 53
[ 13346.513] reporting 4 5 7 53
[ 13346.513] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 13347.324] reporting 4 5 7 53
[ 13347.327] reporting 4 5 7 53
[ 13347.343] reporting 4 5 7 53
[ 13347.365] reporting 4 5 7 53
[ 13347.369] reporting 4 5 7 53
[ 13347.371] reporting 4 5 7 53
[ 13347.673] reporting 4 5 7 53
[ 13347.673] reporting 4 5 7 53
[ 13347.674] reporting 4 5 7 53
[ 13347.674] reporting 4 5 7 53
[ 13347.674] reporting 4 5 7 53
[ 13347.674] reporting 4 5 7 53
[ 13347.674] reporting 4 5 7 53
[ 13347.674] reporting 4 5 7 53
[ 13347.674] reporting 4 5 7 53
[ 13347.674] reporting 4 5 7 53
[ 13347.675] reporting 4 5 7 53
[ 13347.675] reporting 4 5 7 53
[ 13347.675] reporting 4 5 7 53
[ 13347.675] reporting 4 5 7 53
[ 13484.116] reporting 4 5 7 53
[ 13556.224] reporting 4 5 7 53
[ 13556.227] reporting 4 5 7 53
[ 13577.276] reporting 4 5 7 53
[ 13603.746] reporting 4 5 7 53
[ 13603.747] reporting 4 5 7 53
[ 13603.778] reporting 4 5 7 53
[ 13603.832] reporting 4 5 7 53
[ 13603.837] reporting 4 5 7 53
[ 13604.170] reporting 4 5 7 53
[ 13604.329] reporting 4 5 7 53
[ 13604.401] reporting 4 5 7 53
[ 13605.687] reporting 4 5 7 53
[ 13608.687] reporting 4 5 7 53
[ 13613.203] reporting 4 5 7 53
[ 13676.896] reporting 4 5 7 53
[ 13676.934] reporting 4 5 7 53
[ 13676.976] reporting 4 5 7 53
[ 13677.010] reporting 4 5 7 53
[ 13677.016] reporting 4 5 7 53
[ 13677.078] reporting 4 5 7 53
[ 13677.112] reporting 4 5 7 53
[ 13678.722] reporting 4 5 7 53
[ 13678.788] reporting 4 5 7 53
[ 13678.852] reporting 4 5 7 53
[ 13678.909] reporting 4 5 7 53
[ 13678.974] reporting 4 5 7 53
[ 13679.040] reporting 4 5 7 53
[ 13679.105] reporting 4 5 7 53
[ 13679.170] reporting 4 5 7 53
[ 13679.235] reporting 4 5 7 53
[ 13679.299] reporting 4 5 7 53
[ 13679.427] reporting 4 5 7 53
[ 13685.464] reporting 4 5 7 53
[ 13685.506] reporting 4 5 7 53
[ 13685.549] reporting 4 5 7 53
[ 13685.583] reporting 4 5 7 53
[ 13685.592] reporting 4 5 7 53
[ 13685.627] reporting 4 5 7 53
[ 13686.481] reporting 4 5 7 53
[ 13690.356] reporting 4 5 7 53
[ 13721.839] reporting 4 5 7 53
[ 13721.879] reporting 4 5 7 53
[ 13721.916] reporting 4 5 7 53
[ 13721.955] reporting 4 5 7 53
[ 13721.961] reporting 4 5 7 53
[ 13722.008] reporting 4 5 7 53
[ 13722.445] reporting 4 5 7 53
[ 13835.986] reporting 4 5 7 53
[ 13836.063] reporting 4 5 7 53
[ 13836.127] reporting 4 5 7 53
[ 13836.606] reporting 4 5 7 53
[ 13838.412] reporting 4 5 7 53
[ 13841.111] reporting 4 5 7 53
[ 13867.817] reporting 4 5 7 53
[ 13867.859] reporting 4 5 7 53
[ 13867.893] reporting 4 5 7 53
[ 13867.932] reporting 4 5 7 53
[ 13867.940] reporting 4 5 7 53
[ 13867.973] reporting 4 5 7 53
[ 13868.116] reporting 4 5 7 53
[ 13871.006] reporting 4 5 7 53
[ 13873.967] reporting 4 5 7 53
[ 13879.173] reporting 4 5 7 53
[ 13884.131] reporting 4 5 7 53
[ 13884.155] reporting 4 5 7 53
[ 13885.993] reporting 4 5 7 53
[ 13948.355] reporting 4 5 7 53
[ 13948.399] reporting 4 5 7 53
[ 13948.440] reporting 4 5 7 53
[ 13948.478] reporting 4 5 7 53
[ 13948.493] reporting 4 5 7 53
[ 13948.529] reporting 4 5 7 53
[ 13948.608] reporting 4 5 7 53
[ 13956.483] reporting 4 5 7 53
[ 13963.834] reporting 4 5 7 53
[ 13963.874] reporting 4 5 7 53
[ 13963.919] reporting 4 5 7 53
[ 13963.961] reporting 4 5 7 53
[ 13963.970] reporting 4 5 7 53
[ 13964.018] reporting 4 5 7 53
[ 13964.098] reporting 4 5 7 53
[ 13964.373] reporting 4 5 7 53
[ 13989.412] reporting 4 5 7 53
[ 13989.450] reporting 4 5 7 53
[ 13989.492] reporting 4 5 7 53
[ 13989.534] reporting 4 5 7 53
[ 13989.543] reporting 4 5 7 53
[ 13989.575] reporting 4 5 7 53
[ 13989.653] reporting 4 5 7 53
[ 13989.782] reporting 4 5 7 53
[ 13990.983] reporting 4 5 7 53
[ 13992.301] reporting 4 5 7 53
[ 14165.962] reporting 4 5 7 53
[ 14166.062] reporting 4 5 7 53
[ 14166.227] reporting 4 5 7 53
[ 14166.691] reporting 4 5 7 53
[ 14166.866] reporting 4 5 7 53
[ 14167.152] reporting 4 5 7 53
[ 14168.225] reporting 4 5 7 53
[ 14169.221] reporting 4 5 7 53
[ 14200.775] reporting 4 5 7 53
[ 14206.887] reporting 4 5 7 53
[ 14206.929] reporting 4 5 7 53
[ 14206.971] reporting 4 5 7 53
[ 14207.011] reporting 4 5 7 53
[ 14207.020] reporting 4 5 7 53
[ 14207.058] reporting 4 5 7 53
[ 14207.151] reporting 4 5 7 53
[ 14212.154] reporting 4 5 7 53
[ 14214.001] reporting 4 5 7 53
[ 14214.002] (II) intel(0): switch to mode 1024x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 14214.817] reporting 4 5 7 53
[ 14214.822] reporting 4 5 7 53
[ 14214.847] reporting 4 5 7 53
[ 14214.847] reporting 4 5 7 53
[ 14214.847] reporting 4 5 7 53
[ 14215.148] reporting 4 5 7 53
[ 14215.148] reporting 4 5 7 53
[ 14215.148] reporting 4 5 7 53
[ 14215.148] reporting 4 5 7 53
[ 14215.148] reporting 4 5 7 53
[ 14215.148] reporting 4 5 7 53
[ 14215.148] reporting 4 5 7 53
[ 14215.149] reporting 4 5 7 53
[ 14215.150] reporting 4 5 7 53
[ 14215.150] reporting 4 5 7 53
[ 14215.151] reporting 4 5 7 53
[ 14215.151] reporting 4 5 7 53
[ 14215.151] reporting 4 5 7 53
[ 14215.151] reporting 4 5 7 53
[ 14215.653] reporting 4 5 7 53
[ 14215.653] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 14216.413] reporting 4 5 7 53
[ 14216.419] reporting 4 5 7 53
[ 14216.433] reporting 4 5 7 53
[ 14216.436] (II) intel(0): switch to mode 1024x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 14216.934] reporting 4 5 7 53
[ 14216.935] reporting 4 5 7 53
[ 14216.935] reporting 4 5 7 53
[ 14216.935] reporting 4 5 7 53
[ 14216.941] reporting 4 5 7 53
[ 14216.957] reporting 4 5 7 53
[ 14216.958] reporting 4 5 7 53
[ 14216.958] reporting 4 5 7 53
[ 14265.946] reporting 4 5 7 53
[ 14265.946] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 14266.677] reporting 4 5 7 53
[ 14266.680] reporting 4 5 7 53
[ 14266.704] reporting 4 5 7 53
[ 14266.705] reporting 4 5 7 53
[ 14266.705] reporting 4 5 7 53
[ 14267.005] reporting 4 5 7 53
[ 14267.005] reporting 4 5 7 53
[ 14267.006] reporting 4 5 7 53
[ 14267.006] reporting 4 5 7 53
[ 14267.006] reporting 4 5 7 53
[ 14267.006] reporting 4 5 7 53
[ 14267.006] reporting 4 5 7 53
[ 14267.006] reporting 4 5 7 53
[ 14267.007] reporting 4 5 7 53
[ 14267.007] reporting 4 5 7 53
[ 14267.007] reporting 4 5 7 53
[ 14267.007] reporting 4 5 7 53
[ 14267.007] reporting 4 5 7 53
[ 14267.007] reporting 4 5 7 53
[ 14312.616] reporting 4 5 7 53
[ 14485.712] reporting 4 5 7 53
[ 14485.747] reporting 4 5 7 53
[ 14485.786] reporting 4 5 7 53
[ 14485.825] reporting 4 5 7 53
[ 14485.834] reporting 4 5 7 53
[ 14485.871] reporting 4 5 7 53
[ 14485.971] reporting 4 5 7 53
[ 14513.434] reporting 4 5 7 53
[ 14513.474] reporting 4 5 7 53
[ 14513.515] reporting 4 5 7 53
[ 14513.549] reporting 4 5 7 53
[ 14513.558] reporting 4 5 7 53
[ 14513.593] reporting 4 5 7 53
[ 14513.692] reporting 4 5 7 53
[ 14514.930] reporting 4 5 7 53
[ 14516.261] reporting 4 5 7 53
[ 14517.219] reporting 4 5 7 53
[ 14532.335] reporting 4 5 7 53
[ 14532.384] reporting 4 5 7 53
[ 14532.425] reporting 4 5 7 53
[ 14532.463] reporting 4 5 7 53
[ 14532.470] reporting 4 5 7 53
[ 14532.504] reporting 4 5 7 53
[ 14532.606] reporting 4 5 7 53
[ 14545.355] reporting 4 5 7 53
[ 14545.444] reporting 4 5 7 53
[ 14545.519] reporting 4 5 7 53
[ 14545.528] reporting 4 5 7 53
[ 14546.701] reporting 4 5 7 53
[ 14548.013] reporting 4 5 7 53
[ 14625.430] reporting 4 5 7 53
[ 14625.432] reporting 4 5 7 53
[ 14693.139] reporting 4 5 7 53
[ 14693.141] reporting 4 5 7 53
[ 14745.982] reporting 4 5 7 53
[ 14745.990] reporting 4 5 7 53
[ 14913.312] reporting 4 5 7 53
[ 14920.759] reporting 4 5 7 53
[ 14966.756] reporting 4 5 7 53
[ 14966.798] reporting 4 5 7 53
[ 14966.834] reporting 4 5 7 53
[ 14966.876] reporting 4 5 7 53
[ 14966.883] reporting 4 5 7 53
[ 14966.925] reporting 4 5 7 53
[ 14967.021] reporting 4 5 7 53
[ 14967.103] reporting 4 5 7 53
[ 14967.671] reporting 4 5 7 53
[ 14969.949] reporting 4 5 7 53
[ 14974.786] reporting 4 5 7 53
[ 15060.194] reporting 4 5 7 53
[ 15061.845] reporting 4 5 7 53
[ 15063.570] reporting 4 5 7 53
[ 15063.608] reporting 4 5 7 53
[ 15063.654] reporting 4 5 7 53
[ 15063.688] reporting 4 5 7 53
[ 15063.696] reporting 4 5 7 53
[ 15063.731] reporting 4 5 7 53
[ 15063.943] reporting 4 5 7 53
[ 15073.725] reporting 4 5 7 53
[ 15076.016] reporting 4 5 7 53
[ 15076.087] reporting 4 5 7 53
[ 15076.093] reporting 4 5 7 53
[ 15076.173] reporting 4 5 7 53
[ 15081.753] reporting 4 5 7 53
[ 15081.811] reporting 4 5 7 53
[ 15081.873] reporting 4 5 7 53
[ 15081.930] reporting 4 5 7 53
[ 15082.151] reporting 4 5 7 53
[ 15085.219] reporting 4 5 7 53
[ 15091.827] reporting 4 5 7 53
[ 15091.870] reporting 4 5 7 53
[ 15091.909] reporting 4 5 7 53
[ 15091.945] reporting 4 5 7 53
[ 15091.954] reporting 4 5 7 53
[ 15091.990] reporting 4 5 7 53
[ 15092.161] reporting 4 5 7 53
[ 15109.702] reporting 4 5 7 53
[ 15112.569] reporting 4 5 7 53
[ 15118.400] reporting 4 5 7 53
[ 15129.943] reporting 4 5 7 53
[ 15138.541] reporting 4 5 7 53
[ 15144.629] reporting 4 5 7 53
[ 15144.669] reporting 4 5 7 53
[ 15144.710] reporting 4 5 7 53
[ 15144.748] reporting 4 5 7 53
[ 15144.758] reporting 4 5 7 53
[ 15144.800] reporting 4 5 7 53
[ 15144.885] reporting 4 5 7 53
[ 15144.965] reporting 4 5 7 53
[ 15145.541] reporting 4 5 7 53
[ 15147.949] reporting 4 5 7 53
[ 15149.875] reporting 4 5 7 53
[ 15221.300] reporting 4 5 7 53
[ 15226.145] reporting 4 5 7 53
[ 15227.443] reporting 4 5 7 53
[ 15233.257] reporting 4 5 7 53
[ 15233.302] reporting 4 5 7 53
[ 15233.345] reporting 4 5 7 53
[ 15233.387] reporting 4 5 7 53
[ 15233.397] reporting 4 5 7 53
[ 15233.431] reporting 4 5 7 53
[ 15233.514] reporting 4 5 7 53
[ 15233.595] reporting 4 5 7 53
[ 15234.146] reporting 4 5 7 53
[ 15236.198] reporting 4 5 7 53
[ 15238.508] reporting 4 5 7 53
[ 15282.083] reporting 4 5 7 53
[ 15382.584] reporting 4 5 7 53
[ 15435.345] reporting 4 5 7 53
[ 15435.345] reporting 4 5 7 53
[ 15438.195] reporting 4 5 7 53
[ 15438.196] reporting 4 5 7 53
[ 15572.328] reporting 4 5 7 53
[ 15572.369] reporting 4 5 7 53
[ 15572.394] reporting 4 5 7 53
[ 15572.415] reporting 4 5 7 53
[ 15572.482] reporting 4 5 7 53
[ 15572.488] reporting 4 5 7 53
[ 15573.325] reporting 4 5 7 53
[ 15574.292] reporting 4 5 7 53
[ 15589.418] reporting 4 5 7 53
[ 15589.418] reporting 4 5 7 53
[ 15664.418] reporting 4 5 7 53
[ 15664.418] reporting 4 5 7 53
[ 15739.418] reporting 4 5 7 53
[ 15739.418] reporting 4 5 7 53
[ 16833.415] reporting 4 5 7 53
[ 16833.415] reporting 4 5 7 53
[ 16845.076] reporting 4 5 7 53
[ 16845.116] reporting 4 5 7 53
[ 16845.156] reporting 4 5 7 53
[ 16845.206] reporting 4 5 7 53
[ 16845.216] reporting 4 5 7 53
[ 16845.251] reporting 4 5 7 53
[ 16845.333] reporting 4 5 7 53
[ 16845.420] reporting 4 5 7 53
[ 16846.007] reporting 4 5 7 53
[ 16879.083] reporting 4 5 7 53
[ 16881.714] reporting 4 5 7 53
[ 16936.394] reporting 4 5 7 53
[ 16939.098] reporting 4 5 7 53
[ 16960.893] reporting 4 5 7 53
[ 16960.932] reporting 4 5 7 53
[ 16960.975] reporting 4 5 7 53
[ 16961.022] reporting 4 5 7 53
[ 16961.032] reporting 4 5 7 53
[ 16961.090] reporting 4 5 7 53
[ 16961.207] reporting 4 5 7 53
[ 16962.437] reporting 4 5 7 53
[ 16963.746] reporting 4 5 7 53
[ 17004.700] reporting 4 5 7 53
[ 17013.652] reporting 4 5 7 53
[ 17091.811] reporting 4 5 7 53
[ 17155.875] reporting 4 5 7 53
[ 17231.828] reporting 4 5 7 53
[ 17476.425] (II) config/udev: removing device A4TECH USB Device
[ 17476.437] (II) evdev: A4TECH USB Device: Close
[ 17476.780] (II) UnloadModule: "evdev"
[ 17476.782] (II) config/udev: removing device A4TECH USB Device
[ 17476.784] (II) evdev: A4TECH USB Device: Close
[ 17476.784] (II) UnloadModule: "evdev"
[ 17507.425] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/js0)
[ 17507.475] (II) No input driver specified, ignoring this device.
[ 17507.475] (II) This device may have been added with another device file.
[ 17507.475] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/mouse0)
[ 17507.475] (II) No input driver specified, ignoring this device.
[ 17507.475] (II) This device may have been added with another device file.
[ 17507.476] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/event7)
[ 17507.476] (**) A4TECH USB Device: Applying InputClass "evdev pointer catchall"
[ 17507.476] (II) Using input driver 'evdev' for 'A4TECH USB Device'
[ 17507.476] (**) A4TECH USB Device: always reports core events
[ 17507.476] (**) evdev: A4TECH USB Device: Device: "/dev/input/event7"
[ 17507.552] (--) evdev: A4TECH USB Device: Vendor 0x9da Product 0x9090
[ 17507.552] (--) evdev: A4TECH USB Device: Found 20 mouse buttons
[ 17507.552] (--) evdev: A4TECH USB Device: Found scroll wheel(s)
[ 17507.552] (--) evdev: A4TECH USB Device: Found relative axes
[ 17507.552] (--) evdev: A4TECH USB Device: Found x and y relative axes
[ 17507.552] (II) evdev: A4TECH USB Device: Configuring as mouse
[ 17507.552] (II) evdev: A4TECH USB Device: Adding scrollwheel support
[ 17507.552] (**) evdev: A4TECH USB Device: YAxisMapping: buttons 4 and 5
[ 17507.552] (**) evdev: A4TECH USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 17507.552] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.1/0003:09DA:9090.0004/input/input17/event7"
[ 17507.552] (II) XINPUT: Adding extended input device "A4TECH USB Device" (type: MOUSE, id 10)
[ 17507.553] (II) evdev: A4TECH USB Device: initialized for relative axes.
[ 17507.553] (**) A4TECH USB Device: (accel) keeping acceleration scheme 1
[ 17507.553] (**) A4TECH USB Device: (accel) acceleration profile 0
[ 17507.553] (**) A4TECH USB Device: (accel) acceleration factor: 2.000
[ 17507.553] (**) A4TECH USB Device: (accel) acceleration threshold: 4
[ 17507.554] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/event6)
[ 17507.554] (**) A4TECH USB Device: Applying InputClass "evdev keyboard catchall"
[ 17507.554] (II) Using input driver 'evdev' for 'A4TECH USB Device'
[ 17507.554] (**) A4TECH USB Device: always reports core events
[ 17507.554] (**) evdev: A4TECH USB Device: Device: "/dev/input/event6"
[ 17507.554] (--) evdev: A4TECH USB Device: Vendor 0x9da Product 0x9090
[ 17507.554] (--) evdev: A4TECH USB Device: Found 1 mouse buttons
[ 17507.554] (--) evdev: A4TECH USB Device: Found scroll wheel(s)
[ 17507.554] (--) evdev: A4TECH USB Device: Found relative axes
[ 17507.554] (--) evdev: A4TECH USB Device: Found absolute axes
[ 17507.554] (--) evdev: A4TECH USB Device: Found absolute multitouch axes
[ 17507.554] (--) evdev: A4TECH USB Device: Found x and y absolute axes
[ 17507.554] (--) evdev: A4TECH USB Device: Found keys
[ 17507.554] (II) evdev: A4TECH USB Device: Forcing relative x/y axes to exist.
[ 17507.554] (II) evdev: A4TECH USB Device: Configuring as mouse
[ 17507.554] (II) evdev: A4TECH USB Device: Configuring as keyboard
[ 17507.554] (II) evdev: A4TECH USB Device: Adding scrollwheel support
[ 17507.554] (**) evdev: A4TECH USB Device: YAxisMapping: buttons 4 and 5
[ 17507.554] (**) evdev: A4TECH USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 17507.554] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/0003:09DA:9090.0003/input/input16/event6"
[ 17507.555] (II) XINPUT: Adding extended input device "A4TECH USB Device" (type: KEYBOARD, id 11)
[ 17507.555] (**) Option "xkb_rules" "evdev"
[ 17507.555] (**) Option "xkb_model" "pc105"
[ 17507.555] (**) Option "xkb_layout" "gb"
[ 17507.580] (II) evdev: A4TECH USB Device: initialized for relative axes.
[ 17507.580] (WW) evdev: A4TECH USB Device: ignoring absolute axes.
[ 17507.580] (**) A4TECH USB Device: (accel) keeping acceleration scheme 1
[ 17507.580] (**) A4TECH USB Device: (accel) acceleration profile 0
[ 17507.580] (**) A4TECH USB Device: (accel) acceleration factor: 2.000
[ 17507.581] (**) A4TECH USB Device: (accel) acceleration threshold: 4
[ 17507.736] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AA2FC318445DE966DF48706BBC15B7668547E20.xkm
[ 17507.949] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AA2FC318445DE966DF48706BBC15B7668547E20.xkm
[ 17510.021] (II) config/udev: removing device A4TECH USB Device
[ 17510.040] (II) evdev: A4TECH USB Device: Close
[ 17510.040] (II) UnloadModule: "evdev"
[ 17510.057] (II) config/udev: removing device A4TECH USB Device
[ 17510.076] (II) evdev: A4TECH USB Device: Close
[ 17510.076] (II) UnloadModule: "evdev"
[ 17510.094] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[ 17510.116] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AA2FC318445DE966DF48706BBC15B7668547E20.xkm
[ 17517.065] reporting 4 5 7 53
[ 17519.157] reporting 4 5 7 53
[ 17519.528] reporting 4 5 7 53
[ 17519.722] reporting 4 5 7 53
[ 17519.905] reporting 4 5 7 53
[ 17520.098] reporting 4 5 7 53
[ 17520.282] reporting 4 5 7 53
[ 17580.187] reporting 4 5 7 53
[ 17610.186] reporting 4 5 7 53
[ 17638.088] reporting 4 5 7 53
[ 17685.020] reporting 4 5 7 53
[ 17807.258] reporting 4 5 7 53
[ 17807.577] reporting 4 5 7 53
[ 18264.517] reporting 4 5 7 53
[ 18265.979] reporting 4 5 7 53
[ 18417.199] reporting 4 5 7 53
[ 18418.526] reporting 4 5 7 53
[ 18437.739] reporting 4 5 7 53
[ 18437.739] reporting 4 5 7 53
[ 18437.739] reporting 4 5 7 53
[ 18437.740] reporting 4 5 7 53
[ 18437.740] reporting 4 5 7 53
[ 18437.740] reporting 4 5 7 53
[ 18437.741] reporting 4 5 7 53
[ 18437.741] reporting 4 5 7 53
[ 18437.741] reporting 4 5 7 53
[ 18437.741] reporting 4 5 7 53
[ 18437.741] reporting 4 5 7 53
[ 18437.741] reporting 4 5 7 53
[ 18437.741] reporting 4 5 7 53
[ 18437.742] reporting 4 5 7 53
[ 18437.742] reporting 4 5 7 53
[ 18437.742] reporting 4 5 7 53
[ 18437.742] reporting 4 5 7 53
[ 18437.743] reporting 4 5 7 53
[ 18437.743] reporting 4 5 7 53
[ 18437.743] reporting 4 5 7 53
[ 18437.784] reporting 4 5 7 53
[ 18437.784] reporting 4 5 7 53
[ 18437.785] reporting 4 5 7 53
[ 18437.785] reporting 4 5 7 53
[ 18437.785] reporting 4 5 7 53
[ 18437.785] reporting 4 5 7 53
[ 18437.785] reporting 4 5 7 53
[ 18614.161] reporting 4 5 7 53
[ 18615.646] reporting 4 5 7 53
[ 18626.326] reporting 4 5 7 53
[ 18626.327] reporting 4 5 7 53
[ 18626.327] reporting 4 5 7 53
[ 18626.327] reporting 4 5 7 53
[ 18626.328] reporting 4 5 7 53
[ 18626.328] reporting 4 5 7 53
[ 18626.328] reporting 4 5 7 53
[ 18626.329] reporting 4 5 7 53
[ 18626.329] reporting 4 5 7 53
[ 18626.329] reporting 4 5 7 53
[ 18626.329] reporting 4 5 7 53
[ 18626.329] reporting 4 5 7 53
[ 18626.329] reporting 4 5 7 53
[ 18626.330] reporting 4 5 7 53
[ 18626.330] reporting 4 5 7 53
[ 18626.331] reporting 4 5 7 53
[ 18626.331] reporting 4 5 7 53
[ 18626.331] reporting 4 5 7 53
[ 18626.331] reporting 4 5 7 53
[ 18626.331] reporting 4 5 7 53
[ 18626.356] reporting 4 5 7 53
[ 18626.356] reporting 4 5 7 53
[ 18626.356] reporting 4 5 7 53
[ 18626.356] reporting 4 5 7 53
[ 18626.356] reporting 4 5 7 53
[ 18626.356] reporting 4 5 7 53
[ 18626.356] reporting 4 5 7 53
[ 26718.859] reporting 4 5 7 53
[ 26806.537] reporting 4 5 7 53
[ 27196.217] reporting 4 5 7 53
[ 27196.354] reporting 4 5 7 53
[ 29714.554] reporting 4 5 7 53
[ 29842.226] reporting 4 5 7 53
[    18.440] 
X.Org X Server 1.17.1
Release Date: 2015-02-10
[    18.440] X Protocol Version 11, Revision 0
[    18.440] Build Operating System: Linux 3.19.0-28-generic x86_64 Ubuntu
[    18.440] Current Operating System: Linux Kristijan1999 3.19.0-32-generic #37~14.04.1-Ubuntu SMP Thu Oct 22 09:41:40 UTC 2015 x86_64
[    18.440] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-32-generic.efi.signed root=UUID=e55fcb5a-5900-4293-af60-6d6a5f503798 ro quiet splash vt.handoff=7
[    18.440] Build Date: 11 September 2015  10:33:14AM
[    18.440] xorg-server 2:1.17.1-0ubuntu3.1~trusty1 (For technical support please see http://www.ubuntu.com/support) 
[    18.440] Current version of pixman: 0.30.2
[    18.440] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    18.440] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.440] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov  8 14:17:30 2015
[    18.463] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.463] (==) No Layout section.  Using the first Screen section.
[    18.463] (==) No screen section available. Using defaults.
[    18.463] (**) |-->Screen "Default Screen Section" (0)
[    18.463] (**) |   |-->Monitor "<default monitor>"
[    18.464] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    18.464] (==) Automatically adding devices
[    18.464] (==) Automatically enabling devices
[    18.464] (==) Automatically adding GPU devices
[    18.464] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.464] 	Entry deleted from font path.
[    18.464] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.464] 	Entry deleted from font path.
[    18.464] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.464] 	Entry deleted from font path.
[    18.464] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.464] 	Entry deleted from font path.
[    18.464] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.464] 	Entry deleted from font path.
[    18.464] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    18.464] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.464] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.464] (II) Loader magic: 0x7fe1fcc60c60
[    18.464] (II) Module ABI versions:
[    18.464] 	X.Org ANSI C Emulation: 0.4
[    18.464] 	X.Org Video Driver: 19.0
[    18.464] 	X.Org XInput driver : 21.0
[    18.464] 	X.Org Server Extension : 9.0
[    18.464] (II) xfree86: Adding drm device (/dev/dri/card1)
[    18.464] (II) xfree86: Adding drm device (/dev/dri/card0)
[    18.466] (--) PCI:*(0:0:2:0) 8086:0166:17aa:3800 rev 9, Mem @ 0xd8000000/4194304, 0xc0000000/268435456, I/O @ 0x00004000/64
[    18.466] (--) PCI: (0:1:0:0) 1002:6663:17aa:3800 rev 0, Mem @ 0xd0000000/134217728, 0xd8600000/262144, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[    18.466] (II) LoadModule: "glx"
[    18.467] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.778] (II) Module glx: vendor="X.Org Foundation"
[    18.778] 	compiled for 1.17.1, module version = 1.0.0
[    18.778] 	ABI class: X.Org Server Extension, version 9.0
[    18.778] (==) AIGLX enabled
[    18.778] (==) Matched intel as autoconfigured driver 0
[    18.778] (==) Matched fglrx as autoconfigured driver 1
[    18.778] (==) Matched ati as autoconfigured driver 2
[    18.778] (==) Matched intel as autoconfigured driver 3
[    18.778] (==) Matched modesetting as autoconfigured driver 4
[    18.778] (==) Matched fbdev as autoconfigured driver 5
[    18.778] (==) Matched vesa as autoconfigured driver 6
[    18.778] (==) Assigned the driver to the xf86ConfigLayout
[    18.778] (II) LoadModule: "intel"
[    18.779] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    18.800] (II) Module intel: vendor="X.Org Foundation"
[    18.800] 	compiled for 1.17.1, module version = 2.99.917
[    18.800] 	Module class: X.Org Video Driver
[    18.800] 	ABI class: X.Org Video Driver, version 19.0
[    18.800] (II) LoadModule: "fglrx"
[    18.801] (WW) Warning, couldn't open module fglrx
[    18.801] (II) UnloadModule: "fglrx"
[    18.801] (II) Unloading fglrx
[    18.801] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    18.801] (II) LoadModule: "ati"
[    18.801] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    18.801] (II) Module ati: vendor="X.Org Foundation"
[    18.801] 	compiled for 1.17.1, module version = 7.5.0
[    18.801] 	Module class: X.Org Video Driver
[    18.801] 	ABI class: X.Org Video Driver, version 19.0
[    18.801] (II) LoadModule: "radeon"
[    18.801] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    18.802] (II) Module radeon: vendor="X.Org Foundation"
[    18.802] 	compiled for 1.17.1, module version = 7.5.0
[    18.802] 	Module class: X.Org Video Driver
[    18.802] 	ABI class: X.Org Video Driver, version 19.0
[    18.802] (II) LoadModule: "modesetting"
[    18.802] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    18.802] (II) Module modesetting: vendor="X.Org Foundation"
[    18.802] 	compiled for 1.17.1, module version = 1.17.1
[    18.802] 	Module class: X.Org Video Driver
[    18.802] 	ABI class: X.Org Video Driver, version 19.0
[    18.802] (II) LoadModule: "fbdev"
[    18.802] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.802] (II) Module fbdev: vendor="X.Org Foundation"
[    18.802] 	compiled for 1.17.1, module version = 0.4.4
[    18.802] 	Module class: X.Org Video Driver
[    18.802] 	ABI class: X.Org Video Driver, version 19.0
[    18.802] (II) LoadModule: "vesa"
[    18.802] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.802] (II) Module vesa: vendor="X.Org Foundation"
[    18.802] 	compiled for 1.17.1, module version = 2.3.3
[    18.802] 	Module class: X.Org Video Driver
[    18.802] 	ABI class: X.Org Video Driver, version 19.0
[    18.802] (==) Matched intel as autoconfigured driver 0
[    18.802] (==) Matched fglrx as autoconfigured driver 1
[    18.802] (==) Matched ati as autoconfigured driver 2
[    18.802] (==) Matched intel as autoconfigured driver 3
[    18.802] (==) Matched modesetting as autoconfigured driver 4
[    18.802] (==) Matched fbdev as autoconfigured driver 5
[    18.802] (==) Matched vesa as autoconfigured driver 6
[    18.802] (==) Assigned the driver to the xf86ConfigLayout
[    18.802] (II) LoadModule: "intel"
[    18.802] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    18.802] (II) Module intel: vendor="X.Org Foundation"
[    18.802] 	compiled for 1.17.1, module version = 2.99.917
[    18.802] 	Module class: X.Org Video Driver
[    18.802] 	ABI class: X.Org Video Driver, version 19.0
[    18.802] (II) UnloadModule: "intel"
[    18.802] (II) Unloading intel
[    18.802] (II) Failed to load module "intel" (already loaded, 32737)
[    18.802] (II) LoadModule: "fglrx"
[    18.803] (WW) Warning, couldn't open module fglrx
[    18.803] (II) UnloadModule: "fglrx"
[    18.803] (II) Unloading fglrx
[    18.803] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    18.803] (II) LoadModule: "ati"
[    18.803] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    18.803] (II) Module ati: vendor="X.Org Foundation"
[    18.803] 	compiled for 1.17.1, module version = 7.5.0
[    18.803] 	Module class: X.Org Video Driver
[    18.803] 	ABI class: X.Org Video Driver, version 19.0
[    18.803] (II) LoadModule: "modesetting"
[    18.803] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    18.803] (II) Module modesetting: vendor="X.Org Foundation"
[    18.803] 	compiled for 1.17.1, module version = 1.17.1
[    18.803] 	Module class: X.Org Video Driver
[    18.803] 	ABI class: X.Org Video Driver, version 19.0
[    18.803] (II) UnloadModule: "modesetting"
[    18.803] (II) Unloading modesetting
[    18.803] (II) Failed to load module "modesetting" (already loaded, 0)
[    18.803] (II) LoadModule: "fbdev"
[    18.803] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.803] (II) Module fbdev: vendor="X.Org Foundation"
[    18.803] 	compiled for 1.17.1, module version = 0.4.4
[    18.803] 	Module class: X.Org Video Driver
[    18.803] 	ABI class: X.Org Video Driver, version 19.0
[    18.803] (II) UnloadModule: "fbdev"
[    18.803] (II) Unloading fbdev
[    18.803] (II) Failed to load module "fbdev" (already loaded, 0)
[    18.803] (II) LoadModule: "vesa"
[    18.803] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.803] (II) Module vesa: vendor="X.Org Foundation"
[    18.803] 	compiled for 1.17.1, module version = 2.3.3
[    18.803] 	Module class: X.Org Video Driver
[    18.803] 	ABI class: X.Org Video Driver, version 19.0
[    18.803] (II) UnloadModule: "vesa"
[    18.803] (II) Unloading vesa
[    18.803] (II) Failed to load module "vesa" (already loaded, 0)
[    18.803] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    18.803] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    18.803] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    18.803] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    18.803] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
	ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
	ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
	OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
	HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE,
	BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
	BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
	MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
	MULLINS, MULLINS, MULLINS, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
	HAWAII, HAWAII, HAWAII, HAWAII, HAWAII
[    18.808] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    18.808] (II) FBDEV: driver for framebuffer: fbdev
[    18.808] (II) VESA: driver for VESA chipsets: vesa
[    18.808] (++) using VT number 7


[    18.808] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20141121
[    18.808] (II) intel(0): SNA compiled: xserver-xorg-video-intel-lts-vivid 2:2.99.917-1~exp1ubuntu2.2~trusty1 (Timo Aaltonen <tjaalton@debian.org>)
[    18.808] (II) intel(0): SNA compiled for use with valgrind
[    18.808] (II) [KMS] Kernel modesetting enabled.
[    18.808] (WW) Falling back to old probe method for modesetting
[    18.808] (WW) Falling back to old probe method for fbdev
[    18.808] (II) Loading sub module "fbdevhw"
[    18.808] (II) LoadModule: "fbdevhw"
[    18.809] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    18.809] (II) Module fbdevhw: vendor="X.Org Foundation"
[    18.809] 	compiled for 1.17.1, module version = 0.0.2
[    18.809] 	ABI class: X.Org Video Driver, version 19.0
[    18.809] (WW) Falling back to old probe method for vesa
[    18.809] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4000
[    18.809] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[    18.809] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    18.809] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    18.809] (==) intel(0): RGB weight 888
[    18.809] (==) intel(0): Default visual is TrueColor
[    18.809] (II) intel(0): Output LVDS1 has no monitor section
[    18.809] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output LVDS1
[    18.809] (II) intel(0): Enabled output LVDS1
[    18.809] (II) intel(0): Output VGA1 has no monitor section
[    18.809] (II) intel(0): Enabled output VGA1
[    18.809] (II) intel(0): Output HDMI1 has no monitor section
[    18.809] (II) intel(0): Enabled output HDMI1
[    18.809] (II) intel(0): Output DP1 has no monitor section
[    18.809] (II) intel(0): Enabled output DP1
[    18.809] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    18.809] (II) intel(0): Output VIRTUAL1 has no monitor section
[    18.809] (II) intel(0): Enabled output VIRTUAL1
[    18.809] (--) intel(0): Output LVDS1 using initial mode 1366x768 on pipe 0
[    18.809] (==) intel(0): TearFree disabled
[    18.809] (==) intel(0): DPI set to (96, 96)
[    18.809] (II) Loading sub module "dri2"
[    18.809] (II) LoadModule: "dri2"
[    18.809] (II) Module "dri2" already built-in
[    18.809] (II) Loading sub module "present"
[    18.810] (II) LoadModule: "present"
[    18.810] (II) Module "present" already built-in
[    18.810] (==) RADEON(G0): Depth 24, (--) framebuffer bpp 32
[    18.810] (II) RADEON(G0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    18.810] (==) RADEON(G0): Default visual is TrueColor
[    18.810] (==) RADEON(G0): RGB weight 888
[    18.810] (II) RADEON(G0): Using 8 bits per RGB (8 bit DAC)
[    18.810] (--) RADEON(G0): Chipset: "HAINAN" (ChipID = 0x6663)
[    18.810] (II) Loading sub module "dri2"
[    18.810] (II) LoadModule: "dri2"
[    18.810] (II) Module "dri2" already built-in
[    18.810] (II) Loading sub module "glamoregl"
[    18.810] (II) LoadModule: "glamoregl"
[    18.810] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    18.835] (II) Module glamoregl: vendor="X.Org Foundation"
[    18.835] 	compiled for 1.17.1, module version = 1.0.0
[    18.835] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.835] (II) glamor: OpenGL accelerated X.org driver based.
[    18.938] (II) glamor: EGL version 1.4 (DRI2):
[    18.940] (II) RADEON(G0): glamor detected, initialising EGL layer.
[    18.940] (II) RADEON(G0): KMS Color Tiling: enabled
[    18.940] (II) RADEON(G0): KMS Color Tiling 2D: enabled
[    18.940] (II) RADEON(G0): KMS Pageflipping: enabled
[    18.940] (II) RADEON(G0): SwapBuffers wait for vsync: enabled
[    18.940] (II) RADEON(G0): mem size init: gart size :3fbcf000 vram size: s:80000000 visible:7fabe000
[    18.940] (==) RADEON(G0): DPI set to (96, 96)
[    18.940] (II) Loading sub module "fb"
[    18.940] (II) LoadModule: "fb"
[    18.940] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.940] (II) Module fb: vendor="X.Org Foundation"
[    18.940] 	compiled for 1.17.1, module version = 1.0.0
[    18.940] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.940] (==) RADEON(G0): Using gamma correction (1.0, 1.0, 1.0)
[    18.940] (II) Loading sub module "ramdac"
[    18.940] (II) LoadModule: "ramdac"
[    18.940] (II) Module "ramdac" already built-in
[    18.940] (II) UnloadModule: "modesetting"
[    18.940] (II) Unloading modesetting
[    18.940] (II) UnloadModule: "fbdev"
[    18.940] (II) Unloading fbdev
[    18.940] (II) UnloadSubModule: "fbdevhw"
[    18.940] (II) Unloading fbdevhw
[    18.940] (II) UnloadModule: "vesa"
[    18.940] (II) Unloading vesa
[    18.940] (==) Depth 24 pixmap format is 32 bpp
[    18.940] (II) RADEON(G0): [DRI2] Setup complete
[    18.940] (II) RADEON(G0): [DRI2]   DRI driver: radeonsi
[    18.940] (II) RADEON(G0): [DRI2]   VDPAU driver: radeonsi
[    18.940] (II) RADEON(G0): Front buffer size: 3072K
[    18.940] (II) RADEON(G0): VRAM usage limit set to 1879826K
[    18.940] (==) RADEON(G0): Backing store enabled
[    18.940] (II) RADEON(G0): Direct rendering enabled
[    19.001] (II) RADEON(G0): Use GLAMOR acceleration.
[    19.001] (II) RADEON(G0): Acceleration enabled
[    19.001] (==) RADEON(G0): DPMS enabled
[    19.001] (==) RADEON(G0): Silken mouse enabled
[    19.001] (II) RADEON(G0): Set up textured video (glamor)
[    19.001] (II) RADEON(G0): [XvMC] Associated with GLAMOR Textured Video.
[    19.001] (EE) RADEON(G0): [XvMC] Failed to initialize extension.
[    19.001] (II) RADEON(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    19.001] (II) intel(0): SNA initialized with Ivybridge (gen7, gt2) backend
[    19.001] (==) intel(0): Backing store enabled
[    19.001] (==) intel(0): Silken mouse enabled
[    19.001] (II) intel(0): HW Cursor enabled
[    19.001] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    19.002] (==) intel(0): DPMS enabled
[    19.002] (==) intel(0): display hotplug detection enabled
[    19.002] (II) intel(0): [DRI2] Setup complete
[    19.002] (II) intel(0): [DRI2]   DRI driver: i965
[    19.002] (II) intel(0): [DRI2]   VDPAU driver: i965
[    19.002] (II) intel(0): direct rendering: DRI2 enabled
[    19.002] (II) intel(0): hardware support for Present enabled
[    19.002] (--) RandR disabled
[    19.029] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    19.029] (II) AIGLX: enabled GLX_ARB_create_context
[    19.029] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    19.029] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    19.029] (II) AIGLX: enabled GLX_INTEL_swap_event
[    19.029] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    19.029] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    19.029] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    19.029] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    19.029] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    19.029] (II) AIGLX: Loaded and initialized i965
[    19.029] (II) GLX: Initialized DRI2 GL provider for screen 0
[    19.042] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    19.057] (II) intel(0): Setting screen physical size to 361 x 203
[    19.064] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.066] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    19.066] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.066] (II) LoadModule: "evdev"
[    19.066] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.080] (II) Module evdev: vendor="X.Org Foundation"
[    19.081] 	compiled for 1.17.1, module version = 2.9.0
[    19.081] 	Module class: X.Org XInput Driver
[    19.081] 	ABI class: X.Org XInput driver, version 21.0
[    19.081] (II) Using input driver 'evdev' for 'Power Button'
[    19.081] (**) Power Button: always reports core events
[    19.081] (**) evdev: Power Button: Device: "/dev/input/event2"
[    19.081] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.081] (--) evdev: Power Button: Found keys
[    19.081] (II) evdev: Power Button: Configuring as keyboard
[    19.081] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    19.081] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    19.081] (**) Option "xkb_rules" "evdev"
[    19.081] (**) Option "xkb_model" "pc105"
[    19.081] (**) Option "xkb_layout" "gb"
[    19.083] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    19.084] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    19.084] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    19.084] (II) Using input driver 'evdev' for 'Video Bus'
[    19.084] (**) Video Bus: always reports core events
[    19.084] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    19.084] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    19.084] (--) evdev: Video Bus: Found keys
[    19.084] (II) evdev: Video Bus: Configuring as keyboard
[    19.084] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:03/input/input8/event5"
[    19.084] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    19.084] (**) Option "xkb_rules" "evdev"
[    19.084] (**) Option "xkb_model" "pc105"
[    19.084] (**) Option "xkb_layout" "gb"
[    19.084] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    19.084] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.084] (II) Using input driver 'evdev' for 'Power Button'
[    19.084] (**) Power Button: always reports core events
[    19.084] (**) evdev: Power Button: Device: "/dev/input/event0"
[    19.084] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.084] (--) evdev: Power Button: Found keys
[    19.084] (II) evdev: Power Button: Configuring as keyboard
[    19.084] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0/event0"
[    19.084] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    19.084] (**) Option "xkb_rules" "evdev"
[    19.084] (**) Option "xkb_model" "pc105"
[    19.084] (**) Option "xkb_layout" "gb"
[    19.085] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    19.085] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    19.085] (II) Using input driver 'evdev' for 'Video Bus'
[    19.085] (**) Video Bus: always reports core events
[    19.085] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    19.085] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    19.085] (--) evdev: Video Bus: Found keys
[    19.085] (II) evdev: Video Bus: Configuring as keyboard
[    19.085] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:35/LNXVIDEO:00/input/input7/event4"
[    19.085] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 9)
[    19.085] (**) Option "xkb_rules" "evdev"
[    19.085] (**) Option "xkb_model" "pc105"
[    19.085] (**) Option "xkb_layout" "gb"
[    19.085] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    19.085] (II) No input driver specified, ignoring this device.
[    19.085] (II) This device may have been added with another device file.
[    19.086] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/event6)
[    19.086] (**) A4TECH USB Device: Applying InputClass "evdev keyboard catchall"
[    19.086] (II) Using input driver 'evdev' for 'A4TECH USB Device'
[    19.086] (**) A4TECH USB Device: always reports core events
[    19.086] (**) evdev: A4TECH USB Device: Device: "/dev/input/event6"
[    19.086] (--) evdev: A4TECH USB Device: Vendor 0x9da Product 0x9090
[    19.086] (--) evdev: A4TECH USB Device: Found 1 mouse buttons
[    19.086] (--) evdev: A4TECH USB Device: Found scroll wheel(s)
[    19.086] (--) evdev: A4TECH USB Device: Found relative axes
[    19.086] (--) evdev: A4TECH USB Device: Found absolute axes
[    19.086] (--) evdev: A4TECH USB Device: Found absolute multitouch axes
[    19.086] (--) evdev: A4TECH USB Device: Found x and y absolute axes
[    19.086] (--) evdev: A4TECH USB Device: Found keys
[    19.086] (II) evdev: A4TECH USB Device: Forcing relative x/y axes to exist.
[    19.086] (II) evdev: A4TECH USB Device: Configuring as mouse
[    19.086] (II) evdev: A4TECH USB Device: Configuring as keyboard
[    19.086] (II) evdev: A4TECH USB Device: Adding scrollwheel support
[    19.086] (**) evdev: A4TECH USB Device: YAxisMapping: buttons 4 and 5
[    19.086] (**) evdev: A4TECH USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.086] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/0003:09DA:9090.0001/input/input9/event6"
[    19.086] (II) XINPUT: Adding extended input device "A4TECH USB Device" (type: KEYBOARD, id 10)
[    19.086] (**) Option "xkb_rules" "evdev"
[    19.086] (**) Option "xkb_model" "pc105"
[    19.086] (**) Option "xkb_layout" "gb"
[    19.086] (II) evdev: A4TECH USB Device: initialized for relative axes.
[    19.086] (WW) evdev: A4TECH USB Device: ignoring absolute axes.
[    19.087] (**) A4TECH USB Device: (accel) keeping acceleration scheme 1
[    19.087] (**) A4TECH USB Device: (accel) acceleration profile 0
[    19.087] (**) A4TECH USB Device: (accel) acceleration factor: 2.000
[    19.087] (**) A4TECH USB Device: (accel) acceleration threshold: 4
[    19.087] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/js0)
[    19.087] (II) No input driver specified, ignoring this device.
[    19.087] (II) This device may have been added with another device file.
[    19.087] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/event7)
[    19.087] (**) A4TECH USB Device: Applying InputClass "evdev pointer catchall"
[    19.087] (II) Using input driver 'evdev' for 'A4TECH USB Device'
[    19.087] (**) A4TECH USB Device: always reports core events
[    19.087] (**) evdev: A4TECH USB Device: Device: "/dev/input/event7"
[    19.140] (--) evdev: A4TECH USB Device: Vendor 0x9da Product 0x9090
[    19.140] (--) evdev: A4TECH USB Device: Found 20 mouse buttons
[    19.140] (--) evdev: A4TECH USB Device: Found scroll wheel(s)
[    19.140] (--) evdev: A4TECH USB Device: Found relative axes
[    19.140] (--) evdev: A4TECH USB Device: Found x and y relative axes
[    19.140] (II) evdev: A4TECH USB Device: Configuring as mouse
[    19.140] (II) evdev: A4TECH USB Device: Adding scrollwheel support
[    19.140] (**) evdev: A4TECH USB Device: YAxisMapping: buttons 4 and 5
[    19.140] (**) evdev: A4TECH USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.140] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.1/0003:09DA:9090.0002/input/input10/event7"
[    19.140] (II) XINPUT: Adding extended input device "A4TECH USB Device" (type: MOUSE, id 11)
[    19.140] (II) evdev: A4TECH USB Device: initialized for relative axes.
[    19.140] (**) A4TECH USB Device: (accel) keeping acceleration scheme 1
[    19.140] (**) A4TECH USB Device: (accel) acceleration profile 0
[    19.140] (**) A4TECH USB Device: (accel) acceleration factor: 2.000
[    19.140] (**) A4TECH USB Device: (accel) acceleration threshold: 4
[    19.141] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/mouse0)
[    19.141] (II) No input driver specified, ignoring this device.
[    19.141] (II) This device may have been added with another device file.
[    19.141] (II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event13)
[    19.141] (**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
[    19.141] (II) Using input driver 'evdev' for 'Lenovo EasyCamera'
[    19.141] (**) Lenovo EasyCamera: always reports core events
[    19.141] (**) evdev: Lenovo EasyCamera: Device: "/dev/input/event13"
[    19.141] (--) evdev: Lenovo EasyCamera: Vendor 0xbda Product 0x5728
[    19.141] (--) evdev: Lenovo EasyCamera: Found keys
[    19.141] (II) evdev: Lenovo EasyCamera: Configuring as keyboard
[    19.141] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/input/input15/event13"
[    19.141] (II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 12)
[    19.141] (**) Option "xkb_rules" "evdev"
[    19.141] (**) Option "xkb_model" "pc105"
[    19.141] (**) Option "xkb_layout" "gb"
[    19.141] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    19.141] (II) No input driver specified, ignoring this device.
[    19.141] (II) This device may have been added with another device file.
[    19.142] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    19.142] (II) No input driver specified, ignoring this device.
[    19.142] (II) This device may have been added with another device file.
[    19.142] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[    19.142] (II) No input driver specified, ignoring this device.
[    19.142] (II) This device may have been added with another device file.
[    19.142] (II) config/udev: Adding input device Ideapad extra buttons (/dev/input/event9)
[    19.142] (**) Ideapad extra buttons: Applying InputClass "evdev keyboard catchall"
[    19.142] (II) Using input driver 'evdev' for 'Ideapad extra buttons'
[    19.142] (**) Ideapad extra buttons: always reports core events
[    19.142] (**) evdev: Ideapad extra buttons: Device: "/dev/input/event9"
[    19.142] (--) evdev: Ideapad extra buttons: Vendor 0 Product 0
[    19.142] (--) evdev: Ideapad extra buttons: Found keys
[    19.142] (II) evdev: Ideapad extra buttons: Configuring as keyboard
[    19.142] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1f.0/PNP0C09:00/VPC2004:00/input/input11/event9"
[    19.142] (II) XINPUT: Adding extended input device "Ideapad extra buttons" (type: KEYBOARD, id 13)
[    19.142] (**) Option "xkb_rules" "evdev"
[    19.142] (**) Option "xkb_model" "pc105"
[    19.142] (**) Option "xkb_layout" "gb"
[    19.143] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    19.143] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    19.143] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    19.143] (**) AT Translated Set 2 keyboard: always reports core events
[    19.143] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    19.143] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    19.143] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    19.143] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    19.143] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    19.143] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 14)
[    19.143] (**) Option "xkb_rules" "evdev"
[    19.143] (**) Option "xkb_model" "pc105"
[    19.143] (**) Option "xkb_layout" "gb"
[    19.143] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event8)
[    19.143] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    19.143] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    19.143] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    19.143] (II) LoadModule: "synaptics"
[    19.143] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    19.143] (II) Module synaptics: vendor="X.Org Foundation"
[    19.143] 	compiled for 1.17.1, module version = 1.8.99
[    19.143] 	Module class: X.Org XInput Driver
[    19.143] 	ABI class: X.Org XInput driver, version 21.0
[    19.143] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    19.143] (**) ETPS/2 Elantech Touchpad: always reports core events
[    19.143] (**) Option "Device" "/dev/input/event8"
[    19.156] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2940 (res 0)
[    19.156] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1260 (res 0)
[    19.156] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    19.156] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    19.156] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    19.156] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    19.156] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    19.156] (**) ETPS/2 Elantech Touchpad: always reports core events
[    19.168] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event8"
[    19.168] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 15)
[    19.168] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    19.168] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    19.168] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.063
[    19.168] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    19.168] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    19.168] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    19.168] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    19.168] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    19.169] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    19.169] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    49.369] reporting 4 5 1 8
[    53.256] (II) intel(0): EDID vendor "LGD", prod id 826
[    53.256] (II) intel(0): Printing DDC gathered Modelines:
[    53.256] (II) intel(0): Modeline "1366x768"x0.0   70.00  1366 1402 1450 1492  768 771 776 782 -hsync -vsync (46.9 kHz eP)
[    53.259] reporting 4 5 7 53
[    53.361] reporting 4 5 7 53
[    53.361] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.362] reporting 4 5 7 53
[    53.643] reporting 4 5 7 53
[    53.643] reporting 4 5 7 53
[    53.643] reporting 4 5 7 53
[    53.643] reporting 4 5 7 53
[    53.643] reporting 4 5 7 53
[    53.643] reporting 4 5 7 53
[    53.643] reporting 4 5 7 53
[    54.213] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AA2FC318445DE966DF48706BBC15B7668547E20.xkm
[    55.502] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.994] reporting 4 5 7 53
[    55.995] reporting 4 5 7 53
[    56.040] reporting 4 5 7 53
[    56.040] reporting 4 5 7 53
[    56.041] reporting 4 5 7 53
[    56.041] reporting 4 5 7 53
[    56.041] reporting 4 5 7 53
[    56.041] reporting 4 5 7 53
[    56.041] reporting 4 5 7 53
[    56.054] reporting 4 5 7 53
[    56.054] reporting 4 5 7 53
[    56.054] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.055] reporting 4 5 7 53
[    56.085] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.086] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.087] reporting 4 5 7 53
[    56.088] reporting 4 5 7 53
[    56.107] reporting 4 5 7 53
[    56.107] reporting 4 5 7 53
[   114.208] reporting 4 5 7 53
[   128.100] reporting 4 5 7 53
[   339.790] reporting 4 5 7 53
[   530.263] reporting 4 5 7 53
[   530.263] reporting 4 5 7 53
[   530.263] reporting 4 5 7 53
[   530.575] reporting 4 5 7 53
[   530.673] reporting 4 5 7 53
[   531.861] reporting 4 5 7 53
[   596.488] reporting 4 5 7 53
[   596.533] reporting 4 5 7 53
[   596.584] reporting 4 5 7 53
[   596.615] reporting 4 5 7 53
[   596.624] reporting 4 5 7 53
[   596.656] reporting 4 5 7 53
[   597.360] reporting 4 5 7 53
[   600.105] reporting 4 5 7 53
[   600.913] reporting 4 5 7 53
[   600.933] reporting 4 5 7 53
[   600.933] (II) intel(0): switch to mode 640x480@59.9 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   601.686] reporting 4 5 7 53
[   601.689] reporting 4 5 7 53
[   601.726] reporting 4 5 7 53
[   601.726] reporting 4 5 7 53
[   601.726] reporting 4 5 7 53
[   602.026] reporting 4 5 7 53
[   602.026] reporting 4 5 7 53
[   602.026] reporting 4 5 7 53
[   602.026] reporting 4 5 7 53
[   602.027] reporting 4 5 7 53
[   602.027] reporting 4 5 7 53
[   602.027] reporting 4 5 7 53
[   602.027] reporting 4 5 7 53
[   602.027] reporting 4 5 7 53
[   602.028] reporting 4 5 7 53
[   602.028] reporting 4 5 7 53
[   602.028] reporting 4 5 7 53
[   602.028] reporting 4 5 7 53
[   602.028] reporting 4 5 7 53
[   609.124] reporting 4 5 7 53
[   609.124] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   609.885] reporting 4 5 7 53
[   609.889] reporting 4 5 7 53
[   609.947] reporting 4 5 7 53
[   609.947] reporting 4 5 7 53
[   609.947] reporting 4 5 7 53
[   610.247] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.248] reporting 4 5 7 53
[   610.249] reporting 4 5 7 53
[   610.249] reporting 4 5 7 53
[   610.249] reporting 4 5 7 53
[   610.355] reporting 4 5 7 53
[   610.387] reporting 4 5 7 53
[   610.387] (II) intel(0): switch to mode 1024x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   611.189] reporting 4 5 7 53
[   611.194] reporting 4 5 7 53
[   611.228] reporting 4 5 7 53
[   611.228] reporting 4 5 7 53
[   611.229] reporting 4 5 7 53
[   611.529] reporting 4 5 7 53
[   611.529] reporting 4 5 7 53
[   611.529] reporting 4 5 7 53
[   611.529] reporting 4 5 7 53
[   611.529] reporting 4 5 7 53
[   611.530] reporting 4 5 7 53
[   611.530] reporting 4 5 7 53
[   611.530] reporting 4 5 7 53
[   611.530] reporting 4 5 7 53
[   611.530] reporting 4 5 7 53
[   611.530] reporting 4 5 7 53
[   611.530] reporting 4 5 7 53
[   611.530] reporting 4 5 7 53
[   611.530] reporting 4 5 7 53
[   653.793] reporting 4 5 7 53
[   653.793] (II) intel(0): switch to mode 640x480@59.9 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   654.546] reporting 4 5 7 53
[   654.549] reporting 4 5 7 53
[   654.587] reporting 4 5 7 53
[   654.587] reporting 4 5 7 53
[   654.587] reporting 4 5 7 53
[   654.887] reporting 4 5 7 53
[   654.888] reporting 4 5 7 53
[   654.888] reporting 4 5 7 53
[   654.888] reporting 4 5 7 53
[   654.888] reporting 4 5 7 53
[   654.888] reporting 4 5 7 53
[   654.888] reporting 4 5 7 53
[   654.889] reporting 4 5 7 53
[   654.889] reporting 4 5 7 53
[   654.889] reporting 4 5 7 53
[   654.889] reporting 4 5 7 53
[   654.889] reporting 4 5 7 53
[   654.889] reporting 4 5 7 53
[   654.890] reporting 4 5 7 53
[   663.532] reporting 4 5 7 53
[   663.532] (II) intel(0): switch to mode 1024x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   664.357] reporting 4 5 7 53
[   664.362] reporting 4 5 7 53
[   664.395] reporting 4 5 7 53
[   664.399] reporting 4 5 7 53
[   664.400] reporting 4 5 7 53
[   664.700] reporting 4 5 7 53
[   664.700] reporting 4 5 7 53
[   664.701] reporting 4 5 7 53
[   664.701] reporting 4 5 7 53
[   664.701] reporting 4 5 7 53
[   664.701] reporting 4 5 7 53
[   664.701] reporting 4 5 7 53
[   664.702] reporting 4 5 7 53
[   664.702] reporting 4 5 7 53
[   664.702] reporting 4 5 7 53
[   664.702] reporting 4 5 7 53
[   664.702] reporting 4 5 7 53
[   664.703] reporting 4 5 7 53
[   664.703] reporting 4 5 7 53
[   665.862] reporting 4 5 7 53
[   665.862] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   666.657] reporting 4 5 7 53
[   666.660] reporting 4 5 7 53
[   666.697] reporting 4 5 7 53
[   666.697] reporting 4 5 7 53
[   666.697] reporting 4 5 7 53
[   666.998] reporting 4 5 7 53
[   666.998] reporting 4 5 7 53
[   666.998] reporting 4 5 7 53
[   666.998] reporting 4 5 7 53
[   666.998] reporting 4 5 7 53
[   666.998] reporting 4 5 7 53
[   666.998] reporting 4 5 7 53
[   666.999] reporting 4 5 7 53
[   666.999] reporting 4 5 7 53
[   666.999] reporting 4 5 7 53
[   666.999] reporting 4 5 7 53
[   666.999] reporting 4 5 7 53
[   666.999] reporting 4 5 7 53
[   666.999] reporting 4 5 7 53
[  1747.830] reporting 4 5 7 53
[  1822.830] reporting 4 5 7 53
[  1897.829] reporting 4 5 7 53
[  2594.471] reporting 4 5 7 53
[  6680.609] reporting 4 5 7 53
[  6687.046] reporting 4 5 7 53
[  6846.392] reporting 4 5 7 53
[  7187.062] reporting 4 5 7 53
[  7231.844] reporting 4 5 7 53
[  7283.000] reporting 4 5 7 53
[  7306.398] reporting 4 5 7 53
[  7434.616] reporting 4 5 7 53
[  7637.434] reporting 4 5 7 53
[  7665.531] reporting 4 5 7 53
[  7810.771] reporting 4 5 7 53
[  8000.544] reporting 4 5 7 53
[  8000.548] reporting 4 5 7 53
[  8040.983] reporting 4 5 7 53
[  8040.984] reporting 4 5 7 53
[  8225.499] reporting 4 5 7 53
[  8827.271] reporting 4 5 7 53
[  8899.741] reporting 4 5 7 53
[  9146.910] reporting 4 5 7 53
[  9150.502] reporting 4 5 7 53
[  9374.923] reporting 4 5 7 53
[  9419.409] reporting 4 5 7 53
[  9586.987] reporting 4 5 7 53
[  9791.290] reporting 4 5 7 53
[  9952.420] reporting 4 5 7 53
[ 10189.686] reporting 4 5 7 53
[ 10191.814] reporting 4 5 7 53
[ 11003.526] reporting 4 5 7 53
[ 11013.383] reporting 4 5 7 53
[ 11029.386] reporting 4 5 7 53
[ 11112.675] reporting 4 5 7 53
[ 11223.046] reporting 4 5 7 53
[ 11230.545] reporting 4 5 7 53
[ 11646.462] reporting 4 5 7 53
[ 11948.050] reporting 4 5 7 53
[ 11950.287] reporting 4 5 7 53
[ 12100.385] reporting 4 5 7 53
[ 12175.384] reporting 4 5 7 53
[ 12220.970] reporting 4 5 7 53
[ 12251.827] reporting 4 5 7 53
[ 12772.535] reporting 4 5 7 53
[ 12791.910] reporting 4 5 7 53
[ 12791.910] reporting 4 5 7 53
[ 12791.910] reporting 4 5 7 53
[ 12792.521] reporting 4 5 7 53
[ 12792.728] reporting 4 5 7 53
[ 12794.422] reporting 4 5 7 53
[ 12795.098] reporting 4 5 7 53
[ 12795.675] reporting 4 5 7 53
[ 12969.346] reporting 4 5 7 53
[ 12973.860] reporting 4 5 7 53
[ 13123.905] reporting 4 5 7 53
[ 13125.597] reporting 4 5 7 53
[ 13184.975] reporting 4 5 7 53
[ 13184.985] reporting 4 5 7 53
[ 13184.985] reporting 4 5 7 53
[ 13184.985] reporting 4 5 7 53
[ 13184.985] reporting 4 5 7 53
[ 13184.985] reporting 4 5 7 53
[ 13184.985] reporting 4 5 7 53
[ 13184.986] reporting 4 5 7 53
[ 13185.651] reporting 4 5 7 53
[ 13185.699] reporting 4 5 7 53
[ 13187.087] reporting 4 5 7 53
[ 13203.661] reporting 4 5 7 53
[ 13203.854] reporting 4 5 7 53
[ 13216.494] reporting 4 5 7 53
[ 13282.153] reporting 4 5 7 53
[ 13282.188] reporting 4 5 7 53
[ 13282.230] reporting 4 5 7 53
[ 13282.275] reporting 4 5 7 53
[ 13282.317] reporting 4 5 7 53
[ 13282.324] reporting 4 5 7 53
[ 13282.880] reporting 4 5 7 53
[ 13285.920] reporting 4 5 7 53
[ 13289.444] reporting 4 5 7 53
[ 13289.465] (II) intel(0): switch to mode 1024x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 13290.312] reporting 4 5 7 53
[ 13290.316] reporting 4 5 7 53
[ 13290.487] reporting 4 5 7 53
[ 13290.531] reporting 4 5 7 53
[ 13290.531] reporting 4 5 7 53
[ 13290.900] reporting 4 5 7 53
[ 13290.900] reporting 4 5 7 53
[ 13290.901] reporting 4 5 7 53
[ 13290.901] reporting 4 5 7 53
[ 13290.901] reporting 4 5 7 53
[ 13290.901] reporting 4 5 7 53
[ 13290.901] reporting 4 5 7 53
[ 13290.901] reporting 4 5 7 53
[ 13290.902] reporting 4 5 7 53
[ 13290.902] reporting 4 5 7 53
[ 13290.902] reporting 4 5 7 53
[ 13290.902] reporting 4 5 7 53
[ 13290.902] reporting 4 5 7 53
[ 13290.902] reporting 4 5 7 53
[ 13291.422] reporting 4 5 7 53
[ 13291.422] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 13292.189] reporting 4 5 7 53
[ 13292.192] reporting 4 5 7 53
[ 13292.204] reporting 4 5 7 53
[ 13292.210] (II) intel(0): switch to mode 1024x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 13292.703] reporting 4 5 7 53
[ 13292.706] reporting 4 5 7 53
[ 13292.711] reporting 4 5 7 53
[ 13292.712] reporting 4 5 7 53
[ 13292.712] reporting 4 5 7 53
[ 13292.733] reporting 4 5 7 53
[ 13292.733] reporting 4 5 7 53
[ 13292.734] reporting 4 5 7 53
[ 13346.513] reporting 4 5 7 53
[ 13346.513] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 13347.324] reporting 4 5 7 53
[ 13347.327] reporting 4 5 7 53
[ 13347.343] reporting 4 5 7 53
[ 13347.365] reporting 4 5 7 53
[ 13347.369] reporting 4 5 7 53
[ 13347.371] reporting 4 5 7 53
[ 13347.673] reporting 4 5 7 53
[ 13347.673] reporting 4 5 7 53
[ 13347.674] reporting 4 5 7 53
[ 13347.674] reporting 4 5 7 53
[ 13347.674] reporting 4 5 7 53
[ 13347.674] reporting 4 5 7 53
[ 13347.674] reporting 4 5 7 53
[ 13347.674] reporting 4 5 7 53
[ 13347.674] reporting 4 5 7 53
[ 13347.674] reporting 4 5 7 53
[ 13347.675] reporting 4 5 7 53
[ 13347.675] reporting 4 5 7 53
[ 13347.675] reporting 4 5 7 53
[ 13347.675] reporting 4 5 7 53
[ 13484.116] reporting 4 5 7 53
[ 13556.224] reporting 4 5 7 53
[ 13556.227] reporting 4 5 7 53
[ 13577.276] reporting 4 5 7 53
[ 13603.746] reporting 4 5 7 53
[ 13603.747] reporting 4 5 7 53
[ 13603.778] reporting 4 5 7 53
[ 13603.832] reporting 4 5 7 53
[ 13603.837] reporting 4 5 7 53
[ 13604.170] reporting 4 5 7 53
[ 13604.329] reporting 4 5 7 53
[ 13604.401] reporting 4 5 7 53
[ 13605.687] reporting 4 5 7 53
[ 13608.687] reporting 4 5 7 53
[ 13613.203] reporting 4 5 7 53
[ 13676.896] reporting 4 5 7 53
[ 13676.934] reporting 4 5 7 53
[ 13676.976] reporting 4 5 7 53
[ 13677.010] reporting 4 5 7 53
[ 13677.016] reporting 4 5 7 53
[ 13677.078] reporting 4 5 7 53
[ 13677.112] reporting 4 5 7 53
[ 13678.722] reporting 4 5 7 53
[ 13678.788] reporting 4 5 7 53
[ 13678.852] reporting 4 5 7 53
[ 13678.909] reporting 4 5 7 53
[ 13678.974] reporting 4 5 7 53
[ 13679.040] reporting 4 5 7 53
[ 13679.105] reporting 4 5 7 53
[ 13679.170] reporting 4 5 7 53
[ 13679.235] reporting 4 5 7 53
[ 13679.299] reporting 4 5 7 53
[ 13679.427] reporting 4 5 7 53
[ 13685.464] reporting 4 5 7 53
[ 13685.506] reporting 4 5 7 53
[ 13685.549] reporting 4 5 7 53
[ 13685.583] reporting 4 5 7 53
[ 13685.592] reporting 4 5 7 53
[ 13685.627] reporting 4 5 7 53
[ 13686.481] reporting 4 5 7 53
[ 13690.356] reporting 4 5 7 53
[ 13721.839] reporting 4 5 7 53
[ 13721.879] reporting 4 5 7 53
[ 13721.916] reporting 4 5 7 53
[ 13721.955] reporting 4 5 7 53
[ 13721.961] reporting 4 5 7 53
[ 13722.008] reporting 4 5 7 53
[ 13722.445] reporting 4 5 7 53
[ 13835.986] reporting 4 5 7 53
[ 13836.063] reporting 4 5 7 53
[ 13836.127] reporting 4 5 7 53
[ 13836.606] reporting 4 5 7 53
[ 13838.412] reporting 4 5 7 53
[ 13841.111] reporting 4 5 7 53
[ 13867.817] reporting 4 5 7 53
[ 13867.859] reporting 4 5 7 53
[ 13867.893] reporting 4 5 7 53
[ 13867.932] reporting 4 5 7 53
[ 13867.940] reporting 4 5 7 53
[ 13867.973] reporting 4 5 7 53
[ 13868.116] reporting 4 5 7 53
[ 13871.006] reporting 4 5 7 53
[ 13873.967] reporting 4 5 7 53
[ 13879.173] reporting 4 5 7 53
[ 13884.131] reporting 4 5 7 53
[ 13884.155] reporting 4 5 7 53
[ 13885.993] reporting 4 5 7 53
[ 13948.355] reporting 4 5 7 53
[ 13948.399] reporting 4 5 7 53
[ 13948.440] reporting 4 5 7 53
[ 13948.478] reporting 4 5 7 53
[ 13948.493] reporting 4 5 7 53
[ 13948.529] reporting 4 5 7 53
[ 13948.608] reporting 4 5 7 53
[ 13956.483] reporting 4 5 7 53
[ 13963.834] reporting 4 5 7 53
[ 13963.874] reporting 4 5 7 53
[ 13963.919] reporting 4 5 7 53
[ 13963.961] reporting 4 5 7 53
[ 13963.970] reporting 4 5 7 53
[ 13964.018] reporting 4 5 7 53
[ 13964.098] reporting 4 5 7 53
[ 13964.373] reporting 4 5 7 53
[ 13989.412] reporting 4 5 7 53
[ 13989.450] reporting 4 5 7 53
[ 13989.492] reporting 4 5 7 53
[ 13989.534] reporting 4 5 7 53
[ 13989.543] reporting 4 5 7 53
[ 13989.575] reporting 4 5 7 53
[ 13989.653] reporting 4 5 7 53
[ 13989.782] reporting 4 5 7 53
[ 13990.983] reporting 4 5 7 53
[ 13992.301] reporting 4 5 7 53
[ 14165.962] reporting 4 5 7 53
[ 14166.062] reporting 4 5 7 53
[ 14166.227] reporting 4 5 7 53
[ 14166.691] reporting 4 5 7 53
[ 14166.866] reporting 4 5 7 53
[ 14167.152] reporting 4 5 7 53
[ 14168.225] reporting 4 5 7 53
[ 14169.221] reporting 4 5 7 53
[ 14200.775] reporting 4 5 7 53
[ 14206.887] reporting 4 5 7 53
[ 14206.929] reporting 4 5 7 53
[ 14206.971] reporting 4 5 7 53
[ 14207.011] reporting 4 5 7 53
[ 14207.020] reporting 4 5 7 53
[ 14207.058] reporting 4 5 7 53
[ 14207.151] reporting 4 5 7 53
[ 14212.154] reporting 4 5 7 53
[ 14214.001] reporting 4 5 7 53
[ 14214.002] (II) intel(0): switch to mode 1024x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 14214.817] reporting 4 5 7 53
[ 14214.822] reporting 4 5 7 53
[ 14214.847] reporting 4 5 7 53
[ 14214.847] reporting 4 5 7 53
[ 14214.847] reporting 4 5 7 53
[ 14215.148] reporting 4 5 7 53
[ 14215.148] reporting 4 5 7 53
[ 14215.148] reporting 4 5 7 53
[ 14215.148] reporting 4 5 7 53
[ 14215.148] reporting 4 5 7 53
[ 14215.148] reporting 4 5 7 53
[ 14215.148] reporting 4 5 7 53
[ 14215.149] reporting 4 5 7 53
[ 14215.150] reporting 4 5 7 53
[ 14215.150] reporting 4 5 7 53
[ 14215.151] reporting 4 5 7 53
[ 14215.151] reporting 4 5 7 53
[ 14215.151] reporting 4 5 7 53
[ 14215.151] reporting 4 5 7 53
[ 14215.653] reporting 4 5 7 53
[ 14215.653] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 14216.413] reporting 4 5 7 53
[ 14216.419] reporting 4 5 7 53
[ 14216.433] reporting 4 5 7 53
[ 14216.436] (II) intel(0): switch to mode 1024x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 14216.934] reporting 4 5 7 53
[ 14216.935] reporting 4 5 7 53
[ 14216.935] reporting 4 5 7 53
[ 14216.935] reporting 4 5 7 53
[ 14216.941] reporting 4 5 7 53
[ 14216.957] reporting 4 5 7 53
[ 14216.958] reporting 4 5 7 53
[ 14216.958] reporting 4 5 7 53
[ 14265.946] reporting 4 5 7 53
[ 14265.946] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 14266.677] reporting 4 5 7 53
[ 14266.680] reporting 4 5 7 53
[ 14266.704] reporting 4 5 7 53
[ 14266.705] reporting 4 5 7 53
[ 14266.705] reporting 4 5 7 53
[ 14267.005] reporting 4 5 7 53
[ 14267.005] reporting 4 5 7 53
[ 14267.006] reporting 4 5 7 53
[ 14267.006] reporting 4 5 7 53
[ 14267.006] reporting 4 5 7 53
[ 14267.006] reporting 4 5 7 53
[ 14267.006] reporting 4 5 7 53
[ 14267.006] reporting 4 5 7 53
[ 14267.007] reporting 4 5 7 53
[ 14267.007] reporting 4 5 7 53
[ 14267.007] reporting 4 5 7 53
[ 14267.007] reporting 4 5 7 53
[ 14267.007] reporting 4 5 7 53
[ 14267.007] reporting 4 5 7 53
[ 14312.616] reporting 4 5 7 53
[ 14485.712] reporting 4 5 7 53
[ 14485.747] reporting 4 5 7 53
[ 14485.786] reporting 4 5 7 53
[ 14485.825] reporting 4 5 7 53
[ 14485.834] reporting 4 5 7 53
[ 14485.871] reporting 4 5 7 53
[ 14485.971] reporting 4 5 7 53
[ 14513.434] reporting 4 5 7 53
[ 14513.474] reporting 4 5 7 53
[ 14513.515] reporting 4 5 7 53
[ 14513.549] reporting 4 5 7 53
[ 14513.558] reporting 4 5 7 53
[ 14513.593] reporting 4 5 7 53
[ 14513.692] reporting 4 5 7 53
[ 14514.930] reporting 4 5 7 53
[ 14516.261] reporting 4 5 7 53
[ 14517.219] reporting 4 5 7 53
[ 14532.335] reporting 4 5 7 53
[ 14532.384] reporting 4 5 7 53
[ 14532.425] reporting 4 5 7 53
[ 14532.463] reporting 4 5 7 53
[ 14532.470] reporting 4 5 7 53
[ 14532.504] reporting 4 5 7 53
[ 14532.606] reporting 4 5 7 53
[ 14545.355] reporting 4 5 7 53
[ 14545.444] reporting 4 5 7 53
[ 14545.519] reporting 4 5 7 53
[ 14545.528] reporting 4 5 7 53
[ 14546.701] reporting 4 5 7 53
[ 14548.013] reporting 4 5 7 53
[ 14625.430] reporting 4 5 7 53
[ 14625.432] reporting 4 5 7 53
[ 14693.139] reporting 4 5 7 53
[ 14693.141] reporting 4 5 7 53
[ 14745.982] reporting 4 5 7 53
[ 14745.990] reporting 4 5 7 53
[ 14913.312] reporting 4 5 7 53
[ 14920.759] reporting 4 5 7 53
[ 14966.756] reporting 4 5 7 53
[ 14966.798] reporting 4 5 7 53
[ 14966.834] reporting 4 5 7 53
[ 14966.876] reporting 4 5 7 53
[ 14966.883] reporting 4 5 7 53
[ 14966.925] reporting 4 5 7 53
[ 14967.021] reporting 4 5 7 53
[ 14967.103] reporting 4 5 7 53
[ 14967.671] reporting 4 5 7 53
[ 14969.949] reporting 4 5 7 53
[ 14974.786] reporting 4 5 7 53
[ 15060.194] reporting 4 5 7 53
[ 15061.845] reporting 4 5 7 53
[ 15063.570] reporting 4 5 7 53
[ 15063.608] reporting 4 5 7 53
[ 15063.654] reporting 4 5 7 53
[ 15063.688] reporting 4 5 7 53
[ 15063.696] reporting 4 5 7 53
[ 15063.731] reporting 4 5 7 53
[ 15063.943] reporting 4 5 7 53
[ 15073.725] reporting 4 5 7 53
[ 15076.016] reporting 4 5 7 53
[ 15076.087] reporting 4 5 7 53
[ 15076.093] reporting 4 5 7 53
[ 15076.173] reporting 4 5 7 53
[ 15081.753] reporting 4 5 7 53
[ 15081.811] reporting 4 5 7 53
[ 15081.873] reporting 4 5 7 53
[ 15081.930] reporting 4 5 7 53
[ 15082.151] reporting 4 5 7 53
[ 15085.219] reporting 4 5 7 53
[ 15091.827] reporting 4 5 7 53
[ 15091.870] reporting 4 5 7 53
[ 15091.909] reporting 4 5 7 53
[ 15091.945] reporting 4 5 7 53
[ 15091.954] reporting 4 5 7 53
[ 15091.990] reporting 4 5 7 53
[ 15092.161] reporting 4 5 7 53
[ 15109.702] reporting 4 5 7 53
[ 15112.569] reporting 4 5 7 53
[ 15118.400] reporting 4 5 7 53
[ 15129.943] reporting 4 5 7 53
[ 15138.541] reporting 4 5 7 53
[ 15144.629] reporting 4 5 7 53
[ 15144.669] reporting 4 5 7 53
[ 15144.710] reporting 4 5 7 53
[ 15144.748] reporting 4 5 7 53
[ 15144.758] reporting 4 5 7 53
[ 15144.800] reporting 4 5 7 53
[ 15144.885] reporting 4 5 7 53
[ 15144.965] reporting 4 5 7 53
[ 15145.541] reporting 4 5 7 53
[ 15147.949] reporting 4 5 7 53
[ 15149.875] reporting 4 5 7 53
[ 15221.300] reporting 4 5 7 53
[ 15226.145] reporting 4 5 7 53
[ 15227.443] reporting 4 5 7 53
[ 15233.257] reporting 4 5 7 53
[ 15233.302] reporting 4 5 7 53
[ 15233.345] reporting 4 5 7 53
[ 15233.387] reporting 4 5 7 53
[ 15233.397] reporting 4 5 7 53
[ 15233.431] reporting 4 5 7 53
[ 15233.514] reporting 4 5 7 53
[ 15233.595] reporting 4 5 7 53
[ 15234.146] reporting 4 5 7 53
[ 15236.198] reporting 4 5 7 53
[ 15238.508] reporting 4 5 7 53
[ 15282.083] reporting 4 5 7 53
[ 15382.584] reporting 4 5 7 53
[ 15435.345] reporting 4 5 7 53
[ 15435.345] reporting 4 5 7 53
[ 15438.195] reporting 4 5 7 53
[ 15438.196] reporting 4 5 7 53
[ 15572.328] reporting 4 5 7 53
[ 15572.369] reporting 4 5 7 53
[ 15572.394] reporting 4 5 7 53
[ 15572.415] reporting 4 5 7 53
[ 15572.482] reporting 4 5 7 53
[ 15572.488] reporting 4 5 7 53
[ 15573.325] reporting 4 5 7 53
[ 15574.292] reporting 4 5 7 53
[ 15589.418] reporting 4 5 7 53
[ 15589.418] reporting 4 5 7 53
[ 15664.418] reporting 4 5 7 53
[ 15664.418] reporting 4 5 7 53
[ 15739.418] reporting 4 5 7 53
[ 15739.418] reporting 4 5 7 53
[ 16833.415] reporting 4 5 7 53
[ 16833.415] reporting 4 5 7 53
[ 16845.076] reporting 4 5 7 53
[ 16845.116] reporting 4 5 7 53
[ 16845.156] reporting 4 5 7 53
[ 16845.206] reporting 4 5 7 53
[ 16845.216] reporting 4 5 7 53
[ 16845.251] reporting 4 5 7 53
[ 16845.333] reporting 4 5 7 53
[ 16845.420] reporting 4 5 7 53
[ 16846.007] reporting 4 5 7 53
[ 16879.083] reporting 4 5 7 53
[ 16881.714] reporting 4 5 7 53
[ 16936.394] reporting 4 5 7 53
[ 16939.098] reporting 4 5 7 53
[ 16960.893] reporting 4 5 7 53
[ 16960.932] reporting 4 5 7 53
[ 16960.975] reporting 4 5 7 53
[ 16961.022] reporting 4 5 7 53
[ 16961.032] reporting 4 5 7 53
[ 16961.090] reporting 4 5 7 53
[ 16961.207] reporting 4 5 7 53
[ 16962.437] reporting 4 5 7 53
[ 16963.746] reporting 4 5 7 53
[ 17004.700] reporting 4 5 7 53
[ 17013.652] reporting 4 5 7 53
[ 17091.811] reporting 4 5 7 53
[ 17155.875] reporting 4 5 7 53
[ 17231.828] reporting 4 5 7 53
[ 17476.425] (II) config/udev: removing device A4TECH USB Device
[ 17476.437] (II) evdev: A4TECH USB Device: Close
[ 17476.780] (II) UnloadModule: "evdev"
[ 17476.782] (II) config/udev: removing device A4TECH USB Device
[ 17476.784] (II) evdev: A4TECH USB Device: Close
[ 17476.784] (II) UnloadModule: "evdev"
[ 17507.425] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/js0)
[ 17507.475] (II) No input driver specified, ignoring this device.
[ 17507.475] (II) This device may have been added with another device file.
[ 17507.475] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/mouse0)
[ 17507.475] (II) No input driver specified, ignoring this device.
[ 17507.475] (II) This device may have been added with another device file.
[ 17507.476] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/event7)
[ 17507.476] (**) A4TECH USB Device: Applying InputClass "evdev pointer catchall"
[ 17507.476] (II) Using input driver 'evdev' for 'A4TECH USB Device'
[ 17507.476] (**) A4TECH USB Device: always reports core events
[ 17507.476] (**) evdev: A4TECH USB Device: Device: "/dev/input/event7"
[ 17507.552] (--) evdev: A4TECH USB Device: Vendor 0x9da Product 0x9090
[ 17507.552] (--) evdev: A4TECH USB Device: Found 20 mouse buttons
[ 17507.552] (--) evdev: A4TECH USB Device: Found scroll wheel(s)
[ 17507.552] (--) evdev: A4TECH USB Device: Found relative axes
[ 17507.552] (--) evdev: A4TECH USB Device: Found x and y relative axes
[ 17507.552] (II) evdev: A4TECH USB Device: Configuring as mouse
[ 17507.552] (II) evdev: A4TECH USB Device: Adding scrollwheel support
[ 17507.552] (**) evdev: A4TECH USB Device: YAxisMapping: buttons 4 and 5
[ 17507.552] (**) evdev: A4TECH USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 17507.552] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.1/0003:09DA:9090.0004/input/input17/event7"
[ 17507.552] (II) XINPUT: Adding extended input device "A4TECH USB Device" (type: MOUSE, id 10)
[ 17507.553] (II) evdev: A4TECH USB Device: initialized for relative axes.
[ 17507.553] (**) A4TECH USB Device: (accel) keeping acceleration scheme 1
[ 17507.553] (**) A4TECH USB Device: (accel) acceleration profile 0
[ 17507.553] (**) A4TECH USB Device: (accel) acceleration factor: 2.000
[ 17507.553] (**) A4TECH USB Device: (accel) acceleration threshold: 4
[ 17507.554] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/event6)
[ 17507.554] (**) A4TECH USB Device: Applying InputClass "evdev keyboard catchall"
[ 17507.554] (II) Using input driver 'evdev' for 'A4TECH USB Device'
[ 17507.554] (**) A4TECH USB Device: always reports core events
[ 17507.554] (**) evdev: A4TECH USB Device: Device: "/dev/input/event6"
[ 17507.554] (--) evdev: A4TECH USB Device: Vendor 0x9da Product 0x9090
[ 17507.554] (--) evdev: A4TECH USB Device: Found 1 mouse buttons
[ 17507.554] (--) evdev: A4TECH USB Device: Found scroll wheel(s)
[ 17507.554] (--) evdev: A4TECH USB Device: Found relative axes
[ 17507.554] (--) evdev: A4TECH USB Device: Found absolute axes
[ 17507.554] (--) evdev: A4TECH USB Device: Found absolute multitouch axes
[ 17507.554] (--) evdev: A4TECH USB Device: Found x and y absolute axes
[ 17507.554] (--) evdev: A4TECH USB Device: Found keys
[ 17507.554] (II) evdev: A4TECH USB Device: Forcing relative x/y axes to exist.
[ 17507.554] (II) evdev: A4TECH USB Device: Configuring as mouse
[ 17507.554] (II) evdev: A4TECH USB Device: Configuring as keyboard
[ 17507.554] (II) evdev: A4TECH USB Device: Adding scrollwheel support
[ 17507.554] (**) evdev: A4TECH USB Device: YAxisMapping: buttons 4 and 5
[ 17507.554] (**) evdev: A4TECH USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 17507.554] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/0003:09DA:9090.0003/input/input16/event6"
[ 17507.555] (II) XINPUT: Adding extended input device "A4TECH USB Device" (type: KEYBOARD, id 11)
[ 17507.555] (**) Option "xkb_rules" "evdev"
[ 17507.555] (**) Option "xkb_model" "pc105"
[ 17507.555] (**) Option "xkb_layout" "gb"
[ 17507.580] (II) evdev: A4TECH USB Device: initialized for relative axes.
[ 17507.580] (WW) evdev: A4TECH USB Device: ignoring absolute axes.
[ 17507.580] (**) A4TECH USB Device: (accel) keeping acceleration scheme 1
[ 17507.580] (**) A4TECH USB Device: (accel) acceleration profile 0
[ 17507.580] (**) A4TECH USB Device: (accel) acceleration factor: 2.000
[ 17507.581] (**) A4TECH USB Device: (accel) acceleration threshold: 4
[ 17507.736] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AA2FC318445DE966DF48706BBC15B7668547E20.xkm
[ 17507.949] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AA2FC318445DE966DF48706BBC15B7668547E20.xkm
[ 17510.021] (II) config/udev: removing device A4TECH USB Device
[ 17510.040] (II) evdev: A4TECH USB Device: Close
[ 17510.040] (II) UnloadModule: "evdev"
[ 17510.057] (II) config/udev: removing device A4TECH USB Device
[ 17510.076] (II) evdev: A4TECH USB Device: Close
[ 17510.076] (II) UnloadModule: "evdev"
[ 17510.094] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[ 17510.116] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AA2FC318445DE966DF48706BBC15B7668547E20.xkm
[ 17517.065] reporting 4 5 7 53
[ 17519.157] reporting 4 5 7 53
[ 17519.528] reporting 4 5 7 53
[ 17519.722] reporting 4 5 7 53
[ 17519.905] reporting 4 5 7 53
[ 17520.098] reporting 4 5 7 53
[ 17520.282] reporting 4 5 7 53
[ 17580.187] reporting 4 5 7 53
[ 17610.186] reporting 4 5 7 53
[ 17638.088] reporting 4 5 7 53
[ 17685.020] reporting 4 5 7 53
[ 17807.258] reporting 4 5 7 53
[ 17807.577] reporting 4 5 7 53
[ 18264.517] reporting 4 5 7 53
[ 18265.979] reporting 4 5 7 53
[ 18417.199] reporting 4 5 7 53
[ 18418.526] reporting 4 5 7 53
[ 18437.739] reporting 4 5 7 53
[ 18437.739] reporting 4 5 7 53
[ 18437.739] reporting 4 5 7 53
[ 18437.740] reporting 4 5 7 53
[ 18437.740] reporting 4 5 7 53
[ 18437.740] reporting 4 5 7 53
[ 18437.741] reporting 4 5 7 53
[ 18437.741] reporting 4 5 7 53
[ 18437.741] reporting 4 5 7 53
[ 18437.741] reporting 4 5 7 53
[ 18437.741] reporting 4 5 7 53
[ 18437.741] reporting 4 5 7 53
[ 18437.741] reporting 4 5 7 53
[ 18437.742] reporting 4 5 7 53
[ 18437.742] reporting 4 5 7 53
[ 18437.742] reporting 4 5 7 53
[ 18437.742] reporting 4 5 7 53
[ 18437.743] reporting 4 5 7 53
[ 18437.743] reporting 4 5 7 53
[ 18437.743] reporting 4 5 7 53
[ 18437.784] reporting 4 5 7 53
[ 18437.784] reporting 4 5 7 53
[ 18437.785] reporting 4 5 7 53
[ 18437.785] reporting 4 5 7 53
[ 18437.785] reporting 4 5 7 53
[ 18437.785] reporting 4 5 7 53
[ 18437.785] reporting 4 5 7 53
[ 18614.161] reporting 4 5 7 53
[ 18615.646] reporting 4 5 7 53
[ 18626.326] reporting 4 5 7 53
[ 18626.327] reporting 4 5 7 53
[ 18626.327] reporting 4 5 7 53
[ 18626.327] reporting 4 5 7 53
[ 18626.328] reporting 4 5 7 53
[ 18626.328] reporting 4 5 7 53
[ 18626.328] reporting 4 5 7 53
[ 18626.329] reporting 4 5 7 53
[ 18626.329] reporting 4 5 7 53
[ 18626.329] reporting 4 5 7 53
[ 18626.329] reporting 4 5 7 53
[ 18626.329] reporting 4 5 7 53
[ 18626.329] reporting 4 5 7 53
[ 18626.330] reporting 4 5 7 53
[ 18626.330] reporting 4 5 7 53
[ 18626.331] reporting 4 5 7 53
[ 18626.331] reporting 4 5 7 53
[ 18626.331] reporting 4 5 7 53
[ 18626.331] reporting 4 5 7 53
[ 18626.331] reporting 4 5 7 53
[ 18626.356] reporting 4 5 7 53
[ 18626.356] reporting 4 5 7 53
[ 18626.356] reporting 4 5 7 53
[ 18626.356] reporting 4 5 7 53
[ 18626.356] reporting 4 5 7 53
[ 18626.356] reporting 4 5 7 53
[ 18626.356] reporting 4 5 7 53
[ 26718.859] reporting 4 5 7 53
[ 26806.537] reporting 4 5 7 53
[ 27196.217] reporting 4 5 7 53
[ 27196.354] reporting 4 5 7 53
[ 29714.554] reporting 4 5 7 53
[ 29842.226] reporting 4 5 7 53




```

---

### Post by Bashing-om on 2015-11-08
stefanoskikristijan; Hey !

Hybrid graphics ! wrong command to initilaize the driver .. but as I am reading .. I keep reading, see what else I can come up with .

[INDENT][INDENT]look'n is good
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-11-08
stefanoskikristijan; Sheessshhh ..


Log file tells us
> 
18.801] (EE) Failed to load module "fglrx" (module does not exist, 0)

But, does not tell us why the driver does not build.

Reboot the box to a console ( login screen, key combo ctl+alt+F1)
Let's try it again, from the top:
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade

```


clean up again:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo apt-get purge 'fglrx*'

```

Install:
```

sudo apt-get install fglrx-updates
sudo aticonfig --adapter=all --initial -f

```
Paying close attention for any errors the system may report .

Reboot once more to see the effect .. from CCC can you switch graphics sets ?

[INDENT][INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-08
> **Bashing-om said:**
> stefanoskikristijan; Sheessshhh ..


Log file tells us

But, does not tell us why the driver does not build.

Reboot the box to a console ( login screen, key combo ctl+alt+F1)
Let's try it again, from the top:
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade

```


clean up again:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo apt-get purge 'fglrx*'

```

Install:
```

sudo apt-get install fglrx-updates
sudo aticonfig --adapter=all --initial -f

```
Paying close attention for any errors the system may report .

Reboot once more to see the effect .. from CCC can you switch graphics sets ?
[INDENT][INDENT][INDENT]sometimes I do wonder
[/INDENT]
[/INDENT]
[/INDENT]


Okay im trying this now also i cant even start catalyst because i get the same massage as when i try to initialise "No supported graphic card adapter found"...

---

### Post by stefanoskikristijan on 2015-11-08
> **Bashing-om said:**
> stefanoskikristijan; Sheessshhh ..


Log file tells us

But, does not tell us why the driver does not build.

Reboot the box to a console ( login screen, key combo ctl+alt+F1)
Let's try it again, from the top:
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade

```


clean up again:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo apt-get purge 'fglrx*'

```

Install:
```

sudo apt-get install fglrx-updates
sudo aticonfig --adapter=all --initial -f

```
Paying close attention for any errors the system may report .

Reboot once more to see the effect .. from CCC can you switch graphics sets ?
[INDENT][INDENT][INDENT]sometimes I do wonder
[/INDENT]
[/INDENT]
[/INDENT]


Okay so went into console mod and did it all without problem but when i tried to initialise i got:
```

sudo aticonfig --adapter=all -initial -f
Unitialised file found, configuring.
PowerXpres info: Diagnostic output from /usr/lib/fglrx/switchlibglx:
update-alternatives: warning: forcing reinstalation of alternative /usr/lib/fglrx/id.so.conf because link group x86_64-linux-gnu_gl_conf is broken
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link

using /etc/X11/xorg.conf
Savinf backup to /etc/X11/xorg.conf.origianal-o

```

---

### Post by Bashing-om on 2015-11-08
stefanoskikristijan; Hummm ..

Sorta stuck here, as we have no info to think on.

Let me consider for a bit .. maybe purge and install the open source driver .

If that goes well ??? maybe then we can get the stable FGLRX driver to install ??

Anyone else with a better suggestion ? Hey I am open .

[INDENT][INDENT]be back in a bit
[INDENT][INDENT][INDENT]after due consideration
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-08
Well i purged fglrx and installed x.org driver from the additional drivers window, i really dont know if anyone can get so unlucky as i do with my first cup of ubuntu xD

---

### Post by Bashing-om on 2015-11-09
stefanoskikristijan; Nawww ..

It ain't just you .. It is the lack of OEM support for linux with hybrid graphics and learning how to deal with hybrid graphics .
If you decide to remain with the open source driver, it is "switcheroo" to control the graphic's sets.
Else we continue the fight to get a FGLRX driver to install .
There is another utility
 [https://github.com/beidl/amd-indicator](https://github.com/beidl/amd-indicator)
available to control the sets . I have not used it, so have no direct experience with it. However, if you want to try and see, I am more than willing to see what our results can be.

[INDENT][INDENT]ain't no quitting
[/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-09
> **Bashing-om said:**
> stefanoskikristijan; Nawww ..

It ain't just you .. It is the lack of OEM support for linux with hybrid graphics and learning how to deal with hybrid graphics .
If you decide to remain with the open source driver, it is "switcheroo" to control the graphic's sets.
Else we continue the fight to get a FGLRX driver to install .
There is another utility
 [https://github.com/beidl/amd-indicator](https://github.com/beidl/amd-indicator)
available to control the sets . I have not used it, so have no direct experience with it. However, if you want to try and see, I am more than willing to see what our results can be.[INDENT][INDENT]ain't no quitting
[/INDENT]
[/INDENT]


If you can istruct me to set up AMD Indicator i am open to try it, else i am good with the VGA Switcheroo but i don't know the right commands to do the switch from the Intel to the discrete GPU.

Here is what i get when i try to use switcheroo:
```

user@user:~$ sudo grep -i switcheroo /boot/config-*
[sudo] password for user: 
/boot/config-3.19.0-25-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-3.19.0-32-generic:CONFIG_VGA_SWITCHEROO=y


user@user:~$ sudo ls -l /sys/kernel/debug/vgaswitcheroo/switch
-rw-r--r-- 1 root root 0 Nov  9 17:47 /sys/kernel/debug/vgaswitcheroo/switch


user@user:~$ sudo cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :DynOff:0000:01:00.0


user@user~$ sudo echo ON > /sys/kernel/debug/vgaswitcheroo/switch
bash: /sys/kernel/debug/vgaswitcheroo/switch: Permission denied


user@user:~$ sudo echo DIS > /sys/kernel/debug/vgaswitcheroo/switch
bash: /sys/kernel/debug/vgaswitcheroo/switch: Permission denied

```

Do you have any idea why the permission is denied ? Maybe i have to edit something in the bootloader like to run in nomodeset or whatever 

EDIT: I solved the problem using "**sudo su"** but when i run the commands nothing happens i dont get any error but also i dont see changes, i truen on the AMD card but again its disconected when i check :(

---

### Post by stefanoskikristijan on 2015-11-09
Here is what i discovered while playing with the switcheroo in the last hour:

1. When i run 
```
DRI_PRIME=1 glxgears
```
It says that the Discrete is Powered ON when i check with the switcheroo command.

2. When i dont run **DRI_PRIME=1 glxgearx **and try to power on the AMD CARD it doesnt power on.

3. So i guess i would have to wake up the card with glxgears every time i want to switch because the command to power it on doesnt work, but i am worried about what will happen  when i switch to it and restart the computer because glxgears is exiting so the card with power off and the computer will most probably run into black screen...

---

### Post by Bashing-om on 2015-11-09
stefanoskikristijan' Yeah ...

I am all for staying with open source ---- when we can make it work for us.

switcheroo :
Have you seen :
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

I think is that definitive guide.

If we are going open source, make sure all the FGLRX stuff is gone:
```

ls -al /etc/X11/xorg.conf
dpkg -l | grep fglrx

```

[INDENT][INDENT]as we try and make this work[/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-09
> **Bashing-om said:**
> stefanoskikristijan' Yeah ...

I am all for staying with open source ---- when we can make it work for us.

switcheroo :
Have you seen :
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

I think is that definitive guide.

If we are going open source, make sure all the FGLRX stuff is gone:
```

ls -al /etc/X11/xorg.conf
dpkg -l | grep fglrx

```
[INDENT][INDENT]as we try and make this work[/INDENT]
[/INDENT]


Definitely the fglrx stuff is gone, but i cannot manage switcheroo to power on the AMD GPU i can only power it on using glxgears...

---

### Post by Bashing-om on 2015-11-09
stefanoskikristijan; Hummm ....

Right off hand I do not know what to advise.
Let's verify/check:
```

ls -al /etc/X11/xorg.conf 
dpkg -l | grep -i fglrx
dpkg -l | grep -i nvidia
sudo lshw -C display

```

[INDENT][INDENT]see where we go from here
[/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-09
> **Bashing-om said:**
> stefanoskikristijan; Hummm ....

Right off hand I do not know what to advise.
Let's verify/check:
```

ls -al /etc/X11/xorg.conf 
dpkg -l | grep -i fglrx
dpkg -l | grep -i nvidia
sudo lshw -C display

```
[INDENT][INDENT]see where we go from here
[/INDENT]
[/INDENT]


```
 ls -al /etc/X11/xorg.conf 
ls: cannot access /etc/X11/xorg.conf: No such file or directory

```

```

dpkg -l | grep -i fglrx
**Nothing happens.**

```

```

dpkg -l | grep -i nvidia
**Nothing happens.**

```

```

sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:27 memory:d8000000-d83fffff memory:c0000000-cfffffff ioport:4000(size=64)



```

---

### Post by Bashing-om on 2015-11-09
stefanoskikristijan; K;

That shows you are presently running the Intel chip set.
What results when you set radeon to start on the next login ?

Confirm that you are running ubuntu with the unity Desktop Environment - else the DE commands will be different.
Go to console from the GUI - key combo ctl+alt+f1 ( or log off in the GUI menu )
here issue terminal command:
```

sudo service lightdm stop

```

```

sudo echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch
sudo service lightdm start

```


Just not making a lot of sense,
[INDENT][INDENT][INDENT][INDENT]yet
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-09
> **Bashing-om said:**
> stefanoskikristijan; K;

That shows you are presently running the Intel chip set.
What results when you set radeon to start on the next login ?

Confirm that you are running ubuntu with the unity Desktop Environment - else the DE commands will be different.
Go to console from the GUI - key combo ctl+alt+f1 ( or log off in the GUI menu )
here issue terminal command:
```

sudo service lightdm stop

```

```

sudo echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch
sudo service lightdm start

```


Just not making a lot of sense,[INDENT][INDENT][INDENT][INDENT]yet
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


After i run 
sudo echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch 
My pc screen just turned black and didnt happen anything for 2mins so i restarted my laptop... Btw im on kubunt with KDE...

---

### Post by Bashing-om on 2015-11-09
stefanoskikristijan; Welp :

The DE then is KDM, substitute kdm for lightdm.

Anyway, what have we now ?
```

sudo lshw -C display
cat /var/log/Xorg.0.log

```
Let's look and see what the system has built .

[INDENT][INDENT]everything is great, except
[INDENT][INDENT][INDENT]it just don't work
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-09
> **Bashing-om said:**
> stefanoskikristijan; Welp :

The DE then is KDM, substitute kdm for lightdm.

Anyway, what have we now ?
```

sudo lshw -C display
cat /var/log/Xorg.0.log

```
Let's look and see what the system has built .
[INDENT][INDENT]everything is great, except[INDENT][INDENT][INDENT]it just don't work
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


```

sudo lshw -C display
 *-display               
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:27 memory:d8000000-d83fffff memory:c0000000-cfffffff ioport:4000(size=64)



```

```

cat /var/log/Xorg.0.log
[    21.159] 
X.Org X Server 1.17.1
Release Date: 2015-02-10
[    21.159] X Protocol Version 11, Revision 0
[    21.159] Build Operating System: Linux 3.19.0-28-generic x86_64 Ubuntu
[    21.159] Current Operating System: Linux Kristijan1999 3.19.0-32-generic #37~14.04.1-Ubuntu SMP Thu Oct 22 09:41:40 UTC 2015 x86_64
[    21.159] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-32-generic.efi.signed root=UUID=e55fcb5a-5900-4293-af60-6d6a5f503798 ro quiet splash vt.handoff=7
[    21.159] Build Date: 11 September 2015  10:33:14AM
[    21.159] xorg-server 2:1.17.1-0ubuntu3.1~trusty1 (For technical support please see http://www.ubuntu.com/support) 
[    21.159] Current version of pixman: 0.30.2
[    21.159]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    21.159] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.159] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov  9 23:23:18 2015
[    21.172] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.172] (==) No Layout section.  Using the first Screen section.
[    21.172] (==) No screen section available. Using defaults.
[    21.172] (**) |-->Screen "Default Screen Section" (0)
[    21.172] (**) |   |-->Monitor "<default monitor>"
[    21.172] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    21.172] (==) Automatically adding devices
[    21.172] (==) Automatically enabling devices
[    21.172] (==) Automatically adding GPU devices
[    21.327] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.327]    Entry deleted from font path.
[    21.327] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    21.327]    Entry deleted from font path.
[    21.327] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    21.327]    Entry deleted from font path.
[    21.328] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    21.328]    Entry deleted from font path.
[    21.328] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    21.328]    Entry deleted from font path.
[    21.328] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    21.328] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.328] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.328] (II) Loader magic: 0x7fc2057d2c60
[    21.328] (II) Module ABI versions:
[    21.328]    X.Org ANSI C Emulation: 0.4
[    21.328]    X.Org Video Driver: 19.0
[    21.328]    X.Org XInput driver : 21.0
[    21.328]    X.Org Server Extension : 9.0
[    21.328] (II) xfree86: Adding drm device (/dev/dri/card1)
[    21.328] (II) xfree86: Adding drm device (/dev/dri/card0)
[    21.330] (--) PCI:*(0:0:2:0) 8086:0166:17aa:3800 rev 9, Mem @ 0xd8000000/4194304, 0xc0000000/268435456, I/O @ 0x00004000/64
[    21.330] (--) PCI: (0:1:0:0) 1002:6663:17aa:3800 rev 0, Mem @ 0xd0000000/134217728, 0xd8600000/262144, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[    21.330] (II) LoadModule: "glx"
[    21.400] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.838] (II) Module glx: vendor="X.Org Foundation"
[    21.838]    compiled for 1.17.1, module version = 1.0.0
[    21.838]    ABI class: X.Org Server Extension, version 9.0
[    21.838] (==) AIGLX enabled
[    21.838] (==) Matched intel as autoconfigured driver 0
[    21.838] (==) Matched fglrx as autoconfigured driver 1
[    21.838] (==) Matched ati as autoconfigured driver 2
[    21.838] (==) Matched intel as autoconfigured driver 3
[    21.838] (==) Matched modesetting as autoconfigured driver 4
[    21.838] (==) Matched fbdev as autoconfigured driver 5
[    21.838] (==) Matched vesa as autoconfigured driver 6
[    21.838] (==) Assigned the driver to the xf86ConfigLayout
[    21.838] (II) LoadModule: "intel"
[    21.838] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    21.850] (II) Module intel: vendor="X.Org Foundation"
[    21.851]    compiled for 1.17.1, module version = 2.99.917
[    21.851]    Module class: X.Org Video Driver
[    21.851]    ABI class: X.Org Video Driver, version 19.0
[    21.851] (II) LoadModule: "fglrx"
[    21.851] (WW) Warning, couldn't open module fglrx
[    21.851] (II) UnloadModule: "fglrx"
[    21.851] (II) Unloading fglrx
[    21.851] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    21.851] (II) LoadModule: "ati"
[    21.851] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    21.863] (II) Module ati: vendor="X.Org Foundation"
[    21.863]    compiled for 1.17.1, module version = 7.5.0
[    21.863]    Module class: X.Org Video Driver
[    21.863]    ABI class: X.Org Video Driver, version 19.0
[    21.863] (II) LoadModule: "radeon"
[    21.863] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    21.872] (II) Module radeon: vendor="X.Org Foundation"
[    21.872]    compiled for 1.17.1, module version = 7.5.0
[    21.872]    Module class: X.Org Video Driver
[    21.872]    ABI class: X.Org Video Driver, version 19.0
[    21.872] (II) LoadModule: "modesetting"
[    21.872] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    21.881] (II) Module modesetting: vendor="X.Org Foundation"
[    21.881]    compiled for 1.17.1, module version = 1.17.1
[    21.881]    Module class: X.Org Video Driver
[    21.881]    ABI class: X.Org Video Driver, version 19.0
[    21.881] (II) LoadModule: "fbdev"
[    21.881] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.891] (II) Module fbdev: vendor="X.Org Foundation"
[    21.891]    compiled for 1.17.1, module version = 0.4.4
[    21.891]    Module class: X.Org Video Driver
[    21.891]    ABI class: X.Org Video Driver, version 19.0
[    21.891] (II) LoadModule: "vesa"
[    21.892] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.896] (II) Module vesa: vendor="X.Org Foundation"
[    21.896]    compiled for 1.17.1, module version = 2.3.3
[    21.896]    Module class: X.Org Video Driver
[    21.896]    ABI class: X.Org Video Driver, version 19.0
[    21.896] (==) Matched intel as autoconfigured driver 0
[    21.896] (==) Matched fglrx as autoconfigured driver 1
[    21.896] (==) Matched ati as autoconfigured driver 2
[    21.896] (==) Matched intel as autoconfigured driver 3
[    21.896] (==) Matched modesetting as autoconfigured driver 4
[    21.896] (==) Matched fbdev as autoconfigured driver 5
[    21.896] (==) Matched vesa as autoconfigured driver 6
[    21.896] (==) Assigned the driver to the xf86ConfigLayout
[    21.896] (II) LoadModule: "intel"
[    21.896] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    21.896] (II) Module intel: vendor="X.Org Foundation"
[    21.896]    compiled for 1.17.1, module version = 2.99.917
[    21.896]    Module class: X.Org Video Driver
[    21.896]    ABI class: X.Org Video Driver, version 19.0
[    21.896] (II) UnloadModule: "intel"
[    21.896] (II) Unloading intel
[    21.896] (II) Failed to load module "intel" (already loaded, 32706)
[    21.896] (II) LoadModule: "fglrx"
[    21.897] (WW) Warning, couldn't open module fglrx
[    21.897] (II) UnloadModule: "fglrx"
[    21.897] (II) Unloading fglrx
[    21.897] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    21.897] (II) LoadModule: "ati"
[    21.897] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    21.897] (II) Module ati: vendor="X.Org Foundation"
[    21.897]    compiled for 1.17.1, module version = 7.5.0
[    21.897]    Module class: X.Org Video Driver
[    21.897]    ABI class: X.Org Video Driver, version 19.0
[    21.897] (II) LoadModule: "modesetting"
[    21.897] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    21.897] (II) Module modesetting: vendor="X.Org Foundation"
[    21.897]    compiled for 1.17.1, module version = 1.17.1
[    21.897]    Module class: X.Org Video Driver
[    21.897]    ABI class: X.Org Video Driver, version 19.0
[    21.897] (II) UnloadModule: "modesetting"
[    21.897] (II) Unloading modesetting
[    21.897] (II) Failed to load module "modesetting" (already loaded, 0)
[    21.897] (II) LoadModule: "fbdev"
[    21.897] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.897] (II) Module fbdev: vendor="X.Org Foundation"
[    21.897]    compiled for 1.17.1, module version = 0.4.4
[    21.897]    Module class: X.Org Video Driver
[    21.897]    ABI class: X.Org Video Driver, version 19.0
[    21.897] (II) UnloadModule: "fbdev"
[    21.897] (II) Unloading fbdev
[    21.897] (II) Failed to load module "fbdev" (already loaded, 0)
[    21.897] (II) LoadModule: "vesa"
[    21.897] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.897] (II) Module vesa: vendor="X.Org Foundation"
[    21.897]    compiled for 1.17.1, module version = 2.3.3
[    21.897]    Module class: X.Org Video Driver
[    21.897]    ABI class: X.Org Video Driver, version 19.0
[    21.897] (II) UnloadModule: "vesa"
[    21.897] (II) Unloading vesa
[    21.897] (II) Failed to load module "vesa" (already loaded, 0)
[    21.897] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
        i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
        915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
        Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    21.897] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    21.897] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    21.897] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    21.897] (II) RADEON: Driver for ATI Radeon chipsets:
        ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
        ATI Radeon Mobility X300 (M24) 3152 (PCIE),
        ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
        ATI Radeon X600 (RV380) 3E50 (PCIE),
        ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
        ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
        ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
        ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
        ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
        ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
        ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
        ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
        ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
        ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
        ATI Radeon IGP330M/340M/350M (U2) 4337,
        ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
        ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
        ATI Radeon X800PRO (R420) JI (AGP),
        ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
        ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
        ATI Radeon Mobility 9800 (M18) JN (AGP),
        ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
        ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
        ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
        ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
        ATI Radeon Mobility M7 LW (AGP),
        ATI Mobility FireGL 7800 M7 LX (AGP),
        ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
        ATI FireGL Mobility 9000 (M9) Ld (AGP),
        ATI Radeon Mobility 9000 (M9) Lf (AGP),
        ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
        ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
        ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
        ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
        ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
        ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
        ATI Radeon Mobility 9600 (M10) NQ (AGP),
        ATI Radeon Mobility 9600 (M11) NR (AGP),
        ATI Radeon Mobility 9600 (M10) NS (AGP),
        ATI FireGL Mobility T2 (M10) NT (AGP),
        ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
        ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
        ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
        ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
        ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
        ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
        ATI Radeon Mobility X300 (M22) 5460 (PCIE),
        ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
        ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
        ATI Radeon X800PRO (R423) UI (PCIE),
        ATI Radeon X800LE (R423) UJ (PCIE),
        ATI Radeon X800SE (R423) UK (PCIE),
        ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
        ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
        ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
        ATI FireGL unknown (R423) UR (PCIE),
        ATI FireGL unknown (R423) UT (PCIE),
        ATI Mobility FireGL V5000 (M26) (PCIE),
        ATI Mobility FireGL V5000 (M26) (PCIE),
        ATI Mobility Radeon X700 XL (M26) (PCIE),
        ATI Mobility Radeon X700 (M26) (PCIE),
        ATI Mobility Radeon X700 (M26) (PCIE),
        ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
        ATI Radeon Mobility 9100 IGP (U3) 5835,
        ATI Radeon XPRESS 200 5954 (PCIE),
        ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
        ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
        ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
        ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
        ATI Radeon XPRESS 200M 5975 (PCIE),
        ATI Radeon XPRESS 200 5A41 (PCIE),
        ATI Radeon XPRESS 200M 5A42 (PCIE),
        ATI Radeon XPRESS 200 5A61 (PCIE),
        ATI Radeon XPRESS 200M 5A62 (PCIE),
        ATI Radeon X300 (RV370) 5B60 (PCIE),
        ATI Radeon X600 (RV370) 5B62 (PCIE),
        ATI Radeon X550 (RV370) 5B63 (PCIE),
        ATI FireGL V3100 (RV370) 5B64 (PCIE),
        ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
        ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
        ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
        ATI Mobility Radeon X800 XT (M28) (PCIE),
        ATI Mobility FireGL V5100 (M28) (PCIE),
        ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
        ATI Radeon X850 XT PE (R480) (PCIE),
        ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
        ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
        ATI Radeon X850 XT (R480) (PCIE),
        ATI Radeon X800XT (R423) 5D57 (PCIE),
        ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
        ATI Radeon X700 PRO (RV410) (PCIE),
        ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
        ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
        ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
        ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
        ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
        ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
        ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
        ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
        ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
        ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
        ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
        ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
        ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
        ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
        ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
        ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
        ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
        ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
        ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
        ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
        ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
        ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
        ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
        ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
        ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
        ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
        ATI Mobility Radeon X1700, ATI Radeon X2300HD,
        ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
        ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
        ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
        ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
        ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
        ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
        ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
        ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
        ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
        ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
        ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
        ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
        ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
        ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
        ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
        ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
        ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
        ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
        ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
        ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
        AMD FireStream 9250, ATI FirePro V8700 (FireGL),
        ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
        ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
        ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
        ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
        ATI Mobility Radeon HD 4670, ATI FirePro M5750,
        ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
        ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
        ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
        ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
        ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
        ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
        ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
        ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
        ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
        ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
        ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
        ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
        ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
        ATI Mobility Radeon HD 3850 X2, ATI RV670,
        ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
        ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
        ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
        ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
        ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
        ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
        ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
        ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
        ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
        ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
        ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
        ATI FireGL V3600, ATI Radeon HD 2600 LE,
        ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
        ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
        ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
        ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
        ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
        ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
        ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
        ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
        ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
        ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
        ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
        ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
        ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
        SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
        ATI Radeon 4100, ATI Mobility Radeon HD 4200,
        ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
        AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
        AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
        AMD Radeon HD 6300 Series Graphics,
        AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
        AMD Firestream 9350, ATI Radeon HD 5800 Series,
        ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
        ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
        ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
        ATI Mobility Radeon HD 5800 Series,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
        ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
        ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
        ATI Mobility Radeon HD 5000 Series,
        ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
        ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
        ATI Mobility Radeon HD 5000 Series,
        ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
        ATI Mobility Radeon Graphics, CEDAR,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
        ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
        CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
        AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
        CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
        BARTS, BARTS, Mobility Radeon HD 6000 Series,
        Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
        AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
        AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
        TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
        TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
        CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
        CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
        ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
        ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
        ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
        ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
        TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
        TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
        PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
        VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
        VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
        VERDE, VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
        OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
        HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE,
        BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
        BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
        KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
        KABINI, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
        MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
        MULLINS, MULLINS, MULLINS, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
        KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
        KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
        KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
        HAWAII, HAWAII, HAWAII, HAWAII, HAWAII
[    21.902] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    21.902] (II) FBDEV: driver for framebuffer: fbdev
[    21.902] (II) VESA: driver for VESA chipsets: vesa
[    21.902] (++) using VT number 7


[    21.911] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20141121
[    21.911] (II) intel(0): SNA compiled: xserver-xorg-video-intel-lts-vivid 2:2.99.917-1~exp1ubuntu2.2~trusty1 (Timo Aaltonen <tjaalton@debian.org>)
[    21.911] (II) intel(0): SNA compiled for use with valgrind
[    21.913] (II) [KMS] Kernel modesetting enabled.
[    21.913] (WW) Falling back to old probe method for modesetting
[    21.913] (WW) Falling back to old probe method for fbdev
[    21.913] (II) Loading sub module "fbdevhw"
[    21.913] (II) LoadModule: "fbdevhw"
[    21.913] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.919] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.919]    compiled for 1.17.1, module version = 0.0.2
[    21.919]    ABI class: X.Org Video Driver, version 19.0
[    21.919] (WW) Falling back to old probe method for vesa
[    21.920] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4000
[    21.920] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[    21.920] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    21.920] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    21.920] (==) intel(0): RGB weight 888
[    21.920] (==) intel(0): Default visual is TrueColor
[    21.920] (II) intel(0): Output LVDS1 has no monitor section
[    21.920] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output LVDS1
[    21.920] (II) intel(0): Enabled output LVDS1
[    21.920] (II) intel(0): Output VGA1 has no monitor section
[    21.920] (II) intel(0): Enabled output VGA1
[    21.920] (II) intel(0): Output HDMI1 has no monitor section
[    21.920] (II) intel(0): Enabled output HDMI1
[    21.920] (II) intel(0): Output DP1 has no monitor section
[    21.920] (II) intel(0): Enabled output DP1
[    21.920] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    21.920] (II) intel(0): Output VIRTUAL1 has no monitor section
[    21.920] (II) intel(0): Enabled output VIRTUAL1
[    21.920] (--) intel(0): Output LVDS1 using initial mode 1366x768 on pipe 0
[    21.920] (==) intel(0): TearFree disabled
[    21.920] (==) intel(0): DPI set to (96, 96)
[    21.920] (II) Loading sub module "dri2"
[    21.920] (II) LoadModule: "dri2"
[    21.920] (II) Module "dri2" already built-in
[    21.920] (II) Loading sub module "present"
[    21.921] (II) LoadModule: "present"
[    21.921] (II) Module "present" already built-in
[    21.921] (==) RADEON(G0): Depth 24, (--) framebuffer bpp 32
[    21.921] (II) RADEON(G0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    21.921] (==) RADEON(G0): Default visual is TrueColor
[    21.921] (==) RADEON(G0): RGB weight 888
[    21.921] (II) RADEON(G0): Using 8 bits per RGB (8 bit DAC)
[    21.921] (--) RADEON(G0): Chipset: "HAINAN" (ChipID = 0x6663)
[    21.921] (II) Loading sub module "dri2"
[    21.921] (II) LoadModule: "dri2"
[    21.921] (II) Module "dri2" already built-in
[    21.921] (II) Loading sub module "glamoregl"
[    21.921] (II) LoadModule: "glamoregl"
[    21.921] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    21.977] (II) Module glamoregl: vendor="X.Org Foundation"
[    21.977]    compiled for 1.17.1, module version = 1.0.0
[    21.977]    ABI class: X.Org ANSI C Emulation, version 0.4
[    21.977] (II) glamor: OpenGL accelerated X.org driver based.
[    22.646] (II) glamor: EGL version 1.4 (DRI2):
[    22.698] (II) RADEON(G0): glamor detected, initialising EGL layer.
[    22.698] (II) RADEON(G0): KMS Color Tiling: enabled
[    22.698] (II) RADEON(G0): KMS Color Tiling 2D: enabled
[    22.698] (II) RADEON(G0): KMS Pageflipping: enabled
[    22.698] (II) RADEON(G0): SwapBuffers wait for vsync: enabled
[    22.698] (II) RADEON(G0): mem size init: gart size :3fbcf000 vram size: s:80000000 visible:7fabe000
[    22.698] (==) RADEON(G0): DPI set to (96, 96)
[    22.698] (II) Loading sub module "fb"
[    22.698] (II) LoadModule: "fb"
[    22.698] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.698] (II) Module fb: vendor="X.Org Foundation"
[    22.698]    compiled for 1.17.1, module version = 1.0.0
[    22.698]    ABI class: X.Org ANSI C Emulation, version 0.4
[    22.698] (==) RADEON(G0): Using gamma correction (1.0, 1.0, 1.0)
[    22.698] (II) Loading sub module "ramdac"
[    22.698] (II) LoadModule: "ramdac"
[    22.698] (II) Module "ramdac" already built-in
[    22.698] (II) UnloadModule: "modesetting"
[    22.698] (II) Unloading modesetting
[    22.698] (II) UnloadModule: "fbdev"
[    22.698] (II) Unloading fbdev
[    22.698] (II) UnloadSubModule: "fbdevhw"
[    22.698] (II) Unloading fbdevhw
[    22.698] (II) UnloadModule: "vesa"
[    22.698] (II) Unloading vesa
[    22.698] (==) Depth 24 pixmap format is 32 bpp
[    22.699] (II) RADEON(G0): [DRI2] Setup complete
[    22.699] (II) RADEON(G0): [DRI2]   DRI driver: radeonsi
[    22.699] (II) RADEON(G0): [DRI2]   VDPAU driver: radeonsi
[    22.699] (II) RADEON(G0): Front buffer size: 3072K
[    22.699] (II) RADEON(G0): VRAM usage limit set to 1879826K
[    22.699] (==) RADEON(G0): Backing store enabled
[    22.699] (II) RADEON(G0): Direct rendering enabled
[    22.762] (II) RADEON(G0): Use GLAMOR acceleration.
[    22.762] (II) RADEON(G0): Acceleration enabled
[    22.762] (==) RADEON(G0): DPMS enabled
[    22.762] (==) RADEON(G0): Silken mouse enabled
[    22.762] (II) RADEON(G0): Set up textured video (glamor)
[    22.762] (II) RADEON(G0): [XvMC] Associated with GLAMOR Textured Video.
[    22.762] (EE) RADEON(G0): [XvMC] Failed to initialize extension.
[    22.762] (II) RADEON(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    22.791] (II) intel(0): SNA initialized with Ivybridge (gen7, gt2) backend
[    22.791] (==) intel(0): Backing store enabled
[    22.791] (==) intel(0): Silken mouse enabled
[    22.791] (II) intel(0): HW Cursor enabled
[    22.791] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    22.791] (==) intel(0): DPMS enabled
[    22.792] (==) intel(0): display hotplug detection enabled
[    22.792] (II) intel(0): [DRI2] Setup complete
[    22.792] (II) intel(0): [DRI2]   DRI driver: i965
[    22.792] (II) intel(0): [DRI2]   VDPAU driver: i965
[    22.792] (II) intel(0): direct rendering: DRI2 enabled
[    22.792] (II) intel(0): hardware support for Present enabled
[    22.792] (--) RandR disabled
[    22.927] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    22.927] (II) AIGLX: enabled GLX_ARB_create_context
[    22.927] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    22.927] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    22.927] (II) AIGLX: enabled GLX_INTEL_swap_event
[    22.927] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    22.927] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    22.927] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    22.927] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    22.927] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    22.927] (II) AIGLX: Loaded and initialized i965
[    22.927] (II) GLX: Initialized DRI2 GL provider for screen 0
[    23.272] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    23.288] (II) intel(0): Setting screen physical size to 361 x 203
[    23.392] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.439] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    23.439] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.439] (II) LoadModule: "evdev"
[    23.439] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.475] (II) Module evdev: vendor="X.Org Foundation"
[    23.475]    compiled for 1.17.1, module version = 2.9.0
[    23.475]    Module class: X.Org XInput Driver
[    23.475]    ABI class: X.Org XInput driver, version 21.0
[    23.475] (II) Using input driver 'evdev' for 'Power Button'
[    23.475] (**) Power Button: always reports core events
[    23.475] (**) evdev: Power Button: Device: "/dev/input/event2"
[    23.475] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.475] (--) evdev: Power Button: Found keys
[    23.475] (II) evdev: Power Button: Configuring as keyboard
[    23.475] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    23.475] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    23.475] (**) Option "xkb_rules" "evdev"
[    23.475] (**) Option "xkb_model" "pc105"
[    23.475] (**) Option "xkb_layout" "gb"
[    23.477] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    23.478] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    23.478] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    23.478] (II) Using input driver 'evdev' for 'Video Bus'
[    23.478] (**) Video Bus: always reports core events
[    23.478] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    23.478] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    23.478] (--) evdev: Video Bus: Found keys
[    23.478] (II) evdev: Video Bus: Configuring as keyboard
[    23.478] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:03/input/input7/event5"
[    23.478] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    23.478] (**) Option "xkb_rules" "evdev"
[    23.478] (**) Option "xkb_model" "pc105"
[    23.478] (**) Option "xkb_layout" "gb"
[    23.479] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    23.479] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.479] (II) Using input driver 'evdev' for 'Power Button'
[    23.479] (**) Power Button: always reports core events
[    23.479] (**) evdev: Power Button: Device: "/dev/input/event0"
[    23.479] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.479] (--) evdev: Power Button: Found keys
[    23.479] (II) evdev: Power Button: Configuring as keyboard
[    23.479] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0/event0"
[    23.479] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    23.479] (**) Option "xkb_rules" "evdev"
[    23.479] (**) Option "xkb_model" "pc105"
[    23.479] (**) Option "xkb_layout" "gb"
[    23.479] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    23.479] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    23.479] (II) Using input driver 'evdev' for 'Video Bus'
[    23.479] (**) Video Bus: always reports core events
[    23.479] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    23.479] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    23.479] (--) evdev: Video Bus: Found keys
[    23.479] (II) evdev: Video Bus: Configuring as keyboard
[    23.479] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:35/LNXVIDEO:00/input/input6/event4"
[    23.479] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 9)
[    23.479] (**) Option "xkb_rules" "evdev"
[    23.479] (**) Option "xkb_model" "pc105"
[    23.480] (**) Option "xkb_layout" "gb"
[    23.480] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    23.480] (II) No input driver specified, ignoring this device.
[    23.480] (II) This device may have been added with another device file.
[    23.480] (II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event11)
[    23.480] (**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
[    23.480] (II) Using input driver 'evdev' for 'Lenovo EasyCamera'
[    23.480] (**) Lenovo EasyCamera: always reports core events
[    23.480] (**) evdev: Lenovo EasyCamera: Device: "/dev/input/event11"
[    23.480] (--) evdev: Lenovo EasyCamera: Vendor 0xbda Product 0x5728
[    23.480] (--) evdev: Lenovo EasyCamera: Found keys
[    23.481] (II) evdev: Lenovo EasyCamera: Configuring as keyboard
[    23.481] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/input/input12/event11"
[    23.481] (II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 10)
[    23.481] (**) Option "xkb_rules" "evdev"
[    23.481] (**) Option "xkb_model" "pc105"
[    23.481] (**) Option "xkb_layout" "gb"
[    23.481] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event9)
[    23.481] (II) No input driver specified, ignoring this device.
[    23.481] (II) This device may have been added with another device file.
[    23.481] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event10)
[    23.481] (II) No input driver specified, ignoring this device.
[    23.481] (II) This device may have been added with another device file.
[    23.481] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event8)
[    23.481] (II) No input driver specified, ignoring this device.
[    23.481] (II) This device may have been added with another device file.
[    23.482] (II) config/udev: Adding input device Ideapad extra buttons (/dev/input/event7)
[    23.482] (**) Ideapad extra buttons: Applying InputClass "evdev keyboard catchall"
[    23.482] (II) Using input driver 'evdev' for 'Ideapad extra buttons'
[    23.482] (**) Ideapad extra buttons: always reports core events
[    23.482] (**) evdev: Ideapad extra buttons: Device: "/dev/input/event7"
[    23.482] (--) evdev: Ideapad extra buttons: Vendor 0 Product 0
[    23.482] (--) evdev: Ideapad extra buttons: Found keys
[    23.482] (II) evdev: Ideapad extra buttons: Configuring as keyboard
[    23.482] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1f.0/PNP0C09:00/VPC2004:00/input/input8/event7"
[    23.482] (II) XINPUT: Adding extended input device "Ideapad extra buttons" (type: KEYBOARD, id 11)
[    23.482] (**) Option "xkb_rules" "evdev"
[    23.482] (**) Option "xkb_model" "pc105"
[    23.482] (**) Option "xkb_layout" "gb"
[    23.482] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    23.482] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    23.482] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    23.482] (**) AT Translated Set 2 keyboard: always reports core events
[    23.482] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    23.482] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    23.482] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    23.482] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    23.482] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    23.482] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    23.482] (**) Option "xkb_rules" "evdev"
[    23.482] (**) Option "xkb_model" "pc105"
[    23.482] (**) Option "xkb_layout" "gb"
[    23.483] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[    23.483] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    23.483] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    23.483] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    23.483] (II) LoadModule: "synaptics"
[    23.483] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    23.483] (II) Module synaptics: vendor="X.Org Foundation"
[    23.483]    compiled for 1.17.1, module version = 1.8.99
[    23.483]    Module class: X.Org XInput Driver
[    23.483]    ABI class: X.Org XInput driver, version 21.0
[    23.483] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    23.483] (**) ETPS/2 Elantech Touchpad: always reports core events
[    23.483] (**) Option "Device" "/dev/input/event6"
[    23.492] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2940 (res 0)
[    23.492] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1260 (res 0)
[    23.492] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    23.492] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    23.492] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    23.492] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    23.492] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    23.492] (**) ETPS/2 Elantech Touchpad: always reports core events
[    23.504] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event6"
[    23.504] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 13)
[    23.504] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    23.504] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    23.504] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.063
[    23.504] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    23.504] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    23.504] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    23.504] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    23.504] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    23.505] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    23.505] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    38.764] reporting 4 5 1 8
[    39.004] reporting 4 5 1 8
[    42.637] (II) intel(0): EDID vendor "LGD", prod id 826
[    42.638] (II) intel(0): Printing DDC gathered Modelines:
[    42.638] (II) intel(0): Modeline "1366x768"x0.0   70.00  1366 1402 1450 1492  768 771 776 782 -hsync -vsync (46.9 kHz eP)
[    42.640] reporting 4 5 7 53
[    42.640] reporting 4 5 7 53
[    42.735] reporting 4 5 7 53
[    42.735] reporting 4 5 7 53
[    42.735] reporting 4 5 7 53
[    42.735] reporting 4 5 7 53
[    42.735] reporting 4 5 7 53
[    42.735] reporting 4 5 7 53
[    42.735] reporting 4 5 7 53
[    42.736] reporting 4 5 7 53
[    42.736] reporting 4 5 7 53
[    42.736] reporting 4 5 7 53
[    42.736] reporting 4 5 7 53
[    42.736] reporting 4 5 7 53
[    42.736] reporting 4 5 7 53
[    42.931] reporting 4 5 7 53
[    42.931] reporting 4 5 7 53
[    42.931] reporting 4 5 7 53
[    42.931] reporting 4 5 7 53
[    42.931] reporting 4 5 7 53
[    42.931] reporting 4 5 7 53
[    42.931] reporting 4 5 7 53
[    43.544] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AA2FC318445DE966DF48706BBC15B7668547E20.xkm
[    44.399] reporting 4 5 7 53
[    45.124] reporting 4 5 7 53
[    45.124] reporting 4 5 7 53
[    45.124] reporting 4 5 7 53
[    45.124] reporting 4 5 7 53
[    45.124] reporting 4 5 7 53
[    45.124] reporting 4 5 7 53
[    45.124] reporting 4 5 7 53
[    45.124] reporting 4 5 7 53
[    45.125] reporting 4 5 7 53
[    45.125] reporting 4 5 7 53
[    45.125] reporting 4 5 7 53
[    45.125] reporting 4 5 7 53
[    45.170] reporting 4 5 7 53
[    45.170] reporting 4 5 7 53
[    45.170] reporting 4 5 7 53
[    45.170] reporting 4 5 7 53
[    45.170] reporting 4 5 7 53
[    45.170] reporting 4 5 7 53
[    45.171] reporting 4 5 7 53
[    45.172] reporting 4 5 7 53
[    45.173] reporting 4 5 7 53
[    45.173] reporting 4 5 7 53
[    45.173] reporting 4 5 7 53
[    45.173] reporting 4 5 7 53
[    45.173] reporting 4 5 7 53
[    45.173] reporting 4 5 7 53
[    45.173] reporting 4 5 7 53
[    45.173] reporting 4 5 7 53
[    45.173] reporting 4 5 7 53
[    45.173] reporting 4 5 7 53
[    45.174] reporting 4 5 7 53
[    45.174] reporting 4 5 7 53
[    45.174] reporting 4 5 7 53
[    45.184] reporting 4 5 7 53
[    45.184] reporting 4 5 7 53
[    45.185] reporting 4 5 7 53
[    45.185] reporting 4 5 7 53
[    45.185] reporting 4 5 7 53
[    45.185] reporting 4 5 7 53
[    45.185] reporting 4 5 7 53
[    45.185] reporting 4 5 7 53
[    45.185] reporting 4 5 7 53
[    45.186] reporting 4 5 7 53
[    45.186] reporting 4 5 7 53
[    45.186] reporting 4 5 7 53
[    45.186] reporting 4 5 7 53
[    45.186] reporting 4 5 7 53
[    45.186] reporting 4 5 7 53
[    45.186] reporting 4 5 7 53
[    45.186] reporting 4 5 7 53
[    45.186] reporting 4 5 7 53
[    45.186] reporting 4 5 7 53
[    45.186] reporting 4 5 7 53
[    45.186] reporting 4 5 7 53
[    45.186] reporting 4 5 7 53
[    45.187] reporting 4 5 7 53
[    45.187] reporting 4 5 7 53
[    45.187] reporting 4 5 7 53
[    45.187] reporting 4 5 7 53
[    45.187] reporting 4 5 7 53
[    45.187] reporting 4 5 7 53
[    45.187] reporting 4 5 7 53
[    45.202] reporting 4 5 7 53
[    45.202] reporting 4 5 7 53
[    63.299] reporting 4 5 7 53
[    81.722] reporting 4 5 7 53
[    81.722] reporting 4 5 7 53
[    83.204] reporting 4 5 7 53
[    83.207] reporting 4 5 7 53

```

By the way, thank you for all your support by now.

---

### Post by Bashing-om on 2015-11-09
stefanoskikristijan; sheesshh ... OK !

Still stuck:
> 
21.851] (WW) Warning, couldn't open module fglrx

Let's rebuild:
```

sudo apt update
sudo apt upgrade
sudo update-alternatives --set x86_64-linux-gnu_gl_conf /usr/lib/fglrx/ld.so.conf
sudo ldconfig -n

sudo update-initramfs -u

```

reboot and show a new xorg log file.

[INDENT][INDENT]maybe now we can build 
[/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-09
> **Bashing-om said:**
> stefanoskikristijan; sheesshh ... OK !

Still stuck:

Let's rebuild:
```

sudo apt update
sudo apt upgrade
sudo update-alternatives --set x86_64-linux-gnu_gl_conf /usr/lib/fglrx/ld.so.conf
sudo ldconfig -n

sudo update-initramfs -u

```

reboot and show a new xorg log file.
[INDENT][INDENT]maybe now we can build 
[/INDENT]
[/INDENT]


hmm i get this sort of error:
```

sudo update-alternatives --set x86_64-linux-gnu_gl_conf /usr/lib/fglrx/ld.so.conf
update-alternatives: error: alternative /usr/lib/fglrx/ld.so.conf for x86_64-linux-gnu_gl_conf not registered; not setting



```

---

### Post by Bashing-om on 2015-11-09
stefanoskikristijan; Well,

At least that is something ! 
Think'n

[INDENT][INDENT]I will be back
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-11-09
stefanoskikristijan; Humm .....

While I am stuttering, do we have the headers installed to build any package ?
```

dpkg -l linux-headers-generic
dpkg -l linux-headers-$(uname -r)

```

[INDENT][INDENT]just dotting i's
[/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-09
> **Bashing-om said:**
> stefanoskikristijan; Humm .....

While I am stuttering, do we have the headers installed to build any package ?
```

dpkg -l linux-headers-generic
dpkg -l linux-headers-$(uname -r)

```
[INDENT][INDENT]just dotting i's
[/INDENT]
[/INDENT]


Yes, we are good to go...
```

user@user:~$ dpkg -l linux-headers-generic
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                    Version          Architecture     Description
+++-=======================-================-================-===================================================
ii  linux-headers-generic   3.13.0.67.73     amd64            Generic Linux kernel headers
user@user:~$ dpkg -l linux-headers-$(uname -r)
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                    Version          Architecture     Description
+++-=======================-================-================-===================================================
ii  linux-headers-3.19.0-32 3.19.0-32.37~14. amd64            Linux kernel headers for version 3.19.0 on 64 bit x

```

---

### Post by stefanoskikristijan on 2015-11-10
Ok newest info:
I sucessfuly made a fresh install of Ubuntu Mate 15.10 and finally got to install FGLRX without running in BLACK SCREEN(low graphic mode) ! 
```

dpkg -l | grep fglrx
ii  fglrx                                       2:15.201-0ubuntu1                          amd64        Video driver for the AMD graphics accelerators
ii  fglrx-amdcccle                              2:15.201-0ubuntu1                          amd64        Catalyst Control Center for the AMD graphics accelerators
ii  fglrx-core                                  2:15.201-0ubuntu1                          amd64        Minimal video driver for the AMD graphics accelerators

```

But now the only problem is that i cannot start catalyst because i get this massage:
 [B]There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
[/B]**No AMD graphics driver is installed, or the AMD driver is not functioning properly.**
[B]Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.

[/B]Latest LOG:
```

 cat /var/log/Xorg.0.log
[    19.835] 
X.Org X Server 1.17.2
Release Date: 2015-06-16
[    19.835] X Protocol Version 11, Revision 0
[    19.835] Build Operating System: Linux 3.19.0-30-generic x86_64 Ubuntu
[    19.835] Current Operating System: Linux Kristijan-Lenovo-G500 4.2.0-18-generic #22-Ubuntu SMP Fri Nov 6 18:25:50 UTC 2015 x86_64
[    19.835] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-18-generic.efi.signed root=UUID=1536bfd3-dae8-40d1-ab69-241c9a53dc85 ro quiet splash vt.handoff=7
[    19.835] Build Date: 30 September 2015  09:08:47AM
[    19.835] xorg-server 2:1.17.2-1ubuntu9 (For technical support please see http://www.ubuntu.com/support) 
[    19.835] Current version of pixman: 0.32.6
[    19.835]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    19.835] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.835] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 10 12:12:01 2015
[    19.893] (==) Using config file: "/etc/X11/xorg.conf"
[    19.893] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.943] (==) No Layout section.  Using the first Screen section.
[    19.943] (==) No screen section available. Using defaults.
[    19.943] (**) |-->Screen "Default Screen Section" (0)
[    19.943] (**) |   |-->Monitor "<default monitor>"
[    19.943] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    19.943] (**) |   |-->Device "Default Card 0"
[    19.943] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    19.943] (==) Automatically adding devices
[    19.943] (==) Automatically enabling devices
[    19.943] (==) Automatically adding GPU devices
[    19.953] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.953]     Entry deleted from font path.
[    19.953] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.953]     Entry deleted from font path.
[    19.953] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.953]     Entry deleted from font path.
[    19.957] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.957]     Entry deleted from font path.
[    19.957] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.957]     Entry deleted from font path.
[    19.957] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    19.957] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.957] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.964] (II) Loader magic: 0x561916157d40
[    19.964] (II) Module ABI versions:
[    19.964]     X.Org ANSI C Emulation: 0.4
[    19.964]     X.Org Video Driver: 19.0
[    19.964]     X.Org XInput driver : 21.0
[    19.964]     X.Org Server Extension : 9.0
[    19.965] (II) xfree86: Adding drm device (/dev/dri/card1)
[    19.965] (II) xfree86: Adding drm device (/dev/dri/card0)
[    19.967] (--) PCI:*(0:0:2:0) 8086:0166:17aa:3800 rev 9, Mem @ 0xd8000000/4194304, 0xc0000000/268435456, I/O @ 0x00004000/64
[    19.967] (--) PCI: (0:1:0:0) 1002:6663:17aa:3800 rev 0, Mem @ 0xd0000000/134217728, 0xd8600000/262144, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[    19.968] (II) LoadModule: "glx"
[    19.994] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.104] (II) Module glx: vendor="X.Org Foundation"
[    20.104]     compiled for 1.17.2, module version = 1.0.0
[    20.104]     ABI class: X.Org Server Extension, version 9.0
[    20.104] (==) AIGLX enabled
[    20.104] (==) Matched intel as autoconfigured driver 0
[    20.104] (==) Matched fglrx as autoconfigured driver 1
[    20.104] (==) Matched ati as autoconfigured driver 2
[    20.104] (==) Matched intel as autoconfigured driver 3
[    20.104] (==) Matched modesetting as autoconfigured driver 4
[    20.104] (==) Matched fbdev as autoconfigured driver 5
[    20.104] (==) Matched vesa as autoconfigured driver 6
[    20.104] (==) Assigned the driver to the xf86ConfigLayout
[    20.104] (II) LoadModule: "intel"
[    20.104] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    20.218] (II) Module intel: vendor="X.Org Foundation"
[    20.218]     compiled for 1.17.2, module version = 2.99.917
[    20.218]     Module class: X.Org Video Driver
[    20.218]     ABI class: X.Org Video Driver, version 19.0
[    20.218] (II) LoadModule: "fglrx"
[    20.218] (WW) Warning, couldn't open module fglrx
[    20.218] (II) UnloadModule: "fglrx"
[    20.219] (II) Unloading fglrx
[    20.219] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    20.219] (II) LoadModule: "ati"
[    20.219] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    20.246] (II) Module ati: vendor="X.Org Foundation"
[    20.246]     compiled for 1.17.2, module version = 7.5.99
[    20.246]     Module class: X.Org Video Driver
[    20.246]     ABI class: X.Org Video Driver, version 19.0
[    20.246] (II) LoadModule: "modesetting"
[    20.247] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    20.265] (II) Module modesetting: vendor="X.Org Foundation"
[    20.265]     compiled for 1.17.2, module version = 1.17.2
[    20.265]     Module class: X.Org Video Driver
[    20.265]     ABI class: X.Org Video Driver, version 19.0
[    20.265] (II) LoadModule: "fbdev"
[    20.265] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.265] (II) Module fbdev: vendor="X.Org Foundation"
[    20.265]     compiled for 1.17.1, module version = 0.4.4
[    20.265]     Module class: X.Org Video Driver
[    20.265]     ABI class: X.Org Video Driver, version 19.0
[    20.265] (II) LoadModule: "vesa"
[    20.265] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.272] (II) Module vesa: vendor="X.Org Foundation"
[    20.272]     compiled for 1.17.1, module version = 2.3.4
[    20.272]     Module class: X.Org Video Driver
[    20.272]     ABI class: X.Org Video Driver, version 19.0
[    20.272] (==) Matched intel as autoconfigured driver 0
[    20.272] (==) Matched fglrx as autoconfigured driver 1
[    20.272] (==) Matched ati as autoconfigured driver 2
[    20.272] (==) Matched intel as autoconfigured driver 3
[    20.272] (==) Matched modesetting as autoconfigured driver 4
[    20.272] (==) Matched fbdev as autoconfigured driver 5
[    20.272] (==) Matched vesa as autoconfigured driver 6
[    20.272] (==) Assigned the driver to the xf86ConfigLayout
[    20.272] (II) LoadModule: "intel"
[    20.273] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    20.273] (II) Module intel: vendor="X.Org Foundation"
[    20.273]     compiled for 1.17.2, module version = 2.99.917
[    20.273]     Module class: X.Org Video Driver
[    20.273]     ABI class: X.Org Video Driver, version 19.0
[    20.273] (II) UnloadModule: "intel"
[    20.273] (II) Unloading intel
[    20.273] (II) Failed to load module "intel" (already loaded, 22041)
[    20.273] (II) LoadModule: "fglrx"
[    20.273] (WW) Warning, couldn't open module fglrx
[    20.273] (II) UnloadModule: "fglrx"
[    20.273] (II) Unloading fglrx
[    20.273] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    20.273] (II) LoadModule: "ati"
[    20.273] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    20.273] (II) Module ati: vendor="X.Org Foundation"
[    20.273]     compiled for 1.17.2, module version = 7.5.99
[    20.273]     Module class: X.Org Video Driver
[    20.273]     ABI class: X.Org Video Driver, version 19.0
[    20.273] (II) LoadModule: "modesetting"
[    20.273] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    20.273] (II) Module modesetting: vendor="X.Org Foundation"
[    20.273]     compiled for 1.17.2, module version = 1.17.2
[    20.273]     Module class: X.Org Video Driver
[    20.273]     ABI class: X.Org Video Driver, version 19.0
[    20.273] (II) UnloadModule: "modesetting"
[    20.273] (II) Unloading modesetting
[    20.273] (II) Failed to load module "modesetting" (already loaded, 0)
[    20.273] (II) LoadModule: "fbdev"
[    20.273] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.273] (II) Module fbdev: vendor="X.Org Foundation"
[    20.273]     compiled for 1.17.1, module version = 0.4.4
[    20.273]     Module class: X.Org Video Driver
[    20.273]     ABI class: X.Org Video Driver, version 19.0
[    20.273] (II) UnloadModule: "fbdev"
[    20.273] (II) Unloading fbdev
[    20.273] (II) Failed to load module "fbdev" (already loaded, 0)
[    20.273] (II) LoadModule: "vesa"
[    20.274] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.274] (II) Module vesa: vendor="X.Org Foundation"
[    20.274]     compiled for 1.17.1, module version = 2.3.4
[    20.274]     Module class: X.Org Video Driver
[    20.274]     ABI class: X.Org Video Driver, version 19.0
[    20.274] (II) UnloadModule: "vesa"
[    20.274] (II) Unloading vesa
[    20.274] (II) Failed to load module "vesa" (already loaded, 0)
[    20.274] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    20.274] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    20.274] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    20.274] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    20.274] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    20.274] (II) FBDEV: driver for framebuffer: fbdev
[    20.274] (II) VESA: driver for VESA chipsets: vesa
[    20.274] (++) using VT number 7

[    20.274] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20150522
[    20.274] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150808-0ubuntu4 (Robert Ancell <robert.ancell@canonical.com>)
[    20.274] (II) intel(0): SNA compiled for use with valgrind
[    20.280] (WW) Falling back to old probe method for modesetting
[    20.280] (WW) Falling back to old probe method for fbdev
[    20.280] (II) Loading sub module "fbdevhw"
[    20.280] (II) LoadModule: "fbdevhw"
[    20.280] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.287] (II) Module fbdevhw: vendor="X.Org Foundation"
[    20.287]     compiled for 1.17.2, module version = 0.0.2
[    20.287]     ABI class: X.Org Video Driver, version 19.0
[    20.287] (WW) Falling back to old probe method for vesa
[    20.288] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4000
[    20.288] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx; using a maximum of 2 threads
[    20.288] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    20.288] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    20.288] (==) intel(0): RGB weight 888
[    20.288] (==) intel(0): Default visual is TrueColor
[    20.288] (II) intel(0): Output LVDS1 has no monitor section
[    20.300] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output LVDS1
[    20.300] (II) intel(0): Enabled output LVDS1
[    20.300] (II) intel(0): Output VGA1 has no monitor section
[    20.300] (II) intel(0): Enabled output VGA1
[    20.300] (II) intel(0): Output HDMI1 has no monitor section
[    20.300] (II) intel(0): Enabled output HDMI1
[    20.300] (II) intel(0): Output DP1 has no monitor section
[    20.300] (II) intel(0): Enabled output DP1
[    20.300] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    20.300] (II) intel(0): Output VIRTUAL1 has no monitor section
[    20.300] (II) intel(0): Enabled output VIRTUAL1
[    20.300] (--) intel(0): Output LVDS1 using initial mode 1366x768 on pipe 0
[    20.300] (==) intel(0): TearFree disabled
[    20.300] (==) intel(0): DPI set to (96, 96)
[    20.300] (II) Loading sub module "dri2"
[    20.300] (II) LoadModule: "dri2"
[    20.300] (II) Module "dri2" already built-in
[    20.300] (II) Loading sub module "present"
[    20.300] (II) LoadModule: "present"
[    20.300] (II) Module "present" already built-in
[    20.300] (II) UnloadModule: "fbdev"
[    20.300] (II) Unloading fbdev
[    20.300] (II) UnloadSubModule: "fbdevhw"
[    20.300] (II) Unloading fbdevhw
[    20.300] (II) UnloadModule: "vesa"
[    20.300] (II) Unloading vesa
[    20.300] (==) Depth 24 pixmap format is 32 bpp
[    20.360] (II) intel(0): SNA initialized with Ivybridge (gen7, gt2) backend
[    20.360] (==) intel(0): Backing store enabled
[    20.360] (==) intel(0): Silken mouse enabled
[    20.361] (II) intel(0): HW Cursor enabled
[    20.361] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    20.361] (==) intel(0): DPMS enabled
[    20.362] (==) intel(0): Display hotplug detection enabled
[    20.362] (II) intel(0): [DRI2] Setup complete
[    20.362] (II) intel(0): [DRI2]   DRI driver: i965
[    20.362] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    20.362] (II) intel(0): direct rendering: DRI2 enabled
[    20.362] (II) intel(0): hardware support for Present enabled
[    20.362] (--) RandR disabled
[    20.370] (II) SELinux: Disabled on system
[    20.698] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    20.698] (II) AIGLX: enabled GLX_ARB_create_context
[    20.698] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    20.698] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    20.698] (II) AIGLX: enabled GLX_INTEL_swap_event
[    20.698] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    20.698] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    20.698] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    20.698] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    20.698] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    20.698] (II) AIGLX: Loaded and initialized i965
[    20.698] (II) GLX: Initialized DRI2 GL provider for screen 0
[    20.701] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    20.701] (II) intel(0): Setting screen physical size to 361 x 203
[    20.824] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.851] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    20.851] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.851] (**) Power Button: Applying InputClass "keyboard defaults"
[    20.851] (II) LoadModule: "evdev"
[    20.851] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.980] (II) Module evdev: vendor="X.Org Foundation"
[    20.980]     compiled for 1.17.1, module version = 2.9.2
[    20.980]     Module class: X.Org XInput Driver
[    20.980]     ABI class: X.Org XInput driver, version 21.0
[    20.980] (II) Using input driver 'evdev' for 'Power Button'
[    20.980] (**) Power Button: always reports core events
[    20.980] (**) evdev: Power Button: Device: "/dev/input/event2"
[    20.981] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.981] (--) evdev: Power Button: Found keys
[    20.981] (II) evdev: Power Button: Configuring as keyboard
[    20.981] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    20.981] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    20.981] (**) Option "xkb_rules" "evdev"
[    20.981] (**) Option "xkb_model" "pc105"
[    20.981] (**) Option "xkb_layout" "gb"
[    20.981] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    20.983] (II) XKB: reuse xkmfile /var/lib/xkb/server-7996F6726817F73651B9DE0FDA11E35FC4524568.xkm
[    20.984] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    20.984] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    20.984] (**) Video Bus: Applying InputClass "keyboard defaults"
[    20.984] (II) Using input driver 'evdev' for 'Video Bus'
[    20.984] (**) Video Bus: always reports core events
[    20.984] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    20.984] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    20.984] (--) evdev: Video Bus: Found keys
[    20.984] (II) evdev: Video Bus: Configuring as keyboard
[    20.984] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:03/input/input8/event5"
[    20.984] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    20.984] (**) Option "xkb_rules" "evdev"
[    20.984] (**) Option "xkb_model" "pc105"
[    20.984] (**) Option "xkb_layout" "gb"
[    20.984] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    20.985] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    20.985] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.985] (**) Power Button: Applying InputClass "keyboard defaults"
[    20.985] (II) Using input driver 'evdev' for 'Power Button'
[    20.985] (**) Power Button: always reports core events
[    20.985] (**) evdev: Power Button: Device: "/dev/input/event0"
[    20.985] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.985] (--) evdev: Power Button: Found keys
[    20.985] (II) evdev: Power Button: Configuring as keyboard
[    20.985] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0/event0"
[    20.985] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    20.985] (**) Option "xkb_rules" "evdev"
[    20.985] (**) Option "xkb_model" "pc105"
[    20.985] (**) Option "xkb_layout" "gb"
[    20.985] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    20.985] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    20.985] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    20.985] (**) Video Bus: Applying InputClass "keyboard defaults"
[    20.985] (II) Using input driver 'evdev' for 'Video Bus'
[    20.985] (**) Video Bus: always reports core events
[    20.985] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    20.985] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    20.985] (--) evdev: Video Bus: Found keys
[    20.986] (II) evdev: Video Bus: Configuring as keyboard
[    20.986] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:35/LNXVIDEO:00/input/input7/event4"
[    20.986] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 9)
[    20.986] (**) Option "xkb_rules" "evdev"
[    20.986] (**) Option "xkb_model" "pc105"
[    20.986] (**) Option "xkb_layout" "gb"
[    20.986] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    20.986] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    20.986] (II) No input driver specified, ignoring this device.
[    20.986] (II) This device may have been added with another device file.
[    20.987] (II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event11)
[    20.987] (**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
[    20.987] (**) Lenovo EasyCamera: Applying InputClass "keyboard defaults"
[    20.987] (II) Using input driver 'evdev' for 'Lenovo EasyCamera'
[    20.987] (**) Lenovo EasyCamera: always reports core events
[    20.987] (**) evdev: Lenovo EasyCamera: Device: "/dev/input/event11"
[    20.987] (--) evdev: Lenovo EasyCamera: Vendor 0xbda Product 0x5728
[    20.987] (--) evdev: Lenovo EasyCamera: Found keys
[    20.987] (II) evdev: Lenovo EasyCamera: Configuring as keyboard
[    20.987] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/input/input13/event11"
[    20.987] (II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 10)
[    20.987] (**) Option "xkb_rules" "evdev"
[    20.987] (**) Option "xkb_model" "pc105"
[    20.987] (**) Option "xkb_layout" "gb"
[    20.987] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    20.987] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event8)
[    20.987] (II) No input driver specified, ignoring this device.
[    20.987] (II) This device may have been added with another device file.
[    20.988] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[    20.988] (II) No input driver specified, ignoring this device.
[    20.988] (II) This device may have been added with another device file.
[    20.988] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event7)
[    20.988] (II) No input driver specified, ignoring this device.
[    20.988] (II) This device may have been added with another device file.
[    20.989] (II) config/udev: Adding input device Ideapad extra buttons (/dev/input/event10)
[    20.989] (**) Ideapad extra buttons: Applying InputClass "evdev keyboard catchall"
[    20.989] (**) Ideapad extra buttons: Applying InputClass "keyboard defaults"
[    20.989] (II) Using input driver 'evdev' for 'Ideapad extra buttons'
[    20.989] (**) Ideapad extra buttons: always reports core events
[    20.989] (**) evdev: Ideapad extra buttons: Device: "/dev/input/event10"
[    20.989] (--) evdev: Ideapad extra buttons: Vendor 0 Product 0
[    20.989] (--) evdev: Ideapad extra buttons: Found keys
[    20.989] (II) evdev: Ideapad extra buttons: Configuring as keyboard
[    20.989] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1f.0/PNP0C09:00/VPC2004:00/input/input12/event10"
[    20.989] (II) XINPUT: Adding extended input device "Ideapad extra buttons" (type: KEYBOARD, id 11)
[    20.989] (**) Option "xkb_rules" "evdev"
[    20.989] (**) Option "xkb_model" "pc105"
[    20.989] (**) Option "xkb_layout" "gb"
[    20.989] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    20.989] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    20.989] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    20.989] (**) AT Translated Set 2 keyboard: Applying InputClass "keyboard defaults"
[    20.989] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    20.989] (**) AT Translated Set 2 keyboard: always reports core events
[    20.989] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    20.989] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    20.989] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    20.989] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    20.989] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    20.989] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    20.989] (**) Option "xkb_rules" "evdev"
[    20.989] (**) Option "xkb_model" "pc105"
[    20.989] (**) Option "xkb_layout" "gb"
[    20.989] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    20.990] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[    20.990] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    20.990] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    20.990] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    20.990] (II) LoadModule: "synaptics"
[    20.990] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    20.990] (II) Module synaptics: vendor="X.Org Foundation"
[    20.990]     compiled for 1.17.1, module version = 1.8.2
[    20.991]     Module class: X.Org XInput Driver
[    20.991]     ABI class: X.Org XInput driver, version 21.0
[    20.991] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    20.991] (**) ETPS/2 Elantech Touchpad: always reports core events
[    20.991] (**) Option "Device" "/dev/input/event6"
[    21.012] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2940 (res 31)
[    21.012] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1260 (res 31)
[    21.012] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    21.012] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    21.012] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    21.012] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    21.012] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    21.012] (**) ETPS/2 Elantech Touchpad: always reports core events
[    21.024] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    21.024] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 13)
[    21.024] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    21.024] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    21.024] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.063
[    21.024] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    21.024] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    21.024] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    21.024] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    21.024] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    21.025] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    21.025] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    21.336] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event12)
[    21.336] (II) No input driver specified, ignoring this device.
[    21.336] (II) This device may have been added with another device file.
[    22.301] (II) intel(0): EDID vendor "LGD", prod id 826
[    22.301] (II) intel(0): Printing DDC gathered Modelines:
[    22.301] (II) intel(0): Modeline "1366x768"x0.0   70.00  1366 1402 1450 1492  768 771 776 782 -hsync -vsync (46.9 kHz eP)


```

---

### Post by Bashing-om on 2015-11-10
stefanoskikristijan; Well ...

(RE-)install was a great thought .. One of the surer ways to correction. Unfortunately, in this case we still have the same same situation:
> 
20.218] (WW) Warning, couldn't open module fglrx
  20.219] (EE) Failed to load module "fglrx" (module does not exist, 0)


And the hunt is on again to find out the why, as I presently do not know.
Let's just see what we can find out and learn:
A fresh install .. so a PPA should not be a factor .. conflicting drivers should not be a factor ---

Is this new install fully updated and upgraded to current ? - Be aware my mirror is not up-to-date ( Hash Sum mismatch ) yours may be in similar transition .

OK, so what version of X do we have ? and we look for known incompatibility issues:
```

X -version
apt-cache show xserver-xorg | grep Version

```

[INDENT][INDENT]it be a puzzle
[/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-10
> **Bashing-om said:**
> stefanoskikristijan; Well ...

(RE-)install was a great thought .. One of the surer ways to correction. Unfortunately, in this case we still have the same same situation:


And the hunt is on again to find out the why, as I presently do not know.
Let's just see what we can find out and learn:
A fresh install .. so a PPA should not be a factor .. conflicting drivers should not be a factor ---

Is this new install fully updated and upgraded to current ? - Be aware my mirror is not up-to-date ( Hash Sum mismatch ) yours may be in similar transition .

OK, so what version of X do we have ? and we look for known incompatibility issues:
```

X -version
apt-cache show xserver-xorg | grep Version

```[INDENT][INDENT]it be a puzzle
[/INDENT]
[/INDENT]


Hmm, i think i have a case to look for. I tried to manually install catalyst and i got an error that linux headers generic version.h is missing, but the headers are installed and updated. Maybe the version.h is somewhere else in the new ubuntu updates ? By default the catalyst look for it in lib/modules/4.2.0-18-generic/build/include/linux/version.h 

```

X.Org X Server 1.17.2
Release Date: 2015-06-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.19.0-30-generic x86_64 Ubuntu
Current Operating System: Linux Kristijan-Lenovo-G500 4.2.0-18-generic #22-Ubuntu SMP Fri Nov 6 18:25:50 UTC 2015 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-18-generic.efi.signed root=UUID=1536bfd3-dae8-40d1-ab69-241c9a53dc85 ro quiet splash vt.handoff=7
Build Date: 30 September 2015  09:08:47AM
xorg-server 2:1.17.2-1ubuntu9 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.32.6
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.

```

```

apt-cache show xserver-xorg | grep Version
Version: 1:7.7+7ubuntu4

```

This is how the installation of FGLRX goes...
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fglrx-amdcccle-updates fglrx-updates-core
The following NEW packages will be installed:
  fglrx-amdcccle-updates fglrx-updates fglrx-updates-core
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/100 MB of archives.
After this operation, 428 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Selecting previously unselected package fglrx-updates-core.
(Reading database ... 205520 files and directories currently installed.)
Preparing to unpack .../fglrx-updates-core_2%3a15.201-0ubuntu1_amd64.deb ...
Unpacking fglrx-updates-core (2:15.201-0ubuntu1) ...
Selecting previously unselected package fglrx-updates.
Preparing to unpack .../fglrx-updates_2%3a15.201-0ubuntu1_amd64.deb ...
Unpacking fglrx-updates (2:15.201-0ubuntu1) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Preparing to unpack .../fglrx-amdcccle-updates_2%3a15.201-0ubuntu1_amd64.deb ...
Unpacking fglrx-amdcccle-updates (2:15.201-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for bamfdaemon (0.5.2~bzr0+15.10.20150627.1-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for systemd (225-1ubuntu9) ...
Setting up fglrx-updates-core (2:15.201-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx-core/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GFXCORE.conf (x86_64-linux-gnu_gfxcore_conf) in auto mode
Loading new fglrx-updates-core-15.201 DKMS files...
First Installation: checking all kernels...
Building only for 4.2.0-18-generic
Building for architecture x86_64
Building initial module for 4.2.0-18-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.2.0-18-generic/updates/dkms/

depmod.......

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Setting up fglrx-updates (2:15.201-0ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
Setting up fglrx-amdcccle-updates (2:15.201-0ubuntu1) ...
Processing triggers for initramfs-tools (0.120ubuntu6) ...
update-initramfs: Generating /boot/initrd.img-4.2.0-18-generic
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (225-1ubuntu9) ...

```

---

### Post by Bashing-om on 2015-11-11
stefanoskikristijan; Morning;

Houston, we may have a problem,:
see:
[http://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064](http://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064)

I "think" I see this right that AMD only supports 12.04 with this card; AMD Catalyst&#8482; 15.9 .
Try'n now to cross reference and verify .

Not to appear to be stupid, but I am going to post this while I continue my search efforts .


EDIT:
Interesting find here .. take a look:
[https://bluehatrecord.wordpress.com/2015/03/22/amd-catalyst-fglrx-error-your-graphics-adapter-is-not-supported-by-this-driver-installation-will-not-proceed/](https://bluehatrecord.wordpress.com/2015/03/22/amd-catalyst-fglrx-error-your-graphics-adapter-is-not-supported-by-this-driver-installation-will-not-proceed/)
What is your thought ?
[INDENT][INDENT]surprise surprise
[/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-11
> **Bashing-om said:**
> stefanoskikristijan; Morning;

Houston, we may have a problem,:
see:
[http://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064](http://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064)

I "think" I see this right that AMD only supports 12.04 with this card; AMD Catalyst™ 15.9 .
Try'n now to cross reference and verify .

Not to appear to be stupid, but I am going to post this while I continue my search efforts .


EDIT:
Interesting find here .. take a look:
[https://bluehatrecord.wordpress.com/2015/03/22/amd-catalyst-fglrx-error-your-graphics-adapter-is-not-supported-by-this-driver-installation-will-not-proceed/](https://bluehatrecord.wordpress.com/2015/03/22/amd-catalyst-fglrx-error-your-graphics-adapter-is-not-supported-by-this-driver-installation-will-not-proceed/)
What is your thought ?[INDENT][INDENT]surprise surprise
[/INDENT]
[/INDENT]


Followed the instructions on the page again with no luck. I dont know what else to say than i give up, we must have tried all the methods already... :(

---

### Post by Bashing-om on 2015-11-11
stefanoskikristijan; Yuk ..

Nope a failure on my part in that I do not know . I am working on that to find us a way forward to find out where the failure is .

What was the result of the boot parameter "radeon.runpm=0" ?

It is for a fact getting real old chasing my tail.
> 
Before attempting to install the AMD Catalyst™ Proprietary Linux Graphics Driver, the following software must be installed:
Xorg/Xserver 7.4 and above (up to 1.17)
Linux kernel 2.6 or above (up to 3.19)
glibc version 2.2 or 2.3
POSIX Shared Memory (/dev/shm) support is required for 3D applications

The only conditions here that are unknown is 'glibc and shm' .
what have we ?
```

dpkg -l glibc
ls -al /dev/shm/

```

I do continue to learn the wherefore .
[INDENT][INDENT]this is a failure on my part
[/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-11
> **Bashing-om said:**
> stefanoskikristijan; Yuk ..

Nope a failure on my part in that I do not know . I am working on that to find us a way forward to find out where the failure is .

What was the result of the boot parameter "radeon.runpm=0" ?

It is for a fact getting real old chasing my tail.

The only conditions here that are unknown is 'glibc and shm' .
what have we ?
```

dpkg -l glibc
ls -al /dev/shm/

```

I do continue to learn the wherefore .[INDENT][INDENT]this is a failure on my part
[/INDENT]
[/INDENT]


Btw i found something interesting when i run with radeon.runpm=0 the AMD GPU IS WORKING AND IS POWERED ON, also i can turn it off and on using switcheroo, which i cannot do without radeon.runpm=0 ! But again i cannot switch to it i tried from terminal and console start both dont want to switch to it but its powered on...

```

dpkg -l glibc
dpkg-query: no packages found matching glibc

```

```
ls -al /dev/shm/
total 232
drwxrwxrwt  2 root          root               260 Nov 11 23:02 .
drwxr-xr-x 19 root          root              4640 Nov 11 22:56 ..
-rwx------  1 kristijan1999 kristijan1999 67108904 Nov 11 22:59 pulse-shm-1036605848
-rwx------  1 kristijan1999 kristijan1999 67108904 Nov 11 22:58 pulse-shm-1425870575
-rwx------  1 kristijan1999 kristijan1999 67108904 Nov 11 22:58 pulse-shm-1447643555
-rwx------  1 kristijan1999 kristijan1999 67108904 Nov 11 23:01 pulse-shm-1979710709
-rwx------  1 kristijan1999 kristijan1999 67108904 Nov 11 23:01 pulse-shm-2364516032
-rwx------  1 kristijan1999 kristijan1999 67108904 Nov 11 23:01 pulse-shm-2757586040
-rwx------  1 kristijan1999 kristijan1999 67108904 Nov 11 22:58 pulse-shm-2890641515
-rwx------  1 kristijan1999 kristijan1999 67108904 Nov 11 23:00 pulse-shm-3239566751
-rwx------  1 kristijan1999 kristijan1999 67108904 Nov 11 22:58 pulse-shm-3555995085
-rwx------  1 kristijan1999 kristijan1999 67108904 Nov 11 22:58 pulse-shm-53057530
-rwx------  1 kristijan1999 kristijan1999 67108904 Nov 11 22:58 pulse-shm-615246294


```

---

### Post by Bashing-om on 2015-11-11
stefanoskikristijan; Yeah,

Interesting result .. power management .
As to ' glibc': Looks like we can not query directly:
what returns :
```

ldd --version

```
and to cover our bases, how about:
```

dpkg -l xserver-xorg-video-ati

```
I do contine to seek to know how we can find the nature of the failure to build.
> 
 i tried from terminal and console start both dont want to switch to it but its powered on...

We got to have the drivers installed to make it work .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-11-11
stefanoskikristijan; I am back !

In addition to me last;
Let's make sure your hardware supports switching:
what returns:
```

/usr/bin/prime-supported

```
that generates the file  /var/log/prime-supported.log, which may be useful .
So what is now in the file ?
```

cat /var/log/prime-supported.log

```

[INDENT][INDENT]just do not know
[/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-12
> **Bashing-om said:**
> stefanoskikristijan; I am back !

In addition to me last;
Let's make sure your hardware supports switching:
what returns:
```

/usr/bin/prime-supported

```
that generates the file  /var/log/prime-supported.log, which may be useful .
So what is now in the file ?
```

cat /var/log/prime-supported.log

```
[INDENT][INDENT]just do not know
[/INDENT]
[/INDENT]


Hello, here are all the outputs you asked for:
```
ldd --version
ldd (Ubuntu GLIBC 2.21-0ubuntu4) 2.21
Copyright (C) 2015 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
Written by Roland McGrath and Ulrich Drepper.


```

```
dpkg -l xserver-xorg-video-ati
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  xserver-xorg-v 1:7.5.0+git2 amd64        X.Org X server -- AMD/ATI display


```

```
/usr/bin/prime-supported
bash: /usr/bin/prime-supported: No such file or directory
```

```
cat /var/log/prime-supported.log
cat: /var/log/prime-supported.log: No such file or directory


```

---

### Post by Bashing-om on 2015-11-12
stefanoskikristijan; Ouch ...

I got to do some more homework as:
> 
/usr/bin/prime-supported
bash: /usr/bin/prime-supported: No such file or directory

presently indicates to me that this system is MUX-less:
MUX-less:  Optimus chipsets - that is, dual GPUs where the outputs are NOT switched between the GPUs using a multiplexer.
 the Intel GPU would need to be active since MUX-less works by the nvidia doing the work but the Intel writing the framebuffer to the outputs, rather than with MUX systems where each GPU writes to its own framebuffers, and the outputs are switched between the 2 GPUs.

Do we we have this option:
```

sudo grep -i switcheroo /boot/config-*

```

[INDENT][INDENT]a lot of effort here for no gain ?
[/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-12
> **Bashing-om said:**
> stefanoskikristijan; Ouch ...

I got to do some more homework as:

presently indicates to me that this system is MUX-less:
MUX-less:  Optimus chipsets - that is, dual GPUs where the outputs are NOT switched between the GPUs using a multiplexer.
 the Intel GPU would need to be active since MUX-less works by the nvidia doing the work but the Intel writing the framebuffer to the outputs, rather than with MUX systems where each GPU writes to its own framebuffers, and the outputs are switched between the 2 GPUs.

Do we we have this option:
```

sudo grep -i switcheroo /boot/config-*

```
[INDENT][INDENT]a lot of effort here for no gain ?
[/INDENT]
[/INDENT]


```
sudo grep -i switcheroo /boot/config-*
[sudo] password for kristijan1999: 
/boot/config-4.2.0-16-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-4.2.0-18-generic:CONFIG_VGA_SWITCHEROO=y


```

---

### Post by Bashing-om on 2015-11-13
stefanoskikristijan; Coninued fight !

OK, let's look again at the hardware:
```

lspci -vnn | grep '\''[030[02]\]'

```
to see if a bug in the python code ( detecting only 0300 ) detects the nvidia devices .

EDIT: Is this a true statement ?
from: [https://bbs.archlinux.org/viewtopic.php?id=192643](https://bbs.archlinux.org/viewtopic.php?id=192643)
> 
The nvidia-prime Ubuntu package is made to only work with LightDM, so if you aren't using LightDM it's not going to work.


[INDENT][INDENT]until we know
[INDENT][INDENT][INDENT]no quitting
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-13
> **Bashing-om said:**
> stefanoskikristijan; Coninued fight !

OK, let's look again at the hardware:
```

lspci -vnn | grep '\''[030[02]\]'

```
to see if a bug in the python code ( detecting only 0300 ) detects the nvidia devices .
[INDENT][INDENT]until we know[INDENT][INDENT][INDENT]no quitting
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


```
-vnn | grep '\''[030[02]\]'
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])


```

---

### Post by Bashing-om on 2015-11-13
stefanoskikristijan; Yuk;;

On that last I had expected to see the AMD's graphic card .. Why do we not see it ??
We keep running into only the Intel chip set is shown !
Anything different:
```

lspci -vnn | grep VGA -A 12
sudo ubuntu-drivers devices
 
```
as at this point I do want to verify that class code for the AMD card.

[INDENT][INDENT]'round and around I go
[/INDENT][/INDENT]

---

### Post by stefanoskikristijan on 2015-11-13
> **Bashing-om said:**
> stefanoskikristijan; Yuk;;

On that last I had expected to see the AMD's graphic card .. Why do we not see it ??
We keep running into only the Intel chip set is shown !
Anything different:
```

lspci -vnn | grep VGA -A 12
sudo ubuntu-drivers devices
 
```
as at this point I do want to verify that class code for the AMD card.
[INDENT][INDENT]'round and around I go
[/INDENT]
[/INDENT]


```
lspci -vnn | grep VGA -A 12
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device [17aa:3800]
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at d8000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, medium devsel, latency 0, IRQ 25


```

```
sudo ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v00001002d00006663sv000017AAsd00003800bc03sc80i00
vendor   : Advanced Micro Devices, Inc. [AMD/ATI]
model    : Sun PRO [Radeon HD 8570A/8570M]
driver   : fglrx - distro non-free
driver   : xserver-xorg-video-ati - distro free builtin recommended
driver   : fglrx-updates - distro non-free

== cpu-microcode.py ==
driver   : intel-microcode - distro non-free


```

---

### Post by Bashing-om on 2015-11-14
stefanoskikristijan; Yukkie ->

On me .. As I do not understand why 'lspci' - list pci devices -with the arguments given- does not show the AMD card .
With no arguments to the command, do we see the card ?
```

lspci

```

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

