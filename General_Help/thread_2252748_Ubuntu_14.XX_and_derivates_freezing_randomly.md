---
title: "Ubuntu 14.XX and derivates freezing randomly"
date: 2014-11-14
forum: General Help
---

### Post by J.G on 2014-11-14
Hi everybody,

A big issue is present since the release of Ubuntu 14.04 that affects it and all Linux distributions that are based on Ubuntu (like Lubuntu, Linux Mint 17, Xubuntu,...). The system randomly freezes for no reason.

Here is informations about my computer :
- Intel(R) Core(TM) i7 CPU (2.80GHz)
- 8 Go RAM
- NVIDIA GeForce GT 230 (using nvidia 340.58)
- Kernel 3.18.X

**Before you answered on this topic, it isn't the fault of NVIDIA proprietary drivers like said others people on the Web/forums**.
**I used before Lubuntu 13.10 with proprietary NVIDIA drivers without issue .**

I tested for the moment 2 methods that didn't solve the issue for me but they can freeze your computer if you don't apply it in some cases :
-> 1°) Go on Firefox and write "about:config" in the URL adress bar. Search the option "layers.acceleration.disabled" and change it to true.
-> 2°) Use a new kernel version ("3.18.0-031800rc4-generic" instead of "3.13.0-24-generic")
32 bit setup :
```
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18-rc4-vivid/linux-headers-3.18.0-031800rc4_3.18.0-031800rc4.201411091835_all.deb
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18-rc4-vivid/linux-headers-3.18.0-031800rc4-generic_3.18.0-031800rc4.201411091835_i386.deb
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18-rc4-vivid/linux-image-3.18.0-031800rc4-generic_3.18.0-031800rc4.201411091835_i386.deb
sudo dpkg -i linux-headers-3.18*.deb linux-image-3.18*.deb
```
64 bit setup :
```
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18-rc4-vivid/linux-headers-3.18.0-031800rc4_3.18.0-031800rc4.201411091835_all.deb
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18-rc4-vivid/linux-headers-3.18.0-031800rc4-generic_3.18.0-031800rc4.201411091835_amd64.deb
wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18-rc4-vivid/linux-image-3.18.0-031800rc4-generic_3.18.0-031800rc4.201411091835_amd64.deb
sudo dpkg -i linux-headers-3.18*.deb linux-image-3.18*.deb
```

I tested now a third method : uninstall the package xserver-xorg-video-nouveau. Even if you setup the NVIDIA proprietary driver, if xserver-xorg-video-nouveau is installed, the system force to use the both drivers and may result in a freeze/crash of the system.
```
sudo apt-get remove xserver-xorg-video-nouveau
```

Do you have another solution ? Will you try to find a solution to this issue and not ignoring it like you did in the different launchpad/forum reports ?

In a friendly manner,
J.G

---

### Post by J.G on 2014-11-17
Issue still here. These 3 methods doesn't solve the problem. Ubuntu and others freeze again, all the periphericals (keyboard, mouse, ...) doesn't work : they were disabled when the freeze comes.

---

### Post by J.G on 2014-11-17
I see that in the logs. The problem comes from X.Org ?

