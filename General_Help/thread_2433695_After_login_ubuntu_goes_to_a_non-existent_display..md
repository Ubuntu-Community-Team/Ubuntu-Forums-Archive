---
title: "After login ubuntu goes to a non-existent display. Help!"
date: 2019-12-23
forum: General Help
---

### Post by Joao Lacerda on 2019-12-23
Friends I really need some help.
After login ubuntu goes to a non-existent screen. 
I only have now a black screen.
I have login with ssh to print some info. 
If someone can help it will be great appreciated.

By the way Ubuntu is running so smoothly on this laptop I just need to fix this issue.

some info:

uname -a
```
root@macbookpro:~# uname -aLinux macbookpro 5.3.0-24-generic #26-Ubuntu SMP Thu Nov 14 01:33:18 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```

xorg.1.log
```
[COLOR=#000000][ 29.983] (II) This device may have been added with another device file.[/COLOR]
[COLOR=#000000][ 29.983] (II) config/udev: Adding input device applesmc (/dev/input/event10)[/COLOR]
[COLOR=#000000][ 29.983] (II) No input driver specified, ignoring this device.[/COLOR]
[COLOR=#000000][ 29.983] (II) This device may have been added with another device file.[/COLOR]
[COLOR=#000000][ 29.983] (II) config/udev: Adding input device applesmc (/dev/input/js0)[/COLOR]
[COLOR=#000000][ 29.983] (II) No input driver specified, ignoring this device.[/COLOR]
[COLOR=#000000][ 29.983] (II) This device may have been added with another device file.[/COLOR]
[COLOR=#000000][ 30.576] (--) NVIDIA(GPU-0): Apple Color LCD (DFP-0): connected[/COLOR]
[COLOR=#000000][ 30.576] (--) NVIDIA(GPU-0): Apple Color LCD (DFP-0): Internal LVDS[/COLOR]
[COLOR=#000000][ 30.576] (--) NVIDIA(GPU-0): Apple Color LCD (DFP-0): 330.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 30.576] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 30.576] (--) NVIDIA(GPU-0): DFP-1: disconnected[/COLOR]
[COLOR=#000000][ 30.576] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS[/COLOR]
[COLOR=#000000][ 30.576] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 30.576] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): DFP-2: disconnected[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): DFP-3: disconnected[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): DFP-3: 165.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): DFP-4: disconnected[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): DFP-4: 480.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): DFP-5: disconnected[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): DFP-5: Internal DisplayPort[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): DFP-5: 480.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): DFP-6: disconnected[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): DFP-6: Internal DisplayPort[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): DFP-6: 480.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): Apple Color LCD (DFP-0): connected[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): Apple Color LCD (DFP-0): Internal LVDS[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): Apple Color LCD (DFP-0): 330.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): DFP-1: disconnected[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 30.577] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0): DFP-2: disconnected[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0): DFP-3: disconnected[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0): DFP-3: 165.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0): DFP-4: disconnected[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0): DFP-4: 480.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0): DFP-5: disconnected[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0): DFP-5: Internal DisplayPort[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0): DFP-5: 480.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0): DFP-6: disconnected[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0): DFP-6: Internal DisplayPort[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0): DFP-6: 480.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 30.578] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 30.776] (II) NVIDIA(0): Setting mode "NULL"[/COLOR]
[COLOR=#000000][ 31.302] randr: falling back to unsynchronized pixmap sharing[/COLOR]
[COLOR=#000000][ 32.800] (--) NVIDIA(GPU-0): Apple Color LCD (DFP-0): connected[/COLOR]
[COLOR=#000000][ 32.800] (--) NVIDIA(GPU-0): Apple Color LCD (DFP-0): Internal LVDS[/COLOR]
[COLOR=#000000][ 32.800] (--) NVIDIA(GPU-0): Apple Color LCD (DFP-0): 330.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 32.800] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 32.800] (--) NVIDIA(GPU-0): DFP-1: disconnected[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0): DFP-2: disconnected[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0): DFP-3: disconnected[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0): DFP-3: 165.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0): DFP-4: disconnected[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0): DFP-4: 480.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0): DFP-5: disconnected[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0): DFP-5: Internal DisplayPort[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0): DFP-5: 480.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0): DFP-6: disconnected[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0): DFP-6: Internal DisplayPort[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0): DFP-6: 480.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 32.801] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): Apple Color LCD (DFP-0): connected[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): Apple Color LCD (DFP-0): Internal LVDS[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): Apple Color LCD (DFP-0): 330.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): DFP-1: disconnected[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): DFP-2: disconnected[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): DFP-3: disconnected[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): DFP-3: 165.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): DFP-4: disconnected[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): DFP-4: 480.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): DFP-5: disconnected[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): DFP-5: Internal DisplayPort[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): DFP-5: 480.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0):[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): DFP-6: disconnected[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): DFP-6: Internal DisplayPort[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): DFP-6: 480.0 MHz maximum pixel clock[/COLOR]
[COLOR=#000000][ 32.802] (--) NVIDIA(GPU-0): [/COLOR]
```

