---
title: "Can't startx"
date: 2023-12-06
forum: General Help
---

### Post by alexelchivo on 2023-12-06
Hello, I have a Jr. Linux Level.

I have Ubuntu server 20.0.4 installed on a VM in proxmox.

When I try startx command it shows me this error.

root@vmi1528525:~# startx




X.Org X Server 1.21.1.4
X Protocol Version 11, Revision 0
Current Operating System: Linux vmi1528525.contaboserver.net 5.15.0-89-generic #99-Ubuntu SMP Mon Oct 30 20:42:41 UTC 2023 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-5.15.0-89-generic root=UUID=d067814e-c906-4bb3-9235-a8a8fa5287f3 ro net.ifnames=0 biosdevname=0 nomodeset
xorg-server 2:21.1.4-2ubuntu1.7~22.04.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
Current version of pixman: 0.40.0
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec  6 13:49:40 2023
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
vesa: Refusing to run on UEFI
(EE)
Fatal server error:
(EE) AddScreen/ScreenInit failed for driver 0
(EE)
(EE)
Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE)
(EE) Server terminated with error (1). Closing log file.


^Cxinit: giving up
xinit: unable to connect to X server: Network is unreachable
xinit: unexpected signal 2

[B]This is the /var/log/Xorf.0.log

[/B][ 94679.528]
X.Org X Server 1.21.1.4
X Protocol Version 11, Revision 0
[ 94679.528] Current Operating System: Linux vmi1528525.contaboserver.net 5.15.0-89-generic #99-Ubuntu SMP Mon Oct 30 20:42:41 UTC 2023 x86_64
[ 94679.528] Kernel command line: BOOT_IMAGE=/vmlinuz-5.15.0-89-generic root=UUID=d067814e-c906-4bb3-9235-a8a8fa5287f3 ro net.ifnames=0 biosdevname=0 nomodeset
[ 94679.528] xorg-server 2:21.1.4-2ubuntu1.7~22.04.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
[ 94679.528] Current version of pixman: 0.40.0
[ 94679.528]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[ 94679.528] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 94679.528] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec  6 13:49:40 2023
[ 94679.529] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 94679.530] (==) No Layout section.  Using the first Screen section.
[ 94679.530] (==) No screen section available. Using defaults.
[ 94679.530] (**) |-->Screen "Default Screen Section" (0)
[ 94679.530] (**) |   |-->Monitor "<default monitor>"
[ 94679.530] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[ 94679.530] (==) Automatically adding devices
[ 94679.530] (==) Automatically enabling devices
[ 94679.530] (==) Automatically adding GPU devices
[ 94679.530] (==) Automatically binding GPU devices
[ 94679.530] (==) Max clients allowed: 256, resource mask: 0x1fffff
[ 94679.533] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/cyrillic,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        built-ins
[ 94679.533] (==) ModulePath set to "/usr/lib/xorg/modules"
[ 94679.533] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[ 94679.533] (II) Loader magic: 0x55e6e567a020
[ 94679.533] (II) Module ABI versions:
[ 94679.533]    X.Org ANSI C Emulation: 0.4
[ 94679.533]    X.Org Video Driver: 25.2
[ 94679.533]    X.Org XInput driver : 24.4
[ 94679.533]    X.Org Server Extension : 10.0
[ 94679.534] (--) using VT number 2


