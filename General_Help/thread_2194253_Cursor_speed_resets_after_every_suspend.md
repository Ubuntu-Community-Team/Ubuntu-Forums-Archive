---
title: "Cursor speed resets after every suspend"
date: 2013-12-17
forum: General Help
---

### Post by Thee on 2013-12-17
Hi

I got a problem with setting the cursor speed. I use the following setting for my needs:
```
xset m 2/1 4
```
But whenever I suspend my computer, the settings reset and I have to do it all over again. is there a way to make it permanent?

Thanks

---

### Post by Toz on 2013-12-17
Try adding that information to the xorg configuration files (instead of running xset). It should make it a permanent default. To do so, either add the releavant entries to your **/etc/X11/xorg.conf** file if you have one, or in the absence of an /etc/X11/xorg.conf file, create (with root privileges) the file **/usr/share/X11/xorg.conf.d/50-mouse-acceleration.conf** with the following content:
```
Section "InputClass"
	Identifier "My Mouse"
	MatchIsPointer "yes"
	Option "AccelerationNumerator" "2"
	Option "AccelerationDenominator" "1"
	Option "AccelerationThreshold" "4"
EndSection
```
...and log out and back in again to test. Review the /var/log/Xorg.0.log file to confirm that these settings were applied.

---

### Post by Thee on 2013-12-18
Hi, thanks for your suggestion. I added what you wrote to the /etc/X11/xorg.conf, but I'm still having the same problem...
Here is the /var/log/Xorg.0.log
```

[    18.459] (II) evdev: Microsoft Comfort Mouse 6000: initialized for relative axes.
[    18.459] (WW) evdev: Microsoft Comfort Mouse 6000: ignoring absolute axes.
[    18.460] (**) Microsoft Comfort Mouse 6000: (accel) keeping acceleration scheme 1
[    18.460] (**) Microsoft Comfort Mouse 6000: (accel) acceleration profile 0
[    18.460] (**) Option "AccelerationNumerator" "2"
[    18.460] (**) Option "AccelerationDenominator" "1"
[    18.460] (**) Option "AccelerationThreshold" "4"
[    18.460] (**) Microsoft Comfort Mouse 6000: (accel) acceleration factor: 2.000
[    18.460] (**) Microsoft Comfort Mouse 6000: (accel) acceleration threshold: 4
[    18.460] (II) config/udev: Adding input device Microsoft Comfort Mouse 6000 (/dev/input/mouse0)
[    18.460] (**) Microsoft Comfort Mouse 6000: Applying InputClass "My Mouse"
[    18.460] (II) No input driver specified, ignoring this device.
[    18.460] (II) This device may have been added with another device file.

```

---

### Post by Toz on 2013-12-18
Did the mouse work properly on boot (with respect to cursor speed) but got reset after suspend again?

What happens if you manually unload the psmouse module prior to suspending:
```
sudo modprobe -r psmouse
```
...then suspend and on resume, manually reload the module:
```
sudo modprobe psmouse
```
...are the settings maintained?

What modules are currently loaded?
```
lsmod
```

---

### Post by Thee on 2013-12-18
No, it didn't work on boot.
Nothing happens when unloading on suspend / loading on wake (cursor speed still resets).

```

Module                  Size  Used by
psmouse                97626  0 
arc4                   12608  0 
md4                    12595  0 
nls_utf8               12557  0 
cifs                  435684  0 
vesafb                 13828  1 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               320455  3 vboxnetadp,vboxnetflt,vboxpci
autofs4                38645  2 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  0 
bnep                   19564  2 
bluetooth             371874  10 bnep,rfcomm
binfmt_misc            17468  1 
nfsd                  279192  2 
auth_rpcgss            54489  1 nfsd
nfs_acl                12837  1 nfsd
nfs                   180519  0 
lockd                  93583  2 nfs,nfsd
sunrpc                271025  6 nfs,nfsd,auth_rpcgss,lockd,nfs_acl
fscache                58475  2 nfs,cifs
joydev                 17377  0 
hid_generic            12548  0 
snd_usb_audio         149162  1 
snd_usbmidi_lib        25070  1 snd_usb_audio
gspca_pac7302          17481  0 
usbhid                 53014  0 
gspca_main             36692  1 gspca_pac7302
hid                   101512  2 hid_generic,usbhid
videodev              133390  2 gspca_main,gspca_pac7302
kvm_amd                59958  0 
kvm                   431315  1 kvm_amd
snd_hda_codec_hdmi     41276  1 
snd_cmipci             44561  2 
snd_mpu401_uart        14169  1 snd_cmipci
snd_hda_codec_realtek    51465  1 
snd_opl3_lib           19131  1 snd_cmipci
gameport               15435  1 snd_cmipci
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_intel          48171  5 
microcode              23518  0 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_rawmidi            30095  3 snd_usbmidi_lib,snd_mpu401_uart,snd_seq_midi
snd_hwdep              13602  3 snd_usb_audio,snd_hda_codec,snd_opl3_lib
snd_pcm               102033  5 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_cmipci
k10temp                13126  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
serio_raw              13413  0 
edac_core              62312  0 
edac_mce_amd           22617  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  4 snd_seq,snd_rawmidi,snd_opl3_lib,snd_seq_midi
snd_timer              29433  3 snd_pcm,snd_seq,snd_opl3_lib
snd                    69141  32 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_mpu401_uart,snd_seq_device,snd_cmipci,snd_opl3_lib,snd_seq_midi
fglrx                6732934  157 
sp5100_tco             13979  0 
i2c_piix4              22106  0 
amd_iommu_v2           19025  1 fglrx
soundcore              12680  1 snd
mac_hid                13205  0 
wmi                    19070  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
r8169                  67341  0 
mii                    13934  1 r8169
firewire_ohci          40060  0 
pata_acpi              13038  0 
firewire_core          64476  1 firewire_ohci
pata_atiixp            13242  0 
pata_jmicron           12758  0 
crc_itu_t              12707  1 firewire_core
ohci_pci               13561  0 
ahci                   25819  2 
libahci                31898  1 ahci

```

---

### Post by Toz on 2013-12-18
> **Thee said:**
> No, it didn't work on boot.
Nothing happens when unloading on suspend / loading on wake (cursor speed still resets).


Okay, remove the /usr/share/X11/xorg.conf.d/50-mouse-acceleration.conf file since its not working.

Lets try this approach instead. Create the file **/etc/pm/sleep.d/000fix_mouse_acceleration** with the following content:
```

#!/bin/sh
export DISPLAY=":0"
case "$1" in
    thaw|resume)
        /usr/bin/xset m 2/1 4
    ;;
esac
```
...save the file and make it executable. It will be run everytime the system resumes from suspend or hibernate and should re-set the mouse settings. Review the /var/log/pm-suspend.log file for errors/messages if it doesn't work.

---

### Post by Thee on 2013-12-18
Still the same.

```

Running hook /etc/pm/sleep.d/000fix_mouse_acceleration resume suspend:
No protocol specified
/usr/bin/xset:  unable to open display ":0"
/etc/pm/sleep.d/000fix_mouse_acceleration resume suspend: Returned exit code 1.

```

---

### Post by Toz on 2013-12-18
Perhaps we need to export Xauthority as well. Change the /etc/pm/sleep.d/000fix_mouse_acceleration file to look like this:
```
#!/bin/sh
username=MYUSERNAME
userhome=/home/$username
export XAUTHORITY="$userhome/.Xauthority"
export DISPLAY=":0"
case "$1" in
    thaw|resume)
        su -c $username "/usr/bin/xset m 2/1 4"
    ;;
esac
```
...change MYUSERNAME to be your system username and try again. Refer to /var/log/pm-suspend.log for errors if it doesn't work.

---

### Post by Thee on 2013-12-19
```

Running hook /etc/pm/sleep.d/000fix_mouse_acceleration resume suspend:
No passwd entry for user '/usr/bin/xset m 2/1 4'
/etc/pm/sleep.d/000fix_mouse_acceleration resume suspend: Returned exit code 1.

```

---

### Post by Toz on 2013-12-19
Can you post back the contents of your /etc/pm/sleep.d/000fix_mouse_acceleration file for a quick once-over? Something might be amiss in the file.

---

### Post by Thee on 2013-12-19
```

#!/bin/sh
username=thee
userhome=/home/$username
export XAUTHORITY="$userhome/.Xauthority"
export DISPLAY=":0"
case "$1" in
    thaw|resume)
        su -c $username "/usr/bin/xset m 2/1 4"
    ;;
esac

```

---

### Post by Toz on 2013-12-19
Oops, my bad. Got the su command wrong. Try this instead:
```
#!/bin/sh
username=thee
userhome=/home/$username
export XAUTHORITY="$userhome/.Xauthority"
export DISPLAY=":0"
case "$1" in
    thaw|resume)
        su $username -c "/usr/bin/xset m 2/1 4"
    ;;
esac
```

---

### Post by Thee on 2013-12-20
```
Running hook /etc/pm/sleep.d/000fix_mouse_acceleration resume suspend:
/etc/pm/sleep.d/000fix_mouse_acceleration resume suspend: success.
```

The log shows as successful, but my mouse speed is still unchanged after suspend :/ this is getting silly

---

### Post by Toz on 2013-12-20
> **Thee said:**
> this is getting silly
It sure is. I wonder whether something later on in the resume cycle is overwritting that setting change back to the default. Try adding a delay:
```
su $username -c "/usr/bin/sleep 3; /usr/bin/xset m 2/1 4" &
```
...also try adjusting the "sleep 3" to longer durations.

Ideally, fixing it in the Xorg config files would be the way to go to make it default. Can you post back your complete /var/log/Xorg.0.log file (without the /X11/xorg.conf.d/50-mouse-acceleration.conf active), so I can see whether the configuration file is wrong and maybe the information could go elsewhere? Perhaps /usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf, assuming we can figure out the correct matching tags).

---

### Post by Thee on 2013-12-21
Same thing happens with the timer script, set to 7.
Here's the log.

