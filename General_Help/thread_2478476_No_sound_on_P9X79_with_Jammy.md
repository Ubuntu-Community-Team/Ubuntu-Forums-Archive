---
title: "No sound on P9X79 with Jammy"
date: 2022-08-27
forum: General Help
---

### Post by DuckHook on 2022-08-27
I'm groping around in the dark with the new pipewire framework and would greatly appreciate any direction from more knowledgeable forum members.

My main box installed 22.04 with no sound problems, but an older box meant as my backup desktop has no sound. Both boxes are virgin installations, and it is my understanding that the new audio server is now pipewire.

I've compared services running within the two boxes and they appear identical.

Web searches have indicated that a workaround is to install pipewire-pulse. I'm not at all clear about this but I gather that this reactivates pulseaudio as the audio server. However, I don't want to add back deprecated services if I can solve the problem more elegantly.

How does pipewire work and why would it see a newer MOBO but not an older one?

HW specs for the problematic older box are as follows:```
duckhook@Artemis:~$  sudo lshw -c bus -c multimedia
  *-core                    
       description: Motherboard
       product: P9X79
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev 1.xx
       serial: 120801434101124
       slot: To be filled by O.E.M.
  *-multimedia
       description: Audio device
       product: Tahiti HDMI Audio [Radeon HD 7870 XT / 7950/7970]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0.1
       bus info: pci@0000:01:00.1
       logical name: card1
       logical name: /dev/snd/controlC1
       logical name: /dev/snd/hwC1D0
       logical name: /dev/snd/pcmC1D10p
       logical name: /dev/snd/pcmC1D11p
       logical name: /dev/snd/pcmC1D3p
       logical name: /dev/snd/pcmC1D7p
       logical name: /dev/snd/pcmC1D8p
       logical name: /dev/snd/pcmC1D9p
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:53 memory:fbe60000-fbe63fff
  *-usb:0
       description: USB controller
       product: C600/X79 series chipset USB2 Enhanced Host Controller #2
       vendor: Intel Corporation
       physical id: 1a
       bus info: pci@0000:00:1a.0
       version: 06
       width: 32 bits
       clock: 33MHz
       capabilities: pm debug ehci bus_master cap_list
       configuration: driver=ehci-pci latency=0
       resources: irq:23 memory:fbf27000-fbf273ff
     *-usbhost
          product: EHCI Host Controller
          vendor: Linux 5.15.0-46-generic ehci_hcd
          physical id: 1
          bus info: usb@1
          logical name: usb1
          version: 5.15
          capabilities: usb-2.00
          configuration: driver=hub slots=2 speed=480Mbit/s
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
       product: C600/X79 series chipset High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       logical name: card0
       logical name: /dev/snd/controlC0
       logical name: /dev/snd/hwC0D0
       logical name: /dev/snd/pcmC0D0c
       logical name: /dev/snd/pcmC0D0p
       logical name: /dev/snd/pcmC0D1p
       logical name: /dev/snd/pcmC0D2c
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:51 memory:fbf20000-fbf23fff
  *-usb
       description: USB controller
       product: ASM1042 SuperSpeed USB Host Controller
       vendor: ASMedia Technology Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: msi msix pm pciexpress xhci bus_master cap_list
       configuration: driver=xhci_hcd latency=0
       resources: irq:17 memory:fbd00000-fbd07fff
     *-usbhost:0
          product: xHCI Host Controller
          vendor: Linux 5.15.0-46-generic xhci-hcd
          physical id: 0
          bus info: usb@3
          logical name: usb3
          version: 5.15
          capabilities: usb-2.00
          configuration: driver=hub slots=2 speed=480Mbit/s
     *-usbhost:1
          product: xHCI Host Controller
          vendor: Linux 5.15.0-46-generic xhci-hcd
          physical id: 1
          bus info: usb@4
          logical name: usb4
          version: 5.15
          capabilities: usb-3.00
          configuration: driver=hub slots=2 speed=5000Mbit/s
  *-usb
       description: USB controller
       product: ASM1042 SuperSpeed USB Host Controller
       vendor: ASMedia Technology Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: msi msix pm pciexpress xhci bus_master cap_list
       configuration: driver=xhci_hcd latency=0
       resources: irq:19 memory:fbc00000-fbc07fff
     *-usbhost:0
          product: xHCI Host Controller
          vendor: Linux 5.15.0-46-generic xhci-hcd
          physical id: 0
          bus info: usb@5
          logical name: usb5
          version: 5.15
          capabilities: usb-2.00
          configuration: driver=hub slots=2 speed=480Mbit/s
     *-usbhost:1
          product: xHCI Host Controller
          vendor: Linux 5.15.0-46-generic xhci-hcd
          physical id: 1
          bus info: usb@6
          logical name: usb6
          version: 5.15
          capabilities: usb-3.00
          configuration: driver=hub slots=2 speed=5000Mbit/s
  *-firewire
       description: FireWire (IEEE 1394)
       product: VT6315 Series Firewire Controller
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress ohci bus_master cap_list
       configuration: driver=firewire_ohci latency=0
       resources: irq:17 memory:fba00000-fba007ff ioport:c000(size=256)
  *-usb:1
       description: USB controller
       product: C600/X79 series chipset USB2 Enhanced Host Controller #1
       vendor: Intel Corporation
       physical id: 1d
       bus info: pci@0000:00:1d.0
       version: 06
       width: 32 bits
       clock: 33MHz
       capabilities: pm debug ehci bus_master cap_list
       configuration: driver=ehci-pci latency=0
       resources: irq:23 memory:fbf26000-fbf263ff
     *-usbhost
          product: EHCI Host Controller
          vendor: Linux 5.15.0-46-generic ehci_hcd
          physical id: 1
          bus info: usb@2
          logical name: usb2
          version: 5.15
          capabilities: usb-2.00
          configuration: driver=hub slots=2 speed=480Mbit/s
        *-usb
             description: USB hub
             product: Integrated Rate Matching Hub
             vendor: Intel Corp.
             physical id: 1
             bus info: usb@2:1
             version: 0.00
             capabilities: usb-2.00
             configuration: driver=hub slots=8 speed=480Mbit/s
  *-serial
       description: SMBus
       product: C600/X79 series chipset SMBus Host Controller
       vendor: Intel Corporation
       physical id: 1f.3
       bus info: pci@0000:00:1f.3
       version: 06
       width: 64 bits
       clock: 33MHz
       configuration: driver=i801_smbus latency=0
       resources: irq:18 memory:fbf24000-fbf240ff ioport:f000(size=32)

```Gnome does not see the onboard C600/X79 series chipset High Definition Audio Controller audio.

