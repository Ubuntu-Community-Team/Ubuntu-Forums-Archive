---
title: "Kernel Panic when connecting usb peripherals."
date: 2008-06-17
forum: General Help
---

### Post by Raziel-chan on 2008-06-17
Hi.

I seem to have a little kernel panic infestation. It seems to happen when I connect something to any of the USB ports on my PC, but not always.

First, it happened two times, the second right after a reboot forced by the first time, when I connected my D750i cellphone to my PC. When rebooting for the second time, I simply left the phone connected and everything went fine - I was able to connect/disconnect it without problems.

The third Kernel panic happened when k3b was finishing burning a DVD. I don't think that it's connected, as I burned several DVDs before and after that without problems.

Now, more kernel panics happened when I connected my new K770i cellphone. Sometimes it happened even before I selected the connection type in the phone itself.

Another kernel panic happened when I disconnected my rarely-used webcam (it was connected to a usb port in the back. All the previous kernel panics involved the front ports), plugged it to the port beside it and plugged the data cable for my phone (without the phone itself connected to it) to the port that the webcam used previously.

Then, after rebooting, I plugged a shitty usb stick/mp3 player to the front panel and everything was fine. Two times. I even managed to plug the phone in without problems.

But now, after letting the pc run for the night, I plugged the same usb stick/mp3 player again and voila! Another kernel panic.

Anyway, I attached the dmesg file. I hope that someone will be able to help me. Thanks in advance and sorry for bothering you with my problems.

cya
Raziel-chan

Ps. I'm using ubuntu with kde installed later and some of the default gnome files deinstalled.

UPDATE: Now it panicked when I disconnected the phone after safely removing it. ._.;

---

### Post by Raziel-chan on 2008-06-17
What's interesting, I failed to find any indications of a kernel panic in syslog. Everything just seems to be working fine until, suddenly, it indicates a restart - when I restart the PC due to the kernel panic.

For example:

> Jun 17 02:44:10 razielchan-desktop NetworkManager: <debug> [1213663450.289048] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_4857_16C3'). 
Jun 17 02:44:22 razielchan-desktop hald: mounted /dev/sdd1 on behalf of uid 1000
Jun 17 02:44:41 razielchan-desktop kernel: [ 3308.821430] end_request: I/O error, dev fd0, sector 0
Jun 17 02:44:41 razielchan-desktop kernel: [ 3308.845410] end_request: I/O error, dev fd0, sector 0
Jun 17 02:44:46 razielchan-desktop kernel: [ 4046.596532] end_request: I/O error, dev fd0, sector 0
Jun 17 02:44:46 razielchan-desktop kernel: [ 4046.620492] end_request: I/O error, dev fd0, sector 0
Jun 17 02:44:56 razielchan-desktop kernel: [ 4057.622775] end_request: I/O error, dev fd0, sector 0
Jun 17 02:44:56 razielchan-desktop kernel: [ 4057.646733] end_request: I/O error, dev fd0, sector 0
Jun 17 02:45:01 razielchan-desktop /USR/SBIN/CRON[9597]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Jun 17 02:45:07 razielchan-desktop kernel: [ 3660.459355] end_request: I/O error, dev fd0, sector 0
Jun 17 02:45:07 razielchan-desktop kernel: [ 3660.483307] end_request: I/O error, dev fd0, sector 0
Jun 17 02:45:14 razielchan-desktop kernel: [ 4076.529286] end_request: I/O error, dev fd0, sector 0
Jun 17 02:45:14 razielchan-desktop kernel: [ 4076.557255] end_request: I/O error, dev fd0, sector 0
Jun 17 02:47:48 razielchan-desktop hald: unmounted /dev/sdd1 from '/media/PHONE CARD' on behalf of uid 1000
Jun 17 02:47:59 razielchan-desktop kernel: [ 4247.858353] usb 1-2: USB disconnect, address 15
Jun 17 02:47:59 razielchan-desktop NetworkManager: <debug> [1213663679.755595] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_e0b7_3522390287559300_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jun 17 02:48:00 razielchan-desktop NetworkManager: <debug> [1213663680.055818] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_4857_16C3'). 
Jun 17 02:48:00 razielchan-desktop NetworkManager: <debug> [1213663680.084454] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Sony_Eri_Memory_Stick_3522390287559300_0_0'). 
Jun 17 02:48:00 razielchan-desktop NetworkManager: <debug> [1213663680.123713] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_e0b7_3522390287559300_if0_scsi_host_scsi_device_lun0'). 
Jun 17 02:48:00 razielchan-desktop NetworkManager: <debug> [1213663680.124559] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_e0b7_3522390287559300_if0_scsi_host'). 
Jun 17 02:48:00 razielchan-desktop NetworkManager: <debug> [1213663680.190295] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_e0b7_3522390287559300_if0'). 
Jun 17 02:48:00 razielchan-desktop NetworkManager: <debug> [1213663680.276175] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_fce_e0b7_3522390287559300'). 
Jun 17 02:52:36 razielchan-desktop syslogd 1.5.0#1ubuntu1: restart.
Jun 17 02:52:36 razielchan-desktop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jun 17 02:52:36 razielchan-desktop kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.
Jun 17 02:52:36 razielchan-desktop kernel: Symbols match kernel version 2.6.24.
Jun 17 02:52:36 razielchan-desktop kernel: Loaded 33194 symbols from 97 modules.