```

[    19.370] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[    19.370] X Protocol Version 11, Revision 0
[    19.370] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    19.370] Current Operating System: Linux thee-ubuntu 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64
[    19.370] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-12-generic root=UUID=15e6c8c3-360b-4c28-98d8-c0f2d0581de9 ro quiet splash vt.handoff=7
[    19.370] Build Date: 15 October 2013  09:23:37AM
[    19.370] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    19.370] Current version of pixman: 0.30.2
[    19.370] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    19.370] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.370] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 21 08:05:15 2013
[    19.370] (==) Using config file: "/etc/X11/xorg.conf"
[    19.370] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.371] (==) ServerLayout "aticonfig Layout"
[    19.371] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    19.371] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    19.371] (**) |   |-->Device "aticonfig-Device[0]-0"
[    19.371] (==) Automatically adding devices
[    19.371] (==) Automatically enabling devices
[    19.371] (==) Automatically adding GPU devices
[    19.371] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.371] 	Entry deleted from font path.
[    19.371] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.371] 	Entry deleted from font path.
[    19.371] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.371] 	Entry deleted from font path.
[    19.371] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.371] 	Entry deleted from font path.
[    19.371] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.371] 	Entry deleted from font path.
[    19.371] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    19.371] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.371] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.371] (II) Loader magic: 0x7f39b6e1dd20
[    19.371] (II) Module ABI versions:
[    19.371] 	X.Org ANSI C Emulation: 0.4
[    19.371] 	X.Org Video Driver: 14.1
[    19.371] 	X.Org XInput driver : 19.1
[    19.371] 	X.Org Server Extension : 7.0
[    19.373] (--) PCI:*(0:1:0:0) 1002:6739:1787:0b00 rev 0, Mem @ 0xd0000000/268435456, 0xfdec0000/131072, I/O @ 0x0000ee00/256, BIOS @ 0x????????/131072
[    19.373] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.373] Initializing built-in extension Generic Event Extension
[    19.373] Initializing built-in extension SHAPE
[    19.373] Initializing built-in extension MIT-SHM
[    19.373] Initializing built-in extension XInputExtension
[    19.373] Initializing built-in extension XTEST
[    19.373] Initializing built-in extension BIG-REQUESTS
[    19.373] Initializing built-in extension SYNC
[    19.373] Initializing built-in extension XKEYBOARD
[    19.373] Initializing built-in extension XC-MISC
[    19.373] Initializing built-in extension SECURITY
[    19.373] Initializing built-in extension XINERAMA
[    19.373] Initializing built-in extension XFIXES
[    19.373] Initializing built-in extension RENDER
[    19.373] Initializing built-in extension RANDR
[    19.373] Initializing built-in extension COMPOSITE
[    19.373] Initializing built-in extension DAMAGE
[    19.373] Initializing built-in extension MIT-SCREEN-SAVER
[    19.373] Initializing built-in extension DOUBLE-BUFFER
[    19.373] Initializing built-in extension RECORD
[    19.373] Initializing built-in extension DPMS
[    19.373] Initializing built-in extension X-Resource
[    19.373] Initializing built-in extension XVideo
[    19.373] Initializing built-in extension XVideo-MotionCompensation
[    19.373] Initializing built-in extension SELinux
[    19.373] Initializing built-in extension XFree86-VidModeExtension
[    19.373] Initializing built-in extension XFree86-DGA
[    19.373] Initializing built-in extension XFree86-DRI
[    19.373] Initializing built-in extension DRI2
[    19.373] (II) "glx" will be loaded by default.
[    19.373] (WW) "xmir" is not to be loaded by default. Skipping.
[    19.373] (II) LoadModule: "glx"
[    19.374] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    19.374] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    19.374] 	compiled for 6.9.0, module version = 1.0.0
[    19.374] Loading extension GLX
[    19.374] (II) LoadModule: "fglrx"
[    19.401] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    19.419] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    19.419] 	compiled for 1.4.99.906, module version = 13.10.10
[    19.419] 	Module class: X.Org Video Driver
[    19.419] (II) Loading sub module "fglrxdrm"
[    19.419] (II) LoadModule: "fglrxdrm"
[    19.419] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    19.434] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    19.434] 	compiled for 1.4.99.906, module version = 13.10.10
[    19.434] (II) AMD Proprietary Linux Driver Version Identifier:13.10.10
[    19.434] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-13.101                   
[    19.434] (II) AMD Proprietary Linux Driver Build Date: May 23 2013 15:49:35
[    19.434] (++) using VT number 7


[    19.434] (WW) Falling back to old probe method for fglrx
[    19.442] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    19.444] ukiDynamicMajor: found major device number 250
[    19.444] ukiDynamicMajor: found major device number 250
[    19.444] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    19.444] ukiOpenDevice: node name is /dev/ati/card0
[    19.444] ukiOpenDevice: open result is 10, (OK)
[    19.606] ukiOpenByBusid: ukiOpenMinor returns 10
[    19.606] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    19.642] (--) Chipset Supported AMD Graphics Processor (0x6739) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:2:0) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:9:0) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:10:0) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:0) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:1) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:2) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:3) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:0) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:2) found
[    19.642] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    19.642] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    19.642] (II) AMD Video driver is signed
[    19.642] (II) fglrx(0): pEnt->device->identifier=0x7f39b882e4b0
[    19.642] (II) fglrx(0): === [xdl_xs114_atiddxPreInit] === begin
[    19.643] (II) Loading sub module "vgahw"
[    19.643] (II) LoadModule: "vgahw"
[    19.666] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    19.666] (II) Module vgahw: vendor="X.Org Foundation"
[    19.666] 	compiled for 1.14.3, module version = 0.1.0
[    19.666] 	ABI class: X.Org Video Driver, version 14.1
[    19.667] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    19.667] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    19.667] (==) fglrx(0): Default visual is TrueColor
[    19.667] (**) fglrx(0): Option "DPMS" "true"
[    19.667] (==) fglrx(0): RGB weight 888
[    19.667] (II) fglrx(0): Using 8 bits per RGB 
[    19.667] (==) fglrx(0): Buffer Tiling is ON
[    19.667] (II) Loading sub module "fglrxdrm"
[    19.667] (II) LoadModule: "fglrxdrm"
[    19.667] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    19.667] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    19.667] 	compiled for 1.4.99.906, module version = 13.10.10
[    19.669] ukiDynamicMajor: found major device number 250
[    19.669] ukiDynamicMajor: found major device number 250
[    19.669] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    19.669] ukiOpenDevice: node name is /dev/ati/card0
[    19.669] ukiOpenDevice: open result is 13, (OK)
[    19.669] ukiOpenByBusid: ukiOpenMinor returns 13
[    19.669] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    19.670] (**) fglrx(0): NoAccel = NO
[    19.670] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[    19.670] (--) fglrx(0): Chipset: "AMD Radeon HD 6800 Series  " (Chipset = 0x6739)
[    19.670] (--) fglrx(0): (PciSubVendor = 0x1787, PciSubDevice = 0x0b00)
[    19.670] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[    19.670] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    19.670] (--) fglrx(0): MMIO registers at 0xfdec0000
[    19.670] (--) fglrx(0): I/O port at 0x0000ee00
[    19.670] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    19.704] (II) fglrx(0): AC Adapter is used
[    19.707] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    19.707] (II) Loading sub module "vbe"
[    19.707] (II) LoadModule: "vbe"
[    19.707] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    19.707] (II) Module vbe: vendor="X.Org Foundation"
[    19.707] 	compiled for 1.14.3, module version = 1.1.0
[    19.707] 	ABI class: X.Org Video Driver, version 14.1
[    19.708] (II) fglrx(0): VESA BIOS detected
[    19.708] (II) fglrx(0): VESA VBE Version 3.0
[    19.708] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    19.708] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[    19.708] (II) fglrx(0): VESA VBE OEM Software Rev: 13.7
[    19.708] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    19.708] (II) fglrx(0): VESA VBE OEM Product: BARTS
[    19.708] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    19.708] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    19.708] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[    19.708] (II) fglrx(0): PCIE card detected
[    19.708] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    19.708] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    19.708] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    19.708] (II) fglrx(0): RandR 1.2 support is enabled!
[    19.708] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    19.708] (==) fglrx(0): Center Mode is disabled 
[    19.708] (II) Loading sub module "fb"
[    19.708] (II) LoadModule: "fb"
[    19.708] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.708] (II) Module fb: vendor="X.Org Foundation"
[    19.708] 	compiled for 1.14.3, module version = 1.0.0
[    19.708] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    19.708] (II) Loading sub module "ddc"
[    19.708] (II) LoadModule: "ddc"
[    19.708] (II) Module "ddc" already built-in
[    19.829] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    19.829] (II) fglrx(0): Output DFP2 has no monitor section
[    19.829] (II) fglrx(0): Output DFP3 has no monitor section
[    19.829] (II) fglrx(0): Output DFP4 has no monitor section
[    19.829] (II) fglrx(0): Output DFP5 has no monitor section
[    19.829] (II) fglrx(0): Output DFP6 has no monitor section
[    19.829] (II) fglrx(0): Output DFP7 has no monitor section
[    19.829] (II) fglrx(0): Output CRT1 has no monitor section
[    19.829] (II) Loading sub module "ddc"
[    19.829] (II) LoadModule: "ddc"
[    19.829] (II) Module "ddc" already built-in
[    19.829] (II) fglrx(0): Connected Display0: DFP5
[    19.829] (II) fglrx(0):  Display0: Failed to get EDID information. 
[    19.830] (II) fglrx(0): EDID for output DFP1
[    19.830] (II) fglrx(0): EDID for output DFP2
[    19.830] (II) fglrx(0): EDID for output DFP3
[    19.830] (II) fglrx(0): EDID for output DFP4
[    19.831] (II) fglrx(0): EDID for output DFP5
[    19.831] (II) fglrx(0): Manufacturer: GSM  Model: 5807  Serial#: 16843009
[    19.831] (II) fglrx(0): Year: 2009  Week: 1
[    19.831] (II) fglrx(0): EDID Version: 1.3
[    19.831] (II) fglrx(0): Digital Display Input
[    19.831] (II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    19.831] (II) fglrx(0): Gamma: 2.20
[    19.831] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[    19.831] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    19.831] (II) fglrx(0): First detailed timing is preferred mode
[    19.831] (II) fglrx(0): redX: 0.631 redY: 0.349   greenX: 0.341 greenY: 0.622
[    19.831] (II) fglrx(0): blueX: 0.152 blueY: 0.058   whiteX: 0.313 whiteY: 0.329
[    19.831] (II) fglrx(0): Supported established timings:
[    19.831] (II) fglrx(0): 640x480@60Hz
[    19.831] (II) fglrx(0): 800x600@60Hz
[    19.831] (II) fglrx(0): 1024x768@60Hz
[    19.831] (II) fglrx(0): Manufacturer's mask: 0
[    19.831] (II) fglrx(0): Supported standard timings:
[    19.831] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 60  vid: 16497
[    19.831] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    19.831] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    19.831] (II) fglrx(0): #3: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    19.831] (II) fglrx(0): Supported detailed timing:
[    19.831] (II) fglrx(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[    19.831] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    19.831] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    19.831] (II) fglrx(0): Ranges: V min: 56 V max: 61 Hz, H min: 30 H max: 83 kHz, PixClock max 155 MHz
[    19.831] (II) fglrx(0): Monitor name: IPS226
[    19.831] (II) fglrx(0): Serial No: SerialNumber
[    19.831] (II) fglrx(0): Supported detailed timing:
[    19.831] (II) fglrx(0): clock: 148.5 MHz   Image Size:  510 x 290 mm
[    19.831] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    19.831] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    19.831] (II) fglrx(0): Supported detailed timing:
[    19.831] (II) fglrx(0): clock: 74.2 MHz   Image Size:  510 x 290 mm
[    19.831] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    19.831] (II) fglrx(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    19.831] (II) fglrx(0): Supported detailed timing:
[    19.831] (II) fglrx(0): clock: 74.2 MHz   Image Size:  510 x 290 mm
[    19.831] (II) fglrx(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    19.831] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    19.831] (II) fglrx(0): Supported detailed timing:
[    19.831] (II) fglrx(0): clock: 27.0 MHz   Image Size:  510 x 290 mm
[    19.831] (II) fglrx(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    19.831] (II) fglrx(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    19.831] (II) fglrx(0): Number of EDID sections to follow: 1
[    19.831] (II) fglrx(0): EDID (in hex):
[    19.831] (II) fglrx(0): 	00ffffffffffff001e6d075801010101
[    19.831] (II) fglrx(0): 	0113010380301b78ea9535a159579f27
[    19.831] (II) fglrx(0): 	0e5054210800714081808140b3000101
[    19.831] (II) fglrx(0): 	010101010101023a801871382d40582c
[    19.831] (II) fglrx(0): 	4500dd0c1100001e000000fd00383d1e
[    19.831] (II) fglrx(0): 	530f000a202020202020000000fc0049
[    19.831] (II) fglrx(0): 	505332323620202020202020000000ff
[    19.831] (II) fglrx(0): 	0053657269616c4e756d6265720a012d
[    19.831] (II) fglrx(0): Printing probed modes for output DFP5
[    19.831] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    19.831] (II) fglrx(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    19.831] (II) fglrx(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    19.831] (II) fglrx(0): Modeline "1920x1080"x60.0   74.25  1920 2008 2052 2200  1080 1085 1095 1125 interlace +hsync +vsync (33.8 kHz e)
[    19.831] (II) fglrx(0): Modeline "1920x1080"x50.0   74.25  1920 2448 2492 2640  1080 1085 1095 1125 interlace +hsync +vsync (28.1 kHz e)
[    19.831] (II) fglrx(0): Modeline "1920x1080"x59.9   74.18  1920 2008 2052 2200  1080 1085 1095 1125 interlace +hsync +vsync (33.7 kHz e)
[    19.831] (II) fglrx(0): Modeline "1776x1000"x50.0  148.50  1776 2304 2348 2640  1000 1004 1009 1125 +hsync +vsync (56.2 kHz ez)
[    19.831] (II) fglrx(0): Modeline "1776x1000"x59.9  148.35  1776 1864 1908 2200  1000 1004 1009 1125 +hsync +vsync (67.4 kHz ez)
[    19.831] (II) fglrx(0): Modeline "1776x1000"x50.0   74.25  1776 2304 2348 2640  1000 1005 1015 1125 interlace +hsync +vsync (28.1 kHz ez)
[    19.831] (II) fglrx(0): Modeline "1776x1000"x59.9   74.18  1776 1864 1908 2200  1000 1005 1015 1125 interlace +hsync +vsync (33.7 kHz ez)
[    19.831] (II) fglrx(0): Modeline "1680x1050"x50.0  148.50  1680 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    19.831] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    19.831] (II) fglrx(0): Modeline "1400x1050"x50.0  148.50  1400 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    19.831] (II) fglrx(0): Modeline "1400x1050"x60.0  146.25  1400 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    19.831] (II) fglrx(0): Modeline "1600x900"x50.0  148.50  1600 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    19.831] (II) fglrx(0): Modeline "1600x900"x60.0  146.25  1600 1784 1960 2240  900 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    19.831] (II) fglrx(0): Modeline "1360x1024"x50.0  148.50  1360 2448 2492 2640  1024 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    19.831] (II) fglrx(0): Modeline "1360x1024"x60.0  146.25  1360 1784 1960 2240  1024 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    19.831] (II) fglrx(0): Modeline "1280x1024"x50.0  148.50  1280 2448 2492 2640  1024 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    19.831] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    19.831] (II) fglrx(0): Modeline "1440x900"x50.0  148.50  1440 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    19.832] (II) fglrx(0): Modeline "1440x900"x60.0  146.25  1440 1784 1960 2240  900 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    19.832] (II) fglrx(0): Modeline "1280x960"x50.0  148.50  1280 2448 2492 2640  960 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    19.832] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    19.832] (II) fglrx(0): Modeline "1152x864"x50.0  148.50  1152 2448 2492 2640  864 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    19.832] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    19.832] (II) fglrx(0): Modeline "1280x768"x50.0  148.50  1280 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    19.832] (II) fglrx(0): Modeline "1280x768"x60.0  108.00  1280 1376 1488 1800  768 961 964 1000 +hsync +vsync (60.0 kHz e)
[    19.832] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    19.832] (II) fglrx(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    19.832] (II) fglrx(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    19.832] (II) fglrx(0): Modeline "1024x768"x50.0  148.50  1024 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    19.832] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    19.832] (II) fglrx(0): Modeline "1152x648"x50.0   74.25  1152 1592 1632 1980  648 653 658 750 +hsync +vsync (37.5 kHz ez)
[    19.832] (II) fglrx(0): Modeline "1152x648"x59.9   74.18  1152 1262 1302 1650  648 653 658 750 +hsync +vsync (45.0 kHz ez)
[    19.832] (II) fglrx(0): Modeline "800x600"x50.0  148.50  800 2448 2492 2640  600 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    19.832] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    19.832] (II) fglrx(0): Modeline "720x480"x50.0  148.50  720 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    19.832] (II) fglrx(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    19.832] (II) fglrx(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    19.832] (II) fglrx(0): Modeline "640x480"x50.0  148.50  640 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    19.832] (II) fglrx(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    19.832] (II) fglrx(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    19.832] (II) fglrx(0): EDID for output DFP6
[    19.832] (II) fglrx(0): EDID for output DFP7
[    19.832] (II) fglrx(0): EDID for output CRT1
[    19.832] (II) fglrx(0): Output DFP1 disconnected
[    19.832] (II) fglrx(0): Output DFP2 disconnected
[    19.832] (II) fglrx(0): Output DFP3 disconnected
[    19.832] (II) fglrx(0): Output DFP4 disconnected
[    19.832] (II) fglrx(0): Output DFP5 connected
[    19.832] (II) fglrx(0): Output DFP6 disconnected
[    19.832] (II) fglrx(0): Output DFP7 disconnected
[    19.832] (II) fglrx(0): Output CRT1 disconnected
[    19.832] (II) fglrx(0): Using exact sizes for initial modes
[    19.832] (II) fglrx(0): Output DFP5 using initial mode 1920x1080
[    19.832] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    19.832] (II) fglrx(0): DPI set to (96, 96)
[    19.832] (II) fglrx(0): Eyefinity capable adapter detected.
[    19.832] (II) fglrx(0): Adapter AMD Radeon HD 6800 Series   has 6 configurable heads and 1 displays connected.
[    19.832] (==) fglrx(0):  PseudoColor visuals disabled
[    19.832] (II) Loading sub module "ramdac"
[    19.832] (II) LoadModule: "ramdac"
[    19.832] (II) Module "ramdac" already built-in
[    19.832] (==) fglrx(0): NoDRI = NO
[    19.832] (==) fglrx(0): Capabilities: 0x00000000
[    19.832] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    19.832] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    19.832] (==) fglrx(0): UseFastTLS=0
[    19.832] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    19.832] (--) Depth 24 pixmap format is 32 bpp
[    19.837] Loading extension ATIFGLRXDRI
[    19.837] (II) fglrx(0): doing swlDriScreenInit
[    19.837] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    19.838] ukiDynamicMajor: found major device number 250
[    19.838] ukiDynamicMajor: found major device number 250
[    19.838] ukiDynamicMajor: found major device number 250
[    19.838] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    19.838] ukiOpenDevice: node name is /dev/ati/card0
[    19.838] ukiOpenDevice: open result is 14, (OK)
[    19.838] ukiOpenByBusid: ukiOpenMinor returns 14
[    19.838] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    19.838] (II) fglrx(0): [uki] DRM interface version 1.0
[    19.838] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    19.838] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    19.838] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f39b69e1000
[    19.838] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    19.838] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    19.838] (II) fglrx(0): swlDriScreenInit done
[    19.838] (II) fglrx(0): Kernel Module Version Information:
[    19.838] (II) fglrx(0):     Name: fglrx
[    19.838] (II) fglrx(0):     Version: 13.10.10
[    19.838] (II) fglrx(0):     Date: May 23 2013
[    19.838] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[    19.838] (II) fglrx(0): Kernel Module version matches driver.
[    19.838] (II) fglrx(0): Kernel Module Build Time Information:
[    19.838] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.11.0-12-generic
[    19.838] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    19.838] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    19.838] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    19.838] (II) fglrx(0): [uki] register handle = 0x00004000
[    19.839] (II) fglrx(0): DRI initialization successfull
[    19.839] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x010e0000
[    19.839] (==) fglrx(0): Backing store disabled
[    19.839] Loading extension FGLRXEXTENSION
[    19.839] (**) fglrx(0): DPMS enabled
[    19.839] (II) fglrx(0): Initialized in-driver Xinerama extension
[    19.839] (**) fglrx(0): Textured Video is enabled.
[    19.839] (II) LoadModule: "glesx"
[    19.839] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[    19.840] (II) Module glesx: vendor="X.Org Foundation"
[    19.840] 	compiled for 1.4.99.906, module version = 1.0.0
[    19.840] Loading extension GLESX
[    19.840] (II) fglrx(0): GLESX enableFlags = 592
[    19.840] (II) fglrx(0): GLESX is enabled
[    19.840] (II) LoadModule: "amdxmm"
[    19.840] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[    19.840] (II) Module amdxmm: vendor="X.Org Foundation"
[    19.840] 	compiled for 1.4.99.906, module version = 2.0.0
[    19.852] Loading extension AMDXVOPL
[    19.852] Loading extension AMDXVBA
[    19.852] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    19.854] (II) fglrx(0): Enable composite support successfully
[    19.854] (WW) fglrx(0): Option "VendorName" is not used
[    19.855] (WW) fglrx(0): Option "ModelName" is not used
[    19.855] (II) fglrx(0): X context handle = 0x1
[    19.855] (II) fglrx(0): [DRI] installation complete
[    19.855] (==) fglrx(0): Silken mouse enabled
[    19.855] (==) fglrx(0): Using HW cursor of display infrastructure!
[    19.855] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    19.898] (--) RandR disabled
[    19.904] (II) SELinux: Disabled on system
[    19.905] ukiDynamicMajor: found major device number 250
[    19.905] ukiDynamicMajor: found major device number 250
[    19.905] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    19.905] ukiOpenDevice: node name is /dev/ati/card0
[    19.905] ukiOpenDevice: open result is 15, (OK)
[    19.905] ukiOpenByBusid: ukiOpenMinor returns 15
[    19.905] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    19.920] ukiDynamicMajor: found major device number 250
[    19.920] ukiDynamicMajor: found major device number 250
[    19.920] ukiDynamicMajor: found major device number 250
[    19.920] ukiOpenDevice: node name is /dev/ati/card0
[    19.920] ukiOpenDevice: open result is 16, (OK)
[    19.920] ukiGetBusid returned 'PCI:1:0:0'
[    19.920] ukiOpenDevice: node name is /dev/ati/card1
[    19.920] ukiOpenDevice: open result is -1, (No such device)
[    19.920] ukiOpenDevice: open result is -1, (No such device)
[    19.920] ukiOpenDevice: Open failed
[    19.920] ukiOpenDevice: node name is /dev/ati/card2
[    19.920] ukiOpenDevice: open result is -1, (No such device)
[    19.920] ukiOpenDevice: open result is -1, (No such device)
[    19.920] ukiOpenDevice: Open failed
[    19.920] ukiOpenDevice: node name is /dev/ati/card3
[    19.920] ukiOpenDevice: open result is -1, (No such device)
[    19.920] ukiOpenDevice: open result is -1, (No such device)
[    19.920] ukiOpenDevice: Open failed
[    19.920] ukiOpenDevice: node name is /dev/ati/card4
[    19.920] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: Open failed
[    19.921] ukiOpenDevice: node name is /dev/ati/card5
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: Open failed
[    19.921] ukiOpenDevice: node name is /dev/ati/card6
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: Open failed
[    19.921] ukiOpenDevice: node name is /dev/ati/card7
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: Open failed
[    19.921] ukiOpenDevice: node name is /dev/ati/card8
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: Open failed
[    19.921] ukiOpenDevice: node name is /dev/ati/card9
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: Open failed
[    19.921] ukiOpenDevice: node name is /dev/ati/card10
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: Open failed
[    19.921] ukiOpenDevice: node name is /dev/ati/card11
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: Open failed
[    19.921] ukiOpenDevice: node name is /dev/ati/card12
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: Open failed
[    19.921] ukiOpenDevice: node name is /dev/ati/card13
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: Open failed
[    19.921] ukiOpenDevice: node name is /dev/ati/card14
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: Open failed
[    19.921] ukiOpenDevice: node name is /dev/ati/card15
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: open result is -1, (No such device)
[    19.921] ukiOpenDevice: Open failed
[    19.921] ukiDynamicMajor: found major device number 250
[    19.921] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    19.921] ukiOpenDevice: node name is /dev/ati/card0
[    19.921] ukiOpenDevice: open result is 16, (OK)
[    19.921] ukiOpenByBusid: ukiOpenMinor returns 16
[    19.921] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    20.095] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    20.096] ukiDynamicMajor: found major device number 250
[    20.096] ukiDynamicMajor: found major device number 250
[    20.096] ukiDynamicMajor: found major device number 250
[    20.096] ukiOpenDevice: node name is /dev/ati/card0
[    20.096] ukiOpenDevice: open result is 17, (OK)
[    20.096] ukiGetBusid returned 'PCI:1:0:0'
[    20.096] ukiOpenDevice: node name is /dev/ati/card1
[    20.096] ukiOpenDevice: open result is -1, (No such device)
[    20.096] ukiOpenDevice: open result is -1, (No such device)
[    20.096] ukiOpenDevice: Open failed
[    20.096] ukiOpenDevice: node name is /dev/ati/card2
[    20.096] ukiOpenDevice: open result is -1, (No such device)
[    20.096] ukiOpenDevice: open result is -1, (No such device)
[    20.096] ukiOpenDevice: Open failed
[    20.096] ukiOpenDevice: node name is /dev/ati/card3
[    20.096] ukiOpenDevice: open result is -1, (No such device)
[    20.096] ukiOpenDevice: open result is -1, (No such device)
[    20.096] ukiOpenDevice: Open failed
[    20.096] ukiOpenDevice: node name is /dev/ati/card4
[    20.096] ukiOpenDevice: open result is -1, (No such device)
[    20.096] ukiOpenDevice: open result is -1, (No such device)
[    20.096] ukiOpenDevice: Open failed
[    20.096] ukiOpenDevice: node name is /dev/ati/card5
[    20.096] ukiOpenDevice: open result is -1, (No such device)
[    20.096] ukiOpenDevice: open result is -1, (No such device)
[    20.096] ukiOpenDevice: Open failed
[    20.096] ukiOpenDevice: node name is /dev/ati/card6
[    20.096] ukiOpenDevice: open result is -1, (No such device)
[    20.096] ukiOpenDevice: open result is -1, (No such device)
[    20.096] ukiOpenDevice: Open failed
[    20.096] ukiOpenDevice: node name is /dev/ati/card7
[    20.096] ukiOpenDevice: open result is -1, (No such device)
[    20.096] ukiOpenDevice: open result is -1, (No such device)
[    20.096] ukiOpenDevice: Open failed
[    20.096] ukiOpenDevice: node name is /dev/ati/card8
[    20.096] ukiOpenDevice: open result is -1, (No such device)
[    20.096] ukiOpenDevice: open result is -1, (No such device)
[    20.096] ukiOpenDevice: Open failed
[    20.096] ukiOpenDevice: node name is /dev/ati/card9
[    20.097] ukiOpenDevice: open result is -1, (No such device)
[    20.097] ukiOpenDevice: open result is -1, (No such device)
[    20.097] ukiOpenDevice: Open failed
[    20.097] ukiOpenDevice: node name is /dev/ati/card10
[    20.097] ukiOpenDevice: open result is -1, (No such device)
[    20.097] ukiOpenDevice: open result is -1, (No such device)
[    20.097] ukiOpenDevice: Open failed
[    20.097] ukiOpenDevice: node name is /dev/ati/card11
[    20.097] ukiOpenDevice: open result is -1, (No such device)
[    20.097] ukiOpenDevice: open result is -1, (No such device)
[    20.097] ukiOpenDevice: Open failed
[    20.097] ukiOpenDevice: node name is /dev/ati/card12
[    20.097] ukiOpenDevice: open result is -1, (No such device)
[    20.097] ukiOpenDevice: open result is -1, (No such device)
[    20.097] ukiOpenDevice: Open failed
[    20.097] ukiOpenDevice: node name is /dev/ati/card13
[    20.097] ukiOpenDevice: open result is -1, (No such device)
[    20.097] ukiOpenDevice: open result is -1, (No such device)
[    20.097] ukiOpenDevice: Open failed
[    20.097] ukiOpenDevice: node name is /dev/ati/card14
[    20.097] ukiOpenDevice: open result is -1, (No such device)
[    20.097] ukiOpenDevice: open result is -1, (No such device)
[    20.097] ukiOpenDevice: Open failed
[    20.097] ukiOpenDevice: node name is /dev/ati/card15
[    20.097] ukiOpenDevice: open result is -1, (No such device)
[    20.097] ukiOpenDevice: open result is -1, (No such device)
[    20.097] ukiOpenDevice: Open failed
[    20.097] ukiDynamicMajor: found major device number 250
[    20.097] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    20.097] ukiOpenDevice: node name is /dev/ati/card0
[    20.097] ukiOpenDevice: open result is 17, (OK)
[    20.097] ukiOpenByBusid: ukiOpenMinor returns 17
[    20.097] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    20.111] (II) fglrx(0): OverDrive5 Detected!
[    20.118] (II) fglrx(0): Setting screen physical size to 508 x 285
[    20.128] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.131] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    20.131] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.131] (II) LoadModule: "evdev"
[    20.131] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.141] (II) Module evdev: vendor="X.Org Foundation"
[    20.141] 	compiled for 1.14.1, module version = 2.7.3
[    20.141] 	Module class: X.Org XInput Driver
[    20.141] 	ABI class: X.Org XInput driver, version 19.1
[    20.141] (II) Using input driver 'evdev' for 'Power Button'
[    20.142] (**) Power Button: always reports core events
[    20.142] (**) evdev: Power Button: Device: "/dev/input/event1"
[    20.142] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.142] (--) evdev: Power Button: Found keys
[    20.142] (II) evdev: Power Button: Configuring as keyboard
[    20.142] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    20.142] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    20.142] (**) Option "xkb_rules" "evdev"
[    20.142] (**) Option "xkb_model" "pc105"
[    20.142] (**) Option "xkb_layout" "us"
[    20.142] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    20.142] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.142] (II) Using input driver 'evdev' for 'Power Button'
[    20.142] (**) Power Button: always reports core events
[    20.142] (**) evdev: Power Button: Device: "/dev/input/event0"
[    20.142] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.142] (--) evdev: Power Button: Found keys
[    20.142] (II) evdev: Power Button: Configuring as keyboard
[    20.142] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    20.142] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    20.142] (**) Option "xkb_rules" "evdev"
[    20.142] (**) Option "xkb_model" "pc105"
[    20.142] (**) Option "xkb_layout" "us"
[    20.143] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event10)
[    20.143] (II) No input driver specified, ignoring this device.
[    20.143] (II) This device may have been added with another device file.
[    20.143] (II) config/udev: Adding input device Microsoft Comfort Mouse 6000 (/dev/input/event11)
[    20.143] (**) Microsoft Comfort Mouse 6000: Applying InputClass "evdev pointer catchall"
[    20.143] (**) Microsoft Comfort Mouse 6000: Applying InputClass "evdev keyboard catchall"
[    20.143] (II) Using input driver 'evdev' for 'Microsoft Comfort Mouse 6000'
[    20.143] (**) Microsoft Comfort Mouse 6000: always reports core events
[    20.143] (**) evdev: Microsoft Comfort Mouse 6000: Device: "/dev/input/event11"
[    20.143] (--) evdev: Microsoft Comfort Mouse 6000: Vendor 0x45e Product 0x77d
[    20.143] (--) evdev: Microsoft Comfort Mouse 6000: Found 9 mouse buttons
[    20.143] (--) evdev: Microsoft Comfort Mouse 6000: Found scroll wheel(s)
[    20.143] (--) evdev: Microsoft Comfort Mouse 6000: Found relative axes
[    20.143] (--) evdev: Microsoft Comfort Mouse 6000: Found x and y relative axes
[    20.143] (--) evdev: Microsoft Comfort Mouse 6000: Found absolute axes
[    20.143] (II) evdev: Microsoft Comfort Mouse 6000: Forcing absolute x/y axes to exist.
[    20.143] (--) evdev: Microsoft Comfort Mouse 6000: Found keys
[    20.143] (II) evdev: Microsoft Comfort Mouse 6000: Configuring as mouse
[    20.143] (II) evdev: Microsoft Comfort Mouse 6000: Configuring as keyboard
[    20.143] (II) evdev: Microsoft Comfort Mouse 6000: Adding scrollwheel support
[    20.143] (**) evdev: Microsoft Comfort Mouse 6000: YAxisMapping: buttons 4 and 5
[    20.143] (**) evdev: Microsoft Comfort Mouse 6000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.143] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb6/6-1/6-1:1.0/input/input11/event11"
[    20.143] (II) XINPUT: Adding extended input device "Microsoft Comfort Mouse 6000" (type: KEYBOARD, id 8)
[    20.143] (**) Option "xkb_rules" "evdev"
[    20.143] (**) Option "xkb_model" "pc105"
[    20.143] (**) Option "xkb_layout" "us"
[    20.144] (II) evdev: Microsoft Comfort Mouse 6000: initialized for relative axes.
[    20.144] (WW) evdev: Microsoft Comfort Mouse 6000: ignoring absolute axes.
[    20.144] (**) Microsoft Comfort Mouse 6000: (accel) keeping acceleration scheme 1
[    20.144] (**) Microsoft Comfort Mouse 6000: (accel) acceleration profile 0
[    20.144] (**) Microsoft Comfort Mouse 6000: (accel) acceleration factor: 2.000
[    20.144] (**) Microsoft Comfort Mouse 6000: (accel) acceleration threshold: 4
[    20.144] (II) config/udev: Adding input device Microsoft Comfort Mouse 6000 (/dev/input/mouse0)
[    20.144] (II) No input driver specified, ignoring this device.
[    20.144] (II) This device may have been added with another device file.
[    20.144] (II) config/udev: Adding input device Generic USB Keyboard (/dev/input/event12)
[    20.144] (**) Generic USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    20.145] (II) Using input driver 'evdev' for 'Generic USB Keyboard'
[    20.145] (**) Generic USB Keyboard: always reports core events
[    20.145] (**) evdev: Generic USB Keyboard: Device: "/dev/input/event12"
[    20.145] (--) evdev: Generic USB Keyboard: Vendor 0x40b Product 0x2000
[    20.145] (--) evdev: Generic USB Keyboard: Found keys
[    20.145] (II) evdev: Generic USB Keyboard: Configuring as keyboard
[    20.145] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb6/6-5/6-5:1.0/input/input12/event12"
[    20.145] (II) XINPUT: Adding extended input device "Generic USB Keyboard" (type: KEYBOARD, id 9)
[    20.145] (**) Option "xkb_rules" "evdev"
[    20.145] (**) Option "xkb_model" "pc105"
[    20.145] (**) Option "xkb_layout" "us"
[    20.145] (II) config/udev: Adding input device Generic USB Keyboard (/dev/input/event13)
[    20.145] (**) Generic USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    20.145] (II) Using input driver 'evdev' for 'Generic USB Keyboard'
[    20.145] (**) Generic USB Keyboard: always reports core events
[    20.145] (**) evdev: Generic USB Keyboard: Device: "/dev/input/event13"
[    20.145] (--) evdev: Generic USB Keyboard: Vendor 0x40b Product 0x2000
[    20.145] (--) evdev: Generic USB Keyboard: Found scroll wheel(s)
[    20.145] (II) evdev: Generic USB Keyboard: Forcing buttons for scroll wheel(s)
[    20.145] (--) evdev: Generic USB Keyboard: Found relative axes
[    20.145] (--) evdev: Generic USB Keyboard: Found x and y relative axes
[    20.145] (--) evdev: Generic USB Keyboard: Found keys
[    20.145] (II) evdev: Generic USB Keyboard: Configuring as mouse
[    20.145] (II) evdev: Generic USB Keyboard: Configuring as keyboard
[    20.145] (II) evdev: Generic USB Keyboard: Adding scrollwheel support
[    20.145] (**) evdev: Generic USB Keyboard: YAxisMapping: buttons 4 and 5
[    20.145] (**) evdev: Generic USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.145] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb6/6-5/6-5:1.1/input/input13/event13"
[    20.145] (II) XINPUT: Adding extended input device "Generic USB Keyboard" (type: KEYBOARD, id 10)
[    20.145] (**) Option "xkb_rules" "evdev"
[    20.145] (**) Option "xkb_model" "pc105"
[    20.145] (**) Option "xkb_layout" "us"
[    20.146] (II) evdev: Generic USB Keyboard: initialized for relative axes.
[    20.146] (**) Generic USB Keyboard: (accel) keeping acceleration scheme 1
[    20.146] (**) Generic USB Keyboard: (accel) acceleration profile 0
[    20.146] (**) Generic USB Keyboard: (accel) acceleration factor: 2.000
[    20.146] (**) Generic USB Keyboard: (accel) acceleration threshold: 4
[    20.146] (II) config/udev: Adding input device Generic USB Keyboard (/dev/input/mouse1)
[    20.146] (II) No input driver specified, ignoring this device.
[    20.146] (II) This device may have been added with another device file.
[    20.146] (II) config/udev: Adding input device gspca_pac7302 (/dev/input/event14)
[    20.146] (**) gspca_pac7302: Applying InputClass "evdev keyboard catchall"
[    20.146] (II) Using input driver 'evdev' for 'gspca_pac7302'
[    20.146] (**) gspca_pac7302: always reports core events
[    20.146] (**) evdev: gspca_pac7302: Device: "/dev/input/event14"
[    20.146] (--) evdev: gspca_pac7302: Vendor 0x93a Product 0x2621
[    20.146] (--) evdev: gspca_pac7302: Found keys
[    20.146] (II) evdev: gspca_pac7302: Configuring as keyboard
[    20.146] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb7/7-1/input/input14/event14"
[    20.146] (II) XINPUT: Adding extended input device "gspca_pac7302" (type: KEYBOARD, id 11)
[    20.146] (**) Option "xkb_rules" "evdev"
[    20.146] (**) Option "xkb_model" "pc105"
[    20.146] (**) Option "xkb_layout" "us"
[    20.147] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event2)
[    20.147] (II) No input driver specified, ignoring this device.
[    20.147] (II) This device may have been added with another device file.
[    20.147] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event3)
[    20.147] (II) No input driver specified, ignoring this device.
[    20.147] (II) This device may have been added with another device file.
[    20.147] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event4)
[    20.147] (II) No input driver specified, ignoring this device.
[    20.147] (II) This device may have been added with another device file.
[    20.148] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event5)
[    20.148] (II) No input driver specified, ignoring this device.
[    20.148] (II) This device may have been added with another device file.
[    20.148] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event6)
[    20.148] (II) No input driver specified, ignoring this device.
[    20.148] (II) This device may have been added with another device file.
[    20.148] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event7)
[    20.148] (II) No input driver specified, ignoring this device.
[    20.148] (II) This device may have been added with another device file.
[    20.148] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event8)
[    20.148] (II) No input driver specified, ignoring this device.
[    20.148] (II) This device may have been added with another device file.
[    20.148] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event9)
[    20.148] (II) No input driver specified, ignoring this device.
[    20.148] (II) This device may have been added with another device file.
[    20.153] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    22.682] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    22.682] (II) fglrx(0): Using EDID range info for horizontal sync
[    22.682] (II) fglrx(0): Using EDID range info for vertical refresh
[    22.682] (II) fglrx(0): Printing DDC gathered Modelines:
[    22.682] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    22.682] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    22.682] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    22.682] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    22.682] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    22.682] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    22.682] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    22.682] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    22.682] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    22.682] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    22.682] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    22.682] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    22.682] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    22.682] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    22.683] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    22.683] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    22.683] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    23.711] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.818] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    23.818] (II) fglrx(0): Using hsync ranges from config file
[    23.818] (II) fglrx(0): Using vrefresh ranges from config file
[    23.818] (II) fglrx(0): Printing DDC gathered Modelines:
[    23.818] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    23.818] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    23.818] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    23.818] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    23.818] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    23.818] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    23.819] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    23.819] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    23.819] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    23.819] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    23.819] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    23.819] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    23.819] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    23.819] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    23.819] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    23.819] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    23.819] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    24.098] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    24.099] (II) fglrx(0): Using hsync ranges from config file
[    24.099] (II) fglrx(0): Using vrefresh ranges from config file
[    24.099] (II) fglrx(0): Printing DDC gathered Modelines:
[    24.099] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    24.099] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    24.099] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    24.099] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    24.099] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    24.099] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    24.099] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    24.099] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    24.099] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    24.099] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    24.099] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    24.099] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    24.099] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    24.099] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    24.099] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    24.099] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    24.099] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    24.233] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    24.269] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    24.499] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    24.500] (II) fglrx(0): Using hsync ranges from config file
[    24.500] (II) fglrx(0): Using vrefresh ranges from config file
[    24.500] (II) fglrx(0): Printing DDC gathered Modelines:
[    24.500] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    24.500] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    24.500] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    24.500] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    24.500] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    24.500] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    24.500] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    24.500] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    24.500] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    24.500] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    24.500] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    24.500] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    24.500] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    24.500] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    24.500] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    24.500] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    24.500] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    24.796] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    24.796] (II) fglrx(0): Using hsync ranges from config file
[    24.796] (II) fglrx(0): Using vrefresh ranges from config file
[    24.796] (II) fglrx(0): Printing DDC gathered Modelines:
[    24.796] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    24.796] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    24.796] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    24.796] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    24.796] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    24.796] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    24.796] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    24.796] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    24.796] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    24.796] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    24.796] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    24.796] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    24.796] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    24.796] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    24.796] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    24.796] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    24.796] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    26.785] (II) XKB: reuse xkmfile /var/lib/xkb/server-CB537B66032B0DBE0AE956F537017A59DB020654.xkm
[    45.243] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    45.243] (II) fglrx(0): Using hsync ranges from config file
[    45.243] (II) fglrx(0): Using vrefresh ranges from config file
[    45.243] (II) fglrx(0): Printing DDC gathered Modelines:
[    45.243] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    45.243] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    45.243] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    45.243] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    45.243] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    45.243] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    45.243] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    45.243] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    45.243] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    45.243] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    45.243] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    45.243] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    45.243] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    45.243] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    45.243] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    45.243] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    45.243] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)

```

