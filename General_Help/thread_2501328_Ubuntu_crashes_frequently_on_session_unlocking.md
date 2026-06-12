---
title: "Ubuntu crashes frequently on session unlocking"
date: 2024-10-02
forum: General Help
---

### Post by gnu-paco on 2024-10-02
Hello everyone,

I have an annoying problem: after a certain period of inactivity, my session locks (normal and desired behavior).
But when I want to unlock it (by pressing a key on the keyboard for example and then typing my user account password), the system frequently crashes and shows me the GDM page to launch the user session.

Only this time, the image assigned to my account is no longer displayed and when I reconnect (it always works the second time), all previously launched applications are no longer displayed.
So I restart on a new session (instead of restoring the previous one).

I don't know what's causing this, or how to investigate it.

Here's what GNOME's Logs application reveals (the crash was at 9:57 p.m. [21:57]):

```
21:57:47 kernel: usb 1-8: Failed to suspend device, error -110
21:57:36 systemd: Failed to start app-gnome-user\x2ddirs\x2dupdate\x2dgtk-15081.scope - Application launched by gnome-session-binary.
21:57:36 systemd: Failed to start app-gnome-user\x2ddirs\x2dupdate\x2dgtk-15081.scope - Application launched by gnome-session-binary.
21:57:36 systemd: Failed to start app-gnome-im\x2dlaunch-15004.scope - Application launched by gnome-session-binary.
21:57:35 systemd: Failed to start app-gnome-gnome\x2dkeyring\x2dsecrets-14665.scope - Application launched by gnome-session-binary.
21:57:35 systemd: Failed to start app-gnome-gnome\x2dkeyring\x2dpkcs11-14668.scope - Application launched by gnome-session-binary.
21:57:34 gdm-session-wor: gkr-pam: unable to locate daemon control file
21:57:03 kernel: usb 1-8: Failed to suspend device, error -110
21:57:03 kernel: usb 1-8: Failed to suspend device, error -110
20:04:26 kernel: usb 1-8: Failed to suspend device, error -110
20:04:10 kernel: usb 1-8: Failed to suspend device, error -110
20:03:58 kernel: usb 1-8: Failed to suspend device, error -110
20:03:55 systemd: Failed to start app-gnome-xdg\x2duser\x2ddirs-2877.scope - Application launched by gnome-session-binary.
20:03:55 systemd: Failed to start app-gnome-xdg\x2duser\x2ddirs-2877.scope - Application launched by gnome-session-binary.
20:03:55 systemd: Failed to start app-gnome-gnome\x2dkeyring\x2dsecrets-2857.scope - Application launched by gnome-session-binary.
20:03:55 systemd: Failed to start app-gnome-gnome\x2dkeyring\x2dpkcs11-2859.scope - Application launched by gnome-session-binary.
20:03:54 gdm-session-wor: gkr-pam: unable to locate daemon control file
20:03:46 kernel: usb 1-8: Failed to suspend device, error -110
20:03:35 canonical-livep: Task "refresh" returned an error: livepatch check failed: POST request to "https://livepatch.canonical.com/v1/client/74813c857d5f460fa774e38fb8bdc403/updates" failed, retrying in 30s.
20:03:33 kernel: Bluetooth: hci0: BCM: Reset failed (-110)
20:03:33 kernel: Bluetooth: hci0: BCM: Reset failed (-110)
20:03:33 kernel: Bluetooth: hci0: command 0x0c03 tx timeout
20:03:31 kernel: brcmfmac: brcmf_c_preinit_dcmds: Firmware: BCM43602/1 wl0: Nov 10 2015 06:38:10 version 7.35.177.61 (r598657) FWID 01-ea662a8c
20:03:31 kernel: brcmfmac: brcmf_c_preinit_dcmds: Firmware: BCM43602/1 wl0: Nov 10 2015 06:38:10 version 7.35.177.61 (r598657) FWID 01-ea662a8c
20:03:31 kernel: brcmfmac: brcmf_c_process_txcap_blob: no txcap_blob available (err=-2)
20:03:31 kernel: brcmfmac: brcmf_c_process_clm_blob: no clm_blob available (err=-2), device may have limited channels available
20:03:31 kernel: brcmfmac: brcmf_fw_alloc_request: using brcm/brcmfmac43602-pcie for chip BCM43602/1
```

Or this crash when I tried to unlock my session (at 12:00).
The screen went black and when I pressed the keyboard, I could only type text (Grub?):

```
12:03:08 systemd: Failed to start app-gnome-user\x2ddirs\x2dupdate\x2dgtk-5096.scope - Application launched by gnome-session-binary.
12:03:08 systemd: Failed to start app-gnome-user\x2ddirs\x2dupdate\x2dgtk-5096.scope - Application launched by gnome-session-binary.
12:03:06 systemd: Failed to start app-gnome-gnome\x2dkeyring\x2dsecrets-4711.scope - Application launched by gnome-session-binary.
12:03:06 systemd: Failed to start app-gnome-gnome\x2dkeyring\x2dpkcs11-4714.scope - Application launched by gnome-session-binary.
12:03:06 gdm-session-wor: gkr-pam: unable to locate daemon control file
12:02:55 systemd: Failed to start app-gnome-user\x2ddirs\x2dupdate\x2dgtk-3221.scope - Application launched by gnome-session-binary.
12:02:53 gdm-session-wor: gkr-pam: unable to locate daemon control file
12:02:50 canonical-livep: Task "refresh" returned an error: livepatch check failed: POST request to "https://livepatch.canonical.com/v1/client/74813c857d5f460fa774e38fb8bdc403/updates" failed, retrying in 30s.
12:02:43 (uetoothd): Failed to load IRKs for hci0: Invalid Parameters (0x0d)
12:02:43 kernel: brcmfmac: brcmf_c_preinit_dcmds: Firmware: BCM43602/1 wl0: Nov 10 2015 06:38:10 version 7.35.177.61 (r598657) FWID 01-ea662a8c
12:02:10 systemd-cryptse: Failed to deactivate 'dm_crypt-0': Device or resource busy
12:01:11 kernel: usb 1-8: Failed to suspend device, error -110
12:00:58 canonical-livep: daemon shutting down
12:00:58 gdm3: Gdm: Failed to list cached users: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name :1.11 was not provided by any .service files
12:00:40 systemd: Failed to start xdg-desktop-portal-gtk.service - Portal service (GTK/GNOME implementation).
```

Please note that I always connect to the PC:

[LIST]
[*]the laptop's power cable,
[*]an Ethernet-to-USB adapter (although I've encountered this problem with Wi-Fi before),
[*]a mouse (either Bluetooth or USB wireless).
[/LIST]
 
I was unable to establish a link between this bug and the applications running.

My configuration:
```

## Hardware information:
- Hardware model: Apple Inc. MacBookPro11,4
- Memory: 16.0 GB
- Processor: Intel® Core™ i7-4870HQ × 8
- Graphics card: Intel® Iris® Pro Graphics P5200 (HSW GT3)
- Disk capacity: 480.1 GB

## Software information:
- Firmware version: 430.140.3.0.0
- Operating system name: Ubuntu 24.04.1 LTS
- Operating system build: (null)
- Operating system type: 64-bit
- GNOME version: 46
- Window system: Wayland
- Kernel version: Linux 6.8.0-45-generic
```

Kind regards,
Paco

---

### Post by gnu-paco on 2024-10-03
Any idea?

---