The logs tell me nothing. dmesg looks fine, as does journalctl. alsamixer shows that the audio subsystem is detected and working.
```
&#9474; Card: HDA Intel PCH                                                                          F1:  Help               &#9474;
&#9474; Chip: Realtek ALC892                                                                         F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All                                                     F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: -20.00]                                                               Esc: Exit               &#9474;
&#9474;                                                                                                                      &#9474;
&#9474;                                                                                                                      &#9474;
&#9474;                                                                                                                      &#9474;
&#9474;                                                                                                                      &#9474;
&#9474;                                                                                                                      &#9474;
&#9474;                                                                                                                      &#9474;
&#9474;                                                                                                                      &#9474;
&#9474;                                                                                                                      &#9474;
&#9474;                                                                                                                      &#9474;
&#9474;                                                                                                                      &#9474;
&#9474;                                                                                                                      &#9474;
&#9474;                                                                                                                      &#9474;
&#9474;                                                                                                                      &#9474;
&#9474;                                                                                                                      &#9474;
&#9474;                                                                                                                      &#9474;
&#9474;   &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;            &#9474;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#9474;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#9474;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#9474;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#9474;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#9474;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#9474;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#9474;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#9474;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#9474;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#8594;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#9474;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#9474;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#9474;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#9474;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#9474;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#9474;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#9474;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#9474;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;            &#9474;
&#9474;   &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9484;&#9472;&#9472;&#9488;   &#9474;
&#9474;   &#9474;OO&#9474;     &#9474;MM&#9474;              &#9474;OO&#9474;     &#9474;MM&#9474;              &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;MM&#9474;              &#9474;OO&#9474;   &#9474;
&#9474;   &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;   &#9474;
&#9474;    41      0<>0   100<>100 100<>100   0<>0     0<>0   100<>100   100      100    100<>100   0<>0     0<>0            &#9474;
&#9474;< Master >Headphon   PCM     Front   Front Mi Front Mi Surround  Center    LFE      Side     Line   Line Boo  S/PDIF 
```
pactl info shows a sound server with the following:```
duckhook@Artemis:~$ pactl info
Server String: /run/user/1000/pulse/native
Library Protocol Version: 35
Server Protocol Version: 35
Is Local: yes
Client Index: 15
Tile Size: 65472
User Name: duckhook
Host Name: Artemis
Server Name: pulseaudio
Server Version: 15.99.1
Default Sample Specification: s16le 2ch 44100Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_00_1b.0.iec958-stereo
Default Source: alsa_output.pci-0000_00_1b.0.iec958-stereo.monitor
Cookie: 05a9:c34f
```
pipewire services also look fine to my untrained eye:```
duckhook@Artemis:~$  systemctl --user status pipewire pipewire-media-session
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2022-08-27 19:14:27 MDT; 1h 16min ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 2994 (pipewire)
      Tasks: 2 (limit: 76791)
     Memory: 1.4M
        CPU: 26ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire.service
             &#9492;&#9472;2994 /usr/bin/pipewire

Aug 27 19:14:27 Artemis systemd[2981]: Started PipeWire Multimedia Service.

&#9679; pipewire-media-session.service - PipeWire Media Session Manager
     Loaded: loaded (/usr/lib/systemd/user/pipewire-media-session.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2022-08-27 19:14:27 MDT; 1h 16min ago
   Main PID: 2995 (pipewire-media-)
      Tasks: 2 (limit: 76791)
     Memory: 1.4M
        CPU: 17ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire-media-session.service
             &#9492;&#9472;2995 /usr/bin/pipewire-media-session

Aug 27 19:14:27 Artemis systemd[2981]: Started PipeWire Media Session Manager.

```
FWIW, these outputs are almost identical to those of my newer working box, which only adds to the mystery.