---

### Post by Toz on 2013-12-21
Lets try **/usr/share/X11/xorg.conf.d/52-mouse-acceleration.conf ** with the following content:
```
Section "InputClass"
	Identifier          "MS Comfort Mouse Acceleration Quirk"
	MatchTag            "Microsoft Comfort Mouse 6000"
        MatchDevicePath     "/dev/input/event11"
        Driver              "evdev"
	Option              "AccelerationNumerator" "2"
	Option              "AccelerationDenominator" "1"
	Option              "AccelerationThreshold" "4"
EndSection
```

If this works, you will notice that on login, the acceleration will be set properly, no need to run the xset command.

If that one doesn't work, try this version as well:
```
Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "evdev"
        Option      "Device" "/dev/input/event11"
	Option      "AccelerationNumerator" "2"
	Option      "AccelerationDenominator" "1"
	Option      "AccelerationThreshold" "4"
EndSection
```

---

### Post by Thee on 2013-12-22
I tried both and none is working. Damn how can this be...?

---

### Post by Toz on 2013-12-22
> **Thee said:**
> I tried both and none is working. Damn how can this be...?
I wonder if we need to disable the AccelerationProfile. Can you try this file:
```
Section "InputDevice"
        Identifier  "Microsoft Comfort Mouse 6000"
        Driver      "evdev"
        Option      "Device" "/dev/input/event11"
        Option      "AccelerationProfile" "-1"
	Option      "AccelerationNumerator" "2"
	Option      "AccelerationDenominator" "1"
	Option      "AccelerationThreshold" "4"
EndSection
```

Post back the Xorg.0.log log file after booting with this file.

---

### Post by Thee on 2013-12-22
I added that to the /usr/share/X11/xorg.conf.d/52-mouse-acceleration.conf and rebooted, everything is still the same. Here is the log again.

