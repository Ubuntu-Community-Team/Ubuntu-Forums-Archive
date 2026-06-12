---
title: "No nvidia Driver working on New Dell 9570?"
date: 2018-05-27
forum: General Help
---

### Post by klaxmaster on 2018-05-27
Hey guys, 

My company recently started purchasing the newer dell 9570 (instead of the 9560) and i have been having a hard time getting ubuntu to run correctly.

High Level info: 
Ubuntu 16.04.4
UEFI boot
Luks encryption

We used to run it on Legacy. Well, the 9570 doesn't support legacyboot on the m.2, so we have changed to uefi boot. which was a bit of a hangup due to the LUKS encryption, but i got through it.

now I cant log in to the profile. Everything boots just fine until I enter my credentials in the GUI. i have the login loop

I am 95% sure it has to do with the nvidia drivers, as when i purge nvidia* and run with the flag 'nomodeset' it seems to work just fine. i have tried every driver from 360 to 396, and no dice.
i have done all the usual things. reinstall desktop, lightdm, made sure bios setting are set correctly. (including no secure boot) etc.
I am wondering if anyone else got this laptop yet, and has had any similar issues with it on this version of ubuntu. and if there is a driver out there that may work. 

its a gtx1060 btw.

i have seen a lot of solutions for the 9560 (which i never had trouble with), and dont solve my problem. 
i have seen very few google results that include ubuntu and the dell 9570.

---