[ 94679.534] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[ 94679.536] (--) PCI:*(0@0:2:0) 1234:1111:1af4:1100 rev 2, Mem @ 0xfd000000/16777216, 0xfea50000/4096, BIOS @ 0x????????/131072
[ 94679.536] (II) LoadModule: "glx"
[ 94679.537] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[ 94679.538] (II) Module glx: vendor="X.Org Foundation"
[ 94679.538]    compiled for 1.21.1.4, module version = 1.0.0
[ 94679.538]    ABI class: X.Org Server Extension, version 10.0
[ 94679.538] (==) Matched modesetting as autoconfigured driver 0
[ 94679.538] (==) Matched fbdev as autoconfigured driver 1
[ 94679.538] (==) Matched vesa as autoconfigured driver 2
[ 94679.538] (==) Assigned the driver to the xf86ConfigLayout
[ 94679.538] (II) LoadModule: "modesetting"
[ 94679.539] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[ 94679.539] (II) Module modesetting: vendor="X.Org Foundation"
[ 94679.539]    compiled for 1.21.1.4, module version = 1.21.1
[ 94679.539]    Module class: X.Org Video Driver
[ 94679.539]    ABI class: X.Org Video Driver, version 25.2
[ 94679.539] (II) LoadModule: "fbdev"
[ 94679.539] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 94679.540] (II) Module fbdev: vendor="X.Org Foundation"
[ 94679.540]    compiled for 1.21.1.3, module version = 0.5.0
[ 94679.540]    Module class: X.Org Video Driver
[ 94679.540]    ABI class: X.Org Video Driver, version 25.2
[ 94679.540] (II) LoadModule: "vesa"
[ 94679.540] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 94679.540] (II) Module vesa: vendor="X.Org Foundation"
[ 94679.540]    compiled for 1.21.1.3, module version = 2.5.0
[ 94679.540]    Module class: X.Org Video Driver
[ 94679.540]    ABI class: X.Org Video Driver, version 25.2
[ 94679.540] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[ 94679.540] (II) FBDEV: driver for framebuffer: fbdev
[ 94679.540] (II) VESA: driver for VESA chipsets: vesa
[ 94679.542] (EE) open /dev/dri/card0: No such file or directory
[ 94679.542] (WW) Falling back to old probe method for modesetting
[ 94679.542] (EE) open /dev/dri/card0: No such file or directory
[ 94679.542] (II) Loading sub module "fbdevhw"
[ 94679.542] (II) LoadModule: "fbdevhw"
[ 94679.542] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[ 94679.543] (II) Module fbdevhw: vendor="X.Org Foundation"
[ 94679.543]    compiled for 1.21.1.4, module version = 0.0.2
[ 94679.543]    ABI class: X.Org Video Driver, version 25.2
[ 94679.543] (EE) Unable to find a valid framebuffer device
[ 94679.543] (WW) Falling back to old probe method for fbdev
[ 94679.543] (II) Loading sub module "fbdevhw"
[ 94679.543] (II) LoadModule: "fbdevhw"
[ 94679.543] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[ 94679.543] (II) Module fbdevhw: vendor="X.Org Foundation"
[ 94679.543]    compiled for 1.21.1.4, module version = 0.0.2
[ 94679.543]    ABI class: X.Org Video Driver, version 25.2
[ 94679.543] (II) FBDEV(2): using default device
[ 94679.543] vesa: Refusing to run on UEFI
[ 94679.543] (EE) Screen 0 deleted because of no matching config section.
[ 94679.543] (II) UnloadModule: "modesetting"
[ 94679.543] (EE) Screen 0 deleted because of no matching config section.
[ 94679.543] (II) UnloadModule: "fbdev"
[ 94679.543] (II) UnloadSubModule: "fbdevhw"
[ 94679.543] (II) FBDEV(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[ 94679.543] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[ 94679.543] (==) FBDEV(0): RGB weight 888
[ 94679.543] (==) FBDEV(0): Default visual is TrueColor
[ 94679.543] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[ 94679.543] (II) FBDEV(0): hardware: EFI VGA (video memory: 1408kB)
[ 94679.543] (DB) xf86MergeOutputClassOptions unsupported bus type 0
[ 94679.543] (II) FBDEV(0): checking modes against framebuffer device...
[ 94679.543] (II) FBDEV(0): checking modes against monitor...
[ 94679.543] (II) FBDEV(0): Virtual size is 800x600 (pitch 800)
[ 94679.543] (**) FBDEV(0):  Built-in mode "current": 48.0 MHz, 46.9 kHz, 75.1 Hz
[ 94679.543] (II) FBDEV(0): Modeline "current"x0.0   48.00  800 832 928 1024  600 604 608 624 -hsync -vsync -csync (46.9 kHz b)
[ 94679.543] (==) FBDEV(0): DPI set to (96, 96)
[ 94679.543] (II) Loading sub module "fb"
[ 94679.543] (II) LoadModule: "fb"
[ 94679.543] (II) Module "fb" already built-in
[ 94679.543] (**) FBDEV(0): using shadow framebuffer
[ 94679.543] (II) Loading sub module "shadow"
[ 94679.543] (II) LoadModule: "shadow"
[ 94679.543] (II) Loading /usr/lib/xorg/modules/libshadow.so
[ 94679.543] (II) Module shadow: vendor="X.Org Foundation"
[ 94679.543]    compiled for 1.21.1.4, module version = 1.1.0
[ 94679.543]    ABI class: X.Org ANSI C Emulation, version 0.4
[ 94679.544] (EE) FBDEV(0): FBIOPUT_VSCREENINFO succeeded but modified mode
[ 94679.544] (EE) FBDEV(0): mode initialization failed
[ 94679.544] (EE)
Fatal server error:
[ 94679.544] (EE) AddScreen/ScreenInit failed for driver 0
[ 94679.544] (EE)
[ 94679.544] (EE)
Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
[ 94679.544] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 94679.544] (EE)
[ 94679.546] (EE) Server terminated with error (1). Closing log file.