```

[    18.427] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[    18.427] X Protocol Version 11, Revision 0
[    18.427] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    18.427] Current Operating System: Linux thee-ubuntu 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64
[    18.427] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-12-generic root=UUID=15e6c8c3-360b-4c28-98d8-c0f2d0581de9 ro quiet splash vt.handoff=7
[    18.427] Build Date: 15 October 2013  09:23:37AM
[    18.427] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    18.427] Current version of pixman: 0.30.2
[    18.427] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    18.427] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.428] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 22 14:28:14 2013
[    18.428] (==) Using config file: "/etc/X11/xorg.conf"
[    18.428] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.450] (==) ServerLayout "aticonfig Layout"
[    18.450] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    18.450] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    18.450] (**) |   |-->Device "aticonfig-Device[0]-0"
[    18.450] (==) Automatically adding devices
[    18.450] (==) Automatically enabling devices
[    18.450] (==) Automatically adding GPU devices
[    18.450] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.450] 	Entry deleted from font path.
[    18.450] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.450] 	Entry deleted from font path.
[    18.450] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.450] 	Entry deleted from font path.
[    18.450] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.450] 	Entry deleted from font path.
[    18.450] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.450] 	Entry deleted from font path.
[    18.450] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    18.450] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.450] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.450] (II) Loader magic: 0x7f6347a63d20
[    18.450] (II) Module ABI versions:
[    18.450] 	X.Org ANSI C Emulation: 0.4
[    18.450] 	X.Org Video Driver: 14.1
[    18.450] 	X.Org XInput driver : 19.1
[    18.450] 	X.Org Server Extension : 7.0
[    18.452] (--) PCI:*(0:1:0:0) 1002:6739:1787:0b00 rev 0, Mem @ 0xd0000000/268435456, 0xfdec0000/131072, I/O @ 0x0000ee00/256, BIOS @ 0x????????/131072
[    18.452] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.452] Initializing built-in extension Generic Event Extension
[    18.452] Initializing built-in extension SHAPE
[    18.452] Initializing built-in extension MIT-SHM
[    18.452] Initializing built-in extension XInputExtension
[    18.452] Initializing built-in extension XTEST
[    18.452] Initializing built-in extension BIG-REQUESTS
[    18.452] Initializing built-in extension SYNC
[    18.452] Initializing built-in extension XKEYBOARD
[    18.452] Initializing built-in extension XC-MISC
[    18.452] Initializing built-in extension SECURITY
[    18.452] Initializing built-in extension XINERAMA
[    18.452] Initializing built-in extension XFIXES
[    18.452] Initializing built-in extension RENDER
[    18.452] Initializing built-in extension RANDR
[    18.452] Initializing built-in extension COMPOSITE
[    18.452] Initializing built-in extension DAMAGE
[    18.452] Initializing built-in extension MIT-SCREEN-SAVER
[    18.452] Initializing built-in extension DOUBLE-BUFFER
[    18.452] Initializing built-in extension RECORD
[    18.452] Initializing built-in extension DPMS
[    18.452] Initializing built-in extension X-Resource
[    18.452] Initializing built-in extension XVideo
[    18.452] Initializing built-in extension XVideo-MotionCompensation
[    18.452] Initializing built-in extension SELinux
[    18.452] Initializing built-in extension XFree86-VidModeExtension
[    18.452] Initializing built-in extension XFree86-DGA
[    18.452] Initializing built-in extension XFree86-DRI
[    18.452] Initializing built-in extension DRI2
[    18.452] (II) "glx" will be loaded by default.
[    18.452] (WW) "xmir" is not to be loaded by default. Skipping.
[    18.452] (II) LoadModule: "glx"
[    18.453] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    18.453] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    18.453] 	compiled for 6.9.0, module version = 1.0.0
[    18.453] Loading extension GLX
[    18.453] (II) LoadModule: "fglrx"
[    18.469] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    18.487] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    18.487] 	compiled for 1.4.99.906, module version = 13.10.10
[    18.487] 	Module class: X.Org Video Driver
[    18.487] (II) Loading sub module "fglrxdrm"
[    18.487] (II) LoadModule: "fglrxdrm"
[    18.488] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    18.502] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    18.502] 	compiled for 1.4.99.906, module version = 13.10.10
[    18.503] (II) AMD Proprietary Linux Driver Version Identifier:13.10.10
[    18.503] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-13.101                   
[    18.503] (II) AMD Proprietary Linux Driver Build Date: May 23 2013 15:49:35
[    18.503] (++) using VT number 7


[    18.509] (WW) Falling back to old probe method for fglrx
[    18.517] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    18.519] ukiDynamicMajor: found major device number 250
[    18.519] ukiDynamicMajor: found major device number 250
[    18.519] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    18.519] ukiOpenDevice: node name is /dev/ati/card0
[    18.519] ukiOpenDevice: open result is 10, (OK)
[    18.686] ukiOpenByBusid: ukiOpenMinor returns 10
[    18.686] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    18.710] (--) Chipset Supported AMD Graphics Processor (0x6739) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:2:0) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:9:0) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:10:0) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:0) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:1) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:2) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:3) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:0) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:2) found
[    18.710] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    18.710] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    18.710] (II) AMD Video driver is signed
[    18.710] (II) fglrx(0): pEnt->device->identifier=0x7f63488499a0
[    18.710] (II) fglrx(0): === [xdl_xs114_atiddxPreInit] === begin
[    18.711] (II) Loading sub module "vgahw"
[    18.711] (II) LoadModule: "vgahw"
[    18.726] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    18.726] (II) Module vgahw: vendor="X.Org Foundation"
[    18.726] 	compiled for 1.14.3, module version = 0.1.0
[    18.726] 	ABI class: X.Org Video Driver, version 14.1
[    18.727] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    18.727] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    18.727] (==) fglrx(0): Default visual is TrueColor
[    18.727] (**) fglrx(0): Option "DPMS" "true"
[    18.727] (==) fglrx(0): RGB weight 888
[    18.727] (II) fglrx(0): Using 8 bits per RGB 
[    18.727] (==) fglrx(0): Buffer Tiling is ON
[    18.727] (II) Loading sub module "fglrxdrm"
[    18.727] (II) LoadModule: "fglrxdrm"
[    18.727] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    18.727] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    18.727] 	compiled for 1.4.99.906, module version = 13.10.10
[    18.729] ukiDynamicMajor: found major device number 250
[    18.729] ukiDynamicMajor: found major device number 250
[    18.729] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    18.729] ukiOpenDevice: node name is /dev/ati/card0
[    18.729] ukiOpenDevice: open result is 13, (OK)
[    18.729] ukiOpenByBusid: ukiOpenMinor returns 13
[    18.729] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    18.730] (**) fglrx(0): NoAccel = NO
[    18.730] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[    18.730] (--) fglrx(0): Chipset: "AMD Radeon HD 6800 Series  " (Chipset = 0x6739)
[    18.730] (--) fglrx(0): (PciSubVendor = 0x1787, PciSubDevice = 0x0b00)
[    18.730] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[    18.730] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    18.730] (--) fglrx(0): MMIO registers at 0xfdec0000
[    18.730] (--) fglrx(0): I/O port at 0x0000ee00
[    18.730] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    18.760] (II) fglrx(0): AC Adapter is used
[    18.763] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    18.763] (II) Loading sub module "vbe"
[    18.763] (II) LoadModule: "vbe"
[    18.763] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    18.763] (II) Module vbe: vendor="X.Org Foundation"
[    18.763] 	compiled for 1.14.3, module version = 1.1.0
[    18.763] 	ABI class: X.Org Video Driver, version 14.1
[    18.764] (II) fglrx(0): VESA BIOS detected
[    18.764] (II) fglrx(0): VESA VBE Version 3.0
[    18.764] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    18.764] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[    18.764] (II) fglrx(0): VESA VBE OEM Software Rev: 13.7
[    18.764] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    18.764] (II) fglrx(0): VESA VBE OEM Product: BARTS
[    18.764] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    18.764] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    18.764] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[    18.764] (II) fglrx(0): PCIE card detected
[    18.764] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    18.764] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    18.764] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    18.764] (II) fglrx(0): RandR 1.2 support is enabled!
[    18.764] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    18.764] (==) fglrx(0): Center Mode is disabled 
[    18.764] (II) Loading sub module "fb"
[    18.764] (II) LoadModule: "fb"
[    18.764] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.764] (II) Module fb: vendor="X.Org Foundation"
[    18.764] 	compiled for 1.14.3, module version = 1.0.0
[    18.764] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.764] (II) Loading sub module "ddc"
[    18.764] (II) LoadModule: "ddc"
[    18.764] (II) Module "ddc" already built-in
[    18.887] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    18.887] (II) fglrx(0): Output DFP2 has no monitor section
[    18.887] (II) fglrx(0): Output DFP3 has no monitor section
[    18.887] (II) fglrx(0): Output DFP4 has no monitor section
[    18.887] (II) fglrx(0): Output DFP5 has no monitor section
[    18.887] (II) fglrx(0): Output DFP6 has no monitor section
[    18.887] (II) fglrx(0): Output DFP7 has no monitor section
[    18.887] (II) fglrx(0): Output CRT1 has no monitor section
[    18.887] (II) Loading sub module "ddc"
[    18.887] (II) LoadModule: "ddc"
[    18.887] (II) Module "ddc" already built-in
[    18.887] (II) fglrx(0): Connected Display0: DFP5
[    18.887] (II) fglrx(0):  Display0: Failed to get EDID information. 
[    18.888] (II) fglrx(0): EDID for output DFP1
[    18.888] (II) fglrx(0): EDID for output DFP2
[    18.889] (II) fglrx(0): EDID for output DFP3
[    18.889] (II) fglrx(0): EDID for output DFP4
[    18.889] (II) fglrx(0): EDID for output DFP5
[    18.889] (II) fglrx(0): Manufacturer: GSM  Model: 5807  Serial#: 16843009
[    18.889] (II) fglrx(0): Year: 2009  Week: 1
[    18.889] (II) fglrx(0): EDID Version: 1.3
[    18.889] (II) fglrx(0): Digital Display Input
[    18.889] (II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    18.889] (II) fglrx(0): Gamma: 2.20
[    18.889] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[    18.889] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    18.889] (II) fglrx(0): First detailed timing is preferred mode
[    18.889] (II) fglrx(0): redX: 0.631 redY: 0.349   greenX: 0.341 greenY: 0.622
[    18.889] (II) fglrx(0): blueX: 0.152 blueY: 0.058   whiteX: 0.313 whiteY: 0.329
[    18.889] (II) fglrx(0): Supported established timings:
[    18.889] (II) fglrx(0): 640x480@60Hz
[    18.889] (II) fglrx(0): 800x600@60Hz
[    18.889] (II) fglrx(0): 1024x768@60Hz
[    18.889] (II) fglrx(0): Manufacturer's mask: 0
[    18.889] (II) fglrx(0): Supported standard timings:
[    18.889] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 60  vid: 16497
[    18.889] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    18.889] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    18.889] (II) fglrx(0): #3: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    18.889] (II) fglrx(0): Supported detailed timing:
[    18.889] (II) fglrx(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[    18.889] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    18.889] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    18.889] (II) fglrx(0): Ranges: V min: 56 V max: 61 Hz, H min: 30 H max: 83 kHz, PixClock max 155 MHz
[    18.889] (II) fglrx(0): Monitor name: IPS226
[    18.889] (II) fglrx(0): Serial No: SerialNumber
[    18.889] (II) fglrx(0): Supported detailed timing:
[    18.889] (II) fglrx(0): clock: 148.5 MHz   Image Size:  510 x 290 mm
[    18.889] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    18.889] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    18.889] (II) fglrx(0): Supported detailed timing:
[    18.889] (II) fglrx(0): clock: 74.2 MHz   Image Size:  510 x 290 mm
[    18.889] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    18.889] (II) fglrx(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    18.889] (II) fglrx(0): Supported detailed timing:
[    18.889] (II) fglrx(0): clock: 74.2 MHz   Image Size:  510 x 290 mm
[    18.889] (II) fglrx(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    18.889] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    18.889] (II) fglrx(0): Supported detailed timing:
[    18.889] (II) fglrx(0): clock: 27.0 MHz   Image Size:  510 x 290 mm
[    18.889] (II) fglrx(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    18.889] (II) fglrx(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    18.889] (II) fglrx(0): Number of EDID sections to follow: 1
[    18.889] (II) fglrx(0): EDID (in hex):
[    18.889] (II) fglrx(0): 	00ffffffffffff001e6d075801010101
[    18.889] (II) fglrx(0): 	0113010380301b78ea9535a159579f27
[    18.889] (II) fglrx(0): 	0e5054210800714081808140b3000101
[    18.889] (II) fglrx(0): 	010101010101023a801871382d40582c
[    18.889] (II) fglrx(0): 	4500dd0c1100001e000000fd00383d1e
[    18.889] (II) fglrx(0): 	530f000a202020202020000000fc0049
[    18.889] (II) fglrx(0): 	505332323620202020202020000000ff
[    18.889] (II) fglrx(0): 	0053657269616c4e756d6265720a012d
[    18.889] (II) fglrx(0): Printing probed modes for output DFP5
[    18.889] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    18.889] (II) fglrx(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.889] (II) fglrx(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    18.889] (II) fglrx(0): Modeline "1920x1080"x60.0   74.25  1920 2008 2052 2200  1080 1085 1095 1125 interlace +hsync +vsync (33.8 kHz e)
[    18.889] (II) fglrx(0): Modeline "1920x1080"x50.0   74.25  1920 2448 2492 2640  1080 1085 1095 1125 interlace +hsync +vsync (28.1 kHz e)
[    18.889] (II) fglrx(0): Modeline "1920x1080"x59.9   74.18  1920 2008 2052 2200  1080 1085 1095 1125 interlace +hsync +vsync (33.7 kHz e)
[    18.889] (II) fglrx(0): Modeline "1776x1000"x50.0  148.50  1776 2304 2348 2640  1000 1004 1009 1125 +hsync +vsync (56.2 kHz ez)
[    18.889] (II) fglrx(0): Modeline "1776x1000"x59.9  148.35  1776 1864 1908 2200  1000 1004 1009 1125 +hsync +vsync (67.4 kHz ez)
[    18.889] (II) fglrx(0): Modeline "1776x1000"x50.0   74.25  1776 2304 2348 2640  1000 1005 1015 1125 interlace +hsync +vsync (28.1 kHz ez)
[    18.889] (II) fglrx(0): Modeline "1776x1000"x59.9   74.18  1776 1864 1908 2200  1000 1005 1015 1125 interlace +hsync +vsync (33.7 kHz ez)
[    18.889] (II) fglrx(0): Modeline "1680x1050"x50.0  148.50  1680 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.889] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    18.889] (II) fglrx(0): Modeline "1400x1050"x50.0  148.50  1400 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.889] (II) fglrx(0): Modeline "1400x1050"x60.0  146.25  1400 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    18.889] (II) fglrx(0): Modeline "1600x900"x50.0  148.50  1600 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.889] (II) fglrx(0): Modeline "1600x900"x60.0  146.25  1600 1784 1960 2240  900 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    18.889] (II) fglrx(0): Modeline "1360x1024"x50.0  148.50  1360 2448 2492 2640  1024 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.889] (II) fglrx(0): Modeline "1360x1024"x60.0  146.25  1360 1784 1960 2240  1024 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    18.889] (II) fglrx(0): Modeline "1280x1024"x50.0  148.50  1280 2448 2492 2640  1024 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.889] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    18.889] (II) fglrx(0): Modeline "1440x900"x50.0  148.50  1440 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.890] (II) fglrx(0): Modeline "1440x900"x60.0  146.25  1440 1784 1960 2240  900 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    18.890] (II) fglrx(0): Modeline "1280x960"x50.0  148.50  1280 2448 2492 2640  960 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.890] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    18.890] (II) fglrx(0): Modeline "1152x864"x50.0  148.50  1152 2448 2492 2640  864 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.890] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    18.890] (II) fglrx(0): Modeline "1280x768"x50.0  148.50  1280 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.890] (II) fglrx(0): Modeline "1280x768"x60.0  108.00  1280 1376 1488 1800  768 961 964 1000 +hsync +vsync (60.0 kHz e)
[    18.890] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    18.890] (II) fglrx(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    18.890] (II) fglrx(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    18.890] (II) fglrx(0): Modeline "1024x768"x50.0  148.50  1024 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.890] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    18.890] (II) fglrx(0): Modeline "1152x648"x50.0   74.25  1152 1592 1632 1980  648 653 658 750 +hsync +vsync (37.5 kHz ez)
[    18.890] (II) fglrx(0): Modeline "1152x648"x59.9   74.18  1152 1262 1302 1650  648 653 658 750 +hsync +vsync (45.0 kHz ez)
[    18.890] (II) fglrx(0): Modeline "800x600"x50.0  148.50  800 2448 2492 2640  600 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.890] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    18.890] (II) fglrx(0): Modeline "720x480"x50.0  148.50  720 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.890] (II) fglrx(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    18.890] (II) fglrx(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    18.890] (II) fglrx(0): Modeline "640x480"x50.0  148.50  640 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.890] (II) fglrx(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    18.890] (II) fglrx(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    18.890] (II) fglrx(0): EDID for output DFP6
[    18.890] (II) fglrx(0): EDID for output DFP7
[    18.890] (II) fglrx(0): EDID for output CRT1
[    18.890] (II) fglrx(0): Output DFP1 disconnected
[    18.890] (II) fglrx(0): Output DFP2 disconnected
[    18.890] (II) fglrx(0): Output DFP3 disconnected
[    18.890] (II) fglrx(0): Output DFP4 disconnected
[    18.890] (II) fglrx(0): Output DFP5 connected
[    18.890] (II) fglrx(0): Output DFP6 disconnected
[    18.890] (II) fglrx(0): Output DFP7 disconnected
[    18.890] (II) fglrx(0): Output CRT1 disconnected
[    18.890] (II) fglrx(0): Using exact sizes for initial modes
[    18.890] (II) fglrx(0): Output DFP5 using initial mode 1920x1080
[    18.890] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    18.890] (II) fglrx(0): DPI set to (96, 96)
[    18.890] (II) fglrx(0): Eyefinity capable adapter detected.
[    18.890] (II) fglrx(0): Adapter AMD Radeon HD 6800 Series   has 6 configurable heads and 1 displays connected.
[    18.890] (==) fglrx(0):  PseudoColor visuals disabled
[    18.890] (II) Loading sub module "ramdac"
[    18.890] (II) LoadModule: "ramdac"
[    18.890] (II) Module "ramdac" already built-in
[    18.890] (==) fglrx(0): NoDRI = NO
[    18.890] (==) fglrx(0): Capabilities: 0x00000000
[    18.890] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    18.890] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    18.890] (==) fglrx(0): UseFastTLS=0
[    18.890] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    18.890] (--) Depth 24 pixmap format is 32 bpp
[    18.895] Loading extension ATIFGLRXDRI
[    18.895] (II) fglrx(0): doing swlDriScreenInit
[    18.895] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    18.896] ukiDynamicMajor: found major device number 250
[    18.896] ukiDynamicMajor: found major device number 250
[    18.896] ukiDynamicMajor: found major device number 250
[    18.896] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    18.896] ukiOpenDevice: node name is /dev/ati/card0
[    18.896] ukiOpenDevice: open result is 14, (OK)
[    18.896] ukiOpenByBusid: ukiOpenMinor returns 14
[    18.896] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    18.896] (II) fglrx(0): [uki] DRM interface version 1.0
[    18.896] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    18.896] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    18.896] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f6347627000
[    18.896] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    18.896] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    18.896] (II) fglrx(0): swlDriScreenInit done
[    18.896] (II) fglrx(0): Kernel Module Version Information:
[    18.896] (II) fglrx(0):     Name: fglrx
[    18.896] (II) fglrx(0):     Version: 13.10.10
[    18.896] (II) fglrx(0):     Date: May 23 2013
[    18.896] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[    18.896] (II) fglrx(0): Kernel Module version matches driver.
[    18.896] (II) fglrx(0): Kernel Module Build Time Information:
[    18.896] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.11.0-12-generic
[    18.896] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    18.896] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    18.896] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    18.896] (II) fglrx(0): [uki] register handle = 0x00004000
[    18.897] (II) fglrx(0): DRI initialization successfull
[    18.897] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x010e0000
[    18.897] (==) fglrx(0): Backing store disabled
[    18.897] Loading extension FGLRXEXTENSION
[    18.897] (**) fglrx(0): DPMS enabled
[    18.897] (II) fglrx(0): Initialized in-driver Xinerama extension
[    18.897] (**) fglrx(0): Textured Video is enabled.
[    18.897] (II) LoadModule: "glesx"
[    18.897] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[    18.898] (II) Module glesx: vendor="X.Org Foundation"
[    18.898] 	compiled for 1.4.99.906, module version = 1.0.0
[    18.898] Loading extension GLESX
[    18.898] (II) fglrx(0): GLESX enableFlags = 592
[    18.898] (II) fglrx(0): GLESX is enabled
[    18.898] (II) LoadModule: "amdxmm"
[    18.898] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[    18.898] (II) Module amdxmm: vendor="X.Org Foundation"
[    18.898] 	compiled for 1.4.99.906, module version = 2.0.0
[    18.910] Loading extension AMDXVOPL
[    18.910] Loading extension AMDXVBA
[    18.910] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    18.913] (II) fglrx(0): Enable composite support successfully
[    18.913] (WW) fglrx(0): Option "VendorName" is not used
[    18.913] (WW) fglrx(0): Option "ModelName" is not used
[    18.913] (II) fglrx(0): X context handle = 0x1
[    18.913] (II) fglrx(0): [DRI] installation complete
[    18.913] (==) fglrx(0): Silken mouse enabled
[    18.913] (==) fglrx(0): Using HW cursor of display infrastructure!
[    18.913] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    18.962] (--) RandR disabled
[    18.968] (II) SELinux: Disabled on system
[    18.969] ukiDynamicMajor: found major device number 250
[    18.969] ukiDynamicMajor: found major device number 250
[    18.969] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    18.969] ukiOpenDevice: node name is /dev/ati/card0
[    18.969] ukiOpenDevice: open result is 15, (OK)
[    18.969] ukiOpenByBusid: ukiOpenMinor returns 15
[    18.969] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    18.997] ukiDynamicMajor: found major device number 250
[    18.997] ukiDynamicMajor: found major device number 250
[    18.997] ukiDynamicMajor: found major device number 250
[    18.997] ukiOpenDevice: node name is /dev/ati/card0
[    18.997] ukiOpenDevice: open result is 16, (OK)
[    18.997] ukiGetBusid returned 'PCI:1:0:0'
[    18.997] ukiOpenDevice: node name is /dev/ati/card1
[    18.997] ukiOpenDevice: open result is -1, (No such device)
[    18.997] ukiOpenDevice: open result is -1, (No such device)
[    18.997] ukiOpenDevice: Open failed
[    18.997] ukiOpenDevice: node name is /dev/ati/card2
[    18.997] ukiOpenDevice: open result is -1, (No such device)
[    18.997] ukiOpenDevice: open result is -1, (No such device)
[    18.997] ukiOpenDevice: Open failed
[    18.997] ukiOpenDevice: node name is /dev/ati/card3
[    18.997] ukiOpenDevice: open result is -1, (No such device)
[    18.997] ukiOpenDevice: open result is -1, (No such device)
[    18.997] ukiOpenDevice: Open failed
[    18.997] ukiOpenDevice: node name is /dev/ati/card4
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card5
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card6
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card7
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card8
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card9
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card10
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card11
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card12
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card13
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card14
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card15
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiDynamicMajor: found major device number 250
[    18.998] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    18.998] ukiOpenDevice: node name is /dev/ati/card0
[    18.998] ukiOpenDevice: open result is 16, (OK)
[    18.998] ukiOpenByBusid: ukiOpenMinor returns 16
[    18.998] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    19.172] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    19.173] ukiDynamicMajor: found major device number 250
[    19.173] ukiDynamicMajor: found major device number 250
[    19.173] ukiDynamicMajor: found major device number 250
[    19.173] ukiOpenDevice: node name is /dev/ati/card0
[    19.173] ukiOpenDevice: open result is 17, (OK)
[    19.173] ukiGetBusid returned 'PCI:1:0:0'
[    19.173] ukiOpenDevice: node name is /dev/ati/card1
[    19.173] ukiOpenDevice: open result is -1, (No such device)
[    19.173] ukiOpenDevice: open result is -1, (No such device)
[    19.173] ukiOpenDevice: Open failed
[    19.173] ukiOpenDevice: node name is /dev/ati/card2
[    19.173] ukiOpenDevice: open result is -1, (No such device)
[    19.173] ukiOpenDevice: open result is -1, (No such device)
[    19.173] ukiOpenDevice: Open failed
[    19.173] ukiOpenDevice: node name is /dev/ati/card3
[    19.173] ukiOpenDevice: open result is -1, (No such device)
[    19.173] ukiOpenDevice: open result is -1, (No such device)
[    19.173] ukiOpenDevice: Open failed
[    19.173] ukiOpenDevice: node name is /dev/ati/card4
[    19.173] ukiOpenDevice: open result is -1, (No such device)
[    19.173] ukiOpenDevice: open result is -1, (No such device)
[    19.173] ukiOpenDevice: Open failed
[    19.173] ukiOpenDevice: node name is /dev/ati/card5
[    19.173] ukiOpenDevice: open result is -1, (No such device)
[    19.173] ukiOpenDevice: open result is -1, (No such device)
[    19.173] ukiOpenDevice: Open failed
[    19.173] ukiOpenDevice: node name is /dev/ati/card6
[    19.173] ukiOpenDevice: open result is -1, (No such device)
[    19.173] ukiOpenDevice: open result is -1, (No such device)
[    19.173] ukiOpenDevice: Open failed
[    19.173] ukiOpenDevice: node name is /dev/ati/card7
[    19.173] ukiOpenDevice: open result is -1, (No such device)
[    19.173] ukiOpenDevice: open result is -1, (No such device)
[    19.173] ukiOpenDevice: Open failed
[    19.173] ukiOpenDevice: node name is /dev/ati/card8
[    19.173] ukiOpenDevice: open result is -1, (No such device)
[    19.173] ukiOpenDevice: open result is -1, (No such device)
[    19.173] ukiOpenDevice: Open failed
[    19.173] ukiOpenDevice: node name is /dev/ati/card9
[    19.173] ukiOpenDevice: open result is -1, (No such device)
[    19.173] ukiOpenDevice: open result is -1, (No such device)
[    19.173] ukiOpenDevice: Open failed
[    19.173] ukiOpenDevice: node name is /dev/ati/card10
[    19.174] ukiOpenDevice: open result is -1, (No such device)
[    19.174] ukiOpenDevice: open result is -1, (No such device)
[    19.174] ukiOpenDevice: Open failed
[    19.174] ukiOpenDevice: node name is /dev/ati/card11
[    19.174] ukiOpenDevice: open result is -1, (No such device)
[    19.174] ukiOpenDevice: open result is -1, (No such device)
[    19.174] ukiOpenDevice: Open failed
[    19.174] ukiOpenDevice: node name is /dev/ati/card12
[    19.174] ukiOpenDevice: open result is -1, (No such device)
[    19.174] ukiOpenDevice: open result is -1, (No such device)
[    19.174] ukiOpenDevice: Open failed
[    19.174] ukiOpenDevice: node name is /dev/ati/card13
[    19.174] ukiOpenDevice: open result is -1, (No such device)
[    19.174] ukiOpenDevice: open result is -1, (No such device)
[    19.174] ukiOpenDevice: Open failed
[    19.174] ukiOpenDevice: node name is /dev/ati/card14
[    19.174] ukiOpenDevice: open result is -1, (No such device)
[    19.174] ukiOpenDevice: open result is -1, (No such device)
[    19.174] ukiOpenDevice: Open failed
[    19.174] ukiOpenDevice: node name is /dev/ati/card15
[    19.174] ukiOpenDevice: open result is -1, (No such device)
[    19.174] ukiOpenDevice: open result is -1, (No such device)
[    19.174] ukiOpenDevice: Open failed
[    19.174] ukiDynamicMajor: found major device number 250
[    19.174] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    19.174] ukiOpenDevice: node name is /dev/ati/card0
[    19.174] ukiOpenDevice: open result is 17, (OK)
[    19.174] ukiOpenByBusid: ukiOpenMinor returns 17
[    19.174] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    19.187] (II) fglrx(0): OverDrive5 Detected!
[    19.194] (II) fglrx(0): Setting screen physical size to 508 x 285
[    19.204] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.207] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    19.207] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.207] (II) LoadModule: "evdev"
[    19.207] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.218] (II) Module evdev: vendor="X.Org Foundation"
[    19.218] 	compiled for 1.14.1, module version = 2.7.3
[    19.218] 	Module class: X.Org XInput Driver
[    19.218] 	ABI class: X.Org XInput driver, version 19.1
[    19.218] (II) Using input driver 'evdev' for 'Power Button'
[    19.218] (**) Power Button: always reports core events
[    19.218] (**) evdev: Power Button: Device: "/dev/input/event1"
[    19.218] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.218] (--) evdev: Power Button: Found keys
[    19.218] (II) evdev: Power Button: Configuring as keyboard
[    19.218] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    19.218] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    19.218] (**) Option "xkb_rules" "evdev"
[    19.218] (**) Option "xkb_model" "pc105"
[    19.218] (**) Option "xkb_layout" "us"
[    19.219] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    19.219] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.219] (II) Using input driver 'evdev' for 'Power Button'
[    19.219] (**) Power Button: always reports core events
[    19.219] (**) evdev: Power Button: Device: "/dev/input/event0"
[    19.219] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.219] (--) evdev: Power Button: Found keys
[    19.219] (II) evdev: Power Button: Configuring as keyboard
[    19.219] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    19.219] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    19.219] (**) Option "xkb_rules" "evdev"
[    19.219] (**) Option "xkb_model" "pc105"
[    19.219] (**) Option "xkb_layout" "us"
[    19.219] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event10)
[    19.219] (II) No input driver specified, ignoring this device.
[    19.219] (II) This device may have been added with another device file.
[    19.220] (II) config/udev: Adding input device Microsoft Comfort Mouse 6000 (/dev/input/event12)
[    19.220] (**) Microsoft Comfort Mouse 6000: Applying InputClass "evdev pointer catchall"
[    19.220] (**) Microsoft Comfort Mouse 6000: Applying InputClass "evdev keyboard catchall"
[    19.220] (II) Using input driver 'evdev' for 'Microsoft Comfort Mouse 6000'
[    19.220] (**) Microsoft Comfort Mouse 6000: always reports core events
[    19.220] (**) evdev: Microsoft Comfort Mouse 6000: Device: "/dev/input/event12"
[    19.220] (--) evdev: Microsoft Comfort Mouse 6000: Vendor 0x45e Product 0x77d
[    19.220] (--) evdev: Microsoft Comfort Mouse 6000: Found 9 mouse buttons
[    19.220] (--) evdev: Microsoft Comfort Mouse 6000: Found scroll wheel(s)
[    19.220] (--) evdev: Microsoft Comfort Mouse 6000: Found relative axes
[    19.220] (--) evdev: Microsoft Comfort Mouse 6000: Found x and y relative axes
[    19.220] (--) evdev: Microsoft Comfort Mouse 6000: Found absolute axes
[    19.220] (II) evdev: Microsoft Comfort Mouse 6000: Forcing absolute x/y axes to exist.
[    19.220] (--) evdev: Microsoft Comfort Mouse 6000: Found keys
[    19.220] (II) evdev: Microsoft Comfort Mouse 6000: Configuring as mouse
[    19.220] (II) evdev: Microsoft Comfort Mouse 6000: Configuring as keyboard
[    19.220] (II) evdev: Microsoft Comfort Mouse 6000: Adding scrollwheel support
[    19.220] (**) evdev: Microsoft Comfort Mouse 6000: YAxisMapping: buttons 4 and 5
[    19.220] (**) evdev: Microsoft Comfort Mouse 6000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.220] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb6/6-1/6-1:1.0/input/input12/event12"
[    19.220] (II) XINPUT: Adding extended input device "Microsoft Comfort Mouse 6000" (type: KEYBOARD, id 8)
[    19.220] (**) Option "xkb_rules" "evdev"
[    19.220] (**) Option "xkb_model" "pc105"
[    19.220] (**) Option "xkb_layout" "us"
[    19.220] (II) evdev: Microsoft Comfort Mouse 6000: initialized for relative axes.
[    19.220] (WW) evdev: Microsoft Comfort Mouse 6000: ignoring absolute axes.
[    19.221] (**) Microsoft Comfort Mouse 6000: (accel) keeping acceleration scheme 1
[    19.221] (**) Microsoft Comfort Mouse 6000: (accel) acceleration profile 0
[    19.221] (**) Microsoft Comfort Mouse 6000: (accel) acceleration factor: 2.000
[    19.221] (**) Microsoft Comfort Mouse 6000: (accel) acceleration threshold: 4
[    19.221] (II) config/udev: Adding input device Microsoft Comfort Mouse 6000 (/dev/input/mouse0)
[    19.221] (II) No input driver specified, ignoring this device.
[    19.221] (II) This device may have been added with another device file.
[    19.221] (II) config/udev: Adding input device Generic USB Keyboard (/dev/input/event13)
[    19.221] (**) Generic USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    19.221] (II) Using input driver 'evdev' for 'Generic USB Keyboard'
[    19.221] (**) Generic USB Keyboard: always reports core events
[    19.221] (**) evdev: Generic USB Keyboard: Device: "/dev/input/event13"
[    19.221] (--) evdev: Generic USB Keyboard: Vendor 0x40b Product 0x2000
[    19.221] (--) evdev: Generic USB Keyboard: Found keys
[    19.221] (II) evdev: Generic USB Keyboard: Configuring as keyboard
[    19.221] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb6/6-5/6-5:1.0/input/input13/event13"
[    19.221] (II) XINPUT: Adding extended input device "Generic USB Keyboard" (type: KEYBOARD, id 9)
[    19.221] (**) Option "xkb_rules" "evdev"
[    19.221] (**) Option "xkb_model" "pc105"
[    19.221] (**) Option "xkb_layout" "us"
[    19.222] (II) config/udev: Adding input device Generic USB Keyboard (/dev/input/event14)
[    19.222] (**) Generic USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    19.222] (II) Using input driver 'evdev' for 'Generic USB Keyboard'
[    19.222] (**) Generic USB Keyboard: always reports core events
[    19.222] (**) evdev: Generic USB Keyboard: Device: "/dev/input/event14"
[    19.222] (--) evdev: Generic USB Keyboard: Vendor 0x40b Product 0x2000
[    19.222] (--) evdev: Generic USB Keyboard: Found scroll wheel(s)
[    19.222] (II) evdev: Generic USB Keyboard: Forcing buttons for scroll wheel(s)
[    19.222] (--) evdev: Generic USB Keyboard: Found relative axes
[    19.222] (--) evdev: Generic USB Keyboard: Found x and y relative axes
[    19.222] (--) evdev: Generic USB Keyboard: Found keys
[    19.222] (II) evdev: Generic USB Keyboard: Configuring as mouse
[    19.222] (II) evdev: Generic USB Keyboard: Configuring as keyboard
[    19.222] (II) evdev: Generic USB Keyboard: Adding scrollwheel support
[    19.222] (**) evdev: Generic USB Keyboard: YAxisMapping: buttons 4 and 5
[    19.222] (**) evdev: Generic USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.222] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb6/6-5/6-5:1.1/input/input14/event14"
[    19.222] (II) XINPUT: Adding extended input device "Generic USB Keyboard" (type: KEYBOARD, id 10)
[    19.222] (**) Option "xkb_rules" "evdev"
[    19.222] (**) Option "xkb_model" "pc105"
[    19.222] (**) Option "xkb_layout" "us"
[    19.222] (II) evdev: Generic USB Keyboard: initialized for relative axes.
[    19.222] (**) Generic USB Keyboard: (accel) keeping acceleration scheme 1
[    19.222] (**) Generic USB Keyboard: (accel) acceleration profile 0
[    19.222] (**) Generic USB Keyboard: (accel) acceleration factor: 2.000
[    19.222] (**) Generic USB Keyboard: (accel) acceleration threshold: 4
[    19.223] (II) config/udev: Adding input device Generic USB Keyboard (/dev/input/mouse1)
[    19.223] (II) No input driver specified, ignoring this device.
[    19.223] (II) This device may have been added with another device file.
[    19.223] (II) config/udev: Adding input device gspca_pac7302 (/dev/input/event11)
[    19.223] (**) gspca_pac7302: Applying InputClass "evdev keyboard catchall"
[    19.223] (II) Using input driver 'evdev' for 'gspca_pac7302'
[    19.223] (**) gspca_pac7302: always reports core events
[    19.223] (**) evdev: gspca_pac7302: Device: "/dev/input/event11"
[    19.223] (--) evdev: gspca_pac7302: Vendor 0x93a Product 0x2621
[    19.223] (--) evdev: gspca_pac7302: Found keys
[    19.223] (II) evdev: gspca_pac7302: Configuring as keyboard
[    19.223] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb7/7-1/input/input11/event11"
[    19.223] (II) XINPUT: Adding extended input device "gspca_pac7302" (type: KEYBOARD, id 11)
[    19.223] (**) Option "xkb_rules" "evdev"
[    19.223] (**) Option "xkb_model" "pc105"
[    19.223] (**) Option "xkb_layout" "us"
[    19.223] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event2)
[    19.224] (II) No input driver specified, ignoring this device.
[    19.224] (II) This device may have been added with another device file.
[    19.224] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event3)
[    19.224] (II) No input driver specified, ignoring this device.
[    19.224] (II) This device may have been added with another device file.
[    19.224] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event4)
[    19.224] (II) No input driver specified, ignoring this device.
[    19.224] (II) This device may have been added with another device file.
[    19.224] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event5)
[    19.224] (II) No input driver specified, ignoring this device.
[    19.224] (II) This device may have been added with another device file.
[    19.224] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event6)
[    19.224] (II) No input driver specified, ignoring this device.
[    19.224] (II) This device may have been added with another device file.
[    19.225] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event7)
[    19.225] (II) No input driver specified, ignoring this device.
[    19.225] (II) This device may have been added with another device file.
[    19.225] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event8)
[    19.225] (II) No input driver specified, ignoring this device.
[    19.225] (II) This device may have been added with another device file.
[    19.225] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event9)
[    19.225] (II) No input driver specified, ignoring this device.
[    19.225] (II) This device may have been added with another device file.
[    19.230] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    22.124] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    22.125] (II) fglrx(0): Using EDID range info for horizontal sync
[    22.125] (II) fglrx(0): Using EDID range info for vertical refresh
[    22.125] (II) fglrx(0): Printing DDC gathered Modelines:
[    22.125] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    22.125] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    22.125] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    22.125] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    22.125] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    22.125] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    22.125] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    22.125] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    22.125] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    22.125] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    22.125] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    22.125] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    22.125] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    22.125] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    22.125] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    22.125] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    22.125] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    22.831] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.841] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    22.841] (II) fglrx(0): Using hsync ranges from config file
[    22.841] (II) fglrx(0): Using vrefresh ranges from config file
[    22.841] (II) fglrx(0): Printing DDC gathered Modelines:
[    22.841] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    22.841] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    22.841] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    22.841] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    22.841] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    22.841] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    22.841] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    22.841] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    22.841] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    22.841] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    22.841] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    22.841] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    22.841] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    22.841] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    22.841] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    22.841] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    22.841] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    23.668] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    23.668] (II) fglrx(0): Using hsync ranges from config file
[    23.668] (II) fglrx(0): Using vrefresh ranges from config file
[    23.668] (II) fglrx(0): Printing DDC gathered Modelines:
[    23.668] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    23.668] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    23.668] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    23.668] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    23.668] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    23.668] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    23.668] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    23.668] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    23.668] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    23.668] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    23.668] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    23.668] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    23.668] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    23.668] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    23.668] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    23.668] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    23.668] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    23.923] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    23.923] (II) fglrx(0): Using hsync ranges from config file
[    23.923] (II) fglrx(0): Using vrefresh ranges from config file
[    23.923] (II) fglrx(0): Printing DDC gathered Modelines:
[    23.923] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    23.923] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    23.923] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    23.923] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    23.923] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    23.923] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    23.923] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    23.923] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    23.923] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    23.923] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    23.923] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    23.924] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    23.924] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    23.924] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    23.924] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    23.924] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    23.924] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    24.055] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    24.055] (II) fglrx(0): Using hsync ranges from config file
[    24.055] (II) fglrx(0): Using vrefresh ranges from config file
[    24.055] (II) fglrx(0): Printing DDC gathered Modelines:
[    24.055] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    24.055] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    24.055] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    24.055] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    24.055] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    24.056] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    24.056] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    24.056] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    24.056] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    24.056] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    24.056] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    24.056] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    24.056] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    24.056] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    24.056] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    24.056] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    24.056] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    24.984] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.015] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.551] (II) XKB: reuse xkmfile /var/lib/xkb/server-CB537B66032B0DBE0AE956F537017A59DB020654.xkm
[    43.532] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    43.532] (II) fglrx(0): Using hsync ranges from config file
[    43.532] (II) fglrx(0): Using vrefresh ranges from config file
[    43.532] (II) fglrx(0): Printing DDC gathered Modelines:
[    43.532] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    43.532] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    43.532] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    43.532] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    43.532] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    43.532] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    43.532] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    43.532] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    43.532] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    43.532] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    43.532] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    43.532] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    43.532] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    43.532] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    43.532] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    43.532] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    43.532] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)

```