### Post by SL0ltMJGyh on 2018-05-27
What you want to do is try running the nouveau drivers instead of the NVIDIA ones. A reference link to set this up is here: [https://askubuntu.com/questions/360761/cannot-get-rid-of-nvidia-drivers-restore-nouveau-driver-and-get-desktop-working](https://askubuntu.com/questions/360761/cannot-get-rid-of-nvidia-drivers-restore-nouveau-driver-and-get-desktop-working)
Also, check what kernel version you have by typing "uname -r". We need to know if you are running kernel 4.16, as there are some NVIDIA hangups on that kernel version. I had to edit my grub2.cfg to restore NVIDIA functionality.

---

### Post by klaxmaster on 2018-05-27
Thanks for the lead apmarek. i am running 4.13.0-43 at the moment. 

i will be checking the nouveau drivers later tonight and report back

---

### Post by klaxmaster on 2018-06-01
Sorry for the long delay. Work has been super crazy.

long story short. Yes the nouveau drivers work, but we need to use those cudas, so nvidia 384 is the optimum driver for us. 

I have had no luck. 

It is important to note that ubuntu 18.04 works like a charm. (again, cant use it though, libraries wont support our software atm.)

16.04 is still dead in the water.

---

### Post by Bashing-om on 2018-06-01
klaxmaster; Hello -

Try this sequence of terminal commands to get the proprietary driver installed:
Make sure in the firmware that secure boot is disabled, as the driver is 3rd party software.
run:
```

sudo rm /etc/X11/Xorg.conf ## no worry if the file does not exist
sudo apt purge nvidia*
sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall

```
where the system will choose what it thinks is the best driver .

Re-boot to see the effect.

[INDENT]should workie great
[INDENT][INDENT]last long time
[/INDENT][/INDENT][/INDENT]

---

### Post by klaxmaster on 2018-06-01
The above seems to have done the same thing as straight nvidia-384 install, as in that is the driver it grabbed, plus it had the same login loop result.

---

### Post by Bashing-om on 2018-06-01
klaxmaster; Ouch -

Ho-kay then the discovery operation is underway.
show:
```

ls -al .ICEauthority .Xauthority
dpkg -l | grep -i nvidia
cat /var/log/gpu-manager.log

```

see what we can find
[INDENT][INDENT]where to go next
[/INDENT][/INDENT]

---

### Post by klaxmaster on 2018-06-01
here is the requested info



[SIZE=1]ls -al .ICEauthority .Xauthority [/SIZE]
[SIZE=1]-rw------- 1 luminaradmin luminaradmin 326 Jun  1 11:50 .ICEauthority[/SIZE]
[SIZE=1]-rw------- 1 luminaradmin luminaradmin  53 Jun  1 13:25 .Xauthority[/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=1]root@compy386:~# dpkg -l | grep -i nvidia
[/SIZE][SIZE=1]ii  bbswitch-dkms                              		     0.8-3ubuntu1                                 amd64        Interface for toggling the power on [01;31m[KNVIDIA[m[K Optimus video cards[/SIZE]
[SIZE=1]ii  libcuda1-384                             		     384.130-0ubuntu0.16.04.1              amd64        [01;31m[KNVIDIA[m[K CUDA runtime library[/SIZE]
[SIZE=1]ii  [01;31m[Knvidia[m[K-384                           384.130-0ubuntu0.16.04.1              amd64        [01;31m[KNVIDIA[m[K binary driver - version 384.130[/SIZE]
[SIZE=1]ii  [01;31m[Knvidia[m[K-opencl-icd-384           384.130-0ubuntu0.16.04.1              amd64        [01;31m[KNVIDIA[m[K OpenCL ICD[/SIZE]
[SIZE=1]ii  [01;31m[Knvidia[m[K-prime                        0.8.2                                              amd64        Tools to enable [01;31m[KNVIDIA[m[K's Prime[/SIZE]
[SIZE=1]ii  [01;31m[Knvidia[m[K-settings                     361.42-0ubuntu1                            amd64        Tool for configuring the [01;31m[KNVIDIA[m[K graphics driver[/SIZE]
[SIZE=1]root@compy386:~# exit[/SIZE]



gpu-manager.log:
[SIZE=1]log_file: /var/log/gpu-manager.log[/SIZE]
[SIZE=1]last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot[/SIZE]
[SIZE=1]new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot[/SIZE]
[SIZE=1]can't access /run/u-d-c-fglrx-was-loaded file[/SIZE]
[SIZE=1]Looking for fglrx modules in /lib/modules/4.13.0-43-generic/updates/dkms[/SIZE]
[SIZE=1]Looking for nvidia modules in /lib/modules/4.13.0-43-generic/updates/dkms[/SIZE]
[SIZE=1]Found nvidia module: nvidia_384_uvm.ko[/SIZE]
[SIZE=1]Is nvidia loaded? yes[/SIZE]
[SIZE=1]Was nvidia unloaded? no[/SIZE]
[SIZE=1]Is nvidia blacklisted? no[/SIZE]
[SIZE=1]Is fglrx loaded? no[/SIZE]
[SIZE=1]Was fglrx unloaded? no[/SIZE]
[SIZE=1]Is fglrx blacklisted? no[/SIZE]
[SIZE=1]Is intel loaded? yes[/SIZE]
[SIZE=1]Is radeon loaded? no[/SIZE]
[SIZE=1]Is radeon blacklisted? no[/SIZE]
[SIZE=1]Is amdgpu loaded? no[/SIZE]
[SIZE=1]Is amdgpu blacklisted? no[/SIZE]
[SIZE=1]Is nouveau loaded? no[/SIZE]
[SIZE=1]Is nouveau blacklisted? yes[/SIZE]
[SIZE=1]Is fglrx kernel module available? no[/SIZE]
[SIZE=1]Is nvidia kernel module available? yes[/SIZE]
[SIZE=1]Vendor/Device Id: 8086:3e9b[/SIZE]
[SIZE=1]BusID "PCI:0@0:2:0"[/SIZE]
[SIZE=1]Is boot vga? yes[/SIZE]
[SIZE=1]Error: can't access /sys/bus/pci/devices/0000:00:02.0/driver[/SIZE]
[SIZE=1]The device is not bound to any driver. Skipping...[/SIZE]
[SIZE=1]Vendor/Device Id: 10de:1c8c[/SIZE]
[SIZE=1]BusID "PCI:1@0:0:0"[/SIZE]
[SIZE=1]Is boot vga? no[/SIZE]
[SIZE=1]Skipping "/dev/dri/card0", driven by "nvidia-drm"[/SIZE]
[SIZE=1]Skipping "/dev/dri/card0", driven by "nvidia-drm"[/SIZE]
[SIZE=1]Skipping "/dev/dri/card0", driven by "nvidia-drm"[/SIZE]
[SIZE=1]Skipping "/dev/dri/card0", driven by "nvidia-drm"[/SIZE]
[SIZE=1]Does it require offloading? no[/SIZE]
[SIZE=1]last cards number = 1[/SIZE]
[SIZE=1]Has amd? no[/SIZE]
[SIZE=1]Has intel? no[/SIZE]
[SIZE=1]Has nvidia? yes[/SIZE]
[SIZE=1]How many cards? 1[/SIZE]
[SIZE=1]Has the system changed? No[/SIZE]
[SIZE=1]main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu[/SIZE]
[SIZE=1]Current alternative: /usr/lib/nvidia-384/ld.so.conf[/SIZE]
[SIZE=1]Current core alternative: (null)[/SIZE]
[SIZE=1]Current egl alternative: /usr/lib/nvidia-384/ld.so.conf[/SIZE]
[SIZE=1]Is nvidia enabled? yes[/SIZE]
[SIZE=1]Is nvidia egl enabled? yes[/SIZE]
[SIZE=1]Is fglrx enabled? no[/SIZE]
[SIZE=1]Is mesa enabled? no[/SIZE]
[SIZE=1]Is mesa egl enabled? no[/SIZE]
[SIZE=1]Is pxpress enabled? no[/SIZE]
[SIZE=1]Is prime enabled? no[/SIZE]
[SIZE=1]Is prime egl enabled? no[/SIZE]
[SIZE=1]Is nvidia available? yes[/SIZE]
[SIZE=1]Is nvidia egl available? no[/SIZE]
[SIZE=1]Is fglrx available? no[/SIZE]
[SIZE=1]Is fglrx-core available? no[/SIZE]
[SIZE=1]Is mesa available? yes[/SIZE]
[SIZE=1]Is mesa egl available? yes[/SIZE]
[SIZE=1]Is pxpress available? no[/SIZE]
[SIZE=1]Is prime available? yes[/SIZE]
[SIZE=1]Is prime egl available? no[/SIZE]
[SIZE=1]Single card detected[/SIZE]
[SIZE=1]No change - nothing to do[/SIZE]

---

### Post by Bashing-om on 2018-06-01
klaxmaster; Well, well ... Not

we have:
> 
Error: can't access /sys/bus/pci/devices/0000:00:02.0/driver

which to me means the driver failed to build. Now the question is why not ? secure boot is disabled ??
post back:
```

sudo lshw -C display
lspci -k | grep -EA2 'VGA|3D'
sudo dkms status
dpkg -l | grep linux-
lsb_release -a
echo $XDG_SESSION_TYPE
cat /var/log/Xorg.0.log

```

see what we can find out for where the fault lies .

[INDENT][INDENT]the hunt is on
[/INDENT][/INDENT]

---

### Post by klaxmaster on 2018-06-01
Yes. Secure boot is disabled. =P

here is the Xorg.o.log

```
[    29.206] 
X.Org X Server 1.19.5
Release Date: 2017-10-12
[    29.206] X Protocol Version 11, Revision 0
[    29.206] Build Operating System: Linux 4.4.0-101-generic x86_64 Ubuntu
[    29.206] Current Operating System: Linux compy386 4.13.0-43-generic #48~16.04.1-Ubuntu SMP Thu May 17 12:56:46 UTC 2018 x86_64
[    29.206] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-43-generic.efi.signed root=UUID=bc1ca7fc-5bb1-41bb-ae42-78cb021a7609 ro nomodeset quiet splash vt.handoff=7
[    29.206] Build Date: 24 November 2017  09:44:25AM
[    29.206] xorg-server 2:1.19.5-0ubuntu2~16.04.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    29.206] Current version of pixman: 0.33.6
[    29.206]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    29.206] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.206] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun  1 13:25:03 2018
[    29.206] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.206] (==) No Layout section.  Using the first Screen section.
[    29.206] (==) No screen section available. Using defaults.
[    29.206] (**) |-->Screen "Default Screen Section" (0)
[    29.206] (**) |   |-->Monitor "<default monitor>"
[    29.206] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.206] (==) Automatically adding devices
[    29.206] (==) Automatically enabling devices
[    29.206] (==) Automatically adding GPU devices
[    29.206] (==) Automatically binding GPU devices
[    29.206] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    29.206] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.206]     Entry deleted from font path.
[    29.206] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.206]     Entry deleted from font path.
[    29.206] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.206]     Entry deleted from font path.
[    29.206] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.206]     Entry deleted from font path.
[    29.206] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.206]     Entry deleted from font path.
[    29.206] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.206] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.206] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.206] (II) Loader magic: 0x55bc2471ce00
[    29.206] (II) Module ABI versions:
[    29.206]     X.Org ANSI C Emulation: 0.4
[    29.206]     X.Org Video Driver: 23.0
[    29.206]     X.Org XInput driver : 24.1
[    29.206]     X.Org Server Extension : 10.0
[    29.207] (++) using VT number 7

[    29.207] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    29.207] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.209] (--) PCI:*(0:0:2:0) 8086:3e9b:1028:087c rev 0, Mem @ 0xeb000000/16777216, 0x80000000/268435456, I/O @ 0x00004000/64, BIOS @ 0x????????/131072
[    29.209] (--) PCI: (0:1:0:0) 10de:1c8c:1028:087c rev 161, Mem @ 0xec000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00003000/128, BIOS @ 0x????????/524288
[    29.209] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    29.209] (II) "glx" will be loaded by default.
[    29.209] (II) LoadModule: "glx"
[    29.209] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    29.211] (II) Module glx: vendor="NVIDIA Corporation"
[    29.211]     compiled for 4.0.2, module version = 1.0.0
[    29.211]     Module class: X.Org Server Extension
[    29.211] (II) NVIDIA GLX Module  384.130  Wed Mar 21 02:54:48 PDT 2018
[    29.211] (==) Matched nvidia as autoconfigured driver 0
[    29.211] (==) Matched nouveau as autoconfigured driver 1
[    29.211] (==) Matched modesetting as autoconfigured driver 2
[    29.211] (==) Matched fbdev as autoconfigured driver 3
[    29.211] (==) Matched vesa as autoconfigured driver 4
[    29.211] (==) Assigned the driver to the xf86ConfigLayout
[    29.211] (II) LoadModule: "nvidia"
[    29.211] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    29.212] (II) Module nvidia: vendor="NVIDIA Corporation"
[    29.212]     compiled for 4.0.2, module version = 1.0.0
[    29.212]     Module class: X.Org Video Driver
[    29.212] (II) LoadModule: "nouveau"
[    29.212] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    29.212] (II) Module nouveau: vendor="X.Org Foundation"
[    29.212]     compiled for 1.19.5, module version = 1.0.15
[    29.212]     Module class: X.Org Video Driver
[    29.212]     ABI class: X.Org Video Driver, version 23.0
[    29.212] (II) LoadModule: "modesetting"
[    29.212] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    29.212] (II) Module modesetting: vendor="X.Org Foundation"
[    29.212]     compiled for 1.19.5, module version = 1.19.5
[    29.212]     Module class: X.Org Video Driver
[    29.212]     ABI class: X.Org Video Driver, version 23.0
[    29.212] (II) LoadModule: "fbdev"
[    29.212] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.212] (II) Module fbdev: vendor="X.Org Foundation"
[    29.212]     compiled for 1.19.3, module version = 0.4.4
[    29.212]     Module class: X.Org Video Driver
[    29.212]     ABI class: X.Org Video Driver, version 23.0
[    29.212] (II) LoadModule: "vesa"
[    29.212] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.212] (II) Module vesa: vendor="X.Org Foundation"
[    29.212]     compiled for 1.19.3, module version = 2.3.4
[    29.212]     Module class: X.Org Video Driver
[    29.212]     ABI class: X.Org Video Driver, version 23.0
[    29.212] (II) NVIDIA dlloader X Driver  384.130  Wed Mar 21 02:29:29 PDT 2018
[    29.212] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    29.212] (II) NOUVEAU driver Date:   Fri Apr 21 14:41:17 2017 -0400
[    29.212] (II) NOUVEAU driver for NVIDIA chipset families :
[    29.212]     RIVA TNT        (NV04)
[    29.212]     RIVA TNT2       (NV05)
[    29.212]     GeForce 256     (NV10)
[    29.212]     GeForce 2       (NV11, NV15)
[    29.212]     GeForce 4MX     (NV17, NV18)
[    29.212]     GeForce 3       (NV20)
[    29.212]     GeForce 4Ti     (NV25, NV28)
[    29.212]     GeForce FX      (NV3x)
[    29.212]     GeForce 6       (NV4x)
[    29.212]     GeForce 7       (G7x)
[    29.212]     GeForce 8       (G8x)
[    29.212]     GeForce GTX 200 (NVA0)
[    29.212]     GeForce GTX 400 (NVC0)
[    29.212] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    29.212] (II) FBDEV: driver for framebuffer: fbdev
[    29.212] (II) VESA: driver for VESA chipsets: vesa
[    29.212] (EE) [drm] Failed to open DRM device for (null): -22
[    29.212] (WW) Falling back to old probe method for modesetting
[    29.212] (II) Loading sub module "fbdevhw"
[    29.212] (II) LoadModule: "fbdevhw"
[    29.212] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    29.212] (II) Module fbdevhw: vendor="X.Org Foundation"
[    29.212]     compiled for 1.19.5, module version = 0.0.2
[    29.212]     ABI class: X.Org Video Driver, version 23.0
[    29.212] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[    29.212] (II) FBDEV(1): using default device
[    29.212] (WW) Falling back to old probe method for vesa
[    29.212] (EE) Screen 0 deleted because of no matching config section.
[    29.213] (II) UnloadModule: "modesetting"
[    29.213] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    29.213] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    29.213] (==) FBDEV(0): RGB weight 888
[    29.213] (==) FBDEV(0): Default visual is TrueColor
[    29.213] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    29.213] (II) FBDEV(0): hardware: EFI VGA (video memory: 8128kB)
[    29.213] (II) FBDEV(0): checking modes against framebuffer device...
[    29.213] (II) FBDEV(0): checking modes against monitor...
[    29.213] (--) FBDEV(0): Virtual size is 1920x1080 (pitch 1920)
[    29.213] (**) FBDEV(0):  Built-in mode "current": 207.4 MHz, 85.3 kHz, 77.2 Hz
[    29.213] (II) FBDEV(0): Modeline "current"x0.0  207.38  1920 1952 2192 2432  1080 1084 1088 1104 -hsync -vsync -csync (85.3 kHz b)
[    29.213] (==) FBDEV(0): DPI set to (96, 96)
[    29.213] (II) Loading sub module "fb"
[    29.213] (II) LoadModule: "fb"
[    29.213] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.213] (II) Module fb: vendor="X.Org Foundation"
[    29.213]     compiled for 1.19.5, module version = 1.0.0
[    29.213]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.213] (**) FBDEV(0): using shadow framebuffer
[    29.213] (II) Loading sub module "shadow"
[    29.213] (II) LoadModule: "shadow"
[    29.213] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    29.213] (II) Module shadow: vendor="X.Org Foundation"
[    29.213]     compiled for 1.19.5, module version = 1.1.0
[    29.213]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.213] (II) UnloadModule: "vesa"
[    29.213] (II) Unloading vesa
[    29.213] (==) Depth 24 pixmap format is 32 bpp
[    29.213] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[    29.213] (==) FBDEV(0): Backing store enabled
[    29.213] (==) FBDEV(0): DPMS enabled
[    29.213] (==) RandR enabled
[    29.215] (II) SELinux: Disabled on system
[    29.215] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    29.232] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    29.232] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.232] (II) LoadModule: "evdev"
[    29.232] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.232] (II) Module evdev: vendor="X.Org Foundation"
[    29.232]     compiled for 1.19.3, module version = 2.10.5
[    29.232]     Module class: X.Org XInput Driver
[    29.232]     ABI class: X.Org XInput driver, version 24.1
[    29.232] (II) Using input driver 'evdev' for 'Power Button'
[    29.232] (**) Power Button: always reports core events
[    29.232] (**) evdev: Power Button: Device: "/dev/input/event3"
[    29.232] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.232] (--) evdev: Power Button: Found keys
[    29.232] (II) evdev: Power Button: Configuring as keyboard
[    29.232] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    29.232] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    29.232] (**) Option "xkb_rules" "evdev"
[    29.232] (**) Option "xkb_model" "pc105"
[    29.232] (**) Option "xkb_layout" "us"
[    29.232] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    29.232] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.232] (II) Using input driver 'evdev' for 'Power Button'
[    29.232] (**) Power Button: always reports core events
[    29.232] (**) evdev: Power Button: Device: "/dev/input/event1"
[    29.232] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.232] (--) evdev: Power Button: Found keys
[    29.232] (II) evdev: Power Button: Configuring as keyboard
[    29.232] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    29.232] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    29.232] (**) Option "xkb_rules" "evdev"
[    29.232] (**) Option "xkb_model" "pc105"
[    29.232] (**) Option "xkb_layout" "us"
[    29.233] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    29.233] (II) No input driver specified, ignoring this device.
[    29.233] (II) This device may have been added with another device file.
[    29.233] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    29.233] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    29.233] (II) Using input driver 'evdev' for 'Sleep Button'
[    29.233] (**) Sleep Button: always reports core events
[    29.233] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    29.233] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    29.233] (--) evdev: Sleep Button: Found keys
[    29.233] (II) evdev: Sleep Button: Configuring as keyboard
[    29.233] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    29.233] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    29.233] (**) Option "xkb_rules" "evdev"
[    29.233] (**) Option "xkb_model" "pc105"
[    29.233] (**) Option "xkb_layout" "us"
[    29.233] (II) config/udev: Adding input device Integrated_Webcam_HD: Integrate (/dev/input/event8)
[    29.233] (**) Integrated_Webcam_HD: Integrate: Applying InputClass "evdev keyboard catchall"
[    29.233] (II) Using input driver 'evdev' for 'Integrated_Webcam_HD: Integrate'
[    29.233] (**) Integrated_Webcam_HD: Integrate: always reports core events
[    29.233] (**) evdev: Integrated_Webcam_HD: Integrate: Device: "/dev/input/event8"
[    29.233] (--) evdev: Integrated_Webcam_HD: Integrate: Vendor 0xc45 Product 0x671d
[    29.233] (--) evdev: Integrated_Webcam_HD: Integrate: Found keys
[    29.233] (II) evdev: Integrated_Webcam_HD: Integrate: Configuring as keyboard
[    29.233] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-12/1-12:1.0/input/input9/event8"
[    29.233] (II) XINPUT: Adding extended input device "Integrated_Webcam_HD: Integrate" (type: KEYBOARD, id 9)
[    29.233] (**) Option "xkb_rules" "evdev"
[    29.233] (**) Option "xkb_model" "pc105"
[    29.233] (**) Option "xkb_layout" "us"
[    29.234] (II) config/udev: Adding input device SYNA2393:00 06CB:7A13 Touchpad (/dev/input/event10)
[    29.234] (**) SYNA2393:00 06CB:7A13 Touchpad: Applying InputClass "evdev touchpad catchall"
[    29.234] (**) SYNA2393:00 06CB:7A13 Touchpad: Applying InputClass "evdev touchscreen catchall"
[    29.234] (**) SYNA2393:00 06CB:7A13 Touchpad: Applying InputClass "touchpad catchall"
[    29.234] (**) SYNA2393:00 06CB:7A13 Touchpad: Applying InputClass "Default clickpad buttons"
[    29.234] (II) LoadModule: "synaptics"
[    29.234] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    29.234] (II) Module synaptics: vendor="X.Org Foundation"
[    29.234]     compiled for 1.19.3, module version = 1.9.0
[    29.234]     Module class: X.Org XInput Driver
[    29.234]     ABI class: X.Org XInput driver, version 24.1
[    29.234] (II) Using input driver 'synaptics' for 'SYNA2393:00 06CB:7A13 Touchpad'
[    29.234] (**) SYNA2393:00 06CB:7A13 Touchpad: always reports core events
[    29.234] (**) Option "Device" "/dev/input/event10"
[    29.292] (II) synaptics: SYNA2393:00 06CB:7A13 Touchpad: found clickpad property
[    29.292] (--) synaptics: SYNA2393:00 06CB:7A13 Touchpad: x-axis range 0 - 1228 (res 12)
[    29.292] (--) synaptics: SYNA2393:00 06CB:7A13 Touchpad: y-axis range 0 - 928 (res 12)
[    29.292] (II) synaptics: SYNA2393:00 06CB:7A13 Touchpad: device does not report pressure, will use touch data.
[    29.292] (II) synaptics: SYNA2393:00 06CB:7A13 Touchpad: device does not report finger width.
[    29.292] (--) synaptics: SYNA2393:00 06CB:7A13 Touchpad: buttons: left double triple
[    29.292] (--) synaptics: SYNA2393:00 06CB:7A13 Touchpad: Vendor 0x6cb Product 0x7a13
[    29.292] (--) synaptics: SYNA2393:00 06CB:7A13 Touchpad: invalid pressure range.  defaulting to 0 - 255
[    29.292] (--) synaptics: SYNA2393:00 06CB:7A13 Touchpad: invalid finger width range.  defaulting to 0 - 15
[    29.292] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    29.292] (--) synaptics: SYNA2393:00 06CB:7A13 Touchpad: touchpad found
[    29.292] (**) SYNA2393:00 06CB:7A13 Touchpad: always reports core events
[    29.336] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-1/i2c-SYNA2393:00/0018:06CB:7A13.0001/input/input12/event10"
[    29.336] (II) XINPUT: Adding extended input device "SYNA2393:00 06CB:7A13 Touchpad" (type: TOUCHPAD, id 10)
[    29.336] (**) synaptics: SYNA2393:00 06CB:7A13 Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    29.336] (**) synaptics: SYNA2393:00 06CB:7A13 Touchpad: (accel) MaxSpeed is now 1.75
[    29.336] (**) synaptics: SYNA2393:00 06CB:7A13 Touchpad: (accel) AccelFactor is now 0.130
[    29.336] (**) SYNA2393:00 06CB:7A13 Touchpad: (accel) keeping acceleration scheme 1
[    29.336] (**) SYNA2393:00 06CB:7A13 Touchpad: (accel) acceleration profile 1
[    29.336] (**) SYNA2393:00 06CB:7A13 Touchpad: (accel) acceleration factor: 2.000
[    29.336] (**) SYNA2393:00 06CB:7A13 Touchpad: (accel) acceleration threshold: 4
[    29.337] (--) synaptics: SYNA2393:00 06CB:7A13 Touchpad: touchpad found
[    29.337] (II) config/udev: Adding input device SYNA2393:00 06CB:7A13 Touchpad (/dev/input/mouse1)
[    29.337] (**) SYNA2393:00 06CB:7A13 Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    29.337] (II) config/udev: Adding input device HDA Intel PCH Headphone Mic (/dev/input/event11)
[    29.337] (II) No input driver specified, ignoring this device.
[    29.337] (II) This device may have been added with another device file.
[    29.337] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[    29.337] (II) No input driver specified, ignoring this device.
[    29.337] (II) This device may have been added with another device file.
[    29.337] (II) config/udev: Adding input device Intel HID events (/dev/input/event6)
[    29.337] (**) Intel HID events: Applying InputClass "evdev keyboard catchall"
[    29.337] (II) Using input driver 'evdev' for 'Intel HID events'
[    29.337] (**) Intel HID events: always reports core events
[    29.337] (**) evdev: Intel HID events: Device: "/dev/input/event6"
[    29.337] (--) evdev: Intel HID events: Vendor 0 Product 0
[    29.337] (--) evdev: Intel HID events: Found keys
[    29.337] (II) evdev: Intel HID events: Configuring as keyboard
[    29.337] (**) Option "config_info" "udev:/sys/devices/platform/INT33D5:00/input/input7/event6"
[    29.337] (II) XINPUT: Adding extended input device "Intel HID events" (type: KEYBOARD, id 11)
[    29.337] (**) Option "xkb_rules" "evdev"
[    29.337] (**) Option "xkb_model" "pc105"
[    29.337] (**) Option "xkb_layout" "us"
[    29.338] (II) config/udev: Adding input device Intel HID 5 button array (/dev/input/event7)
[    29.338] (**) Intel HID 5 button array: Applying InputClass "evdev keyboard catchall"
[    29.338] (II) Using input driver 'evdev' for 'Intel HID 5 button array'
[    29.338] (**) Intel HID 5 button array: always reports core events
[    29.338] (**) evdev: Intel HID 5 button array: Device: "/dev/input/event7"
[    29.338] (--) evdev: Intel HID 5 button array: Vendor 0 Product 0
[    29.338] (--) evdev: Intel HID 5 button array: Found keys
[    29.338] (II) evdev: Intel HID 5 button array: Configuring as keyboard
[    29.338] (**) Option "config_info" "udev:/sys/devices/platform/INT33D5:00/input/input8/event7"
[    29.338] (II) XINPUT: Adding extended input device "Intel HID 5 button array" (type: KEYBOARD, id 12)
[    29.338] (**) Option "xkb_rules" "evdev"
[    29.338] (**) Option "xkb_model" "pc105"
[    29.338] (**) Option "xkb_layout" "us"
[    29.338] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event9)
[    29.338] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    29.338] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    29.338] (**) Dell WMI hotkeys: always reports core events
[    29.338] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event9"
[    29.338] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    29.338] (--) evdev: Dell WMI hotkeys: Found keys
[    29.338] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    29.338] (**) Option "config_info" "udev:/sys/devices/platform/PNP0C14:05/wmi_bus/wmi_bus-PNP0C14:05/9DBB5994-A997-11DA-B012-B622A1EF5492/input/input10/event9"
[    29.338] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 13)
[    29.338] (**) Option "xkb_rules" "evdev"
[    29.338] (**) Option "xkb_model" "pc105"
[    29.338] (**) Option "xkb_layout" "us"
[    29.338] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    29.338] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    29.338] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    29.338] (**) AT Translated Set 2 keyboard: always reports core events
[    29.338] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    29.338] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    29.338] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    29.338] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    29.338] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    29.338] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 14)
[    29.338] (**) Option "xkb_rules" "evdev"
[    29.338] (**) Option "xkb_model" "pc105"
[    29.338] (**) Option "xkb_layout" "us"
[    29.339] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    29.339] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    29.339] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchscreen catchall"
[    29.339] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    29.339] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    29.339] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    29.339] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    29.339] (**) Option "Device" "/dev/input/event5"
[    29.376] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    29.376] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1278 - 5664 (res 0)
[    29.376] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1206 - 4646 (res 0)
[    29.376] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    29.376] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    29.376] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    29.376] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    29.376] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    29.376] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    29.376] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    29.412] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event5"
[    29.412] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 15)
[    29.412] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    29.412] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    29.412] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.036
[    29.412] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    29.412] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    29.412] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    29.412] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    29.412] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    29.412] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    29.412] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
```

---

### Post by klaxmaster on 2018-06-01
That is so much info. how do you know what you are looking for in all that?  Trying to learn, not just have ,y problem fixed for me with magic, lol.

here are the other commands


```
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
 69
 70
 71
 72
 73
 74
 75
 76
 77
 78
 79
 80
 81
 82
 83
 84
 85
 86
 87
 88
 89
 90
 91
 92
 93
 94
 95
 96
 97
 98
 99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174
175
176
177
178
179
180
181
182
183
184
185
186
187
188
189
190
191
192
193
194
195
196
197
198
199
200
201
202
203
204
205
206
207
208
209
210
211
212
213
214
215
216
217
218
219
220
221
222
223
224
225
226
227
228
229
230
231
232
233
234
235
236
237
238
239
240
241
242
243
244
245
246
247
248
249
250
251
252
253
254
255
256
257
258
259
260
261
262
263
264
265
266
267
268
269
270
271
272
273
274
275
276
277
278
279
280
281
282
283
284
285
286
287
288
289
290
291
292
293
294
295
296
297
298
299
300
301
302
303
304
305
306
307
308
309
310
311
312
313
314
315
316
317
318
319
320
321
322
323
324
325
326
327
328
329
330
331
332
333
334
335
336
337
338
339
340
341
342
343
344
345
346
347
348
349
350
351
352
353
354
355
356
357
358
359
360
361
362
363
364
365
366
367
368
369
370
371
372
373
374
375
376
377
378
379
380
381
382
383
384
385
386
387
388
389
390
391
392
393
394
395
396
397
398
399
400
401
402
403
404
405
406
407
408
409
410
411
412
413
414
415
416
417
418
419
420
421
422
423
424
425
426
427
428
429
430
431
432
433
434
435
436
437
438
439
440
441
442
443
444
445
446
447
448
449
450
451
452
453
454
455
456
457
458
459
460
461
462
463
464
465
466
467
468
469
470
471
472
473
474
475
476
477
478
479
480
481
482
483
484
485
486
487
488
489
490
491
492
[/TD]
[TD="class: code"]Script started on Fri 01 Jun 2018 02:03:07 PM PDT
root@compy386:~# exitdpkg -l | grep -i nvidia
[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[Cexit[K[Ksudo lshw -C display


DMI

   
SMP

   
PA-RISC

       
device-tree

           
SPD

   
memory

      
/proc/cpuinfo

             
CPUID

     
PCI (sysfs)

           
ISA PnP

       
PCMCIA

      
PCMCIA

      
kernel device tree (sysfs)

                          
USB

   
IDE

   
SCSI

    
Network interfaces

                  
Framebuffer devices

                   
Display

       
CPUFreq

       
ABI

   

  *-display
       description: 3D controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:ec000000-ecffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128) memory:ed000000-ed07ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:eb000000-ebffffff memory:80000000-8fffffff ioport:4000(size=64) memory:c0000-dffff


root@compy386:~# lspci =[K-k | grep -EA2 'VGA|3D'
00:02.0 [01;31m[KVGA[m[K compatible controller: Intel Corporation Device 3e9b
	DeviceName:  Onboard IGD
	Subsystem: Dell Device 087c
[36m[K--[m[K
01:00.0 [01;31m[K3D[m[K controller: NVIDIA Corporation Device 1c8c (rev a1)
	Subsystem: Dell Device 087c
	Kernel driver in use: nvidia



root@compy386:~# sudo dkms status
bbswitch, 0.8, 4.13.0-43-generic, x86_64: installed
root@compy386:~# dpkg -l | grep liu[Knux-
ii  [01;31m[Klinux-[m[Kbase                                  4.5ubuntu1~16.04.1                           all          Linux image base package
ii  [01;31m[Klinux-[m[Kfirmware                              1.157.19                                     all          Firmware for Linux kernel drivers
ii  [01;31m[Klinux-[m[Kgeneric-hwe-16.04                     4.13.0.43.62                                 amd64        Complete Generic Linux kernel and headers
ii  [01;31m[Klinux-[m[Kheaders-4.10.0-28                     4.10.0-28.32~16.04.2                         all          Header files related to Linux kernel version 4.10.0
ii  [01;31m[Klinux-[m[Kheaders-4.10.0-28-generic             4.10.0-28.32~16.04.2                         amd64        Linux kernel headers for version 4.10.0 on 64 bit x86 SMP
ii  [01;31m[Klinux-[m[Kheaders-4.13.0-43                     4.13.0-43.48~16.04.1                         all          Header files related to Linux kernel version 4.13.0
ii  [01;31m[Klinux-[m[Kheaders-4.13.0-43-generic             4.13.0-43.48~16.04.1                         amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
ii  [01;31m[Klinux-[m[Kheaders-generic-hwe-16.04             4.13.0.43.62                                 amd64        Generic Linux kernel headers
ii  [01;31m[Klinux-[m[Kimage-4.10.0-28-generic               4.10.0-28.32~16.04.2                         amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  [01;31m[Klinux-[m[Kimage-4.13.0-43-generic               4.13.0-43.48~16.04.1                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  [01;31m[Klinux-[m[Kimage-extra-4.10.0-28-generic         4.10.0-28.32~16.04.2                         amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  [01;31m[Klinux-[m[Kimage-extra-4.13.0-43-generic         4.13.0-43.48~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  [01;31m[Klinux-[m[Kimage-generic-hwe-16.04               4.13.0.43.62                                 amd64        Generic Linux kernel image
ii  [01;31m[Klinux-[m[Klibc-dev:amd64                        4.4.0-127.153                                amd64        Linux Kernel Headers for development
ii  [01;31m[Klinux-[m[Ksigned-generic-hwe-16.04              4.13.0.43.62                                 amd64        Complete Signed Generic Linux kernel and headers
ii  [01;31m[Klinux-[m[Ksigned-image-4.13.0-43-generic        4.13.0-43.48~16.04.1                         amd64        Signed kernel image generic
ii  [01;31m[Klinux-[m[Ksigned-image-generic-hwe-16.04        4.13.0.43.62                                 amd64        Signed Generic Linux kernel image
ii  [01;31m[Klinux-[m[Ksound-base                            1.0.25+dfsg-0ubuntu5                         all          base package for ALSA and OSS sound systems
ii  sys[01;31m[Klinux-[m[Kcommon                             3:6.03+dfsg-11ubuntu1                        all          collection of bootloaders (common)
ii  sys[01;31m[Klinux-[m[Klegacy                             2:3.63+dfsg-2ubuntu8                         amd64        Bootloader for Linux/i386 using MS-DOS floppies


root@compy386:~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.4 LTS
Release:	16.04
Codename:	xenial



root@compy386:~# echo $XDG_SESSION [K_TYPE\[K


root@compy386:~# cat /var/log/xor[K[K[KXorg.0.log
[    29.206] 
X.Org X Server 1.19.5
Release Date: 2017-10-12
[    29.206] X Protocol Version 11, Revision 0
[    29.206] Build Operating System: Linux 4.4.0-101-generic x86_64 Ubuntu
[    29.206] Current Operating System: Linux compy386 4.13.0-43-generic #48~16.04.1-Ubuntu SMP Thu May 17 12:56:46 UTC 2018 x86_64
[    29.206] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-43-generic.efi.signed root=UUID=bc1ca7fc-5bb1-41bb-ae42-78cb021a7609 ro nomodeset quiet splash vt.handoff=7
[    29.206] Build Date: 24 November 2017  09:44:25AM
[    29.206] xorg-server 2:1.19.5-0ubuntu2~16.04.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    29.206] Current version of pixman: 0.33.6
[    29.206] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    29.206] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.206] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun  1 13:25:03 2018
[    29.206] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.206] (==) No Layout section.  Using the first Screen section.
[    29.206] (==) No screen section available. Using defaults.
[    29.206] (**) |-->Screen "Default Screen Section" (0)
[    29.206] (**) |   |-->Monitor "<default monitor>"
[    29.206] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    29.206] (==) Automatically adding devices
[    29.206] (==) Automatically enabling devices
[    29.206] (==) Automatically adding GPU devices
[    29.206] (==) Automatically binding GPU devices
[    29.206] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    29.206] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.206] 	Entry deleted from font path.
[    29.206] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.206] 	Entry deleted from font path.
[    29.206] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.206] 	Entry deleted from font path.
[    29.206] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.206] 	Entry deleted from font path.
[    29.206] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.206] 	Entry deleted from font path.
[    29.206] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    29.206] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.206] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.206] (II) Loader magic: 0x55bc2471ce00
[    29.206] (II) Module ABI versions:
[    29.206] 	X.Org ANSI C Emulation: 0.4
[    29.206] 	X.Org Video Driver: 23.0
[    29.206] 	X.Org XInput driver : 24.1
[    29.206] 	X.Org Server Extension : 10.0
[    29.207] (++) using VT number 7

[    29.207] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    29.207] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.209] (--) PCI:*(0:0:2:0) 8086:3e9b:1028:087c rev 0, Mem @ 0xeb000000/16777216, 0x80000000/268435456, I/O @ 0x00004000/64, BIOS @ 0x????????/131072
[    29.209] (--) PCI: (0:1:0:0) 10de:1c8c:1028:087c rev 161, Mem @ 0xec000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00003000/128, BIOS @ 0x????????/524288
[    29.209] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    29.209] (II) "glx" will be loaded by default.
[    29.209] (II) LoadModule: "glx"
[    29.209] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    29.211] (II) Module glx: vendor="NVIDIA Corporation"
[    29.211] 	compiled for 4.0.2, module version = 1.0.0
[    29.211] 	Module class: X.Org Server Extension
[    29.211] (II) NVIDIA GLX Module  384.130  Wed Mar 21 02:54:48 PDT 2018
[    29.211] (==) Matched nvidia as autoconfigured driver 0
[    29.211] (==) Matched nouveau as autoconfigured driver 1
[    29.211] (==) Matched modesetting as autoconfigured driver 2
[    29.211] (==) Matched fbdev as autoconfigured driver 3
[    29.211] (==) Matched vesa as autoconfigured driver 4
[    29.211] (==) Assigned the driver to the xf86ConfigLayout
[    29.211] (II) LoadModule: "nvidia"
[    29.211] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    29.212] (II) Module nvidia: vendor="NVIDIA Corporation"
[    29.212] 	compiled for 4.0.2, module version = 1.0.0
[    29.212] 	Module class: X.Org Video Driver
[    29.212] (II) LoadModule: "nouveau"
[    29.212] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    29.212] (II) Module nouveau: vendor="X.Org Foundation"
[    29.212] 	compiled for 1.19.5, module version = 1.0.15
[    29.212] 	Module class: X.Org Video Driver
[    29.212] 	ABI class: X.Org Video Driver, version 23.0
[    29.212] (II) LoadModule: "modesetting"
[    29.212] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    29.212] (II) Module modesetting: vendor="X.Org Foundation"
[    29.212] 	compiled for 1.19.5, module version = 1.19.5
[    29.212] 	Module class: X.Org Video Driver
[    29.212] 	ABI class: X.Org Video Driver, version 23.0
[    29.212] (II) LoadModule: "fbdev"
[    29.212] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.212] (II) Module fbdev: vendor="X.Org Foundation"
[    29.212] 	compiled for 1.19.3, module version = 0.4.4
[    29.212] 	Module class: X.Org Video Driver
[    29.212] 	ABI class: X.Org Video Driver, version 23.0
[    29.212] (II) LoadModule: "vesa"
[    29.212] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.212] (II) Module vesa: vendor="X.Org Foundation"
[    29.212] 	compiled for 1.19.3, module version = 2.3.4
[    29.212] 	Module class: X.Org Video Driver
[    29.212] 	ABI class: X.Org Video Driver, version 23.0
[    29.212] (II) NVIDIA dlloader X Driver  384.130  Wed Mar 21 02:29:29 PDT 2018
[    29.212] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    29.212] (II) NOUVEAU driver Date:   Fri Apr 21 14:41:17 2017 -0400
[    29.212] (II) NOUVEAU driver for NVIDIA chipset families :
[    29.212] 	RIVA TNT        (NV04)
[    29.212] 	RIVA TNT2       (NV05)
[    29.212] 	GeForce 256     (NV10)
[    29.212] 	GeForce 2       (NV11, NV15)
[    29.212] 	GeForce 4MX     (NV17, NV18)
[    29.212] 	GeForce 3       (NV20)
[    29.212] 	GeForce 4Ti     (NV25, NV28)
[    29.212] 	GeForce FX      (NV3x)
[    29.212] 	GeForce 6       (NV4x)
[    29.212] 	GeForce 7       (G7x)
[    29.212] 	GeForce 8       (G8x)
[    29.212] 	GeForce GTX 200 (NVA0)
[    29.212] 	GeForce GTX 400 (NVC0)
[    29.212] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    29.212] (II) FBDEV: driver for framebuffer: fbdev
[    29.212] (II) VESA: driver for VESA chipsets: vesa
[    29.212] (EE) [drm] Failed to open DRM device for (null): -22
[    29.212] (WW) Falling back to old probe method for modesetting
[    29.212] (II) Loading sub module "fbdevhw"
[    29.212] (II) LoadModule: "fbdevhw"
[    29.212] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    29.212] (II) Module fbdevhw: vendor="X.Org Foundation"
[    29.212] 	compiled for 1.19.5, module version = 0.0.2
[    29.212] 	ABI class: X.Org Video Driver, version 23.0
[    29.212] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[    29.212] (II) FBDEV(1): using default device
[    29.212] (WW) Falling back to old probe method for vesa
[    29.212] (EE) Screen 0 deleted because of no matching config section.
[    29.213] (II) UnloadModule: "modesetting"
[    29.213] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    29.213] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    29.213] (==) FBDEV(0): RGB weight 888
[    29.213] (==) FBDEV(0): Default visual is TrueColor
[    29.213] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    29.213] (II) FBDEV(0): hardware: EFI VGA (video memory: 8128kB)
[    29.213] (II) FBDEV(0): checking modes against framebuffer device...
[    29.213] (II) FBDEV(0): checking modes against monitor...
[    29.213] (--) FBDEV(0): Virtual size is 1920x1080 (pitch 1920)
[    29.213] (**) FBDEV(0):  Built-in mode "current": 207.4 MHz, 85.3 kHz, 77.2 Hz
[    29.213] (II) FBDEV(0): Modeline "current"x0.0  207.38  1920 1952 2192 2432  1080 1084 1088 1104 -hsync -vsync -csync (85.3 kHz b)
[    29.213] (==) FBDEV(0): DPI set to (96, 96)
[    29.213] (II) Loading sub module "fb"
[    29.213] (II) LoadModule: "fb"
[    29.213] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.213] (II) Module fb: vendor="X.Org Foundation"
[    29.213] 	compiled for 1.19.5, module version = 1.0.0
[    29.213] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    29.213] (**) FBDEV(0): using shadow framebuffer
[    29.213] (II) Loading sub module "shadow"
[    29.213] (II) LoadModule: "shadow"
[    29.213] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    29.213] (II) Module shadow: vendor="X.Org Foundation"
[    29.213] 	compiled for 1.19.5, module version = 1.1.0
[    29.213] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    29.213] (II) UnloadModule: "vesa"
[    29.213] (II) Unloading vesa
[    29.213] (==) Depth 24 pixmap format is 32 bpp
[    29.213] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[    29.213] (==) FBDEV(0): Backing store enabled
[    29.213] (==) FBDEV(0): DPMS enabled
[    29.213] (==) RandR enabled
[    29.215] (II) SELinux: Disabled on system
[    29.215] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    29.232] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    29.232] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.232] (II) LoadModule: "evdev"
[    29.232] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.232] (II) Module evdev: vendor="X.Org Foundation"
[    29.232] 	compiled for 1.19.3, module version = 2.10.5
[    29.232] 	Module class: X.Org XInput Driver
[    29.232] 	ABI class: X.Org XInput driver, version 24.1
[    29.232] (II) Using input driver 'evdev' for 'Power Button'
[    29.232] (**) Power Button: always reports core events
[    29.232] (**) evdev: Power Button: Device: "/dev/input/event3"
[    29.232] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.232] (--) evdev: Power Button: Found keys
[    29.232] (II) evdev: Power Button: Configuring as keyboard
[    29.232] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    29.232] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    29.232] (**) Option "xkb_rules" "evdev"
[    29.232] (**) Option "xkb_model" "pc105"
[    29.232] (**) Option "xkb_layout" "us"
[    29.232] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    29.232] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.232] (II) Using input driver 'evdev' for 'Power Button'
[    29.232] (**) Power Button: always reports core events
[    29.232] (**) evdev: Power Button: Device: "/dev/input/event1"
[    29.232] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.232] (--) evdev: Power Button: Found keys
[    29.232] (II) evdev: Power Button: Configuring as keyboard
[    29.232] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    29.232] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    29.232] (**) Option "xkb_rules" "evdev"
[    29.232] (**) Option "xkb_model" "pc105"
[    29.232] (**) Option "xkb_layout" "us"
[    29.233] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    29.233] (II) No input driver specified, ignoring this device.
[    29.233] (II) This device may have been added with another device file.
[    29.233] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    29.233] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    29.233] (II) Using input driver 'evdev' for 'Sleep Button'
[    29.233] (**) Sleep Button: always reports core events
[    29.233] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    29.233] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    29.233] (--) evdev: Sleep Button: Found keys
[    29.233] (II) evdev: Sleep Button: Configuring as keyboard
[    29.233] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    29.233] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    29.233] (**) Option "xkb_rules" "evdev"
[    29.233] (**) Option "xkb_model" "pc105"
[    29.233] (**) Option "xkb_layout" "us"
[    29.233] (II) config/udev: Adding input device Integrated_Webcam_HD: Integrate (/dev/input/event8)
[    29.233] (**) Integrated_Webcam_HD: Integrate: Applying InputClass "evdev keyboard catchall"
[    29.233] (II) Using input driver 'evdev' for 'Integrated_Webcam_HD: Integrate'
[    29.233] (**) Integrated_Webcam_HD: Integrate: always reports core events
[    29.233] (**) evdev: Integrated_Webcam_HD: Integrate: Device: "/dev/input/event8"
[    29.233] (--) evdev: Integrated_Webcam_HD: Integrate: Vendor 0xc45 Product 0x671d
[    29.233] (--) evdev: Integrated_Webcam_HD: Integrate: Found keys
[    29.233] (II) evdev: Integrated_Webcam_HD: Integrate: Configuring as keyboard
[    29.233] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-12/1-12:1.0/input/input9/event8"
[    29.233] (II) XINPUT: Adding extended input device "Integrated_Webcam_HD: Integrate" (type: KEYBOARD, id 9)
[    29.233] (**) Option "xkb_rules" "evdev"
[    29.233] (**) Option "xkb_model" "pc105"
[    29.233] (**) Option "xkb_layout" "us"
[    29.234] (II) config/udev: Adding input device SYNA2393:00 06CB:7A13 Touchpad (/dev/input/event10)
[    29.234] (**) SYNA2393:00 06CB:7A13 Touchpad: Applying InputClass "evdev touchpad catchall"
[    29.234] (**) SYNA2393:00 06CB:7A13 Touchpad: Applying InputClass "evdev touchscreen catchall"
[    29.234] (**) SYNA2393:00 06CB:7A13 Touchpad: Applying InputClass "touchpad catchall"
[    29.234] (**) SYNA2393:00 06CB:7A13 Touchpad: Applying InputClass "Default clickpad buttons"
[    29.234] (II) LoadModule: "synaptics"
[    29.234] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    29.234] (II) Module synaptics: vendor="X.Org Foundation"
[    29.234] 	compiled for 1.19.3, module version = 1.9.0
[    29.234] 	Module class: X.Org XInput Driver
[    29.234] 	ABI class: X.Org XInput driver, version 24.1
[    29.234] (II) Using input driver 'synaptics' for 'SYNA2393:00 06CB:7A13 Touchpad'
[    29.234] (**) SYNA2393:00 06CB:7A13 Touchpad: always reports core events
[    29.234] (**) Option "Device" "/dev/input/event10"
[    29.292] (II) synaptics: SYNA2393:00 06CB:7A13 Touchpad: found clickpad property
[    29.292] (--) synaptics: SYNA2393:00 06CB:7A13 Touchpad: x-axis range 0 - 1228 (res 12)
[    29.292] (--) synaptics: SYNA2393:00 06CB:7A13 Touchpad: y-axis range 0 - 928 (res 12)
[    29.292] (II) synaptics: SYNA2393:00 06CB:7A13 Touchpad: device does not report pressure, will use touch data.
[    29.292] (II) synaptics: SYNA2393:00 06CB:7A13 Touchpad: device does not report finger width.
[    29.292] (--) synaptics: SYNA2393:00 06CB:7A13 Touchpad: buttons: left double triple
[    29.292] (--) synaptics: SYNA2393:00 06CB:7A13 Touchpad: Vendor 0x6cb Product 0x7a13
[    29.292] (--) synaptics: SYNA2393:00 06CB:7A13 Touchpad: invalid pressure range.  defaulting to 0 - 255
[    29.292] (--) synaptics: SYNA2393:00 06CB:7A13 Touchpad: invalid finger width range.  defaulting to 0 - 15
[    29.292] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    29.292] (--) synaptics: SYNA2393:00 06CB:7A13 Touchpad: touchpad found
[    29.292] (**) SYNA2393:00 06CB:7A13 Touchpad: always reports core events
[    29.336] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-1/i2c-SYNA2393:00/0018:06CB:7A13.0001/input/input12/event10"
[    29.336] (II) XINPUT: Adding extended input device "SYNA2393:00 06CB:7A13 Touchpad" (type: TOUCHPAD, id 10)
[    29.336] (**) synaptics: SYNA2393:00 06CB:7A13 Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    29.336] (**) synaptics: SYNA2393:00 06CB:7A13 Touchpad: (accel) MaxSpeed is now 1.75
[    29.336] (**) synaptics: SYNA2393:00 06CB:7A13 Touchpad: (accel) AccelFactor is now 0.130
[    29.336] (**) SYNA2393:00 06CB:7A13 Touchpad: (accel) keeping acceleration scheme 1
[    29.336] (**) SYNA2393:00 06CB:7A13 Touchpad: (accel) acceleration profile 1
[    29.336] (**) SYNA2393:00 06CB:7A13 Touchpad: (accel) acceleration factor: 2.000
[    29.336] (**) SYNA2393:00 06CB:7A13 Touchpad: (accel) acceleration threshold: 4
[    29.337] (--) synaptics: SYNA2393:00 06CB:7A13 Touchpad: touchpad found
[    29.337] (II) config/udev: Adding input device SYNA2393:00 06CB:7A13 Touchpad (/dev/input/mouse1)
[    29.337] (**) SYNA2393:00 06CB:7A13 Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    29.337] (II) config/udev: Adding input device HDA Intel PCH Headphone Mic (/dev/input/event11)
[    29.337] (II) No input driver specified, ignoring this device.
[    29.337] (II) This device may have been added with another device file.
[    29.337] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[    29.337] (II) No input driver specified, ignoring this device.
[    29.337] (II) This device may have been added with another device file.
[    29.337] (II) config/udev: Adding input device Intel HID events (/dev/input/event6)
[    29.337] (**) Intel HID events: Applying InputClass "evdev keyboard catchall"
[    29.337] (II) Using input driver 'evdev' for 'Intel HID events'
[    29.337] (**) Intel HID events: always reports core events
[    29.337] (**) evdev: Intel HID events: Device: "/dev/input/event6"
[    29.337] (--) evdev: Intel HID events: Vendor 0 Product 0
[    29.337] (--) evdev: Intel HID events: Found keys
[    29.337] (II) evdev: Intel HID events: Configuring as keyboard
[    29.337] (**) Option "config_info" "udev:/sys/devices/platform/INT33D5:00/input/input7/event6"
[    29.337] (II) XINPUT: Adding extended input device "Intel HID events" (type: KEYBOARD, id 11)
[    29.337] (**) Option "xkb_rules" "evdev"
[    29.337] (**) Option "xkb_model" "pc105"
[    29.337] (**) Option "xkb_layout" "us"
[    29.338] (II) config/udev: Adding input device Intel HID 5 button array (/dev/input/event7)
[    29.338] (**) Intel HID 5 button array: Applying InputClass "evdev keyboard catchall"
[    29.338] (II) Using input driver 'evdev' for 'Intel HID 5 button array'
[    29.338] (**) Intel HID 5 button array: always reports core events
[    29.338] (**) evdev: Intel HID 5 button array: Device: "/dev/input/event7"
[    29.338] (--) evdev: Intel HID 5 button array: Vendor 0 Product 0
[    29.338] (--) evdev: Intel HID 5 button array: Found keys
[    29.338] (II) evdev: Intel HID 5 button array: Configuring as keyboard
[    29.338] (**) Option "config_info" "udev:/sys/devices/platform/INT33D5:00/input/input8/event7"
[    29.338] (II) XINPUT: Adding extended input device "Intel HID 5 button array" (type: KEYBOARD, id 12)
[    29.338] (**) Option "xkb_rules" "evdev"
[    29.338] (**) Option "xkb_model" "pc105"
[    29.338] (**) Option "xkb_layout" "us"
[    29.338] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event9)
[    29.338] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    29.338] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    29.338] (**) Dell WMI hotkeys: always reports core events
[    29.338] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event9"
[    29.338] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    29.338] (--) evdev: Dell WMI hotkeys: Found keys
[    29.338] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    29.338] (**) Option "config_info" "udev:/sys/devices/platform/PNP0C14:05/wmi_bus/wmi_bus-PNP0C14:05/9DBB5994-A997-11DA-B012-B622A1EF5492/input/input10/event9"
[    29.338] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 13)
[    29.338] (**) Option "xkb_rules" "evdev"
[    29.338] (**) Option "xkb_model" "pc105"
[    29.338] (**) Option "xkb_layout" "us"
[    29.338] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    29.338] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    29.338] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    29.338] (**) AT Translated Set 2 keyboard: always reports core events
[    29.338] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    29.338] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    29.338] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    29.338] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    29.338] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    29.338] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 14)
[    29.338] (**) Option "xkb_rules" "evdev"
[    29.338] (**) Option "xkb_model" "pc105"
[    29.338] (**) Option "xkb_layout" "us"
[    29.339] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    29.339] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    29.339] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchscreen catchall"
[    29.339] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    29.339] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    29.339] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    29.339] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    29.339] (**) Option "Device" "/dev/input/event5"
[    29.376] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    29.376] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1278 - 5664 (res 0)
[    29.376] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1206 - 4646 (res 0)
[    29.376] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    29.376] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    29.376] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    29.376] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    29.376] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    29.376] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    29.376] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    29.412] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event5"
[    29.412] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 15)
[    29.412] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    29.412] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    29.412] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.036
[    29.412] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    29.412] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    29.412] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    29.412] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    29.412] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    29.412] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    29.412] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
root@compy386:~# exit
exit

Script done on Fri 01 Jun 2018 02:06:36 PM PDT

```

---

### Post by Bashing-om on 2018-06-01
klaxmaster; Ho boy ---

From the Xorg log file:
> 
[ 29.206] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-43-generic.efi.signed root=UUID=bc1ca7fc-5bb1-41bb-ae42-78cb021a7609 ro [color=red]nomodeset[/color] quiet splash vt.handoff=7

so long as 'nomodeset' is set. then Kernel Mode Setting is disabled, no can load a higher level GUI driver. How are you setting 'nomodeset' ?

Also; we have no driver loaded for the Intel chip set .. nomodeset also effecting? .. just do not know a lot about the Intel side of things, but as the nvidia data stream passes through the Intel chip set, got to have Intel operational for nvidia to function.

Remove the nomodeset boot parameter. reboot and let's see now what we have . 


As to how we learn these things ... time and effort ! .. breaking the system many times and learning how we broke it .. and then how we fix it .. time and effort .. and a *LOT* of reading :)

[INDENT][INDENT]still on the hunt[/INDENT][/INDENT]

---

### Post by wildmanne39 on 2018-06-01
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by klaxmaster on 2018-06-01
TY. will do that from now on

---

### Post by klaxmaster on 2018-06-01
Didn't realize nomodeset was on at that moment, but it makes no real difference. i've gone through various iterations of fixes with it both on and off.

shall i regrab the last commands and xorg with nomodeset disabled?

---

### Post by Bashing-om on 2018-06-01
klaxmaster; Well ..
Try this; at the login screen choose the guest session and boot in there .. is the GUI functional in the guest session ?

If so, then we have it isolated to a config issue in your account .
as to:
> 
shall i regrab the last commands and xorg with nomodeset disabled?

we put that back in our back pocket and see'n what the guest account yields.

[INDENT][INDENT]maybe this maybe that[/INDENT][/INDENT]

---

### Post by klaxmaster on 2018-06-01
Sorry, the guest account is no dice. double checked it right now.

update: I have blacklisted the nouveau drivers at the request of the director of it. I used this:

[https://askubuntu.com/questions/841876/how-to-disable-nouveau-kernel-driver;](https://askubuntu.com/questions/841876/how-to-disable-nouveau-kernel-driver;)

and nothing changed. and in the xorg.0 it looks like it is still loading anyway

---

### Post by Bashing-om on 2018-06-01
klaxmaster; Hummm ..

System wide issue .

The nouveau driver is blacklisted per the gpu-manager log:
> 
Is nouveau loaded? no
Is nouveau blacklisted? yes


Hybrid graphics and the /etc/X11/Xorg.conf config file is required in 16.04; does the file exist ?
```

cat /etc/X11/Xorg.conf

```

Gotta be a reason, and I keep on look'n .
[INDENT]inquiring minds want to know
[/INDENT]

---

### Post by klaxmaster on 2018-06-01
there is a xorg.conf.failsafe only

---

### Post by monkeybrain20122 on 2018-06-01
> **apmarek said:**
> What you want to do is try running the nouveau drivers instead of the NVIDIA ones. A reference link to set this up is here: [https://askubuntu.com/questions/360761/cannot-get-rid-of-nvidia-drivers-restore-nouveau-driver-and-get-desktop-working](https://askubuntu.com/questions/360761/cannot-get-rid-of-nvidia-drivers-restore-nouveau-driver-and-get-desktop-working)
Also, check what kernel version you have by typing "uname -r". We need to know if you are running kernel 4.16, as there are some NVIDIA hangups on that kernel version. I had to edit my grub2.cfg to restore NVIDIA functionality.

That is not a solution. Why would you pay for an expensive nvidia gpu and run noveau on it? You'll save a lot of money and get better result with an intel card.

---

### Post by Bashing-om on 2018-06-01
klaxmaster; Well well !

As I said, in 16.04 that config file is required. and should have been generated when the driver was building.

How about we take a shot in the dark here and see what results when we have nvidia build the file:
```

sudo nvidia-xconfig

```

If it generates the file with no errors, reboot then to see the effect.

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by klaxmaster on 2018-06-01
> **monkeybrain20122 said:**
> That is not a solution. Why would you pay for an expensive nvidia gpu and run noveau on it? You'll save a lot of money and get better result with an intel card.


Agreed. lol. and this isn't a for fun machine anyway. our software team needs those cards and to use it to its full potential

---

### Post by klaxmaster on 2018-06-01
> **Bashing-om said:**
> klaxmaster; Well well !

As I said, in 16.04 that config file is required. and should have been generated when the driver was building.

How about we take a shot in the dark here and see what results when we have nvidia build the file:
```

sudo nvidia-xconfig

```

If it generates the file with no errors, reboot then to see the effect.[INDENT][INDENT]sometimes I do wonder
[/INDENT]
[/INDENT]


generated without any errors. still have the login loop. here is what it generated.

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 384.130  (buildmeister@swio-display-x86-rhel47-03)  Wed Mar 21 04:09:03 PDT 2018


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection


Section "Files"
EndSection


Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection


Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection


Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by monkeybrain20122 on 2018-06-01
The login loop seems to mean the driver is not building with the kernel. Maybe trying a different kernel like boot into noveau, download kernel 4.15 from mainline ppa and then upgrade and try again? Is this an optimus machine?

P.S. if you are using cuda there should be a cuda-driver from Nvidia's cuda package for your card. Maybe you should try that one instead of the repo.

---

### Post by Bashing-om on 2018-06-01
klaxmaster; Humm ..

Still no sign of the Intel chip set.
Let's try and get the Intel card recognized:
Remove the config file:
```

sudo rm /etc/X11/xorg.conf

```

Now see what results when we re-install the Xserver components:
```

sudo apt-get install --reinstall xserver-xorg-core xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri libgl1-mesa-glx:i386 libgl1-mesa-dri:i386  
sudo dpkg-reconfigure xserver-xorg 
sudo reboot

```


After the reboot, what have we now to work with ?
```

sudo lshw -C display

```

[INDENT][INDENT]gots to be some joy somewhere
[/INDENT][/INDENT]

---

### Post by klaxmaster on 2018-06-04
the entire gui seems to be broken now. lol

just displays
```
/dev/[drive]: clean ###/### files, ###/### blocks
```
when trying to boot into desktop. 

have to ctrl+alt+fn+F# into terminal.

---

### Post by Bashing-om on 2018-06-04
klaxmaster; Yukkie poo

And we still do not know why Intel is acting up  - was hoping to get the Intel chip set recognized; Intel is enabled in bios else Xorg would not see it.

what shows:
```

echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
cat /etc/X11/default-display-manager
ls /usr/share/xsessions
sudo lshw -C display

```
So we know what we are working with in 16.04.

[INDENT][INDENT]'times I just do not know
[/INDENT][/INDENT]

---

### Post by klaxmaster on 2018-06-07
Hey Bashing-om, we got it working. 

After my own defeat, and the company starting to take a loss of productivity, (4 new hires with out a laptop for almost a week!) the sys admin and director of it spent a couple days on it, and around 3am last night, got it working.

there is a single kernel that it is working on. all these steps performed on kernel 4.10 through the latest do not work. 

except on 4.15..0-15

here is the magic

```

#!/bin/sh


sed -i 's/Update-Package-Lists "1"/Update-Package-Lists "0"/' /etc/apt/apt.conf.d/10periodic
sed -i 's/Update-Package-Lists "1"/Update-Package-Lists "0"/' /etc/apt/apt.conf.d/20auto-upgrades
sed -i 's/Unattended-Upgrade "1"/Unattended-Upgrade "0"/' /etc/apt/apt.conf.d/20auto-upgrades
sed -i 's/^GRUB_HIDDEN/#GRUB_HIDDEN/g' /etc/default/grub
update-grub


add-apt-repository ppa:graphics-drivers/ppa -y
apt-get update
apt-get dist-upgrade -y
apt-get install linux-image-extra-4.15.0-15-generic linux-headers-4.15.0-15 linux-headers-4.15.0-15-generic -y
apt-get install nvidia-390 -y
apt-get autoremove -y
apt-get autoclean
apt-get clean
sync

```

---

### Post by klaxmaster on 2018-06-07
as you can see, it basically works out of box with that kernel. and just literally doesn't work on any other kernel.

here is hoping that anyone who wants to use an nvidia driver on a 9570 using 16.04 comes across this thread!

weird problem for a piece of new hardware to have...

---

### Post by Bashing-om on 2018-06-07
klaxmaster; Humm ..

unexpected method of resolution - driver does not build on 4.15.0.22.23 ??
If it does not - for what ever reason - be good to start a bug report .

For my peace of mind - what shows now :
```

sudo lshw -C display
dpkg -l | grep -i nvidia
dpkg -l | grep linux-

```
'cause
[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by petersimi on 2018-06-08
I spent about 2 days straight on the EXACT process that klaxmaster has  gone through on the 9570 (Ubuntu 16.04, tried every driver version,  every driver installation method, all the common attempts for login loop  with lightdm, .Xauthority, ran nvidia-xconfig, blacklist nouveau, etc.  -- literally everything) and his solution in post #28 is finally what  worked. THANK YOU!

---

### Post by aimaster on 2018-07-08
> **klaxmaster said:**
> Hey Bashing-om, we got it working. 

After my own defeat, and the company starting to take a loss of productivity, (4 new hires with out a laptop for almost a week!) the sys admin and director of it spent a couple days on it, and around 3am last night, got it working.

there is a single kernel that it is working on. all these steps performed on kernel 4.10 through the latest do not work. 

except on 4.15..0-15

here is the magic



Cheers, mate. I created an account just to thank you for saving me from having to compile a new kernel to get it working.

---

### Post by clemw on 2018-07-21
I'm having the same/similar problem, except that things were working until a few days ago after I did some sort of system update (not sure exactly what...)  What happens to me now, is when I try to attach my Dell monitor, the mouse and keyboard lock up.  (To recover, I hit C-A-F1, remove the Dell monitor and hit C-A-F7 to log back in.)  I'm not having trouble with my new big IIIP monitor which is connected via HDMI.  I was trying to add the Dell monitor via Thunderbolt.  The model of the Dell is P2213

My system:

 uname -a
Linux clem-lt 4.15.0-24-generic #26~16.04.1-Ubuntu SMP Fri Jun 15 14:35:08 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

* NVidia Driver 396.37
* X Server version 11.0
* Server Vendor Version 1.19.6
* NV-Control Version 1.29

I have an NVidia 1080 card.

---

### Post by klaxmaster on 2018-07-21
> **clemw said:**
> I'm having the same/similar problem, except that things were working until a few days ago after I did some sort of system update (not sure exactly what...)  What happens to me now, is when I try to attach my Dell monitor, the mouse and keyboard lock up.  (To recover, I hit C-A-F1, remove the Dell monitor and hit C-A-F7 to log back in.)  I'm not having trouble with my new big IIIP monitor which is connected via HDMI.  I was trying to add the Dell monitor via Thunderbolt.  The model of the Dell is P2213

My system:

 uname -a
Linux clem-lt 4.15.0-24-generic #26~16.04.1-Ubuntu SMP Fri Jun 15 14:35:08 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

* NVidia Driver 396.37
* X Server version 11.0
* Server Vendor Version 1.19.6
* NV-Control Version 1.29

I have an NVidia 1080 card.

Problem seems a bit different. I did notice that you are not using the suggested kernel though, maybe try the -15 version? 
I have always had a problem with display link on ubuntu (and its recent complete incompatibility with OS X) is the thunderbolt using displaylink?

---

### Post by klaxmaster on 2018-07-21
Nice, glad it helped!

---

### Post by klaxmaster on 2018-07-21
> **petersimi said:**
> I spent about 2 days straight on the EXACT process that klaxmaster has  gone through on the 9570 (Ubuntu 16.04, tried every driver version,  every driver installation method, all the common attempts for login loop  with lightdm, .Xauthority, ran nvidia-xconfig, blacklist nouveau, etc.  -- literally everything) and his solution in post #28 is finally what  worked. THANK YOU!

Nice! Glad you got your machine working. 

also found out recently that the 9560's discontinued. so we have to start using 9570's from here on out. =/

I can already hear the software engineers saying 'i didnt do anything, no changes. it just didnt boot this morning!' when they update their kernel and the machine no longer boots. ,-_-,

---

### Post by jimmyleehales on 2018-08-27
I'm having the same issue. I've run your code, yet after I reboot I run `uname -a` and I'm seeing:

'4.15.0-33-generic...'

It doesn't seem to be installing the older kernal :/ Do you have any idea why that might be?

---

### Post by klaxmaster on 2018-08-30
just want to be sure you're on ubuntu 16.04 (I don't think 16.04 would grab a 4.15 kernel. in fact, i know it only uses 4.4 by default, unless you dist-upgrade, or install linux-image, even then, you would have to add a repository to go past 4.13)

If you are, you should be able to edit grub to point to the kernel you want. grub otherwise it will auto load the newest version, which in this case, is 4.15.0-33,.

If you REALLY want, you can sudo apt-get purge the kernel after it, but its not totally necessary.  If you want to test it before you change grub, you can go to 'advance settings' in the boot menu, and choose a specific kernel

---