[B]Additional information


[/B]root@vmi1528525:~#  lspci -k | grep -EA3 'VGA|3D'
00:02.0 VGA compatible controller: Device 1234:1111 (rev 02)
        Subsystem: Red Hat, Inc. Device 1100
        Kernel modules: bochs
00:05.0 SCSI storage controller: Red Hat, Inc. Virtio SCSI

Hope you can help me.

Thanks.

---

### Post by MAFoElffen on 2023-12-06
Is this a KVM VM? I see the device ID as 1234:1111, which is often used by QEMU  "stdvga", What is the guest OS and kernel version?

---

### Post by alexelchivo on 2023-12-07
root@:/etc# uname -r
5.15.0-89-generic
root@:/etc# uname -a
Linux 5.15.0-89-generic #99-Ubuntu SMP Mon Oct 30 20:42:41 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
root@vmi1528525:/etc# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:        22.04
Codename:       jammy

---

### Post by TheFu on 2023-12-07
If you want a desktop, install a desktop, not a server.  In Linux, "Servers" don't have a GUI.  Adding one means you accept having a Frankenstein system.  That's fine, but not recommended for someone new to Linux.

Don't use root.  Use sudo.

I've never used proxmox.  Thought the OS took over the entire OS and provided just a webGUI for management. Use a different workstation to manage the proxmox.  Then you'll need to use some remote desktop software to access a desktop, if that isn't built-into proxmox.  

I use KVM+libvirt, so **virt-viewer** is the way to remotely access my desktops running inside a VM within my LAN. Most of the time, I'll just use remote X11 from my workstation through ssh tunnels to run specific GUI programs.  A full remote desktop brings lots of overhead.  Over the internet, I use **x2go** instead for better security and more responsive use than other remote desktop options.

virt-viewer leveraging the Spice protocol works with any libvirt virtual machine running KVM.  
The other two options work with Unix-only systems, but they do work with all of them, regardless of virtualization (or no virtualization).

I don't know the solution. Sorry. Just throwing out some other options.

---

### Post by MAFoElffen on 2023-12-07
<< This would be addressed better in the Virtualization Section >>
Welcome to Ubuntu Forums!

I am surprised that no one has mentioned to you that it is a Forum Policy to post all commands and raw output within [noparse]```
 ___ 
```[/noparse] Tags... You might want to go back and edit your posts to correct those. I know that the Proxmox Forums have that same policy..

This is not a question about Ubuntu (specifically), this is a question about both #1) Setting up VM Guest Machine's for Linux OS'es, and #2) Running XServer in Linux.

Proxmox is KVM/LibVirt based.

Like TheFu said, basically, it is failing for 3 reasons. 

What he also said it true, in that Proxmox takes over what should be simple, and controllable by the user, shielding them away from many choices... I support a whole lot OS'es and Virtualization Hosting systems. I have used Proxmox, enough to know I didn't want to use it. Proxmox didn't give me anything I already had with just KVM. It takes away many abilities and control I had with just KVM with the way it does it's interface. I still support the KVM/QEMU features underneath it.