Both boxes are running fully up to date vanilla Ubuntu Jammy. I strive to leave the base OS in its default state, so both boxes are almost pristine virgin installs.

Frankly, I'm at a loss what to do next.

---

### Post by &amp;KyT$0P# on 2022-08-28
> **DuckHook said:**
> My main box installed 22.04 with no sound problems, but an older box meant as my backup desktop has no sound. Both boxes are virgin installations, and it is my understanding that the new audio server is now pipewire.

[Not by default.]("https://ubuntuforums.org/showthread.php?t=2474831")  Although it is possible to set that up, but I needed a newer version of Pipewire than what's in standard 22.04 repositories to get it working for audio.

> install pipewire-pulse. I'm not at all clear about this but I gather that this reactivates pulseaudio as the audio server. However, I don't want to add back deprecated services if I can solve the problem more elegantly.

No, pipewire-pulse still uses Pipewire.  Think of pipewire-pulse as basically a "PulseAudio toolkit" for apps to use for audio.  I guess it's like, pipewire-pulse is to Pipewire what GTK is to X11 or Wayland.

> pactl info shows a sound server with the following:

You are using PulseAudio.  If you were using Pipewire for audio it'd look like this (emphasis mine) -
```
$ pactl info
Server String: /run/user/1000/pulse/native
Library Protocol Version: 35
Server Protocol Version: 35
Is Local: yes
Client Index: 56
Tile Size: 65472
User Name: <snipped>
Host Name: <snipped>
Server Name: PulseAudio [COLOR="#FF0000"]**(on PipeWire 0.3.56)**[/COLOR]
Server Version: 15.0.0
Default Sample Specification: float32le 2ch 48000Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_00_1f.3.analog-stereo
Default Source: alsa_output.pci-0000_00_1f.3.analog-stereo.monitor
Cookie: xxxx:xxxx

```

---

### Post by DuckHook on 2022-08-28
Thanks for your reply, halogen2. It clarifies many things.

I forgot to mention that my setup is rather sensitive to workarounds because I sandbox most of my apps within LXD, and LXD may not yet be pipewire friendly since passing sound from container to host still relies on pulseaudio.

So, since pulseaudio is still the active audio server in Jammy, I now understand why my LXD containers are still working.

Your link to your previous thread is very informative. Likewise, the further links within that thread.

I'm going to try installing pipewire-pulse to see if it solves the sound problem. Will report back on my results.

---

### Post by DuckHook on 2022-08-28
> **DuckHook said:**
> I'm going to try installing pipewire-pulse to see if it solves the sound problem. Will report back on my results.
Nope. No joy.

I'm afraid that installing pipewire-pulse makes things marginally worse. I can't get sound from MOBO audio either way but, without pipewire-pulse, I can at least get S/PDIF digital output (even if it does me no good) whereas even this option goes missing once I install pipewire-pulse. I've purged pipewire-pulse and am back to square one.

I'm going to try researching this a bit more, but I don't expect results to be any better than previous searches.

I just can't wrap my head around why some systems "just work" while others don't.

---

