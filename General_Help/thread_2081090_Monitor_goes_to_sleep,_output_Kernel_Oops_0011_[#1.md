---
title: "Monitor goes to sleep, output Kernel: Oops: 0011 [#1] SMP"
date: 2012-11-05
forum: General Help
---

### Post by 28c64 on 2012-11-05
Hi everyone. I'm not sure if these two are related, but it's happened about twice now. Randomly my monitor went to sleep and I was unable to wake it back up, I checked through the kern.log's and found something that struck my attention. Hoping someone may be able to help if these are related and possibly help me out.

I'm still continuing to research, so far haven't found a solution.. Thanks.


**/var/log/kern.log**
```

Nov  5 21:38:20 midgar kernel: [101293.216605] kernel tried to execute NX-protected page - exploit attempt? (uid: 0)
Nov  5 21:38:20 midgar kernel: [101293.216608] BUG: unable to handle kernel paging request at ffff8801fa125988
Nov  5 21:38:20 midgar kernel: [101293.216619] IP: [<ffff8801fa125988>] 0xffff8801fa125987
Nov  5 21:38:20 midgar kernel: [101293.216625] PGD 1c06063 PUD deff9067 PMD 1fe805063 PTE 80000001fa125163
Nov  5 21:38:20 midgar kernel: [101293.216631] Oops: 0011 [#1] SMP 
Nov  5 21:38:20 midgar kernel: [101293.216634] CPU 0 
Nov  5 21:38:20 midgar kernel: [101293.216636] Modules linked in: vesafb rfcomm bnep bluetooth parport_pc ppdev snd_hda_codec_hdmi nvidia(P) joydev xpad ff_memless snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device eeepc_wmi asus_wmi video sparse_keymap snd mac_hid psmouse serio_raw usbhid wmi hid lp soundcore parport mei(C) snd_page_alloc usb_storage r8169
Nov  5 21:38:20 midgar kernel: [101293.216668] 
Nov  5 21:38:20 midgar kernel: [101293.216672] Pid: 1208, comm: Xorg Tainted: P         C O 3.2.0-32-generic #51-Ubuntu System manufacturer System Product Name/P8Z77-V LX
Nov  5 21:38:20 midgar kernel: [10129Nov  5 21:39:57 midgar kernel: imklog 5.8.6, log source = /proc/kmsg started.

```[B]

lspci -v[/B]
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f4000000-f60fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000ebffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, medium devsel, latency 0, IRQ 42
    Memory at f6100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f611a000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f6118000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 8445
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f6110000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: ec300000-ec4fffff
    Prefetchable memory behind bridge: 00000000ec500000-00000000ec6fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Prefetchable memory behind bridge: 00000000ec100000-00000000ec1fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c4) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
    Capabilities: <access denied>

00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f6117000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f050 [size=8]
    I/O ports at f040 [size=4]
    I/O ports at f020 [size=32]
    Memory at f6116000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: medium devsel, IRQ 5
    Memory at f6115000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f000 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ZOTAC International (MCO) Ltd. Device 5194
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f4000000 (32-bit, non-prefetchable) [size=32M]
    Memory at e0000000 (64-bit, prefetchable) [size=128M]
    Memory at e8000000 (64-bit, prefetchable) [size=64M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at f6000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb

01:00.1 Audio device: NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)
    Subsystem: ZOTAC International (MCO) Ltd. Device 5194
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f6080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards
    Flags: bus master, fast devsel, latency 0, IRQ 43
    I/O ports at d000 [size=256]
    Memory at ec104000 (64-bit, prefetchable) [size=4K]
    Memory at ec100000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

04:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=04, secondary=05, subordinate=05, sec-latency=32
    Capabilities: <access denied>

```[B]

/home/{username}/.xsession-errors
[/B]```

openConnection: connect: No such file or directory
cannot connect to brltty at :0
xfce4-settings-helper: Another instance is already running. Leaving...

(xfce4-indicator-plugin:1641): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:1641): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(polkit-gnome-authentication-agent-1:1655): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(polkit-gnome-authentication-agent-1:1655): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
tint2 : nb monitor 1, nb monitor used 1, nb desktop 3
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-smW60h/pkcs11: No such file or directory
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** Message: applet now removed from the notification area

(xfce4-indicator-plugin:1641): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-smW60h/pkcs11: No such file or directory
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-smW60h/pkcs11: No such file or directory

(Thunar:1616): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

(Thunar:1616): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-terminal:2235): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

```

---

