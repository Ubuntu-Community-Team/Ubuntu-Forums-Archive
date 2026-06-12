---
title: "Ubuntu 14.04 freeze a lot. How to fix it?"
date: 2014-04-23
forum: General Help
---

### Post by THPubs on 2014-04-23
[COLOR=#333333][FONT=UbuntuRegular]Since the day I installed Ubuntu 14.04 I face frequent freezes. Today it happened for about six times. When it freeze the mouse barely move. It stays that way for a long time. My GPU is Nvidia GT640 and I use nvidia-331 driver. I don't have Nvidia Optimus (this is a desktop) and I don't have prime installed. Here's the last part of my Xorg.0.log :

```
[/FONT][/COLOR][     6.088] (**) HID 04f3:0103: (accel) acceleration threshold: 4[     6.089] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event10)
[     6.089] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     6.089] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     6.089] (**) Eee PC WMI hotkeys: always reports core events
[     6.089] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event10"
[     6.089] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     6.089] (--) evdev: Eee PC WMI hotkeys: Found keys
[     6.089] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     6.089] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input13/event10"
[     6.089] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 11)
[     6.089] (**) Option "xkb_rules" "evdev"
[     6.089] (**) Option "xkb_model" "pc105"
[     6.089] (**) Option "xkb_layout" "us"
[     6.549] (II) NVIDIA(GPU-0): Display (Samsung SMS19A100 (CRT-0)) does not support NVIDIA 3D
[     6.549] (II) NVIDIA(GPU-0):     Vision stereo.
[     6.560] (II) NVIDIA(GPU-0): Display (Samsung T23B350 (DFP-1)) does not support NVIDIA 3D
[     6.560] (II) NVIDIA(GPU-0):     Vision stereo.
[     6.859] (II) NVIDIA(GPU-0): Display (Samsung SMS19A100 (CRT-0)) does not support NVIDIA 3D
[     6.859] (II) NVIDIA(GPU-0):     Vision stereo.
[     6.869] (II) NVIDIA(GPU-0): Display (Samsung T23B350 (DFP-1)) does not support NVIDIA 3D
[     6.869] (II) NVIDIA(GPU-0):     Vision stereo.
[   975.216] (II) NVIDIA(GPU-0): Display (Samsung SMS19A100 (CRT-0)) does not support NVIDIA 3D
[   975.216] (II) NVIDIA(GPU-0):     Vision stereo.
[   975.226] (II) NVIDIA(GPU-0): Display (Samsung T23B350 (DFP-1)) does not support NVIDIA 3D
[   975.226] (II) NVIDIA(GPU-0):     Vision stereo.
[   975.583] (II) NVIDIA(0): Setting mode "VGA-0: nvidia-auto-select @1366x768 +0+0 {ViewPortIn=1366x768, ViewPortOut=1366x768+0+0}, HDMI-0: nvidia-auto-select @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPort$
[   975.621] (II) NVIDIA(0): Setting mode "VGA-0: nvidia-auto-select @1366x768 +1920+312 {ViewPortIn=1366x768, ViewPortOut=1366x768+0+0}, HDMI-0: nvidia-auto-select @1920x1080 +0+0 {ViewPortIn=1920x1080, Vie$
[   975.745] (II) NVIDIA(GPU-0): Display (Samsung SMS19A100 (CRT-0)) does not support NVIDIA 3D
[   975.746] (II) NVIDIA(GPU-0):     Vision stereo.
[   975.757] (II) NVIDIA(GPU-0): Display (Samsung T23B350 (DFP-1)) does not support NVIDIA 3D
[   975.757] (II) NVIDIA(GPU-0):     Vision stereo.
[   975.865] (II) NVIDIA(GPU-0): Display (Samsung SMS19A100 (CRT-0)) does not support NVIDIA 3D
[   975.865] (II) NVIDIA(GPU-0):     Vision stereo.
[   975.876] (II) NVIDIA(GPU-0): Display (Samsung T23B350 (DFP-1)) does not support NVIDIA 3D
[   975.876] (II) NVIDIA(GPU-0):     Vision stereo.
[   975.958] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   976.609] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   976.627] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   976.723] (II) NVIDIA(GPU-0): Display (Samsung SMS19A100 (CRT-0)) does not support NVIDIA 3D
[   976.723] (II) NVIDIA(GPU-0):     Vision stereo.
[   976.735] (II) NVIDIA(GPU-0): Display (Samsung T23B350 (DFP-1)) does not support NVIDIA 3D
[   976.735] (II) NVIDIA(GPU-0):     Vision stereo.

[   977.780] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm[COLOR=#333333][FONT=UbuntuRegular]
```

Here's the dmesg :

```
[/FONT][/COLOR][    3.239177] ip6_tables: (C) 2000-2006 Netfilter Core Team[    3.331938] asus_wmi: ASUS WMI generic driver loaded
[    3.337421] asus_wmi: Initialization: 0x0
[    3.337438] asus_wmi: BIOS WMI version: 0.9
[    3.337466] asus_wmi: SFUN value: 0x0
[    3.337799] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input13
[    3.348748] asus_wmi: Disabling ACPI video driver
[    3.666802] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[    3.666874] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
[    3.666934] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[    4.142334] init: udev-fallback-graphics main process (642) terminated with status 1
[    4.156800] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[    4.600892] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
[    4.646430] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[    4.717503] init: failsafe main process (758) killed by TERM signal
[    4.788815] Bluetooth: Core ver 2.17
[    4.788831] NET: Registered protocol family 31
[    4.788832] Bluetooth: HCI device and connection manager initialized
[    4.788840] Bluetooth: HCI socket layer initialized
[    4.788843] Bluetooth: L2CAP socket layer initialized
[    4.788848] Bluetooth: SCO socket layer initialized
[    4.792568] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.792571] Bluetooth: BNEP filters: protocol multicast
[    4.792580] Bluetooth: BNEP socket layer initialized
[    4.795499] Bluetooth: RFCOMM TTY layer initialized
[    4.795510] Bluetooth: RFCOMM socket layer initialized
[    4.795515] Bluetooth: RFCOMM ver 1.11
[    4.833055] type=1400 audit(1398261309.769:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=871 comm="apparmor_parser"
[    4.833064] type=1400 audit(1398261309.769:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=871 comm="apparmor_parser"
[    4.833517] type=1400 audit(1398261309.769:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=871 comm="apparmor_parser"
[    4.855534] init: cups main process (876) killed by HUP signal
[    4.855547] init: cups main process ended, respawning
[    4.956330] r8169 0000:03:00.0 eth0: link down
[    4.956361] r8169 0000:03:00.0 eth0: link down
[    4.956382] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.956712] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

[    5.140862] init: nvidia-prime main process (998) terminated with status 127[COLOR=#333333][FONT=UbuntuRegular]
```
[/FONT][/COLOR]

---

### Post by rtalcott on 2014-04-23
I am having a freeze problem with Google Chrome...locks up on multiple machines...Chromium or Firefox no problem...it's Chrome...are you running Chrome?
Edit:  I guess I lied...jsut had Chromium lock up also so it's Chrome and Chromium for me.

---

### Post by THPubs on 2014-04-23
Hmmm... Yes I do use Google Chrome! Is it a Chrome problem or something in Compiz make Chrome act like this?

---

### Post by oldrocker99 on 2014-04-23
This is interesting. Chromium does not accept text input, while Chrome runs just fine. For me.

---

### Post by Boorhin on 2014-11-05
I have the same problem when I start chromium, the machine hangs and Unity struggles until it sorts of crash (the clock is not refreshed, the windows menus disappear). Shortcuts also stop working so it is impossible to start a console. Only the already open programs are actually accessible. I have a big workstation so I doubt it is resource limitations. 
Any suggestion?

---

