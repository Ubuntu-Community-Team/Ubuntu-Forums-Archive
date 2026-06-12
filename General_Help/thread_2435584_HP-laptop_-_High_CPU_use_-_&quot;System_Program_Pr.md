---
title: "HP-laptop - High CPU use - &quot;System Program Problem&quot; -- 18.04.03"
date: 2020-01-22
forum: General Help
---

### Post by ishmael3 on 2020-01-22
I have a new install of 18.04.3 on an HP-Stream-laptop-11 (4GB-RAM, 32GB-eMMC, no Nvidia). The install went smoothly with no changes to the Bios. Not a dual boot. I let the installer decide the partitions.
 
 Problems are: CPU use is high -- 15% to 20% with jumps to 100% while machine is essentially idle.  Also getting frequent pop-ups saying "System Program Problem" asking me to report to Ubuntu. Also occasional hesitation in logging or out. Otherwise functions normally.
 
 I don't know how to diagnose problem. I am hoping someone can get me pointed in the right direction. Including, below, are copies of  "important" and "system" log entries.
 
 Don't know if I should try to fix, re-install, or just live with it.
 
 Thanks for any guidance.

```
Log "Important" tab: 

9:00:00 AM bluetoothd: Failed to set mode: Blocked through rfkill (0x12)
 8:59:58 AM spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
 8:59:54 AM bluetoothd: RFCOMM server failed for :1.143/Profile/HSPHSProfile/00001108-0000-1000-8000-00805f9b34fb: rfcomm_bind: Address already in use (98)
 8:59:54 AM pulseaudio: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
 8:59:54 AM bluetoothd: RFCOMM server failed for Headset Voice gateway: rfcomm_bind: Address already in use (98)
 7:51:10 AM spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
 7:51:06 AM pulseaudio: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
 7:50:43 AM bluetoothd: Failed to set mode: Blocked through rfkill (0x12)
 7:50:42 AM spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
 7:50:34 AM wpa_supplicant: dbus: Failed to construct signal
 7:50:32 AM bluetoothd: Failed to set mode: Blocked through rfkill (0x12)
 7:50:30 AM kernel: ACPI Error: Aborting method \_SB.IPPF._STA due to previous error (AE_NOT_FOUND) (20190703/psparse-531)

```
and
```
Log "System" tab:

 9:22:33 AM kernel: audit: type=1400 audit(1579713753.966:60): apparmor="DENIED" operation="open" profile="snap.gnome-logs.gnome-logs" name="/proc/4877/mounts" pid=4877 comm="gnome-logs" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
 9:22:33 AM kernel: kauditd_printk_skb: 10 callbacks suppressed
 9:22:20 AM kernel: audit: type=1400 audit(1579713740.183:48): apparmor="DENIED" operation="open" profile="snap.gnome-logs.gnome-logs" name="/home/tinylaptop/.bash_history" pid=4877 comm="pool" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
 9:22:19 AM kernel: kauditd_printk_skb: 27 callbacks suppressed
 9:01:41 AM kernel: perf: interrupt took too long (2541 > 2500), lowering kernel.perf_event_max_sample_rate to 78500
 8:59:59 AM kernel: rfkill: input handler disabled
 7:51:06 AM kernel: Bluetooth: RFCOMM ver 1.11
 7:50:48 AM kernel: logitech-hidpp-device 0003:046D:4054.0004: HID++ 4.5 device connected.
 7:50:39 AM kernel: IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
 7:50:38 AM kernel: wlo1: associated
 7:50:38 AM kernel: rtw_pci 0000:01:00.0: sta 80:37:73:81:3d:bb joined with macid 0
 7:50:38 AM kernel: wlo1: RX AssocResp from 80:37:73:81:3d:bb (capab=0x431 status=0 aid=2)
 7:50:34 AM kernel: rtw_pci 0000:01:00.0: start vif 40:5b:d8:44:42:0b on port 0
 7:50:32 AM kernel: Bluetooth: BNEP socket layer initialized
 7:50:32 AM kernel: input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input27
 7:50:32 AM kernel: snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12
 7:50:32 AM kernel: snd_hda_intel 0000:00:1b.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
 7:50:31 AM kernel: audit: type=1400 audit(1579708231.907:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=618 comm="apparmor_parser"
 7:50:31 AM kernel: rtw_pci 0000:01:00.0 wlo1: renamed from wlan0
 7:50:31 AM kernel: input: HP WMI hotkeys as /devices/virtual/input/input19
 7:50:31 AM kernel: hp_wmi: query 0xd returned error 0x5
 7:50:31 AM kernel: kvm: disabled by bios
 7:50:31 AM kernel: intel_rapl_common: Found RAPL domain core
 7:50:31 AM kernel: kvm: disabled by bios
 7:50:31 AM kernel: rtw_pci 0000:01:00.0: pci msi enabled
 7:50:31 AM kernel: ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
 7:50:31 AM kernel: i915 0000:00:02.0: fb0: i915drmfb frame buffer device
 7:50:31 AM kernel: Console: switching to colour frame buffer device 170x48
 7:50:31 AM kernel: fbcon: i915drmfb (fb0) is primary device
 7:50:31 AM kernel: input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input24
 7:50:31 AM kernel: ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
 7:50:31 AM kernel: [drm] Initialized i915 1.6.0 20190619 for 0000:00:02.0 on minor 0
 7:50:31 AM kernel: SSE version of gcm_enc/dec engaged.
 7:50:31 AM kernel: cryptd: max_cpu_qlen set to 1000
 7:50:31 AM kernel: i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=io+mem:owns=io+mem
 7:50:31 AM kernel: [drm] Driver supports precise vblank timestamp query.
 7:50:31 AM kernel: i915 0000:00:02.0: vgaarb: deactivate vga console
 7:50:31 AM kernel: Console: switching to colour dummy device 80x25
 7:50:31 AM kernel: fb0: switching to inteldrmfb from EFI VGA
 7:50:31 AM kernel: checking generic (80000000 408000) vs hw (80000000 10000000)
 7:50:31 AM kernel: i915 0000:00:02.0: Disabling error capture for VT-d workaround
 7:50:31 AM kernel: USB Video Class driver (1.1.1)
 7:50:31 AM kernel: usbcore: registered new interface driver uvcvideo
 7:50:31 AM kernel: input: HP Webcam: HP Webcam as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/input/input23
 7:50:31 AM kernel: uvcvideo 1-5:1.0: Entity type for entity Extension 4 was not initialized!
 7:50:30 AM kernel: uvcvideo: Found UVC 1.00 device HP Webcam (05c8:0233)
 7:50:30 AM kernel: hid-multitouch 0018:04F3:30D3.0001: input,hidraw0: I2C HID v1.00 Mouse [ELAN0704:00 04F3:30D3] on i2c-ELAN0704:00
 7:50:30 AM kernel: input: ELAN0704:00 04F3:30D3 Touchpad as /devices/pci0000:00/808622C1:00/i2c-0/i2c-ELAN0704:00/0018:04F3:30D3.0001/input/input22
 7:50:30 AM kernel: Bluetooth: hci0: RTL: cfg_sz 6, total sz 24866

 7:50:30 AM kernel: usbcore: registered new interface driver btusb
 7:50:30 AM kernel: videodev: Linux video capture interface: v2.00

```

---

### Post by daniell59 on 2020-01-22
I have limited knowledge but this works for me.

sudo rm /var/crash/*

---

### Post by ishmael3 on 2020-01-23
daniell59, thanks much for the response. I have read about people doing that. Seems like it might be okay if I knew I was dealing with a bug that only resulted in annoying pop-ups. But I'm not sure of that yet. When I run
 
 ```
ls -1 /var/crash


``` 
 
 I see there are 21224 entries (if I'm reading the result correctly) in that directory. I have another install of Ubuntu 16.04 that's been up for two years with only 300 entries.  
 
 So, I'm thinking I should try and understand the reason  before eliminating the message.  Please let me know if I'm missing something. Would really like to know why CPU use is so high.

---

### Post by dragonfly41 on 2020-01-23
While you can run cli operations such as htop
my suggestion is to install this handy GUI.

[https://sourceforge.net/projects/stacer/](https://sourceforge.net/projects/stacer/)

Investigate the menu of options.
Service and Processes windows would be a start.

---