dmesg:
```

[    3.210282] applesmc: send_byte(0x00, 0x0300) fail: 0x40
[    3.210284] applesmc: LKSB: write data fail
[    3.211593] wl 0000:03:00.0 wlp3s0: renamed from wlan0
[    3.255357] uvcvideo: Found UVC 1.00 device FaceTime HD Camera (Built-in) (05ac:8509)
[    3.257914] usbcore: registered new interface driver btusb
[    3.263763] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
[    3.264074] snd_hda_intel 0000:01:00.1: enabling device (0000 -> 0002)
[    3.264149] snd_hda_intel 0000:01:00.1: Disabling MSI
[    3.264157] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[    3.279276] uvcvideo 1-1.1:1.0: Entity type for entity Processing 3 was not initialized!
[    3.279278] uvcvideo 1-1.1:1.0: Entity type for entity Camera 1 was not initialized!
[    3.279333] input: FaceTime HD Camera (Built-in):  as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input11
[    3.279421] usbcore: registered new interface driver uvcvideo
[    3.279422] USB Video Class driver (1.1.1)
[    3.319731] [drm] Initialized i915 1.6.0 20190619 for 0000:00:02.0 on minor 0
[    3.319838] [Firmware Bug]: ACPI(GFX0) defines _DOD but not _DOS
[    3.319874] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[    3.319972] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input12
[    3.320814] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
[    3.321023] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input13
[    3.321290] snd_hda_intel 0000:00:1b.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    3.321684] usb 2-1.8.1.1: USB disconnect, device number 6
[    3.331735] nvidia-nvlink: Nvlink Core is being initialized, major device number 236
[    3.332083] nvidia 0000:01:00.0: enabling device (0006 -> 0007)
[    3.332187] nvidia 0000:01:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=io+mem
[    3.332300] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  390.129  Mon Jul 22 21:10:21 PDT 2019 (using threaded interrupts)
[    3.359850] snd_hda_codec_cirrus hdaudioC0D0: autoconfig for CS4206: line_outs=2 (0xb/0xa/0x0/0x0/0x0) type:speaker
[    3.359853] snd_hda_codec_cirrus hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.359855] snd_hda_codec_cirrus hdaudioC0D0:    hp_outs=1 (0x9/0x0/0x0/0x0/0x0)
[    3.359857] snd_hda_codec_cirrus hdaudioC0D0:    mono: mono_out=0x0
[    3.359858] snd_hda_codec_cirrus hdaudioC0D0:    dig-out=0x10/0x0
[    3.359859] snd_hda_codec_cirrus hdaudioC0D0:    inputs:
[    3.359861] snd_hda_codec_cirrus hdaudioC0D0:      Mic=0xd
[    3.359863] snd_hda_codec_cirrus hdaudioC0D0:      Line=0xc
[    3.359864] snd_hda_codec_cirrus hdaudioC0D0:    dig-in=0xf
[    3.365440] Bluetooth: hci0: BCM: chip id 63 build 1818
[    3.366439] Bluetooth: hci0: BCM: product 05ac:821d
[    3.367429] Bluetooth: hci0: BCM: features 0x07
[    3.369054] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    3.383443] Bluetooth: hci0: Apple Bluetooth Device
[    3.384414] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  390.129  Tue Jul 23 00:29:03 PDT 2019
[    3.390132] [drm] [nvidia-drm] [GPU ID 0x00000100] Loading driver
[    3.390134] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:01:00.0 on minor 1
[    3.419512] intel_rapl_common: Found RAPL domain package
[    3.419514] intel_rapl_common: Found RAPL domain core
[    3.419515] intel_rapl_common: Found RAPL domain uncore
[    3.442318] nvidia-uvm: Loaded the UVM driver in 8 mode, major device number 235
[    3.445347] checking generic (90020000 710000) vs hw (b0000000 10000000)
[    3.445419] i915 0000:00:02.0: fb1: i915drmfb frame buffer device
[    3.473754] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    3.473850] input: HDA Intel PCH SPDIF In as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[    3.518486] ACPI Warning: \_SB.PCI0.P0P2.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20190703/nsarguments-59)
[    3.621052] usb 2-1.8.1.2: USB disconnect, device number 8
[    4.069320] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input17
[    4.069393] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input18
[    4.069460] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input19
[    4.295030] audit: type=1400 audit(1577128176.121:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe" pid=814 comm="apparmor_parser"
[    4.295035] audit: type=1400 audit(1577128176.121:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="nvidia_modprobe//kmod" pid=814 comm="apparmor_parser"
[    4.295282] audit: type=1400 audit(1577128176.121:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=810 comm="apparmor_parser"
[    4.295285] audit: type=1400 audit(1577128176.121:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=810 comm="apparmor_parser"
[    4.295287] audit: type=1400 audit(1577128176.121:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" pid=810 comm="apparmor_parser"
[    4.300727] audit: type=1400 audit(1577128176.129:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=812 comm="apparmor_parser"
[    4.300731] audit: type=1400 audit(1577128176.129:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=812 comm="apparmor_parser"
[    4.300733] audit: type=1400 audit(1577128176.129:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=812 comm="apparmor_parser"
[    4.300736] audit: type=1400 audit(1577128176.129:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=812 comm="apparmor_parser"
[    4.972624] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.972625] Bluetooth: BNEP filters: protocol multicast
[    4.972629] Bluetooth: BNEP socket layer initialized
[    9.906894] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[   10.833563] rfkill: input handler disabled
[   28.511968] Bluetooth: RFCOMM TTY layer initialized
[   28.511976] Bluetooth: RFCOMM socket layer initialized
[   28.511992] Bluetooth: RFCOMM ver 1.11
[   29.103247] rfkill: input handler enabled
[   33.306125] rfkill: input handler disabled
[   97.281449] NVRM: GPU at PCI:0000:01:00: GPU-4eb840b1-6dce-796b-5116-869fd5a0afff
[   97.281454] NVRM: Xid (PCI:0000:01:00): 16, Head 00000000 Count 0000088a
[  105.469478] NVRM: Xid (PCI:0000:01:00): 16, Head 00000000 Count 0000088b
[  113.661381] NVRM: Xid (PCI:0000:01:00): 16, Head 00000000 Count 0000088c
[  121.853270] NVRM: Xid (PCI:0000:01:00): 16, Head 00000000 Count 0000088d
[  130.045140] NVRM: Xid (PCI:0000:01:00): 16, Head 00000000 Count 0000088e
[  138.237188] NVRM: Xid (PCI:0000:01:00): 16, Head 00000000 Count 0000088f
[  146.429143] NVRM: Xid (PCI:0000:01:00): 16, Head 00000000 Count 00000890
[  154.625145] NVRM: Xid (PCI:0000:01:00): 16, Head 00000000 Count 00000891
[  321.270422] usb 2-1.8.1: USB disconnect, device number 4
[  321.270427] usb 2-1.8.1.3: USB disconnect, device number 9

```

