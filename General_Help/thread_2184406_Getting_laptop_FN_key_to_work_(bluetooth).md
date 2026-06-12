---
title: "Getting laptop FN key to work (bluetooth)"
date: 2013-10-28
forum: General Help
---

### Post by PeterRJG on 2013-10-28
I own an Aptivo laptop that turns bluetooth on by hitting FN-F12. This works fine under Windows but in Linux (every distro I've tried) it doesn't do a thing. In fact, if I run xev, the FN key does nothing and nothing seems to be mapped to it. In saying this, I can use the FN and F4/5 keys to brighten/darken my display, which seems to be a BIOS thing independent of the OS. But for FN-F12, nothing happens. 

Ubuntu sees the bluetooth device, but I can't turn it on as it doesn't recognise the FN key. I've found a lot of help online for this issue, but mainly for laptops like the Thinkpad or other Lenovo models and none of the answers I've found work for this laptop. I don't have an .Xmodmap file either, if that's any help.

Thanks in advance.

---

### Post by varunendra on 2013-10-29
Please show us the outputs of -
```
uname -mr
lsb_release -d
lsmod
rfkill list all
lsusb
usb-devices
```

---

### Post by PeterRJG on 2013-10-29
Distro Astro is a Mint MATE respin. But I get the same non-working FN keys in Ubuntu too. Here's what you asked for.

uname -mr ```
3.2.0-55-generic i686
```

lsb_release -d ```
Description:	Distro Astro - Linux for Astronomers
```

lsmod ```
Module                  Size  Used by
joydev                 17393  0 
arc4                   12473  2 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32719  3 
snd_hda_codec         109562  4 snd_hda_codec_hdmi,snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  4 snd_hda_codec_hdmi,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
rtl8187                56323  0 
mac80211              436493  1 rtl8187
cfg80211              178877  2 rtl8187,mac80211
eeprom_93cx6           12687  1 rtl8187
parport_pc             32114  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
ppdev                  12849  0 
snd_seq_midi           13132  0 
psmouse                96744  0 
serio_raw              13027  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158447  10 rfcomm,bnep
jmb38x_ms              17406  0 
snd_rawmidi            25424  1 snd_seq_midi
memstick               15857  1 jmb38x_ms
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  17 snd_hda_codec_hdmi,snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13516  0 
r8169                  56396  0 
i915                  428092  2 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
drm_kms_helper         45466  1 i915
drm                   197641  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
wmi                    18744  0 
video                  19115  1 i915
usbhid                 41937  0 
hid                    77428  1 usbhid

```

rfkill list all ```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

lsusb
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 002 Device 004: ID 5986:0241 Acer, Inc BisonCam, NB Pro
Bus 003 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 006 Device 002: ID 192f:0416 Avago Technologies, Pte.

```

Usb-devices echoed too much stuff to paste here, it's at [http://pastebin.com/t5djJQxM](http://pastebin.com/t5djJQxM)

---

### Post by varunendra on 2013-10-29
There is no indication of any bluetooth device in the system, as if it doesn't exist at all.

Are there any hints of it in -
```
dmesg | grep -i bluetooth
grep -i bluetooth /var/log/syslog
```
??

If not, can you check its VID and PID (Vendor ID and Product ID) in windows? It should be listed under a tab (can't remember its name) in Device Manager > Bluetooth device > Properties. At least that may tell us if it is a device known to linux or not.

Although regardless of its ID, having no sign of it could be a difficult problem.

---

### Post by PeterRJG on 2013-10-29
Hi Varun, I'll do that for you in a sec, but my main issue isn't so much that Linux doesn't see it, it's not seeing the FN key to activate it with. My bluetooth is dormant in Windows until I toggle it by FN + F12. I'll get back to you ASAP with the info you want.

---

### Post by PeterRJG on 2013-10-29
Alrighty, output of dmesg | grep -i bluetooth is

```

[   29.934180] Bluetooth: Core ver 2.16
[   29.934426] Bluetooth: HCI device and connection manager initialized
[   29.934429] Bluetooth: HCI socket layer initialized
[   29.934431] Bluetooth: L2CAP socket layer initialized
[   29.934441] Bluetooth: SCO socket layer initialized
[   29.952572] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.952576] Bluetooth: BNEP filters: protocol multicast
[   30.054172] Bluetooth: RFCOMM TTY layer initialized
[   30.054178] Bluetooth: RFCOMM socket layer initialized
[   30.054180] Bluetooth: RFCOMM ver 1.11

```

and grep -i bluetooth /var/log/syslog is:
```

Oct 28 09:26:12 laptop bluetoothd[800]: Bluetooth daemon 4.98
Oct 28 09:26:12 laptop bluetoothd[800]: Starting SDP server
Oct 28 09:26:12 laptop kernel: [   27.087187] Bluetooth: Core ver 2.16
Oct 28 09:26:12 laptop kernel: [   27.087226] Bluetooth: HCI device and connection manager initialized
Oct 28 09:26:12 laptop kernel: [   27.087229] Bluetooth: HCI socket layer initialized
Oct 28 09:26:12 laptop kernel: [   27.087231] Bluetooth: L2CAP socket layer initialized
Oct 28 09:26:12 laptop kernel: [   27.087237] Bluetooth: SCO socket layer initialized
Oct 28 09:26:13 laptop bluetoothd[800]: Failed to init alert plugin
Oct 28 09:26:13 laptop bluetoothd[800]: Failed to init time plugin
Oct 28 09:26:13 laptop bluetoothd[800]: Failed to init proximity plugin
Oct 28 09:26:13 laptop kernel: [   27.818853] Bluetooth: RFCOMM TTY layer initialized
Oct 28 09:26:13 laptop kernel: [   27.818860] Bluetooth: RFCOMM socket layer initialized
Oct 28 09:26:13 laptop kernel: [   27.818862] Bluetooth: RFCOMM ver 1.11
Oct 28 09:26:13 laptop kernel: [   27.903464] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Oct 28 09:26:13 laptop kernel: [   27.903468] Bluetooth: BNEP filters: protocol multicast
Oct 28 09:26:13 laptop bluetoothd[800]: Failed to init gatt_example plugin
Oct 28 20:41:40 laptop bluetoothd[731]: Bluetooth daemon 4.98
Oct 28 20:41:40 laptop bluetoothd[731]: Starting SDP server
Oct 28 20:41:41 laptop kernel: [   27.039748] Bluetooth: Core ver 2.16
Oct 28 20:41:41 laptop kernel: [   27.039782] Bluetooth: HCI device and connection manager initialized
Oct 28 20:41:41 laptop kernel: [   27.039785] Bluetooth: HCI socket layer initialized
Oct 28 20:41:41 laptop kernel: [   27.039787] Bluetooth: L2CAP socket layer initialized
Oct 28 20:41:41 laptop kernel: [   27.039794] Bluetooth: SCO socket layer initialized
Oct 28 20:41:42 laptop bluetoothd[731]: Failed to init alert plugin
Oct 28 20:41:42 laptop bluetoothd[731]: Failed to init time plugin
Oct 28 20:41:42 laptop bluetoothd[731]: Failed to init proximity plugin
Oct 28 20:41:42 laptop kernel: [   27.448152] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Oct 28 20:41:42 laptop kernel: [   27.448156] Bluetooth: BNEP filters: protocol multicast
Oct 28 20:41:43 laptop kernel: [   28.439521] Bluetooth: RFCOMM TTY layer initialized
Oct 28 20:41:43 laptop kernel: [   28.439532] Bluetooth: RFCOMM socket layer initialized
Oct 28 20:41:43 laptop kernel: [   28.439534] Bluetooth: RFCOMM ver 1.11
Oct 28 20:41:43 laptop bluetoothd[731]: Failed to init gatt_example plugin
Oct 28 21:55:01 laptop kernel: [   31.095227] Bluetooth: Core ver 2.16
Oct 28 21:55:01 laptop kernel: [   31.095259] Bluetooth: HCI device and connection manager initialized
Oct 28 21:55:01 laptop kernel: [   31.095262] Bluetooth: HCI socket layer initialized
Oct 28 21:55:01 laptop kernel: [   31.095264] Bluetooth: L2CAP socket layer initialized
Oct 28 21:55:01 laptop kernel: [   31.095274] Bluetooth: SCO socket layer initialized
Oct 28 21:55:01 laptop kernel: [   31.107024] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Oct 28 21:55:01 laptop kernel: [   31.107028] Bluetooth: BNEP filters: protocol multicast
Oct 28 21:55:01 laptop kernel: [   31.125252] Bluetooth: RFCOMM TTY layer initialized
Oct 28 21:55:01 laptop kernel: [   31.125262] Bluetooth: RFCOMM socket layer initialized
Oct 28 21:55:01 laptop kernel: [   31.125264] Bluetooth: RFCOMM ver 1.11
Oct 29 11:25:40 laptop bluetoothd[452]: Failed to init gatt_example plugin
Oct 29 11:25:40 laptop kernel: [   30.933914] Bluetooth: Core ver 2.16
Oct 29 11:25:40 laptop kernel: [   30.933969] Bluetooth: HCI device and connection manager initialized
Oct 29 11:25:40 laptop kernel: [   30.933972] Bluetooth: HCI socket layer initialized
Oct 29 11:25:40 laptop kernel: [   30.933975] Bluetooth: L2CAP socket layer initialized
Oct 29 11:25:40 laptop kernel: [   30.933982] Bluetooth: SCO socket layer initialized
Oct 29 11:25:40 laptop kernel: [   30.968933] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Oct 29 11:25:40 laptop kernel: [   30.968937] Bluetooth: BNEP filters: protocol multicast
Oct 29 11:25:40 laptop kernel: [   30.970130] Bluetooth: RFCOMM TTY layer initialized
Oct 29 11:25:40 laptop kernel: [   30.970137] Bluetooth: RFCOMM socket layer initialized
Oct 29 11:25:40 laptop kernel: [   30.970139] Bluetooth: RFCOMM ver 1.11
Oct 29 15:30:19 laptop kernel: [   30.909081] Bluetooth: Core ver 2.16
Oct 29 15:30:19 laptop kernel: [   30.909108] Bluetooth: HCI device and connection manager initialized
Oct 29 15:30:19 laptop kernel: [   30.909111] Bluetooth: HCI socket layer initialized
Oct 29 15:30:19 laptop kernel: [   30.909113] Bluetooth: L2CAP socket layer initialized
Oct 29 15:30:19 laptop kernel: [   30.909120] Bluetooth: SCO socket layer initialized
Oct 29 15:30:19 laptop kernel: [   30.933070] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Oct 29 15:30:19 laptop kernel: [   30.933073] Bluetooth: BNEP filters: protocol multicast
Oct 29 15:30:19 laptop kernel: [   30.941048] Bluetooth: RFCOMM TTY layer initialized
Oct 29 15:30:19 laptop kernel: [   30.941054] Bluetooth: RFCOMM socket layer initialized
Oct 29 15:30:19 laptop kernel: [   30.941056] Bluetooth: RFCOMM ver 1.11
Oct 29 20:17:36 laptop kernel: [   30.913660] Bluetooth: Core ver 2.16
Oct 29 20:17:36 laptop kernel: [   30.914549] Bluetooth: HCI device and connection manager initialized
Oct 29 20:17:36 laptop kernel: [   30.914552] Bluetooth: HCI socket layer initialized
Oct 29 20:17:36 laptop kernel: [   30.914554] Bluetooth: L2CAP socket layer initialized
Oct 29 20:17:36 laptop kernel: [   30.914566] Bluetooth: SCO socket layer initialized
Oct 29 20:17:36 laptop kernel: [   30.925291] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Oct 29 20:17:36 laptop kernel: [   30.925296] Bluetooth: BNEP filters: protocol multicast
Oct 29 20:17:36 laptop kernel: [   30.928811] Bluetooth: RFCOMM TTY layer initialized
Oct 29 20:17:36 laptop kernel: [   30.928817] Bluetooth: RFCOMM socket layer initialized
Oct 29 20:17:36 laptop kernel: [   30.928819] Bluetooth: RFCOMM ver 1.11
```

OK, Windows sees it as this:
[ATTACH=CONFIG]247372[/ATTACH][ATTACH=CONFIG]247373[/ATTACH]

Thanks for your help so far!

---

### Post by varunendra on 2013-10-30
None of the tools I have tested so far (including xev) can capture Fn key events. Yet the combinations with it work perfectly fine of all machines I could try. I'm not sure how to explain this but it clearly is something different than normal keymap, probably something that is directly handled by BIOS or BIOS+ACPI combination.

Do any other Fn+ key combos (that work only after an OS is loaded, like volume ctrl, vga out etc.) work on your laptop? As much as I understand, these events are handled by the model specific wmi+kernel acpi drivers. But your system doesn't even have such any 'model specific' wmi driver loaded (like acer_wmi, toshiba_acpi, dell_wmi.... etc.).

All the bluetooth references you see in syslog and dmesg are, *I believe*, general bluetooth drivers/services that would load even if there is no bluetooth device in the system. What I was expecting to see is a particular device detected as a bluetooth radio device. Even if it appears to be failed to initialize, it could be a starting point. The screenshots are not of the screen I had in mind (probably the "Properties" button in the "Hardware" tab was it). It gives me the VID (10=0x0010), but not the PID yet, not that it is going to matter at this point.

So in short, I see no way to move further from here. Maybe the acpi settings/protocols of the BIOS are too alien for Linux kernel, in which case, fiddling with various acpi related boot options may help sometimes. Try them and see if any of these can help :
[https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by PeterRJG on 2013-10-30
I think this is the tab you mean.

[ATTACH=CONFIG]247386[/ATTACH]

Re: other Fn keys. Yes, they all work bar the Fn+F12 combo. Fn+F2 turns off the backlight, for example and Fn+F5/F6 change the volume up and down.

There are some ACPI settings in the BIOS I can adjust but none of them seemed to work. In fact one of them caused Windows 7 to blue screen on boot, go figure.

---

### Post by varunendra on 2013-10-30
Yup, that's the one. And the volume control is functional means the Fn key itself is working in the OS.

It seems the device itself should be supported in Linux as per recognized usb IDs database here : [https://code.google.com/p/dsss/source/browse/trunk/work/usbutils-0.86/usb.ids](https://code.google.com/p/dsss/source/browse/trunk/work/usbutils-0.86/usb.ids)

Please check (after a fresh reboot) -
```
grep -i '0a12:0001' /var/log/syslog
```
Anything shows up?

The BSOD in windows would have been caused most probably due to changing the SATA mode to legacy (or "compatible" or whatever they wish to call it) from ahci (or the other way round). That is not required and is not going to help anyway, so leave it at what windows is happy with.

Anyway, did you try the boot options with Grub yet? Which ones?

---

### Post by PeterRJG on 2013-10-31
```
grep -i '0a12:0001' /var/log/syslog
``` returns a blank.

I tried a few boot options. I got a kernel panic with pci=noacpi and a couple, like noapic and acpi=force resulted in a hung computer. 

Thank you for your help so far, but I may have to live with the fact my laptop is too arcane (the manufacturer's website no longer exists) for good old Linux. When I installed Windows 7, there were a whole bunch of chipset drivers I needed to install from the provided disk. Just wondering if the bluetooth activator was part of that.

Might be just time for a cheap USB dongle.

---