I'm wondering where do these I/O errors come from, btw.

Another thing is that it registers a ton of instances of this error:

> Jun 17 02:44:10 razielchan-desktop kernel: [ 4007.321459] attempt to access beyond end of device
Jun 17 02:44:10 razielchan-desktop kernel: [ 4007.321461] sdd: rw=0, want=466944, limit=466907

-upon connecting my cellphone. They all happen in a single second.

Another such occasion:

> Jun 17 03:20:51 razielchan-desktop NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Jun 17 03:20:51 razielchan-desktop NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
Jun 17 03:20:51 razielchan-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Jun 17 03:20:52 razielchan-desktop ntpdate[6466]: adjust time server 91.189.94.4 offset -0.202949 sec
Jun 17 03:20:53 razielchan-desktop avahi-daemon[5310]: Registering new address record for fe80::21c:10ff:fee4:12d2 on wlan0.*.
Jun 17 03:21:02 razielchan-desktop kernel: [  177.210902] wlan0: no IPv6 routers present
Jun 17 03:25:01 razielchan-desktop /USR/SBIN/CRON[6821]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Jun 17 03:30:53 razielchan-desktop scim-bridge: Cleanup, done. Exitting...
Jun 17 03:30:55 razielchan-desktop console-kit-daemon[5535]: WARNING: Unable to activate console: No such device or address 
Jun 17 03:31:02 razielchan-desktop kdm[5290]: StartServerSucces
Jun 17 03:31:34 razielchan-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Jun 17 03:35:01 razielchan-desktop /USR/SBIN/CRON[8062]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Jun 17 03:42:32 razielchan-desktop syslogd 1.5.0#1ubuntu1: restart.
Jun 17 03:42:32 razielchan-desktop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jun 17 03:42:32 razielchan-desktop kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.
Jun 17 03:42:32 razielchan-desktop kernel: Symbols match kernel version 2.6.24.
Jun 17 03:42:32 razielchan-desktop kernel: Loaded 33194 symbols from 97 modules.

There also seem to be some problems with memory allocation:

> Jun 17 03:42:32 razielchan-desktop kernel: [   18.243945] system 00:01: ioport range 0x1000-0x107f has been reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243947] system 00:01: ioport range 0x1080-0x10ff has been reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243950] system 00:01: ioport range 0x1400-0x147f has been reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243952] system 00:01: ioport range 0x1480-0x14ff has been reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243954] system 00:01: ioport range 0x1800-0x187f has been reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243956] system 00:01: ioport range 0x1880-0x18ff has been reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243961] system 00:02: ioport range 0xb78-0xb7b has been reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243963] system 00:02: ioport range 0xf78-0xf7b has been reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243965] system 00:02: ioport range 0xa78-0xa7b has been reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243968] system 00:02: ioport range 0xe78-0xe7b has been reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243970] system 00:02: ioport range 0xbbc-0xbbf has been reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243972] system 00:02: ioport range 0xfbc-0xfbf has been reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243974] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243976] system 00:02: ioport range 0x294-0x297 has been reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243979] system 00:02: ioport range 0x295-0x296 has been reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243986] system 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243990] system 00:0b: iomem range 0xcee00-0xcffff has been reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243992] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243995] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.243997] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.244000] system 00:0b: iomem range 0x7fff0000-0x7fffffff could not be reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.244002] system 00:0b: iomem range 0xffff0000-0xffffffff could not be reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.244005] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.244007] system 00:0b: iomem range 0x100000-0x7ffeffff could not be reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.244010] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.244012] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.244015] system 00:0b: iomem range 0xfefff000-0xfeffffff could not be reserved
Jun 17 03:42:32 razielchan-desktop kernel: [   18.244017] system 00:0b: iomem range 0xfff80000-0xfff80fff could not be reserved

cya
Raziel-chan

---