```
Nov 17 09:16:03 jackobo-MS-7616 mdm[1614]: WARNING: Plymouth is running, asking it to stop...
Nov 17 09:16:03 jackobo-MS-7616 mdm[1614]: WARNING: Plymouth stopped
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   34.745232] init: plymouth-upstart-bridge main process ended, respawning
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   34.749436] init: plymouth-upstart-bridge main process (1622) terminated with status 1
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   34.749446] init: plymouth-upstart-bridge main process ended, respawning
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214007] ------------[ cut here ]------------
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214021] WARNING: CPU: 4 PID: 1627 at /home/apw/COD/linux/drivers/gpu/drm/drm_ioctl.c:143 drm_set_busid.isra.4+0xdf/0xf0 [drm]()
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214076] No drm_driver.set_busid() implementation provided by nv_drm_driver [nvidia]. Use drm_dev_set_unique() to set the unique name explicitly.
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214076] Modules linked in: bnep rfcomm bluetooth binfmt_misc nvidia(POE) snd_usb_audio snd_usbmidi_lib xpad joydev gpio_ich snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm dm_multipath scsi_dh snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq drm snd_seq_device snd_timer snd coretemp kvm_intel soundcore i7core_edac kvm edac_core lpc_ich serio_raw mac_hid parport_pc ppdev hid_wiimote ff_memless lp parport dm_mirror dm_region_hash dm_log uas usb_storage hid_generic usbhid hid firewire_ohci psmouse ahci firewire_core r8169 libahci mii crc_itu_t
**Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214101] CPU: 4 PID: 1627 Comm: Xorg Tainted: P           OE  3.18.0-031800rc4-generic #201411091835**
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214102] Hardware name: MEDIONPC MS-7616/MS-7616, BIOS A7616MLN.10F 01/15/2010
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214103]  000000000000008f ffff88022f687cd8 ffffffff8179f058 0000000000000007
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214105]  ffff88022f687d28 ffff88022f687d18 ffffffff8106eafc ffff8802302d8000
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214106]  ffff8802304fc9c0 ffff880035c7a000 00000000ffffffea ffff88022f687e30
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214108] Call Trace:
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214113]  [<ffffffff8179f058>] dump_stack+0x46/0x58
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214117]  [<ffffffff8106eafc>] warn_slowpath_common+0x8c/0xc0
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214118]  [<ffffffff8106ebe6>] warn_slowpath_fmt+0x46/0x50
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214125]  [<ffffffffc047c23f>] drm_set_busid.isra.4+0xdf/0xf0 [drm]
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214130]  [<ffffffffc047c2a2>] drm_setversion+0x52/0xc0 [drm]
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214136]  [<ffffffffc047bdb7>] drm_ioctl+0x257/0x590 [drm]
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214141]  [<ffffffffc047c250>] ? drm_set_busid.isra.4+0xf0/0xf0 [drm]
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214144]  [<ffffffff811fbfb5>] do_vfs_ioctl+0x75/0x2c0
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214146]  [<ffffffff811e86ea>] ? do_sys_open+0x1aa/0x220
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214147]  [<ffffffff811fc291>] SyS_ioctl+0x91/0xb0
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214149]  [<ffffffff817ac8ad>] system_call_fastpath+0x16/0x1b
Nov 17 09:16:03 jackobo-MS-7616 kernel: [   35.214151] ---[ end trace 1ff80c42c572b024 ]---
Nov 17 09:16:04 jackobo-MS-7616 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 (xid=0x751bea37)
Nov 17 09:16:05 jackobo-MS-7616 nvidia-persistenced: Started (1644)
Nov 17 09:16:05 jackobo-MS-7616 kernel: [   36.819781] nvidia 0000:01:00.0: irq 35 for MSI/MSI-X
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666085] ------------[ cut here ]------------
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666112] WARNING: CPU: 5 PID: 1627 at /home/apw/COD/linux/drivers/gpu/drm/drm_ioctl.c:143 drm_set_busid.isra.4+0xdf/0xf0 [drm]()
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666198] No drm_driver.set_busid() implementation provided by nv_drm_driver [nvidia]. Use drm_dev_set_unique() to set the unique name explicitly.
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666200] Modules linked in: bnep rfcomm bluetooth binfmt_misc nvidia(POE) snd_usb_audio snd_usbmidi_lib xpad joydev gpio_ich snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm dm_multipath scsi_dh snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq drm snd_seq_device snd_timer snd coretemp kvm_intel soundcore i7core_edac kvm edac_core lpc_ich serio_raw mac_hid parport_pc ppdev hid_wiimote ff_memless lp parport dm_mirror dm_region_hash dm_log uas usb_storage hid_generic usbhid hid firewire_ohci psmouse ahci firewire_core r8169 libahci mii crc_itu_t
**Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666261] CPU: 5 PID: 1627 Comm: Xorg Tainted: P        W  OE  3.18.0-031800rc4-generic #201411091835**
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666264] Hardware name: MEDIONPC MS-7616/MS-7616, BIOS A7616MLN.10F 01/15/2010
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666266]  000000000000008f ffff88022f687cd8 ffffffff8179f058 0000000000000007
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666271]  ffff88022f687d28 ffff88022f687d18 ffffffff8106eafc ffff8802302d8000
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666275]  ffff88022f6c0600 ffff880035c7a000 00000000ffffffea ffff88022f687e30
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666280] Call Trace:
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666289]  [<ffffffff8179f058>] dump_stack+0x46/0x58
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666296]  [<ffffffff8106eafc>] warn_slowpath_common+0x8c/0xc0
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666301]  [<ffffffff8106ebe6>] warn_slowpath_fmt+0x46/0x50
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666318]  [<ffffffffc047c23f>] drm_set_busid.isra.4+0xdf/0xf0 [drm]
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666333]  [<ffffffffc047c2a2>] drm_setversion+0x52/0xc0 [drm]
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666348]  [<ffffffffc047bdb7>] drm_ioctl+0x257/0x590 [drm]
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666363]  [<ffffffffc047c250>] ? drm_set_busid.isra.4+0xf0/0xf0 [drm]
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666370]  [<ffffffff811fbfb5>] do_vfs_ioctl+0x75/0x2c0
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666374]  [<ffffffff811e86ea>] ? do_sys_open+0x1aa/0x220
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666379]  [<ffffffff811fc291>] SyS_ioctl+0x91/0xb0
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666384]  [<ffffffff817ac8ad>] system_call_fastpath+0x16/0x1b
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666387] ---[ end trace 1ff80c42c572b025 ]---
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666392] ------------[ cut here ]------------
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666406] WARNING: CPU: 5 PID: 1627 at /home/apw/COD/linux/drivers/gpu/drm/drm_ioctl.c:143 drm_set_busid.isra.4+0xdf/0xf0 [drm]()
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666484] No drm_driver.set_busid() implementation provided by nv_drm_driver [nvidia]. Use drm_dev_set_unique() to set the unique name explicitly.
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666486] Modules linked in: bnep rfcomm bluetooth binfmt_misc nvidia(POE) snd_usb_audio snd_usbmidi_lib xpad joydev gpio_ich snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm dm_multipath scsi_dh snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq drm snd_seq_device snd_timer snd coretemp kvm_intel soundcore i7core_edac kvm edac_core lpc_ich serio_raw mac_hid parport_pc ppdev hid_wiimote ff_memless lp parport dm_mirror dm_region_hash dm_log uas usb_storage hid_generic usbhid hid firewire_ohci psmouse ahci firewire_core r8169 libahci mii crc_itu_t
**Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666539] CPU: 5 PID: 1627 Comm: Xorg Tainted: P        W  OE  3.18.0-031800rc4-generic #201411091835**
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666542] Hardware name: MEDIONPC MS-7616/MS-7616, BIOS A7616MLN.10F 01/15/2010
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666544]  000000000000008f ffff88022f687cd8 ffffffff8179f058 0000000000000007
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666548]  ffff88022f687d28 ffff88022f687d18 ffffffff8106eafc ffff8802302d8000
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666552]  ffff88022f6c0600 ffff880035c7a000 00000000ffffffea ffff88022f687e30
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666557] Call Trace:
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666562]  [<ffffffff8179f058>] dump_stack+0x46/0x58
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666568]  [<ffffffff8106eafc>] warn_slowpath_common+0x8c/0xc0
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666573]  [<ffffffff8106ebe6>] warn_slowpath_fmt+0x46/0x50
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666589]  [<ffffffffc047c23f>] drm_set_busid.isra.4+0xdf/0xf0 [drm]
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666604]  [<ffffffffc047c2a2>] drm_setversion+0x52/0xc0 [drm]
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666618]  [<ffffffffc047bdb7>] drm_ioctl+0x257/0x590 [drm]
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666633]  [<ffffffffc047c250>] ? drm_set_busid.isra.4+0xf0/0xf0 [drm]
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666639]  [<ffffffff811fbfb5>] do_vfs_ioctl+0x75/0x2c0
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666643]  [<ffffffff811e86ea>] ? do_sys_open+0x1aa/0x220
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666648]  [<ffffffff811fc291>] SyS_ioctl+0x91/0xb0
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666652]  [<ffffffff817ac8ad>] system_call_fastpath+0x16/0x1b
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   37.666655] ---[ end trace 1ff80c42c572b026 ]---
Nov 17 09:16:06 jackobo-MS-7616 acpid: client connected from 1627[0:0]
Nov 17 09:16:06 jackobo-MS-7616 acpid: 1 client rule loaded
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.226996] ------------[ cut here ]------------
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227009] WARNING: CPU: 3 PID: 1627 at /home/apw/COD/linux/drivers/gpu/drm/drm_ioctl.c:143 drm_set_busid.isra.4+0xdf/0xf0 [drm]()
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227049] No drm_driver.set_busid() implementation provided by nv_drm_driver [nvidia]. Use drm_dev_set_unique() to set the unique name explicitly.
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227050] Modules linked in: bnep rfcomm bluetooth binfmt_misc nvidia(POE) snd_usb_audio snd_usbmidi_lib xpad joydev gpio_ich snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm dm_multipath scsi_dh snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq drm snd_seq_device snd_timer snd coretemp kvm_intel soundcore i7core_edac kvm edac_core lpc_ich serio_raw mac_hid parport_pc ppdev hid_wiimote ff_memless lp parport dm_mirror dm_region_hash dm_log uas usb_storage hid_generic usbhid hid firewire_ohci psmouse ahci firewire_core r8169 libahci mii crc_itu_t
**Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227075] CPU: 3 PID: 1627 Comm: Xorg Tainted: P        W  OE  3.18.0-031800rc4-generic #201411091835**
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227076] Hardware name: MEDIONPC MS-7616/MS-7616, BIOS A7616MLN.10F 01/15/2010
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227077]  000000000000008f ffff88022f687cd8 ffffffff8179f058 0000000000000007
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227078]  ffff88022f687d28 ffff88022f687d18 ffffffff8106eafc ffff8802302d8000
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227080]  ffff88003601da80 ffff880035c7a000 00000000ffffffea ffff88022f687e30
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227081] Call Trace:
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227087]  [<ffffffff8179f058>] dump_stack+0x46/0x58
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227090]  [<ffffffff8106eafc>] warn_slowpath_common+0x8c/0xc0
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227092]  [<ffffffff8106ebe6>] warn_slowpath_fmt+0x46/0x50
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227098]  [<ffffffffc047c23f>] drm_set_busid.isra.4+0xdf/0xf0 [drm]
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227103]  [<ffffffffc047c2a2>] drm_setversion+0x52/0xc0 [drm]
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227108]  [<ffffffffc047bdb7>] drm_ioctl+0x257/0x590 [drm]
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227113]  [<ffffffffc047c250>] ? drm_set_busid.isra.4+0xf0/0xf0 [drm]
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227117]  [<ffffffff811fbfb5>] do_vfs_ioctl+0x75/0x2c0
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227119]  [<ffffffff811e86ea>] ? do_sys_open+0x1aa/0x220
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227121]  [<ffffffff811fc291>] SyS_ioctl+0x91/0xb0
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227123]  [<ffffffff817ac8ad>] system_call_fastpath+0x16/0x1b
Nov 17 09:16:06 jackobo-MS-7616 kernel: [   38.227124] ---[ end trace 1ff80c42c572b027 ]---
```

---