### Post by &amp;KyT$0P# on 2022-08-28
What is output of
```
aplay -L
```

Have you tried looking in pavucontrol, which sometimes has more options than the GNOME settings?

---

### Post by DuckHook on 2022-08-28
> **halogen2 said:**
> What is output of
```
aplay -L
```
```
duckhook@Artemis:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default
    Playback/recording through the PulseAudio sound server
samplerate
    Rate Converter Plugin Using Samplerate Library
speexrate
    Rate Converter Plugin Using Speex Resampler
jack
    JACK Audio Connection Kit
oss
    Open Sound System
pulse
    PulseAudio Sound Server
upmix
    Plugin for channel upmix (4,6,8)
vdownmix
    Plugin for channel downmix (stereo) with a simple spacialization
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Hardware device with all software conversions
sysdefault:CARD=PCH
    HDA Intel PCH, ALC892 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Front output / input
surround21:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample mixing device
usbstream:CARD=PCH
    HDA Intel PCH
    USB Stream Output
hw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=7
    HDA ATI HDMI, HDMI 1
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=8
    HDA ATI HDMI, HDMI 2
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=9
    HDA ATI HDMI, HDMI 3
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=10
    HDA ATI HDMI, HDMI 4
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=11
    HDA ATI HDMI, HDMI 5
    Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=7
    HDA ATI HDMI, HDMI 1
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=8
    HDA ATI HDMI, HDMI 2
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=9
    HDA ATI HDMI, HDMI 3
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=10
    HDA ATI HDMI, HDMI 4
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=11
    HDA ATI HDMI, HDMI 5
    Hardware device with all software conversions
hdmi:CARD=HDMI,DEV=0
    HDA ATI HDMI, HDMI 0
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=1
    HDA ATI HDMI, HDMI 1
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=2
    HDA ATI HDMI, HDMI 2
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 3
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=4
    HDA ATI HDMI, HDMI 4
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=5
    HDA ATI HDMI, HDMI 5
    HDMI Audio Output
dmix:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct sample mixing device
dmix:CARD=HDMI,DEV=7
    HDA ATI HDMI, HDMI 1
    Direct sample mixing device
dmix:CARD=HDMI,DEV=8
    HDA ATI HDMI, HDMI 2
    Direct sample mixing device
dmix:CARD=HDMI,DEV=9
    HDA ATI HDMI, HDMI 3
    Direct sample mixing device
dmix:CARD=HDMI,DEV=10
    HDA ATI HDMI, HDMI 4
    Direct sample mixing device
dmix:CARD=HDMI,DEV=11
    HDA ATI HDMI, HDMI 5
    Direct sample mixing device
usbstream:CARD=HDMI
    HDA ATI HDMI
    USB Stream Outpu
```
> Have you tried looking in pavucontrol, which sometimes has more options than the GNOME settings?
Installed just now and it shows only S/PDIF output device. No MOBO audio.

---

### Post by DuckHook on 2022-08-28
So this is crazy strange but, just for kicks and giggles, I plugged headphones into the headphone jack and&#8212;surprise!&#8212;they show up in the sound system instantly. I get sound out of them too.

I don't know if that adds to the mystery or helps, but it's another data point.

The alsamixer profile looks different too (which is not a surprise). It now shows headphone output and not speaker output.

---

### Post by DuckHook on 2022-08-28
halogen2:

Firstly, big apologies to you. I feel like an absolute fool.

It turns out that my speakers WERE NOT PLUGGED IN. ](*,)

Once I did that, they showed up and everything is now peachy.

I am clearly losing what little hold I had left on my sanity. Sorry for the false (and embarrassing) alarm.

I'm going off to sit in the corner now and just sulk and eat ice cream.

---

### Post by &amp;KyT$0P# on 2022-08-28
Whew.  Saw your solution post just as I realised I've completely forgotten the PulseAudio command that tells which of those ALSA devices PulseAudio wants to play to :oops:

It's ok, that sort of thing happens to all of us at some point.  Thanks for posting the solution, glad it was a simple fix!

---

### Post by DuckHook on 2022-08-28
It's like:

"My computer won't turn on!"

"Have you checked whether it's plugged in?"

As a (very small) silver lining, thanks to you, at least I learned something about pipewire&#8230;

---

### Post by tea for one on 2022-08-28
Nice thread - happy result.
Many moons ago in these forums, there was a similar thread about no sound output.
After lots of investigation, toing and froing, head-scratching, it transpired that the user did not have any internal or external speakers.

---