the last few lines of:
journalctl:
```
dec 23 21:17:01 macbookpro CRON[22947]: pam_unix(cron:session): session opened for user root by (uid=0)dec 23 21:17:01 macbookpro CRON[22948]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
dec 23 21:17:01 macbookpro CRON[22947]: pam_unix(cron:session): session closed for user root
dec 23 21:17:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.free
dec 23 21:18:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.free
dec 23 21:19:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.free
dec 23 21:20:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.free
dec 23 21:21:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.free
lines 101434-101480/101480 (END)
dec 23 20:41:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 20:42:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 20:43:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 20:44:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 20:45:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 20:46:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 20:47:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 20:48:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 20:49:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 20:50:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 20:50:41 macbookpro wpa_supplicant[868]: wlp3s0: CTRL-EVENT-REGDOM-CHANGE init=BEACON_HINT type=UNKNOWN
dec 23 20:51:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 20:52:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 20:53:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 20:54:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 20:55:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 20:56:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 20:57:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 20:58:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 20:59:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:00:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:01:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:02:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:03:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:04:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:05:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:05:25 macbookpro kernel: applesmc: send_byte(0x40, 0x0300) fail: 0x40
dec 23 21:05:25 macbookpro kernel: applesmc: F1Tg: write data fail
dec 23 21:06:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:07:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:08:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:09:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:10:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:11:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:12:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:13:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:14:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:15:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:16:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:17:01 macbookpro CRON[22947]: pam_unix(cron:session): session opened for user root by (uid=0)
dec 23 21:17:01 macbookpro CRON[22948]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
dec 23 21:17:01 macbookpro CRON[22947]: pam_unix(cron:session): session closed for user root
dec 23 21:17:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:18:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:19:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:20:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
dec 23 21:21:02 macbookpro xdg-desktop-por[1649]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: GDBus.Error:org.fre
lines 101434-101480/101480 (END)

```

---