---

### Post by Toz on 2013-12-22
Hmmm, the Comfort Mouse is showing up as /dev/input/event12 this time (I'm certain it was input11 last time). Can you try adjusting the file to point to event12 and try again? Post back the log file again to confirm.

---

### Post by Thee on 2013-12-23
Added, no change.

```

[    19.402] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[    19.403] X Protocol Version 11, Revision 0
[    19.403] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    19.403] Current Operating System: Linux thee-ubuntu 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64
[    19.403] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-12-generic root=UUID=15e6c8c3-360b-4c28-98d8-c0f2d0581de9 ro quiet splash vt.handoff=7
[    19.403] Build Date: 15 October 2013  09:23:37AM
[    19.403] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    19.403] Current version of pixman: 0.30.2
[    19.403] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    19.403] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.403] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec 23 10:55:41 2013
[    19.544] (==) Using config file: "/etc/X11/xorg.conf"
[    19.544] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.730] (==) ServerLayout "aticonfig Layout"
[    19.730] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    19.730] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    19.764] (**) |   |-->Device "aticonfig-Device[0]-0"
[    19.764] (==) Automatically adding devices
[    19.764] (==) Automatically enabling devices
[    19.764] (==) Automatically adding GPU devices
[    19.896] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.896] 	Entry deleted from font path.
[    19.896] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.896] 	Entry deleted from font path.
[    19.896] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.896] 	Entry deleted from font path.
[    19.897] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.897] 	Entry deleted from font path.
[    19.897] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.897] 	Entry deleted from font path.
[    19.897] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    19.897] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.897] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.897] (II) Loader magic: 0x7f6e6c7d7d20
[    19.897] (II) Module ABI versions:
[    19.897] 	X.Org ANSI C Emulation: 0.4
[    19.897] 	X.Org Video Driver: 14.1
[    19.897] 	X.Org XInput driver : 19.1
[    19.897] 	X.Org Server Extension : 7.0
[    19.899] (--) PCI:*(0:1:0:0) 1002:6739:1787:0b00 rev 0, Mem @ 0xd0000000/268435456, 0xfdec0000/131072, I/O @ 0x0000ee00/256, BIOS @ 0x????????/131072
[    19.899] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.921] Initializing built-in extension Generic Event Extension
[    19.921] Initializing built-in extension SHAPE
[    19.921] Initializing built-in extension MIT-SHM
[    19.921] Initializing built-in extension XInputExtension
[    19.921] Initializing built-in extension XTEST
[    19.921] Initializing built-in extension BIG-REQUESTS
[    19.921] Initializing built-in extension SYNC
[    19.921] Initializing built-in extension XKEYBOARD
[    19.921] Initializing built-in extension XC-MISC
[    19.922] Initializing built-in extension SECURITY
[    19.922] Initializing built-in extension XINERAMA
[    19.922] Initializing built-in extension XFIXES
[    19.922] Initializing built-in extension RENDER
[    19.922] Initializing built-in extension RANDR
[    19.922] Initializing built-in extension COMPOSITE
[    19.922] Initializing built-in extension DAMAGE
[    19.922] Initializing built-in extension MIT-SCREEN-SAVER
[    19.922] Initializing built-in extension DOUBLE-BUFFER
[    19.922] Initializing built-in extension RECORD
[    19.922] Initializing built-in extension DPMS
[    19.922] Initializing built-in extension X-Resource
[    19.922] Initializing built-in extension XVideo
[    19.922] Initializing built-in extension XVideo-MotionCompensation
[    19.922] Initializing built-in extension SELinux
[    19.922] Initializing built-in extension XFree86-VidModeExtension
[    19.922] Initializing built-in extension XFree86-DGA
[    19.922] Initializing built-in extension XFree86-DRI
[    19.922] Initializing built-in extension DRI2
[    19.922] (II) "glx" will be loaded by default.
[    19.922] (WW) "xmir" is not to be loaded by default. Skipping.
[    19.922] (II) LoadModule: "glx"
[    20.118] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    20.164] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    20.164] 	compiled for 6.9.0, module version = 1.0.0
[    20.165] Loading extension GLX
[    20.165] (II) LoadModule: "fglrx"
[    20.185] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    20.468] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    20.468] 	compiled for 1.4.99.906, module version = 13.10.10
[    20.468] 	Module class: X.Org Video Driver
[    20.469] (II) Loading sub module "fglrxdrm"
[    20.469] (II) LoadModule: "fglrxdrm"
[    20.469] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    20.542] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    20.542] 	compiled for 1.4.99.906, module version = 13.10.10
[    20.542] (II) AMD Proprietary Linux Driver Version Identifier:13.10.10
[    20.542] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-13.101                   
[    20.542] (II) AMD Proprietary Linux Driver Build Date: May 23 2013 15:49:35
[    20.542] (++) using VT number 7


[    20.548] (WW) Falling back to old probe method for fglrx
[    20.658] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    20.683] ukiDynamicMajor: found major device number 250
[    20.684] ukiDynamicMajor: found major device number 250
[    20.684] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    20.684] ukiOpenDevice: node name is /dev/ati/card0
[    20.684] ukiOpenDevice: open result is 10, (OK)
[    20.886] ukiOpenByBusid: ukiOpenMinor returns 10
[    20.886] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    20.936] (--) Chipset Supported AMD Graphics Processor (0x6739) found
[    20.948] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
[    20.948] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:2:0) found
[    20.948] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:9:0) found
[    20.948] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:10:0) found
[    20.948] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[    20.948] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    20.948] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[    20.948] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    20.948] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    20.948] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    20.948] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[    20.949] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    20.949] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    20.949] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    20.949] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[    20.949] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:0) found
[    20.949] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:1) found
[    20.949] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:2) found
[    20.949] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:3) found
[    20.949] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:0) found
[    20.949] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:2) found
[    20.949] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    20.957] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    20.958] (II) AMD Video driver is signed
[    20.958] (II) fglrx(0): pEnt->device->identifier=0x7f6e6cc789a0
[    20.958] (II) fglrx(0): === [xdl_xs114_atiddxPreInit] === begin
[    20.958] (II) Loading sub module "vgahw"
[    20.958] (II) LoadModule: "vgahw"
[    21.000] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    21.021] (II) Module vgahw: vendor="X.Org Foundation"
[    21.021] 	compiled for 1.14.3, module version = 0.1.0
[    21.021] 	ABI class: X.Org Video Driver, version 14.1
[    21.022] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    21.022] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    21.022] (==) fglrx(0): Default visual is TrueColor
[    21.022] (**) fglrx(0): Option "DPMS" "true"
[    21.022] (==) fglrx(0): RGB weight 888
[    21.022] (II) fglrx(0): Using 8 bits per RGB 
[    21.022] (==) fglrx(0): Buffer Tiling is ON
[    21.022] (II) Loading sub module "fglrxdrm"
[    21.022] (II) LoadModule: "fglrxdrm"
[    21.023] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    21.023] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    21.023] 	compiled for 1.4.99.906, module version = 13.10.10
[    21.025] ukiDynamicMajor: found major device number 250
[    21.025] ukiDynamicMajor: found major device number 250
[    21.025] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    21.025] ukiOpenDevice: node name is /dev/ati/card0
[    21.025] ukiOpenDevice: open result is 13, (OK)
[    21.025] ukiOpenByBusid: ukiOpenMinor returns 13
[    21.025] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    21.025] (**) fglrx(0): NoAccel = NO
[    21.025] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[    21.025] (--) fglrx(0): Chipset: "AMD Radeon HD 6800 Series  " (Chipset = 0x6739)
[    21.025] (--) fglrx(0): (PciSubVendor = 0x1787, PciSubDevice = 0x0b00)
[    21.025] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[    21.025] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    21.025] (--) fglrx(0): MMIO registers at 0xfdec0000
[    21.025] (--) fglrx(0): I/O port at 0x0000ee00
[    21.025] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    21.084] (II) fglrx(0): AC Adapter is used
[    21.099] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    21.108] (II) Loading sub module "vbe"
[    21.108] (II) LoadModule: "vbe"
[    21.109] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    21.109] (II) Module vbe: vendor="X.Org Foundation"
[    21.109] 	compiled for 1.14.3, module version = 1.1.0
[    21.109] 	ABI class: X.Org Video Driver, version 14.1
[    21.111] (II) fglrx(0): VESA BIOS detected
[    21.111] (II) fglrx(0): VESA VBE Version 3.0
[    21.111] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    21.111] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[    21.111] (II) fglrx(0): VESA VBE OEM Software Rev: 13.7
[    21.111] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    21.111] (II) fglrx(0): VESA VBE OEM Product: BARTS
[    21.111] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    21.111] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    21.111] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[    21.111] (II) fglrx(0): PCIE card detected
[    21.111] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    21.111] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    21.111] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    21.111] (II) fglrx(0): RandR 1.2 support is enabled!
[    21.111] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    21.111] (==) fglrx(0): Center Mode is disabled 
[    21.111] (II) Loading sub module "fb"
[    21.111] (II) LoadModule: "fb"
[    21.111] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.124] (II) Module fb: vendor="X.Org Foundation"
[    21.124] 	compiled for 1.14.3, module version = 1.0.0
[    21.124] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.124] (II) Loading sub module "ddc"
[    21.124] (II) LoadModule: "ddc"
[    21.124] (II) Module "ddc" already built-in
[    21.466] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    21.466] (II) fglrx(0): Output DFP2 has no monitor section
[    21.466] (II) fglrx(0): Output DFP3 has no monitor section
[    21.466] (II) fglrx(0): Output DFP4 has no monitor section
[    21.466] (II) fglrx(0): Output DFP5 has no monitor section
[    21.466] (II) fglrx(0): Output DFP6 has no monitor section
[    21.466] (II) fglrx(0): Output DFP7 has no monitor section
[    21.466] (II) fglrx(0): Output CRT1 has no monitor section
[    21.466] (II) Loading sub module "ddc"
[    21.466] (II) LoadModule: "ddc"
[    21.466] (II) Module "ddc" already built-in
[    21.466] (II) fglrx(0): Connected Display0: DFP5
[    21.466] (II) fglrx(0):  Display0: Failed to get EDID information. 
[    21.467] (II) fglrx(0): EDID for output DFP1
[    21.467] (II) fglrx(0): EDID for output DFP2
[    21.467] (II) fglrx(0): EDID for output DFP3
[    21.467] (II) fglrx(0): EDID for output DFP4
[    21.467] (II) fglrx(0): EDID for output DFP5
[    21.467] (II) fglrx(0): Manufacturer: GSM  Model: 5807  Serial#: 16843009
[    21.467] (II) fglrx(0): Year: 2009  Week: 1
[    21.467] (II) fglrx(0): EDID Version: 1.3
[    21.467] (II) fglrx(0): Digital Display Input
[    21.467] (II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    21.467] (II) fglrx(0): Gamma: 2.20
[    21.467] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[    21.467] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    21.467] (II) fglrx(0): First detailed timing is preferred mode
[    21.468] (II) fglrx(0): redX: 0.631 redY: 0.349   greenX: 0.341 greenY: 0.622
[    21.468] (II) fglrx(0): blueX: 0.152 blueY: 0.058   whiteX: 0.313 whiteY: 0.329
[    21.468] (II) fglrx(0): Supported established timings:
[    21.468] (II) fglrx(0): 640x480@60Hz
[    21.468] (II) fglrx(0): 800x600@60Hz
[    21.468] (II) fglrx(0): 1024x768@60Hz
[    21.468] (II) fglrx(0): Manufacturer's mask: 0
[    21.468] (II) fglrx(0): Supported standard timings:
[    21.468] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 60  vid: 16497
[    21.468] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    21.468] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    21.468] (II) fglrx(0): #3: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    21.468] (II) fglrx(0): Supported detailed timing:
[    21.468] (II) fglrx(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[    21.468] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    21.468] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    21.468] (II) fglrx(0): Ranges: V min: 56 V max: 61 Hz, H min: 30 H max: 83 kHz, PixClock max 155 MHz
[    21.468] (II) fglrx(0): Monitor name: IPS226
[    21.468] (II) fglrx(0): Serial No: SerialNumber
[    21.468] (II) fglrx(0): Supported detailed timing:
[    21.468] (II) fglrx(0): clock: 148.5 MHz   Image Size:  510 x 290 mm
[    21.468] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    21.468] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    21.468] (II) fglrx(0): Supported detailed timing:
[    21.468] (II) fglrx(0): clock: 74.2 MHz   Image Size:  510 x 290 mm
[    21.468] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    21.468] (II) fglrx(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    21.468] (II) fglrx(0): Supported detailed timing:
[    21.468] (II) fglrx(0): clock: 74.2 MHz   Image Size:  510 x 290 mm
[    21.468] (II) fglrx(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    21.468] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    21.468] (II) fglrx(0): Supported detailed timing:
[    21.468] (II) fglrx(0): clock: 27.0 MHz   Image Size:  510 x 290 mm
[    21.468] (II) fglrx(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    21.468] (II) fglrx(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    21.468] (II) fglrx(0): Number of EDID sections to follow: 1
[    21.468] (II) fglrx(0): EDID (in hex):
[    21.468] (II) fglrx(0): 	00ffffffffffff001e6d075801010101
[    21.468] (II) fglrx(0): 	0113010380301b78ea9535a159579f27
[    21.468] (II) fglrx(0): 	0e5054210800714081808140b3000101
[    21.468] (II) fglrx(0): 	010101010101023a801871382d40582c
[    21.468] (II) fglrx(0): 	4500dd0c1100001e000000fd00383d1e
[    21.468] (II) fglrx(0): 	530f000a202020202020000000fc0049
[    21.468] (II) fglrx(0): 	505332323620202020202020000000ff
[    21.468] (II) fglrx(0): 	0053657269616c4e756d6265720a012d
[    21.468] (II) fglrx(0): Printing probed modes for output DFP5
[    21.468] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    21.468] (II) fglrx(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    21.468] (II) fglrx(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    21.468] (II) fglrx(0): Modeline "1920x1080"x60.0   74.25  1920 2008 2052 2200  1080 1085 1095 1125 interlace +hsync +vsync (33.8 kHz e)
[    21.468] (II) fglrx(0): Modeline "1920x1080"x50.0   74.25  1920 2448 2492 2640  1080 1085 1095 1125 interlace +hsync +vsync (28.1 kHz e)
[    21.468] (II) fglrx(0): Modeline "1920x1080"x59.9   74.18  1920 2008 2052 2200  1080 1085 1095 1125 interlace +hsync +vsync (33.7 kHz e)
[    21.468] (II) fglrx(0): Modeline "1776x1000"x50.0  148.50  1776 2304 2348 2640  1000 1004 1009 1125 +hsync +vsync (56.2 kHz ez)
[    21.468] (II) fglrx(0): Modeline "1776x1000"x59.9  148.35  1776 1864 1908 2200  1000 1004 1009 1125 +hsync +vsync (67.4 kHz ez)
[    21.468] (II) fglrx(0): Modeline "1776x1000"x50.0   74.25  1776 2304 2348 2640  1000 1005 1015 1125 interlace +hsync +vsync (28.1 kHz ez)
[    21.468] (II) fglrx(0): Modeline "1776x1000"x59.9   74.18  1776 1864 1908 2200  1000 1005 1015 1125 interlace +hsync +vsync (33.7 kHz ez)
[    21.468] (II) fglrx(0): Modeline "1680x1050"x50.0  148.50  1680 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    21.468] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    21.468] (II) fglrx(0): Modeline "1400x1050"x50.0  148.50  1400 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    21.468] (II) fglrx(0): Modeline "1400x1050"x60.0  146.25  1400 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    21.468] (II) fglrx(0): Modeline "1600x900"x50.0  148.50  1600 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    21.468] (II) fglrx(0): Modeline "1600x900"x60.0  146.25  1600 1784 1960 2240  900 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    21.468] (II) fglrx(0): Modeline "1360x1024"x50.0  148.50  1360 2448 2492 2640  1024 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    21.468] (II) fglrx(0): Modeline "1360x1024"x60.0  146.25  1360 1784 1960 2240  1024 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    21.468] (II) fglrx(0): Modeline "1280x1024"x50.0  148.50  1280 2448 2492 2640  1024 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    21.468] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    21.468] (II) fglrx(0): Modeline "1440x900"x50.0  148.50  1440 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    21.468] (II) fglrx(0): Modeline "1440x900"x60.0  146.25  1440 1784 1960 2240  900 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    21.468] (II) fglrx(0): Modeline "1280x960"x50.0  148.50  1280 2448 2492 2640  960 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    21.468] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    21.468] (II) fglrx(0): Modeline "1152x864"x50.0  148.50  1152 2448 2492 2640  864 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    21.468] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    21.469] (II) fglrx(0): Modeline "1280x768"x50.0  148.50  1280 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    21.469] (II) fglrx(0): Modeline "1280x768"x60.0  108.00  1280 1376 1488 1800  768 961 964 1000 +hsync +vsync (60.0 kHz e)
[    21.469] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    21.469] (II) fglrx(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    21.469] (II) fglrx(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    21.469] (II) fglrx(0): Modeline "1024x768"x50.0  148.50  1024 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    21.469] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    21.469] (II) fglrx(0): Modeline "1152x648"x50.0   74.25  1152 1592 1632 1980  648 653 658 750 +hsync +vsync (37.5 kHz ez)
[    21.469] (II) fglrx(0): Modeline "1152x648"x59.9   74.18  1152 1262 1302 1650  648 653 658 750 +hsync +vsync (45.0 kHz ez)
[    21.469] (II) fglrx(0): Modeline "800x600"x50.0  148.50  800 2448 2492 2640  600 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    21.469] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    21.469] (II) fglrx(0): Modeline "720x480"x50.0  148.50  720 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    21.469] (II) fglrx(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    21.469] (II) fglrx(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    21.469] (II) fglrx(0): Modeline "640x480"x50.0  148.50  640 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    21.469] (II) fglrx(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    21.469] (II) fglrx(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    21.469] (II) fglrx(0): EDID for output DFP6
[    21.469] (II) fglrx(0): EDID for output DFP7
[    21.469] (II) fglrx(0): EDID for output CRT1
[    21.469] (II) fglrx(0): Output DFP1 disconnected
[    21.469] (II) fglrx(0): Output DFP2 disconnected
[    21.469] (II) fglrx(0): Output DFP3 disconnected
[    21.469] (II) fglrx(0): Output DFP4 disconnected
[    21.469] (II) fglrx(0): Output DFP5 connected
[    21.469] (II) fglrx(0): Output DFP6 disconnected
[    21.469] (II) fglrx(0): Output DFP7 disconnected
[    21.469] (II) fglrx(0): Output CRT1 disconnected
[    21.469] (II) fglrx(0): Using exact sizes for initial modes
[    21.469] (II) fglrx(0): Output DFP5 using initial mode 1920x1080
[    21.469] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    21.469] (II) fglrx(0): DPI set to (96, 96)
[    21.469] (II) fglrx(0): Eyefinity capable adapter detected.
[    21.469] (II) fglrx(0): Adapter AMD Radeon HD 6800 Series   has 6 configurable heads and 1 displays connected.
[    21.469] (==) fglrx(0):  PseudoColor visuals disabled
[    21.469] (II) Loading sub module "ramdac"
[    21.469] (II) LoadModule: "ramdac"
[    21.469] (II) Module "ramdac" already built-in
[    21.469] (==) fglrx(0): NoDRI = NO
[    21.469] (==) fglrx(0): Capabilities: 0x00000000
[    21.469] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    21.469] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    21.469] (==) fglrx(0): UseFastTLS=0
[    21.469] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    21.469] (--) Depth 24 pixmap format is 32 bpp
[    21.474] Loading extension ATIFGLRXDRI
[    21.474] (II) fglrx(0): doing swlDriScreenInit
[    21.474] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    21.475] ukiDynamicMajor: found major device number 250
[    21.475] ukiDynamicMajor: found major device number 250
[    21.475] ukiDynamicMajor: found major device number 250
[    21.475] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    21.475] ukiOpenDevice: node name is /dev/ati/card0
[    21.475] ukiOpenDevice: open result is 14, (OK)
[    21.475] ukiOpenByBusid: ukiOpenMinor returns 14
[    21.475] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    21.475] (II) fglrx(0): [uki] DRM interface version 1.0
[    21.475] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    21.475] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    21.475] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f6e6c39b000
[    21.475] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    21.475] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    21.475] (II) fglrx(0): swlDriScreenInit done
[    21.475] (II) fglrx(0): Kernel Module Version Information:
[    21.475] (II) fglrx(0):     Name: fglrx
[    21.475] (II) fglrx(0):     Version: 13.10.10
[    21.475] (II) fglrx(0):     Date: May 23 2013
[    21.475] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[    21.475] (II) fglrx(0): Kernel Module version matches driver.
[    21.475] (II) fglrx(0): Kernel Module Build Time Information:
[    21.475] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.11.0-12-generic
[    21.475] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    21.475] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    21.475] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    21.475] (II) fglrx(0): [uki] register handle = 0x00004000
[    21.545] (II) fglrx(0): DRI initialization successfull
[    21.571] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x010e0000
[    21.641] (==) fglrx(0): Backing store disabled
[    21.641] Loading extension FGLRXEXTENSION
[    21.641] (**) fglrx(0): DPMS enabled
[    21.642] (II) fglrx(0): Initialized in-driver Xinerama extension
[    21.642] (**) fglrx(0): Textured Video is enabled.
[    21.642] (II) LoadModule: "glesx"
[    21.642] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[    21.962] (II) Module glesx: vendor="X.Org Foundation"
[    21.962] 	compiled for 1.4.99.906, module version = 1.0.0
[    21.962] Loading extension GLESX
[    21.962] (II) fglrx(0): GLESX enableFlags = 592
[    22.002] (II) fglrx(0): GLESX is enabled
[    22.002] (II) LoadModule: "amdxmm"
[    22.002] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[    22.071] (II) Module amdxmm: vendor="X.Org Foundation"
[    22.071] 	compiled for 1.4.99.906, module version = 2.0.0
[    22.082] Loading extension AMDXVOPL
[    22.082] Loading extension AMDXVBA
[    22.113] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    22.115] (II) fglrx(0): Enable composite support successfully
[    22.115] (WW) fglrx(0): Option "VendorName" is not used
[    22.115] (WW) fglrx(0): Option "ModelName" is not used
[    22.115] (II) fglrx(0): X context handle = 0x1
[    22.115] (II) fglrx(0): [DRI] installation complete
[    22.115] (==) fglrx(0): Silken mouse enabled
[    22.116] (==) fglrx(0): Using HW cursor of display infrastructure!
[    22.116] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    22.254] (--) RandR disabled
[    22.272] (II) SELinux: Disabled on system
[    22.295] ukiDynamicMajor: found major device number 250
[    22.295] ukiDynamicMajor: found major device number 250
[    22.295] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    22.295] ukiOpenDevice: node name is /dev/ati/card0
[    22.295] ukiOpenDevice: open result is 15, (OK)
[    22.295] ukiOpenByBusid: ukiOpenMinor returns 15
[    22.295] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    23.081] ukiDynamicMajor: found major device number 250
[    23.081] ukiDynamicMajor: found major device number 250
[    23.081] ukiDynamicMajor: found major device number 250
[    23.081] ukiOpenDevice: node name is /dev/ati/card0
[    23.081] ukiOpenDevice: open result is 16, (OK)
[    23.081] ukiGetBusid returned 'PCI:1:0:0'
[    23.081] ukiOpenDevice: node name is /dev/ati/card1
[    23.081] ukiOpenDevice: open result is -1, (No such device)
[    23.081] ukiOpenDevice: open result is -1, (No such device)
[    23.081] ukiOpenDevice: Open failed
[    23.081] ukiOpenDevice: node name is /dev/ati/card2
[    23.081] ukiOpenDevice: open result is -1, (No such device)
[    23.081] ukiOpenDevice: open result is -1, (No such device)
[    23.081] ukiOpenDevice: Open failed
[    23.082] ukiOpenDevice: node name is /dev/ati/card3
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: Open failed
[    23.082] ukiOpenDevice: node name is /dev/ati/card4
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: Open failed
[    23.082] ukiOpenDevice: node name is /dev/ati/card5
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: Open failed
[    23.082] ukiOpenDevice: node name is /dev/ati/card6
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: Open failed
[    23.082] ukiOpenDevice: node name is /dev/ati/card7
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: Open failed
[    23.082] ukiOpenDevice: node name is /dev/ati/card8
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: Open failed
[    23.082] ukiOpenDevice: node name is /dev/ati/card9
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: Open failed
[    23.082] ukiOpenDevice: node name is /dev/ati/card10
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: Open failed
[    23.082] ukiOpenDevice: node name is /dev/ati/card11
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: Open failed
[    23.082] ukiOpenDevice: node name is /dev/ati/card12
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: Open failed
[    23.082] ukiOpenDevice: node name is /dev/ati/card13
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: Open failed
[    23.082] ukiOpenDevice: node name is /dev/ati/card14
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: Open failed
[    23.082] ukiOpenDevice: node name is /dev/ati/card15
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: open result is -1, (No such device)
[    23.082] ukiOpenDevice: Open failed
[    23.082] ukiDynamicMajor: found major device number 250
[    23.082] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    23.082] ukiOpenDevice: node name is /dev/ati/card0
[    23.082] ukiOpenDevice: open result is 16, (OK)
[    23.082] ukiOpenByBusid: ukiOpenMinor returns 16
[    23.082] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    24.840] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    24.841] ukiDynamicMajor: found major device number 250
[    24.842] ukiDynamicMajor: found major device number 250
[    24.842] ukiDynamicMajor: found major device number 250
[    24.842] ukiOpenDevice: node name is /dev/ati/card0
[    24.842] ukiOpenDevice: open result is 17, (OK)
[    24.842] ukiGetBusid returned 'PCI:1:0:0'
[    24.842] ukiOpenDevice: node name is /dev/ati/card1
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: Open failed
[    24.842] ukiOpenDevice: node name is /dev/ati/card2
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: Open failed
[    24.842] ukiOpenDevice: node name is /dev/ati/card3
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: Open failed
[    24.842] ukiOpenDevice: node name is /dev/ati/card4
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: Open failed
[    24.842] ukiOpenDevice: node name is /dev/ati/card5
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: Open failed
[    24.842] ukiOpenDevice: node name is /dev/ati/card6
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: Open failed
[    24.842] ukiOpenDevice: node name is /dev/ati/card7
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: Open failed
[    24.842] ukiOpenDevice: node name is /dev/ati/card8
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: Open failed
[    24.842] ukiOpenDevice: node name is /dev/ati/card9
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: Open failed
[    24.842] ukiOpenDevice: node name is /dev/ati/card10
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: Open failed
[    24.842] ukiOpenDevice: node name is /dev/ati/card11
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: Open failed
[    24.842] ukiOpenDevice: node name is /dev/ati/card12
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: Open failed
[    24.842] ukiOpenDevice: node name is /dev/ati/card13
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: Open failed
[    24.842] ukiOpenDevice: node name is /dev/ati/card14
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: Open failed
[    24.842] ukiOpenDevice: node name is /dev/ati/card15
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.842] ukiOpenDevice: open result is -1, (No such device)
[    24.843] ukiOpenDevice: Open failed
[    24.843] ukiDynamicMajor: found major device number 250
[    24.843] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    24.843] ukiOpenDevice: node name is /dev/ati/card0
[    24.843] ukiOpenDevice: open result is 17, (OK)
[    24.843] ukiOpenByBusid: ukiOpenMinor returns 17
[    24.843] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    24.953] (II) fglrx(0): OverDrive5 Detected!
[    24.960] (II) fglrx(0): Setting screen physical size to 508 x 285
[    25.135] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.147] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    25.147] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.147] (II) LoadModule: "evdev"
[    25.147] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.208] (II) Module evdev: vendor="X.Org Foundation"
[    25.208] 	compiled for 1.14.1, module version = 2.7.3
[    25.208] 	Module class: X.Org XInput Driver
[    25.208] 	ABI class: X.Org XInput driver, version 19.1
[    25.208] (II) Using input driver 'evdev' for 'Power Button'
[    25.208] (**) Power Button: always reports core events
[    25.208] (**) evdev: Power Button: Device: "/dev/input/event1"
[    25.208] (--) evdev: Power Button: Vendor 0 Product 0x1
[    25.208] (--) evdev: Power Button: Found keys
[    25.208] (II) evdev: Power Button: Configuring as keyboard
[    25.208] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    25.208] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    25.208] (**) Option "xkb_rules" "evdev"
[    25.208] (**) Option "xkb_model" "pc105"
[    25.208] (**) Option "xkb_layout" "us"
[    25.209] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    25.209] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.209] (II) Using input driver 'evdev' for 'Power Button'
[    25.209] (**) Power Button: always reports core events
[    25.209] (**) evdev: Power Button: Device: "/dev/input/event0"
[    25.209] (--) evdev: Power Button: Vendor 0 Product 0x1
[    25.209] (--) evdev: Power Button: Found keys
[    25.209] (II) evdev: Power Button: Configuring as keyboard
[    25.209] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    25.209] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    25.209] (**) Option "xkb_rules" "evdev"
[    25.209] (**) Option "xkb_model" "pc105"
[    25.209] (**) Option "xkb_layout" "us"
[    25.209] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event10)
[    25.209] (II) No input driver specified, ignoring this device.
[    25.209] (II) This device may have been added with another device file.
[    25.210] (II) config/udev: Adding input device Microsoft Comfort Mouse 6000 (/dev/input/event11)
[    25.210] (**) Microsoft Comfort Mouse 6000: Applying InputClass "evdev pointer catchall"
[    25.210] (**) Microsoft Comfort Mouse 6000: Applying InputClass "evdev keyboard catchall"
[    25.210] (II) Using input driver 'evdev' for 'Microsoft Comfort Mouse 6000'
[    25.210] (**) Microsoft Comfort Mouse 6000: always reports core events
[    25.210] (**) evdev: Microsoft Comfort Mouse 6000: Device: "/dev/input/event11"
[    25.210] (--) evdev: Microsoft Comfort Mouse 6000: Vendor 0x45e Product 0x77d
[    25.210] (--) evdev: Microsoft Comfort Mouse 6000: Found 9 mouse buttons
[    25.210] (--) evdev: Microsoft Comfort Mouse 6000: Found scroll wheel(s)
[    25.210] (--) evdev: Microsoft Comfort Mouse 6000: Found relative axes
[    25.210] (--) evdev: Microsoft Comfort Mouse 6000: Found x and y relative axes
[    25.210] (--) evdev: Microsoft Comfort Mouse 6000: Found absolute axes
[    25.210] (II) evdev: Microsoft Comfort Mouse 6000: Forcing absolute x/y axes to exist.
[    25.210] (--) evdev: Microsoft Comfort Mouse 6000: Found keys
[    25.210] (II) evdev: Microsoft Comfort Mouse 6000: Configuring as mouse
[    25.210] (II) evdev: Microsoft Comfort Mouse 6000: Configuring as keyboard
[    25.210] (II) evdev: Microsoft Comfort Mouse 6000: Adding scrollwheel support
[    25.210] (**) evdev: Microsoft Comfort Mouse 6000: YAxisMapping: buttons 4 and 5
[    25.210] (**) evdev: Microsoft Comfort Mouse 6000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    25.210] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb6/6-1/6-1:1.0/input/input11/event11"
[    25.210] (II) XINPUT: Adding extended input device "Microsoft Comfort Mouse 6000" (type: KEYBOARD, id 8)
[    25.210] (**) Option "xkb_rules" "evdev"
[    25.210] (**) Option "xkb_model" "pc105"
[    25.210] (**) Option "xkb_layout" "us"
[    25.210] (II) evdev: Microsoft Comfort Mouse 6000: initialized for relative axes.
[    25.210] (WW) evdev: Microsoft Comfort Mouse 6000: ignoring absolute axes.
[    25.211] (**) Microsoft Comfort Mouse 6000: (accel) keeping acceleration scheme 1
[    25.211] (**) Microsoft Comfort Mouse 6000: (accel) acceleration profile 0
[    25.211] (**) Microsoft Comfort Mouse 6000: (accel) acceleration factor: 2.000
[    25.211] (**) Microsoft Comfort Mouse 6000: (accel) acceleration threshold: 4
[    25.211] (II) config/udev: Adding input device Microsoft Comfort Mouse 6000 (/dev/input/mouse0)
[    25.211] (II) No input driver specified, ignoring this device.
[    25.211] (II) This device may have been added with another device file.
[    25.211] (II) config/udev: Adding input device Generic USB Keyboard (/dev/input/event12)
[    25.211] (**) Generic USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    25.211] (II) Using input driver 'evdev' for 'Generic USB Keyboard'
[    25.211] (**) Generic USB Keyboard: always reports core events
[    25.211] (**) evdev: Generic USB Keyboard: Device: "/dev/input/event12"
[    25.211] (--) evdev: Generic USB Keyboard: Vendor 0x40b Product 0x2000
[    25.211] (--) evdev: Generic USB Keyboard: Found keys
[    25.211] (II) evdev: Generic USB Keyboard: Configuring as keyboard
[    25.211] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb6/6-5/6-5:1.0/input/input12/event12"
[    25.211] (II) XINPUT: Adding extended input device "Generic USB Keyboard" (type: KEYBOARD, id 9)
[    25.211] (**) Option "xkb_rules" "evdev"
[    25.211] (**) Option "xkb_model" "pc105"
[    25.211] (**) Option "xkb_layout" "us"
[    25.212] (II) config/udev: Adding input device Generic USB Keyboard (/dev/input/event13)
[    25.212] (**) Generic USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    25.212] (II) Using input driver 'evdev' for 'Generic USB Keyboard'
[    25.212] (**) Generic USB Keyboard: always reports core events
[    25.212] (**) evdev: Generic USB Keyboard: Device: "/dev/input/event13"
[    25.212] (--) evdev: Generic USB Keyboard: Vendor 0x40b Product 0x2000
[    25.212] (--) evdev: Generic USB Keyboard: Found scroll wheel(s)
[    25.212] (II) evdev: Generic USB Keyboard: Forcing buttons for scroll wheel(s)
[    25.212] (--) evdev: Generic USB Keyboard: Found relative axes
[    25.212] (--) evdev: Generic USB Keyboard: Found x and y relative axes
[    25.212] (--) evdev: Generic USB Keyboard: Found keys
[    25.212] (II) evdev: Generic USB Keyboard: Configuring as mouse
[    25.212] (II) evdev: Generic USB Keyboard: Configuring as keyboard
[    25.212] (II) evdev: Generic USB Keyboard: Adding scrollwheel support
[    25.212] (**) evdev: Generic USB Keyboard: YAxisMapping: buttons 4 and 5
[    25.212] (**) evdev: Generic USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    25.212] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb6/6-5/6-5:1.1/input/input13/event13"
[    25.212] (II) XINPUT: Adding extended input device "Generic USB Keyboard" (type: KEYBOARD, id 10)
[    25.212] (**) Option "xkb_rules" "evdev"
[    25.212] (**) Option "xkb_model" "pc105"
[    25.212] (**) Option "xkb_layout" "us"
[    25.212] (II) evdev: Generic USB Keyboard: initialized for relative axes.
[    25.212] (**) Generic USB Keyboard: (accel) keeping acceleration scheme 1
[    25.212] (**) Generic USB Keyboard: (accel) acceleration profile 0
[    25.212] (**) Generic USB Keyboard: (accel) acceleration factor: 2.000
[    25.213] (**) Generic USB Keyboard: (accel) acceleration threshold: 4
[    25.213] (II) config/udev: Adding input device Generic USB Keyboard (/dev/input/mouse1)
[    25.213] (II) No input driver specified, ignoring this device.
[    25.213] (II) This device may have been added with another device file.
[    25.213] (II) config/udev: Adding input device gspca_pac7302 (/dev/input/event14)
[    25.213] (**) gspca_pac7302: Applying InputClass "evdev keyboard catchall"
[    25.213] (II) Using input driver 'evdev' for 'gspca_pac7302'
[    25.213] (**) gspca_pac7302: always reports core events
[    25.213] (**) evdev: gspca_pac7302: Device: "/dev/input/event14"
[    25.213] (--) evdev: gspca_pac7302: Vendor 0x93a Product 0x2621
[    25.213] (--) evdev: gspca_pac7302: Found keys
[    25.213] (II) evdev: gspca_pac7302: Configuring as keyboard
[    25.213] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb7/7-1/input/input14/event14"
[    25.213] (II) XINPUT: Adding extended input device "gspca_pac7302" (type: KEYBOARD, id 11)
[    25.213] (**) Option "xkb_rules" "evdev"
[    25.213] (**) Option "xkb_model" "pc105"
[    25.213] (**) Option "xkb_layout" "us"
[    25.214] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event2)
[    25.214] (II) No input driver specified, ignoring this device.
[    25.214] (II) This device may have been added with another device file.
[    25.214] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event3)
[    25.214] (II) No input driver specified, ignoring this device.
[    25.214] (II) This device may have been added with another device file.
[    25.214] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event4)
[    25.214] (II) No input driver specified, ignoring this device.
[    25.214] (II) This device may have been added with another device file.
[    25.214] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event5)
[    25.214] (II) No input driver specified, ignoring this device.
[    25.214] (II) This device may have been added with another device file.
[    25.214] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event6)
[    25.214] (II) No input driver specified, ignoring this device.
[    25.214] (II) This device may have been added with another device file.
[    25.215] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event7)
[    25.215] (II) No input driver specified, ignoring this device.
[    25.215] (II) This device may have been added with another device file.
[    25.215] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event8)
[    25.215] (II) No input driver specified, ignoring this device.
[    25.215] (II) This device may have been added with another device file.
[    25.215] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event9)
[    25.215] (II) No input driver specified, ignoring this device.
[    25.215] (II) This device may have been added with another device file.
[    25.221] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    33.855] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    33.855] (II) fglrx(0): Using EDID range info for horizontal sync
[    33.855] (II) fglrx(0): Using EDID range info for vertical refresh
[    33.855] (II) fglrx(0): Printing DDC gathered Modelines:
[    33.855] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    33.855] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    33.855] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    33.855] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    33.855] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    33.855] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    33.855] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    33.855] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    33.855] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    33.855] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    33.855] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    33.855] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    33.855] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    33.855] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    33.855] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    33.855] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    33.855] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    35.771] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    37.697] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    37.697] (II) fglrx(0): Using hsync ranges from config file
[    37.697] (II) fglrx(0): Using vrefresh ranges from config file
[    37.697] (II) fglrx(0): Printing DDC gathered Modelines:
[    37.697] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    37.697] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    37.697] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    37.697] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    37.697] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    37.697] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    37.697] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    37.697] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    37.697] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    37.697] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    37.697] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    37.697] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    37.697] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    37.697] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    37.697] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    37.697] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    37.697] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    38.904] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    38.904] (II) fglrx(0): Using hsync ranges from config file
[    38.904] (II) fglrx(0): Using vrefresh ranges from config file
[    38.904] (II) fglrx(0): Printing DDC gathered Modelines:
[    38.904] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    38.904] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    38.904] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    38.904] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    38.904] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    38.904] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    38.904] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    38.904] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    38.904] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    38.904] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    38.904] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    38.904] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    38.904] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    38.904] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    38.904] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    38.904] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    38.904] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    39.529] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    39.554] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    40.325] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    40.325] (II) fglrx(0): Using hsync ranges from config file
[    40.325] (II) fglrx(0): Using vrefresh ranges from config file
[    40.325] (II) fglrx(0): Printing DDC gathered Modelines:
[    40.325] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    40.325] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    40.325] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    40.325] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    40.325] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    40.325] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    40.325] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    40.325] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    40.325] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    40.325] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    40.325] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    40.325] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    40.325] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    40.325] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    40.325] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    40.325] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    40.325] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    41.028] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    41.028] (II) fglrx(0): Using hsync ranges from config file
[    41.028] (II) fglrx(0): Using vrefresh ranges from config file
[    41.028] (II) fglrx(0): Printing DDC gathered Modelines:
[    41.028] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    41.028] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    41.028] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    41.028] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    41.028] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    41.028] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    41.028] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    41.028] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    41.028] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    41.028] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    41.028] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    41.028] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    41.028] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    41.028] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    41.028] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    41.028] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    41.028] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    46.842] (II) XKB: reuse xkmfile /var/lib/xkb/server-CB537B66032B0DBE0AE956F537017A59DB020654.xkm
[    60.471] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    60.471] (II) fglrx(0): Using hsync ranges from config file
[    60.471] (II) fglrx(0): Using vrefresh ranges from config file
[    60.471] (II) fglrx(0): Printing DDC gathered Modelines:
[    60.471] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    60.471] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    60.471] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    60.471] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    60.471] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    60.471] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    60.471] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    60.471] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    60.471] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    60.471] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    60.471] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    60.471] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    60.471] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    60.471] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    60.471] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    60.471] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    60.471] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)

```

---

### Post by Toz on 2013-12-23
> [    25.210] (II) config/udev: Adding input device Microsoft Comfort Mouse 6000 (/dev/input/event11)
Its back to input11 - a moving target.
> [    25.210] (**) Microsoft Comfort Mouse 6000: Applying InputClass "evdev pointer catchall"
...this is from /usr/share/X11/xorg.conf.d/10-evdev.conf. There is also a /usr/share/X11/xorg.conf.d/11-evdev-quirks.conf file for adding quirks. Lets try adding to this file in the format they use. 

First delete the 50-mouse-acceleration.conf file.

Then, add to the end of **/usr/share/X11/xorg.conf.d/11-evdev-quirks.conf**:
```
Section "InputClass"
	Identifier "Microsoft Comfort Mouse 6000"
	MatchIsPointer "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
	MatchUSBID "192f:0416"
        Option      "AccelerationNumerator" "2"
	Option      "AccelerationDenominator" "1"
	Option      "AccelerationThreshold" "4"
EndSection
```
...***Make sure you change the MatchUSBID value to your actual one** that you get from running:
```
lsusb
```
...when the mouse is plugged in.

Just to confirm, please post back the full contents of /usr/share/X11/xorg.conf.d/11-evdev-quirks.conf, the results of your "lsusb" command, and you Xorg.0.log file again.

---

### Post by Thee on 2013-12-23
Still nothing...

```

Section "InputClass"
	Identifier "Avago Technologies mouse quirks (LP: #746639)"
	MatchIsPointer "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
	MatchUSBID "192f:0416"
	Option "Emulate3Buttons" "True"
	Option "Emulate3Timeout" "50"
EndSection


# X/Y axis not working due to device reporting absolute axes
# https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/325581
# https://bugs.freedesktop.org/show_bug.cgi?id=32882
Section "InputClass"
	Identifier	"Benq m310"
	MatchProduct	"HID 0d62:1000"
	Driver		"evdev"
	Option		"IgnoreAbsoluteAxes"	"true"
EndSection


Section "InputClass"
	Identifier "Microsoft Comfort Mouse 6000"
	MatchIsPointer "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
	MatchUSBID "045e:077d"
        Option      "AccelerationNumerator" "2"
	Option      "AccelerationDenominator" "1"
	Option      "AccelerationThreshold" "4"
EndSection

```

```

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 093a:2621 Pixart Imaging, Inc. PAC731x Trust Webcam
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 003: ID 040b:2000 Weltrend Semiconductor 
Bus 006 Device 002: ID 045e:077d Microsoft Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

[    18.183] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[    18.183] X Protocol Version 11, Revision 0
[    18.183] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    18.183] Current Operating System: Linux thee-ubuntu 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64
[    18.183] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-12-generic root=UUID=15e6c8c3-360b-4c28-98d8-c0f2d0581de9 ro quiet splash vt.handoff=7
[    18.184] Build Date: 15 October 2013  09:23:37AM
[    18.184] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    18.184] Current version of pixman: 0.30.2
[    18.184] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    18.184] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.184] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec 23 17:51:03 2013
[    18.184] (==) Using config file: "/etc/X11/xorg.conf"
[    18.184] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.184] (==) ServerLayout "aticonfig Layout"
[    18.184] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    18.184] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    18.184] (**) |   |-->Device "aticonfig-Device[0]-0"
[    18.184] (==) Automatically adding devices
[    18.184] (==) Automatically enabling devices
[    18.184] (==) Automatically adding GPU devices
[    18.185] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.185] 	Entry deleted from font path.
[    18.185] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.185] 	Entry deleted from font path.
[    18.185] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.185] 	Entry deleted from font path.
[    18.185] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.185] 	Entry deleted from font path.
[    18.185] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.185] 	Entry deleted from font path.
[    18.185] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    18.185] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.185] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.185] (II) Loader magic: 0x7f2290b8bd20
[    18.185] (II) Module ABI versions:
[    18.185] 	X.Org ANSI C Emulation: 0.4
[    18.185] 	X.Org Video Driver: 14.1
[    18.185] 	X.Org XInput driver : 19.1
[    18.185] 	X.Org Server Extension : 7.0
[    18.186] (--) PCI:*(0:1:0:0) 1002:6739:1787:0b00 rev 0, Mem @ 0xd0000000/268435456, 0xfdec0000/131072, I/O @ 0x0000ee00/256, BIOS @ 0x????????/131072
[    18.186] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.186] Initializing built-in extension Generic Event Extension
[    18.186] Initializing built-in extension SHAPE
[    18.186] Initializing built-in extension MIT-SHM
[    18.186] Initializing built-in extension XInputExtension
[    18.186] Initializing built-in extension XTEST
[    18.186] Initializing built-in extension BIG-REQUESTS
[    18.186] Initializing built-in extension SYNC
[    18.186] Initializing built-in extension XKEYBOARD
[    18.187] Initializing built-in extension XC-MISC
[    18.187] Initializing built-in extension SECURITY
[    18.187] Initializing built-in extension XINERAMA
[    18.187] Initializing built-in extension XFIXES
[    18.187] Initializing built-in extension RENDER
[    18.187] Initializing built-in extension RANDR
[    18.187] Initializing built-in extension COMPOSITE
[    18.187] Initializing built-in extension DAMAGE
[    18.187] Initializing built-in extension MIT-SCREEN-SAVER
[    18.187] Initializing built-in extension DOUBLE-BUFFER
[    18.187] Initializing built-in extension RECORD
[    18.187] Initializing built-in extension DPMS
[    18.187] Initializing built-in extension X-Resource
[    18.187] Initializing built-in extension XVideo
[    18.187] Initializing built-in extension XVideo-MotionCompensation
[    18.187] Initializing built-in extension SELinux
[    18.187] Initializing built-in extension XFree86-VidModeExtension
[    18.187] Initializing built-in extension XFree86-DGA
[    18.187] Initializing built-in extension XFree86-DRI
[    18.187] Initializing built-in extension DRI2
[    18.187] (II) "glx" will be loaded by default.
[    18.187] (WW) "xmir" is not to be loaded by default. Skipping.
[    18.187] (II) LoadModule: "glx"
[    18.187] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    18.187] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    18.187] 	compiled for 6.9.0, module version = 1.0.0
[    18.187] Loading extension GLX
[    18.187] (II) LoadModule: "fglrx"
[    18.241] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    18.260] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    18.260] 	compiled for 1.4.99.906, module version = 13.10.10
[    18.260] 	Module class: X.Org Video Driver
[    18.260] (II) Loading sub module "fglrxdrm"
[    18.260] (II) LoadModule: "fglrxdrm"
[    18.260] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    18.274] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    18.274] 	compiled for 1.4.99.906, module version = 13.10.10
[    18.274] (II) AMD Proprietary Linux Driver Version Identifier:13.10.10
[    18.274] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-13.101                   
[    18.274] (II) AMD Proprietary Linux Driver Build Date: May 23 2013 15:49:35
[    18.274] (++) using VT number 7


[    18.281] (WW) Falling back to old probe method for fglrx
[    18.289] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    18.291] ukiDynamicMajor: found major device number 250
[    18.291] ukiDynamicMajor: found major device number 250
[    18.291] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    18.291] ukiOpenDevice: node name is /dev/ati/card0
[    18.291] ukiOpenDevice: open result is 10, (OK)
[    18.502] ukiOpenByBusid: ukiOpenMinor returns 10
[    18.502] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    18.530] (--) Chipset Supported AMD Graphics Processor (0x6739) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:2:0) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:9:0) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:10:0) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:0) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:1) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:2) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:3) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:0) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:2) found
[    18.530] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    18.530] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    18.530] (II) AMD Video driver is signed
[    18.530] (II) fglrx(0): pEnt->device->identifier=0x7f2292603820
[    18.530] (II) fglrx(0): === [xdl_xs114_atiddxPreInit] === begin
[    18.530] (II) Loading sub module "vgahw"
[    18.531] (II) LoadModule: "vgahw"
[    18.548] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    18.548] (II) Module vgahw: vendor="X.Org Foundation"
[    18.548] 	compiled for 1.14.3, module version = 0.1.0
[    18.548] 	ABI class: X.Org Video Driver, version 14.1
[    18.549] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    18.549] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    18.549] (==) fglrx(0): Default visual is TrueColor
[    18.549] (**) fglrx(0): Option "DPMS" "true"
[    18.549] (==) fglrx(0): RGB weight 888
[    18.549] (II) fglrx(0): Using 8 bits per RGB 
[    18.549] (==) fglrx(0): Buffer Tiling is ON
[    18.549] (II) Loading sub module "fglrxdrm"
[    18.549] (II) LoadModule: "fglrxdrm"
[    18.549] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    18.549] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    18.549] 	compiled for 1.4.99.906, module version = 13.10.10
[    18.551] ukiDynamicMajor: found major device number 250
[    18.551] ukiDynamicMajor: found major device number 250
[    18.551] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    18.551] ukiOpenDevice: node name is /dev/ati/card0
[    18.551] ukiOpenDevice: open result is 13, (OK)
[    18.551] ukiOpenByBusid: ukiOpenMinor returns 13
[    18.551] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    18.551] (**) fglrx(0): NoAccel = NO
[    18.552] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[    18.552] (--) fglrx(0): Chipset: "AMD Radeon HD 6800 Series  " (Chipset = 0x6739)
[    18.552] (--) fglrx(0): (PciSubVendor = 0x1787, PciSubDevice = 0x0b00)
[    18.552] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[    18.552] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    18.552] (--) fglrx(0): MMIO registers at 0xfdec0000
[    18.552] (--) fglrx(0): I/O port at 0x0000ee00
[    18.552] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    18.584] (II) fglrx(0): AC Adapter is used
[    18.587] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    18.587] (II) Loading sub module "vbe"
[    18.587] (II) LoadModule: "vbe"
[    18.587] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    18.587] (II) Module vbe: vendor="X.Org Foundation"
[    18.587] 	compiled for 1.14.3, module version = 1.1.0
[    18.587] 	ABI class: X.Org Video Driver, version 14.1
[    18.588] (II) fglrx(0): VESA BIOS detected
[    18.588] (II) fglrx(0): VESA VBE Version 3.0
[    18.588] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    18.588] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[    18.588] (II) fglrx(0): VESA VBE OEM Software Rev: 13.7
[    18.588] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    18.588] (II) fglrx(0): VESA VBE OEM Product: BARTS
[    18.588] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    18.588] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    18.588] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[    18.588] (II) fglrx(0): PCIE card detected
[    18.588] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    18.588] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    18.588] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    18.588] (II) fglrx(0): RandR 1.2 support is enabled!
[    18.588] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    18.588] (==) fglrx(0): Center Mode is disabled 
[    18.588] (II) Loading sub module "fb"
[    18.588] (II) LoadModule: "fb"
[    18.588] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.588] (II) Module fb: vendor="X.Org Foundation"
[    18.588] 	compiled for 1.14.3, module version = 1.0.0
[    18.588] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.588] (II) Loading sub module "ddc"
[    18.588] (II) LoadModule: "ddc"
[    18.588] (II) Module "ddc" already built-in
[    18.710] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    18.710] (II) fglrx(0): Output DFP2 has no monitor section
[    18.710] (II) fglrx(0): Output DFP3 has no monitor section
[    18.710] (II) fglrx(0): Output DFP4 has no monitor section
[    18.710] (II) fglrx(0): Output DFP5 has no monitor section
[    18.710] (II) fglrx(0): Output DFP6 has no monitor section
[    18.710] (II) fglrx(0): Output DFP7 has no monitor section
[    18.710] (II) fglrx(0): Output CRT1 has no monitor section
[    18.710] (II) Loading sub module "ddc"
[    18.710] (II) LoadModule: "ddc"
[    18.710] (II) Module "ddc" already built-in
[    18.710] (II) fglrx(0): Connected Display0: DFP5
[    18.710] (II) fglrx(0):  Display0: Failed to get EDID information. 
[    18.711] (II) fglrx(0): EDID for output DFP1
[    18.711] (II) fglrx(0): EDID for output DFP2
[    18.711] (II) fglrx(0): EDID for output DFP3
[    18.711] (II) fglrx(0): EDID for output DFP4
[    18.711] (II) fglrx(0): EDID for output DFP5
[    18.711] (II) fglrx(0): Manufacturer: GSM  Model: 5807  Serial#: 16843009
[    18.711] (II) fglrx(0): Year: 2009  Week: 1
[    18.711] (II) fglrx(0): EDID Version: 1.3
[    18.711] (II) fglrx(0): Digital Display Input
[    18.711] (II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    18.711] (II) fglrx(0): Gamma: 2.20
[    18.711] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[    18.711] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    18.711] (II) fglrx(0): First detailed timing is preferred mode
[    18.711] (II) fglrx(0): redX: 0.631 redY: 0.349   greenX: 0.341 greenY: 0.622
[    18.711] (II) fglrx(0): blueX: 0.152 blueY: 0.058   whiteX: 0.313 whiteY: 0.329
[    18.711] (II) fglrx(0): Supported established timings:
[    18.712] (II) fglrx(0): 640x480@60Hz
[    18.712] (II) fglrx(0): 800x600@60Hz
[    18.712] (II) fglrx(0): 1024x768@60Hz
[    18.712] (II) fglrx(0): Manufacturer's mask: 0
[    18.712] (II) fglrx(0): Supported standard timings:
[    18.712] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 60  vid: 16497
[    18.712] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    18.712] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    18.712] (II) fglrx(0): #3: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    18.712] (II) fglrx(0): Supported detailed timing:
[    18.712] (II) fglrx(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[    18.712] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    18.712] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    18.712] (II) fglrx(0): Ranges: V min: 56 V max: 61 Hz, H min: 30 H max: 83 kHz, PixClock max 155 MHz
[    18.712] (II) fglrx(0): Monitor name: IPS226
[    18.712] (II) fglrx(0): Serial No: SerialNumber
[    18.712] (II) fglrx(0): Supported detailed timing:
[    18.712] (II) fglrx(0): clock: 148.5 MHz   Image Size:  510 x 290 mm
[    18.712] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    18.712] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    18.712] (II) fglrx(0): Supported detailed timing:
[    18.712] (II) fglrx(0): clock: 74.2 MHz   Image Size:  510 x 290 mm
[    18.712] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    18.712] (II) fglrx(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    18.712] (II) fglrx(0): Supported detailed timing:
[    18.712] (II) fglrx(0): clock: 74.2 MHz   Image Size:  510 x 290 mm
[    18.712] (II) fglrx(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    18.712] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    18.712] (II) fglrx(0): Supported detailed timing:
[    18.712] (II) fglrx(0): clock: 27.0 MHz   Image Size:  510 x 290 mm
[    18.712] (II) fglrx(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    18.712] (II) fglrx(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    18.712] (II) fglrx(0): Number of EDID sections to follow: 1
[    18.712] (II) fglrx(0): EDID (in hex):
[    18.712] (II) fglrx(0): 	00ffffffffffff001e6d075801010101
[    18.712] (II) fglrx(0): 	0113010380301b78ea9535a159579f27
[    18.712] (II) fglrx(0): 	0e5054210800714081808140b3000101
[    18.712] (II) fglrx(0): 	010101010101023a801871382d40582c
[    18.712] (II) fglrx(0): 	4500dd0c1100001e000000fd00383d1e
[    18.712] (II) fglrx(0): 	530f000a202020202020000000fc0049
[    18.712] (II) fglrx(0): 	505332323620202020202020000000ff
[    18.712] (II) fglrx(0): 	0053657269616c4e756d6265720a012d
[    18.712] (II) fglrx(0): Printing probed modes for output DFP5
[    18.712] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    18.712] (II) fglrx(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.712] (II) fglrx(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    18.712] (II) fglrx(0): Modeline "1920x1080"x60.0   74.25  1920 2008 2052 2200  1080 1085 1095 1125 interlace +hsync +vsync (33.8 kHz e)
[    18.712] (II) fglrx(0): Modeline "1920x1080"x50.0   74.25  1920 2448 2492 2640  1080 1085 1095 1125 interlace +hsync +vsync (28.1 kHz e)
[    18.712] (II) fglrx(0): Modeline "1920x1080"x59.9   74.18  1920 2008 2052 2200  1080 1085 1095 1125 interlace +hsync +vsync (33.7 kHz e)
[    18.712] (II) fglrx(0): Modeline "1776x1000"x50.0  148.50  1776 2304 2348 2640  1000 1004 1009 1125 +hsync +vsync (56.2 kHz ez)
[    18.712] (II) fglrx(0): Modeline "1776x1000"x59.9  148.35  1776 1864 1908 2200  1000 1004 1009 1125 +hsync +vsync (67.4 kHz ez)
[    18.712] (II) fglrx(0): Modeline "1776x1000"x50.0   74.25  1776 2304 2348 2640  1000 1005 1015 1125 interlace +hsync +vsync (28.1 kHz ez)
[    18.712] (II) fglrx(0): Modeline "1776x1000"x59.9   74.18  1776 1864 1908 2200  1000 1005 1015 1125 interlace +hsync +vsync (33.7 kHz ez)
[    18.712] (II) fglrx(0): Modeline "1680x1050"x50.0  148.50  1680 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.712] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    18.712] (II) fglrx(0): Modeline "1400x1050"x50.0  148.50  1400 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.712] (II) fglrx(0): Modeline "1400x1050"x60.0  146.25  1400 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    18.712] (II) fglrx(0): Modeline "1600x900"x50.0  148.50  1600 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.712] (II) fglrx(0): Modeline "1600x900"x60.0  146.25  1600 1784 1960 2240  900 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    18.712] (II) fglrx(0): Modeline "1360x1024"x50.0  148.50  1360 2448 2492 2640  1024 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.712] (II) fglrx(0): Modeline "1360x1024"x60.0  146.25  1360 1784 1960 2240  1024 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    18.712] (II) fglrx(0): Modeline "1280x1024"x50.0  148.50  1280 2448 2492 2640  1024 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.712] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    18.712] (II) fglrx(0): Modeline "1440x900"x50.0  148.50  1440 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.712] (II) fglrx(0): Modeline "1440x900"x60.0  146.25  1440 1784 1960 2240  900 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    18.712] (II) fglrx(0): Modeline "1280x960"x50.0  148.50  1280 2448 2492 2640  960 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.712] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    18.712] (II) fglrx(0): Modeline "1152x864"x50.0  148.50  1152 2448 2492 2640  864 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.712] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    18.712] (II) fglrx(0): Modeline "1280x768"x50.0  148.50  1280 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.712] (II) fglrx(0): Modeline "1280x768"x60.0  108.00  1280 1376 1488 1800  768 961 964 1000 +hsync +vsync (60.0 kHz e)
[    18.712] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    18.712] (II) fglrx(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    18.712] (II) fglrx(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    18.712] (II) fglrx(0): Modeline "1024x768"x50.0  148.50  1024 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.712] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    18.712] (II) fglrx(0): Modeline "1152x648"x50.0   74.25  1152 1592 1632 1980  648 653 658 750 +hsync +vsync (37.5 kHz ez)
[    18.712] (II) fglrx(0): Modeline "1152x648"x59.9   74.18  1152 1262 1302 1650  648 653 658 750 +hsync +vsync (45.0 kHz ez)
[    18.712] (II) fglrx(0): Modeline "800x600"x50.0  148.50  800 2448 2492 2640  600 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.713] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    18.713] (II) fglrx(0): Modeline "720x480"x50.0  148.50  720 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.713] (II) fglrx(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    18.713] (II) fglrx(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    18.713] (II) fglrx(0): Modeline "640x480"x50.0  148.50  640 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    18.713] (II) fglrx(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    18.713] (II) fglrx(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    18.713] (II) fglrx(0): EDID for output DFP6
[    18.713] (II) fglrx(0): EDID for output DFP7
[    18.713] (II) fglrx(0): EDID for output CRT1
[    18.713] (II) fglrx(0): Output DFP1 disconnected
[    18.713] (II) fglrx(0): Output DFP2 disconnected
[    18.713] (II) fglrx(0): Output DFP3 disconnected
[    18.713] (II) fglrx(0): Output DFP4 disconnected
[    18.713] (II) fglrx(0): Output DFP5 connected
[    18.713] (II) fglrx(0): Output DFP6 disconnected
[    18.713] (II) fglrx(0): Output DFP7 disconnected
[    18.713] (II) fglrx(0): Output CRT1 disconnected
[    18.713] (II) fglrx(0): Using exact sizes for initial modes
[    18.713] (II) fglrx(0): Output DFP5 using initial mode 1920x1080
[    18.713] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    18.713] (II) fglrx(0): DPI set to (96, 96)
[    18.713] (II) fglrx(0): Eyefinity capable adapter detected.
[    18.713] (II) fglrx(0): Adapter AMD Radeon HD 6800 Series   has 6 configurable heads and 1 displays connected.
[    18.713] (==) fglrx(0):  PseudoColor visuals disabled
[    18.713] (II) Loading sub module "ramdac"
[    18.713] (II) LoadModule: "ramdac"
[    18.713] (II) Module "ramdac" already built-in
[    18.713] (==) fglrx(0): NoDRI = NO
[    18.713] (==) fglrx(0): Capabilities: 0x00000000
[    18.713] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    18.713] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    18.713] (==) fglrx(0): UseFastTLS=0
[    18.713] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    18.713] (--) Depth 24 pixmap format is 32 bpp
[    18.718] Loading extension ATIFGLRXDRI
[    18.718] (II) fglrx(0): doing swlDriScreenInit
[    18.718] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    18.718] ukiDynamicMajor: found major device number 250
[    18.718] ukiDynamicMajor: found major device number 250
[    18.718] ukiDynamicMajor: found major device number 250
[    18.718] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    18.718] ukiOpenDevice: node name is /dev/ati/card0
[    18.718] ukiOpenDevice: open result is 14, (OK)
[    18.718] ukiOpenByBusid: ukiOpenMinor returns 14
[    18.718] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    18.718] (II) fglrx(0): [uki] DRM interface version 1.0
[    18.718] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    18.719] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    18.719] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f229074f000
[    18.719] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    18.719] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    18.719] (II) fglrx(0): swlDriScreenInit done
[    18.719] (II) fglrx(0): Kernel Module Version Information:
[    18.719] (II) fglrx(0):     Name: fglrx
[    18.719] (II) fglrx(0):     Version: 13.10.10
[    18.719] (II) fglrx(0):     Date: May 23 2013
[    18.719] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[    18.719] (II) fglrx(0): Kernel Module version matches driver.
[    18.719] (II) fglrx(0): Kernel Module Build Time Information:
[    18.719] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.11.0-12-generic
[    18.719] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    18.719] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    18.719] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    18.719] (II) fglrx(0): [uki] register handle = 0x00004000
[    18.719] (II) fglrx(0): DRI initialization successfull
[    18.719] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x010e0000
[    18.720] (==) fglrx(0): Backing store disabled
[    18.720] Loading extension FGLRXEXTENSION
[    18.720] (**) fglrx(0): DPMS enabled
[    18.720] (II) fglrx(0): Initialized in-driver Xinerama extension
[    18.720] (**) fglrx(0): Textured Video is enabled.
[    18.720] (II) LoadModule: "glesx"
[    18.720] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[    18.721] (II) Module glesx: vendor="X.Org Foundation"
[    18.721] 	compiled for 1.4.99.906, module version = 1.0.0
[    18.721] Loading extension GLESX
[    18.721] (II) fglrx(0): GLESX enableFlags = 592
[    18.721] (II) fglrx(0): GLESX is enabled
[    18.721] (II) LoadModule: "amdxmm"
[    18.721] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[    18.721] (II) Module amdxmm: vendor="X.Org Foundation"
[    18.721] 	compiled for 1.4.99.906, module version = 2.0.0
[    18.733] Loading extension AMDXVOPL
[    18.733] Loading extension AMDXVBA
[    18.733] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    18.735] (II) fglrx(0): Enable composite support successfully
[    18.735] (WW) fglrx(0): Option "VendorName" is not used
[    18.735] (WW) fglrx(0): Option "ModelName" is not used
[    18.735] (II) fglrx(0): X context handle = 0x1
[    18.735] (II) fglrx(0): [DRI] installation complete
[    18.735] (==) fglrx(0): Silken mouse enabled
[    18.736] (==) fglrx(0): Using HW cursor of display infrastructure!
[    18.736] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    18.778] (--) RandR disabled
[    18.785] (II) SELinux: Disabled on system
[    18.786] ukiDynamicMajor: found major device number 250
[    18.786] ukiDynamicMajor: found major device number 250
[    18.786] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    18.786] ukiOpenDevice: node name is /dev/ati/card0
[    18.786] ukiOpenDevice: open result is 15, (OK)
[    18.786] ukiOpenByBusid: ukiOpenMinor returns 15
[    18.786] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    18.822] ukiDynamicMajor: found major device number 250
[    18.822] ukiDynamicMajor: found major device number 250
[    18.822] ukiDynamicMajor: found major device number 250
[    18.822] ukiOpenDevice: node name is /dev/ati/card0
[    18.822] ukiOpenDevice: open result is 16, (OK)
[    18.822] ukiGetBusid returned 'PCI:1:0:0'
[    18.822] ukiOpenDevice: node name is /dev/ati/card1
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: Open failed
[    18.822] ukiOpenDevice: node name is /dev/ati/card2
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: Open failed
[    18.822] ukiOpenDevice: node name is /dev/ati/card3
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: Open failed
[    18.822] ukiOpenDevice: node name is /dev/ati/card4
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: Open failed
[    18.822] ukiOpenDevice: node name is /dev/ati/card5
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: Open failed
[    18.822] ukiOpenDevice: node name is /dev/ati/card6
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: Open failed
[    18.822] ukiOpenDevice: node name is /dev/ati/card7
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: Open failed
[    18.822] ukiOpenDevice: node name is /dev/ati/card8
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: Open failed
[    18.822] ukiOpenDevice: node name is /dev/ati/card9
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: Open failed
[    18.822] ukiOpenDevice: node name is /dev/ati/card10
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: open result is -1, (No such device)
[    18.822] ukiOpenDevice: Open failed
[    18.822] ukiOpenDevice: node name is /dev/ati/card11
[    18.823] ukiOpenDevice: open result is -1, (No such device)
[    18.823] ukiOpenDevice: open result is -1, (No such device)
[    18.823] ukiOpenDevice: Open failed
[    18.823] ukiOpenDevice: node name is /dev/ati/card12
[    18.823] ukiOpenDevice: open result is -1, (No such device)
[    18.823] ukiOpenDevice: open result is -1, (No such device)
[    18.823] ukiOpenDevice: Open failed
[    18.823] ukiOpenDevice: node name is /dev/ati/card13
[    18.823] ukiOpenDevice: open result is -1, (No such device)
[    18.823] ukiOpenDevice: open result is -1, (No such device)
[    18.823] ukiOpenDevice: Open failed
[    18.823] ukiOpenDevice: node name is /dev/ati/card14
[    18.823] ukiOpenDevice: open result is -1, (No such device)
[    18.823] ukiOpenDevice: open result is -1, (No such device)
[    18.823] ukiOpenDevice: Open failed
[    18.823] ukiOpenDevice: node name is /dev/ati/card15
[    18.823] ukiOpenDevice: open result is -1, (No such device)
[    18.823] ukiOpenDevice: open result is -1, (No such device)
[    18.823] ukiOpenDevice: Open failed
[    18.823] ukiDynamicMajor: found major device number 250
[    18.823] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    18.823] ukiOpenDevice: node name is /dev/ati/card0
[    18.823] ukiOpenDevice: open result is 16, (OK)
[    18.823] ukiOpenByBusid: ukiOpenMinor returns 16
[    18.823] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    18.997] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    18.998] ukiDynamicMajor: found major device number 250
[    18.998] ukiDynamicMajor: found major device number 250
[    18.998] ukiDynamicMajor: found major device number 250
[    18.998] ukiOpenDevice: node name is /dev/ati/card0
[    18.998] ukiOpenDevice: open result is 17, (OK)
[    18.998] ukiGetBusid returned 'PCI:1:0:0'
[    18.998] ukiOpenDevice: node name is /dev/ati/card1
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card2
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card3
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card4
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card5
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card6
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card7
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card8
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card9
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card10
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card11
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: open result is -1, (No such device)
[    18.998] ukiOpenDevice: Open failed
[    18.998] ukiOpenDevice: node name is /dev/ati/card12
[    18.999] ukiOpenDevice: open result is -1, (No such device)
[    18.999] ukiOpenDevice: open result is -1, (No such device)
[    18.999] ukiOpenDevice: Open failed
[    18.999] ukiOpenDevice: node name is /dev/ati/card13
[    18.999] ukiOpenDevice: open result is -1, (No such device)
[    18.999] ukiOpenDevice: open result is -1, (No such device)
[    18.999] ukiOpenDevice: Open failed
[    18.999] ukiOpenDevice: node name is /dev/ati/card14
[    18.999] ukiOpenDevice: open result is -1, (No such device)
[    18.999] ukiOpenDevice: open result is -1, (No such device)
[    18.999] ukiOpenDevice: Open failed
[    18.999] ukiOpenDevice: node name is /dev/ati/card15
[    18.999] ukiOpenDevice: open result is -1, (No such device)
[    18.999] ukiOpenDevice: open result is -1, (No such device)
[    18.999] ukiOpenDevice: Open failed
[    18.999] ukiDynamicMajor: found major device number 250
[    18.999] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    18.999] ukiOpenDevice: node name is /dev/ati/card0
[    18.999] ukiOpenDevice: open result is 17, (OK)
[    18.999] ukiOpenByBusid: ukiOpenMinor returns 17
[    18.999] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    19.012] (II) fglrx(0): OverDrive5 Detected!
[    19.019] (II) fglrx(0): Setting screen physical size to 508 x 285
[    19.029] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.032] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    19.032] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.032] (II) LoadModule: "evdev"
[    19.032] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.040] (II) Module evdev: vendor="X.Org Foundation"
[    19.040] 	compiled for 1.14.1, module version = 2.7.3
[    19.040] 	Module class: X.Org XInput Driver
[    19.040] 	ABI class: X.Org XInput driver, version 19.1
[    19.040] (II) Using input driver 'evdev' for 'Power Button'
[    19.040] (**) Power Button: always reports core events
[    19.040] (**) evdev: Power Button: Device: "/dev/input/event1"
[    19.040] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.040] (--) evdev: Power Button: Found keys
[    19.040] (II) evdev: Power Button: Configuring as keyboard
[    19.040] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    19.040] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    19.040] (**) Option "xkb_rules" "evdev"
[    19.040] (**) Option "xkb_model" "pc105"
[    19.040] (**) Option "xkb_layout" "us"
[    19.041] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    19.041] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.041] (II) Using input driver 'evdev' for 'Power Button'
[    19.041] (**) Power Button: always reports core events
[    19.041] (**) evdev: Power Button: Device: "/dev/input/event0"
[    19.041] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.041] (--) evdev: Power Button: Found keys
[    19.041] (II) evdev: Power Button: Configuring as keyboard
[    19.041] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    19.041] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    19.041] (**) Option "xkb_rules" "evdev"
[    19.041] (**) Option "xkb_model" "pc105"
[    19.041] (**) Option "xkb_layout" "us"
[    19.041] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event10)
[    19.041] (II) No input driver specified, ignoring this device.
[    19.041] (II) This device may have been added with another device file.
[    19.042] (II) config/udev: Adding input device Microsoft Comfort Mouse 6000 (/dev/input/event12)
[    19.042] (**) Microsoft Comfort Mouse 6000: Applying InputClass "evdev pointer catchall"
[    19.042] (**) Microsoft Comfort Mouse 6000: Applying InputClass "evdev keyboard catchall"
[    19.042] (**) Microsoft Comfort Mouse 6000: Applying InputClass "Microsoft Comfort Mouse 6000"
[    19.042] (II) Using input driver 'evdev' for 'Microsoft Comfort Mouse 6000'
[    19.042] (**) Microsoft Comfort Mouse 6000: always reports core events
[    19.042] (**) evdev: Microsoft Comfort Mouse 6000: Device: "/dev/input/event12"
[    19.042] (--) evdev: Microsoft Comfort Mouse 6000: Vendor 0x45e Product 0x77d
[    19.042] (--) evdev: Microsoft Comfort Mouse 6000: Found 9 mouse buttons
[    19.042] (--) evdev: Microsoft Comfort Mouse 6000: Found scroll wheel(s)
[    19.042] (--) evdev: Microsoft Comfort Mouse 6000: Found relative axes
[    19.042] (--) evdev: Microsoft Comfort Mouse 6000: Found x and y relative axes
[    19.042] (--) evdev: Microsoft Comfort Mouse 6000: Found absolute axes
[    19.042] (II) evdev: Microsoft Comfort Mouse 6000: Forcing absolute x/y axes to exist.
[    19.042] (--) evdev: Microsoft Comfort Mouse 6000: Found keys
[    19.042] (II) evdev: Microsoft Comfort Mouse 6000: Configuring as mouse
[    19.042] (II) evdev: Microsoft Comfort Mouse 6000: Configuring as keyboard
[    19.042] (II) evdev: Microsoft Comfort Mouse 6000: Adding scrollwheel support
[    19.042] (**) evdev: Microsoft Comfort Mouse 6000: YAxisMapping: buttons 4 and 5
[    19.042] (**) evdev: Microsoft Comfort Mouse 6000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.042] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb6/6-1/6-1:1.0/input/input12/event12"
[    19.042] (II) XINPUT: Adding extended input device "Microsoft Comfort Mouse 6000" (type: KEYBOARD, id 8)
[    19.042] (**) Option "xkb_rules" "evdev"
[    19.042] (**) Option "xkb_model" "pc105"
[    19.042] (**) Option "xkb_layout" "us"
[    19.042] (II) evdev: Microsoft Comfort Mouse 6000: initialized for relative axes.
[    19.042] (WW) evdev: Microsoft Comfort Mouse 6000: ignoring absolute axes.
[    19.042] (**) Microsoft Comfort Mouse 6000: (accel) keeping acceleration scheme 1
[    19.042] (**) Microsoft Comfort Mouse 6000: (accel) acceleration profile 0
[    19.042] (**) Option "AccelerationNumerator" "2"
[    19.042] (**) Option "AccelerationDenominator" "1"
[    19.042] (**) Option "AccelerationThreshold" "4"
[    19.042] (**) Microsoft Comfort Mouse 6000: (accel) acceleration factor: 2.000
[    19.042] (**) Microsoft Comfort Mouse 6000: (accel) acceleration threshold: 4
[    19.043] (II) config/udev: Adding input device Microsoft Comfort Mouse 6000 (/dev/input/mouse0)
[    19.043] (II) No input driver specified, ignoring this device.
[    19.043] (II) This device may have been added with another device file.
[    19.043] (II) config/udev: Adding input device Generic USB Keyboard (/dev/input/event13)
[    19.043] (**) Generic USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    19.043] (II) Using input driver 'evdev' for 'Generic USB Keyboard'
[    19.043] (**) Generic USB Keyboard: always reports core events
[    19.043] (**) evdev: Generic USB Keyboard: Device: "/dev/input/event13"
[    19.043] (--) evdev: Generic USB Keyboard: Vendor 0x40b Product 0x2000
[    19.043] (--) evdev: Generic USB Keyboard: Found keys
[    19.043] (II) evdev: Generic USB Keyboard: Configuring as keyboard
[    19.043] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb6/6-5/6-5:1.0/input/input13/event13"
[    19.043] (II) XINPUT: Adding extended input device "Generic USB Keyboard" (type: KEYBOARD, id 9)
[    19.043] (**) Option "xkb_rules" "evdev"
[    19.043] (**) Option "xkb_model" "pc105"
[    19.043] (**) Option "xkb_layout" "us"
[    19.044] (II) config/udev: Adding input device Generic USB Keyboard (/dev/input/event14)
[    19.044] (**) Generic USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    19.044] (II) Using input driver 'evdev' for 'Generic USB Keyboard'
[    19.044] (**) Generic USB Keyboard: always reports core events
[    19.044] (**) evdev: Generic USB Keyboard: Device: "/dev/input/event14"
[    19.044] (--) evdev: Generic USB Keyboard: Vendor 0x40b Product 0x2000
[    19.044] (--) evdev: Generic USB Keyboard: Found scroll wheel(s)
[    19.044] (II) evdev: Generic USB Keyboard: Forcing buttons for scroll wheel(s)
[    19.044] (--) evdev: Generic USB Keyboard: Found relative axes
[    19.044] (--) evdev: Generic USB Keyboard: Found x and y relative axes
[    19.044] (--) evdev: Generic USB Keyboard: Found keys
[    19.044] (II) evdev: Generic USB Keyboard: Configuring as mouse
[    19.044] (II) evdev: Generic USB Keyboard: Configuring as keyboard
[    19.044] (II) evdev: Generic USB Keyboard: Adding scrollwheel support
[    19.044] (**) evdev: Generic USB Keyboard: YAxisMapping: buttons 4 and 5
[    19.044] (**) evdev: Generic USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.044] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb6/6-5/6-5:1.1/input/input14/event14"
[    19.044] (II) XINPUT: Adding extended input device "Generic USB Keyboard" (type: KEYBOARD, id 10)
[    19.044] (**) Option "xkb_rules" "evdev"
[    19.044] (**) Option "xkb_model" "pc105"
[    19.044] (**) Option "xkb_layout" "us"
[    19.044] (II) evdev: Generic USB Keyboard: initialized for relative axes.
[    19.044] (**) Generic USB Keyboard: (accel) keeping acceleration scheme 1
[    19.044] (**) Generic USB Keyboard: (accel) acceleration profile 0
[    19.044] (**) Generic USB Keyboard: (accel) acceleration factor: 2.000
[    19.044] (**) Generic USB Keyboard: (accel) acceleration threshold: 4
[    19.045] (II) config/udev: Adding input device Generic USB Keyboard (/dev/input/mouse1)
[    19.045] (II) No input driver specified, ignoring this device.
[    19.045] (II) This device may have been added with another device file.
[    19.045] (II) config/udev: Adding input device gspca_pac7302 (/dev/input/event11)
[    19.045] (**) gspca_pac7302: Applying InputClass "evdev keyboard catchall"
[    19.045] (II) Using input driver 'evdev' for 'gspca_pac7302'
[    19.045] (**) gspca_pac7302: always reports core events
[    19.045] (**) evdev: gspca_pac7302: Device: "/dev/input/event11"
[    19.045] (--) evdev: gspca_pac7302: Vendor 0x93a Product 0x2621
[    19.045] (--) evdev: gspca_pac7302: Found keys
[    19.045] (II) evdev: gspca_pac7302: Configuring as keyboard
[    19.045] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb7/7-1/input/input11/event11"
[    19.045] (II) XINPUT: Adding extended input device "gspca_pac7302" (type: KEYBOARD, id 11)
[    19.045] (**) Option "xkb_rules" "evdev"
[    19.045] (**) Option "xkb_model" "pc105"
[    19.045] (**) Option "xkb_layout" "us"
[    19.045] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event2)
[    19.045] (II) No input driver specified, ignoring this device.
[    19.045] (II) This device may have been added with another device file.
[    19.046] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event3)
[    19.046] (II) No input driver specified, ignoring this device.
[    19.046] (II) This device may have been added with another device file.
[    19.046] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event4)
[    19.046] (II) No input driver specified, ignoring this device.
[    19.046] (II) This device may have been added with another device file.
[    19.046] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event5)
[    19.046] (II) No input driver specified, ignoring this device.
[    19.046] (II) This device may have been added with another device file.
[    19.046] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event6)
[    19.046] (II) No input driver specified, ignoring this device.
[    19.046] (II) This device may have been added with another device file.
[    19.046] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event7)
[    19.046] (II) No input driver specified, ignoring this device.
[    19.046] (II) This device may have been added with another device file.
[    19.047] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event8)
[    19.047] (II) No input driver specified, ignoring this device.
[    19.047] (II) This device may have been added with another device file.
[    19.047] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event9)
[    19.047] (II) No input driver specified, ignoring this device.
[    19.047] (II) This device may have been added with another device file.
[    19.052] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    22.024] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    22.025] (II) fglrx(0): Using EDID range info for horizontal sync
[    22.025] (II) fglrx(0): Using EDID range info for vertical refresh
[    22.025] (II) fglrx(0): Printing DDC gathered Modelines:
[    22.025] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    22.025] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    22.025] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    22.025] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    22.025] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    22.025] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    22.025] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    22.025] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    22.025] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    22.025] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    22.025] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    22.025] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    22.025] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    22.025] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    22.025] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    22.025] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    22.025] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    22.538] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.545] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    22.545] (II) fglrx(0): Using hsync ranges from config file
[    22.545] (II) fglrx(0): Using vrefresh ranges from config file
[    22.545] (II) fglrx(0): Printing DDC gathered Modelines:
[    22.545] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    22.545] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    22.545] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    22.545] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    22.545] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    22.545] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    22.545] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    22.545] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    22.545] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    22.545] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    22.545] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    22.545] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    22.545] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    22.545] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    22.545] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    22.545] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    22.545] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    23.558] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    23.558] (II) fglrx(0): Using hsync ranges from config file
[    23.558] (II) fglrx(0): Using vrefresh ranges from config file
[    23.558] (II) fglrx(0): Printing DDC gathered Modelines:
[    23.558] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    23.558] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    23.558] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    23.558] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    23.558] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    23.558] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    23.558] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    23.558] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    23.558] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    23.558] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    23.558] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    23.558] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    23.558] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    23.558] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    23.558] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    23.558] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    23.558] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    23.813] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    23.814] (II) fglrx(0): Using hsync ranges from config file
[    23.814] (II) fglrx(0): Using vrefresh ranges from config file
[    23.814] (II) fglrx(0): Printing DDC gathered Modelines:
[    23.814] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    23.814] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    23.814] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    23.814] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    23.814] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    23.814] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    23.814] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    23.814] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    23.814] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    23.814] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    23.814] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    23.814] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    23.814] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    23.814] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    23.814] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    23.814] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    23.814] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    23.877] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    23.877] (II) fglrx(0): Using hsync ranges from config file
[    23.877] (II) fglrx(0): Using vrefresh ranges from config file
[    23.877] (II) fglrx(0): Printing DDC gathered Modelines:
[    23.877] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    23.877] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    23.877] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    23.877] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    23.877] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    23.877] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    23.877] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    23.877] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    23.877] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    23.878] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    23.878] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    23.878] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    23.878] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    23.878] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    23.878] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    23.878] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    23.878] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    24.463] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    24.499] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.414] (II) XKB: reuse xkmfile /var/lib/xkb/server-CB537B66032B0DBE0AE956F537017A59DB020654.xkm
[    43.639] (II) fglrx(0): EDID vendor "GSM", prod id 22535
[    43.639] (II) fglrx(0): Using hsync ranges from config file
[    43.639] (II) fglrx(0): Using vrefresh ranges from config file
[    43.639] (II) fglrx(0): Printing DDC gathered Modelines:
[    43.639] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    43.639] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    43.639] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    43.639] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    43.639] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    43.639] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    43.639] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    43.639] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz e)
[    43.639] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    43.639] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    43.639] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    43.639] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    43.639] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    43.639] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    43.639] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    43.639] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    43.639] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)

```

---

### Post by mc4man on 2013-12-23
Is your mouse plugged into the keyboard?

---

### Post by Thee on 2013-12-23
No.

---

### Post by Toz on 2013-12-24
I'm sorry but I don't know what else to offer. Its been a year or so since I've tinkered with mouse acceleration, but it was never this difficult/quirky. I will step back and let someone else take the helm.

---

### Post by Thee on 2013-12-24
No problem man, you did more then I thought was possible, I mean, who would have thought that there were so many ways to fix a mouse problem :P
So thanks a thousand, you really gave your best to help me out, I really appreciate it ;)

I'll learn to live with it until some upgrade or reinstall, if no one offers a solution ofc.

---

### Post by norayr2 on 2014-09-25
> **Toz said:**
> Perhaps we need to export Xauthority as well. Change the /etc/pm/sleep.d/000fix_mouse_acceleration file to look like this:   ```
#!/bin/sh username=MYUSERNAME userhome=/home/$username export XAUTHORITY="$userhome/.Xauthority" export DISPLAY=":0"  case "$1" in     thaw|resume)          su -c $username "/usr/bin/xset m 2/1 4"      ;; esac 
```  ...change MYUSERNAME to be your system username and try again. Refer to /var/log/pm-suspend.log for errors if it doesn't work.         it will work, just need to change   >su -l $username -c "/usr/bin/xset m 2/1 4"  so it should look like:   ```
#!/bin/sh  username=MYUSERNAME userhome=/home/$username export XAUTHORITY="$userhome/.Xauthority" export DISPLAY=":0"     case "$1" in     thaw|resume)                  su -l $username -c "/usr/bin/xset m 2/1 4"     ;; esac 
```  good luck.

---