Do you know that you could install KVM/LibVirt on a Desktop Edition Machine, and you could learn and do so much more with that? That is still an option open to you. You are just starting out... Something for you to think about... Then you could actually, productively use that computer while you learn, instead of being shielded away from it.

In the VM Guest machine setup, for Modern Linux, if you chose Ubuntu <release> in VirtualMachine Manager of KVM, it would have chosen Spice/QXL as the Graphics / Video for the machine. If you are using QEMU, then you would add those to your creation script or run script. I do not know what ProMox provides within it's own toolset now.

As TheFu Mentioned, the Linux Graphics Layer is a GUI interface for Users, not for root. In fact in most Linux OS'es you have to do special things 'hacking' Linux, to allow the root user to display a GUI. Those hacks are considered by many to expose security vulnerabilities to the system. So you create a user, with an .Xauthority file.

Also, Server Edition(s) assume you are comfortable at a console screen, and a command prompt. Even Windows OS has accepted with Win Server Core, that with GUI's, you accept risk and vulnerabilities. On the other side of that, it is easier for you to learn Linux if you have a GUI to help you along. 

Then, you did not mention if you installed anything else beyond just XServer(?)... such as any Desktop for the XServer graphics engine to display(?) Usually people install something along those lines.

You could install a Graphics Engine and Desktop on a Linux Server Edition base to create a Minimal-Install Desktop... But then, what is your goal? Are you just creating a light-weight desktop that you can use and learn Linux on?

If so, one you could to build on your own, piecing it together, resulting in a Franken-Linux Desktop like you are doing, learning from trial and error as you go along... That is the strength of Linux, being able to pick & choose whatever you want. But that is not normally a choice for someone just starting out, learning...

Another option might be to install any pre-built Desktop Edition (Flavor) of Ubuntu, where there is pleanty of documentation, and user support for what you installed... For a beginner, just starting out, that is usually a mainstream kind of choice. Until you learn some commands and skills to venture into the beyond. Just think, you could use those VM Guests to decide on what you want to learn on, and use as a real, day-to-day daily driver, for full-time use.

I wish you well, and success in whatever yo want to do. The opportunities are endless.

---

### Post by TheFu on 2023-12-07
It is Pro**x**mox - [https://www.proxmox.com/en/](https://www.proxmox.com/en/)

The reason I'd want to use Proxmox would be for the built-in clustering and if you want easier LVM snapshots for backups without really understand them.  I've seen places, usually small businesses, that ran their VoIP systems in a VM under Proxmox. They had the clustering enabled to ensure service availability. Initially, they had issues with jitter, but newer hardware and VTx support solved nearly all of that.  I ran a FreeSwitch VoIP server under KVM. Worked well enough with minimal jitter noticed on calls.

For other HA needs, like websites, there are easier, less restrictive solutions. Of course, the type of clustering Proxmox provides is Active-Failover, not active-active and shared storage is still mandatory.  For a DBMS cluster, it would be better to setup a cluster for that specific DBMS anyway. For websites, a pair of reverse proxies with DNS controlling access to both is the industry standard.

The reasons NOT to want to use Proxmox include that another workstation is required to access and manage the proxmox setup. The server(s) cannot be used for this, at least not trivially.

---

### Post by MAFoElffen on 2023-12-07
+1 -- I agree. 

Even though I beta test VMware vSphere / vCenter... I do that by plugging in a drive into a slot in my workstation's hot-swap bay... And when through, remove it.

I do not like that it takes over the machine, have to connect to it remotely, and lost the ability to do anything else on it. 

I shy away from things that take away abilities to do things, and take away control. (And especially to things that take over a system with very deep hooks.)

That concept is sort of 'counter-intuitive' to the goals of virtualization where you are trying to add the ability to do many different things at once with what you have, right?

---

### Post by TheFu on 2023-12-07
Depending on the motherboard and GPU, PCIe GPU passthru may be possible. 

[https://www.reddit.com/r/Proxmox/comments/rm5wkq/has_anyone_ever_used_proxmox_to_run_their_main/](https://www.reddit.com/r/Proxmox/comments/rm5wkq/has_anyone_ever_used_proxmox_to_run_their_main/) has people claiming they do it. I don't know how easy or hard it is.  Cheap GPUs need not try.

---

