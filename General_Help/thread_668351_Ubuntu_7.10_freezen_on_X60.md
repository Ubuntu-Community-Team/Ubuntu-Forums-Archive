---
title: "Ubuntu 7.10 freezen on X60"
date: 2008-01-15
forum: General Help
---

### Post by rogerxue on 2008-01-15
I'm new to Linux, installed Ubuntu only 2 months ago. At first, every thing was going very well, but recently it freezes every other day, Here is the typical symptom is : The hdd light blink all the time, I can't do anything, including moving the mouse. If I wait 40-60 mins it may recover. It seems like not software dependent, sometimes it freezes when I use FF, sometimes freezes when nothing's running.....


thanks for any help!!

---

### Post by rogerxue on 2008-01-15
it's freezes again just now, and I waited for 90 mins, it's still freese, and the hdd's light flashes crazy!!

it freesed at around 9.30 and I reboot the computer at around 11:00

this is the log:

[COLOR="DarkGreen"]Jan 15 21:17:02 roger-laptop /USR/SBIN/CRON[10492]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 15 21:42:06 roger-laptop input[5393]: Incoming connection on PSM 17
Jan 15 21:42:06 roger-laptop input[5393]: Incoming connection on PSM 19
Jan 15 21:42:09 roger-laptop input[5393]: New input device 00:0D:3A:A8:78:3F (Microsoft Mouse)
Jan 15 21:42:09 roger-laptop NetworkManager: <debug> [1200451328.878733] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_2110_noserial_if0_bluetooth_hci_bluetooth_hci'). 
Jan 15 21:42:10 roger-laptop kernel: [41976.484000] input: Microsoft Mouse as /class/input/input16
Jan 15 21:42:36 roger-laptop NetworkManager: <debug> [1200451351.429120] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_2110_noserial_if0_bluetooth_hci_bluetooth_hci_logicaldev_input'). 
Jan 15 21:49:49 roger-laptop kernel: [42436.040000] usb 5-2: USB disconnect, address 5
Jan 15 21:50:04 roger-laptop NetworkManager: <debug> [1200451802.969772] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_701_noserial_if0_scsi_host_scsi_device_lun0'). 
Jan 15 21:50:06 roger-laptop NetworkManager: <debug> [1200451805.164740] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_701_noserial_if0_scsi_host'). 
Jan 15 21:50:11 roger-laptop hald[5021]: forcibly attempting to lazy unmount /dev/scd1 as enclosing drive was disconnected
Jan 15 21:50:11 roger-laptop NetworkManager: <debug> [1200451809.440075] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_701_noserial_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jan 15 21:50:12 roger-laptop NetworkManager: <debug> [1200451812.090377] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_701_noserial_if0'). 
Jan 15 21:50:12 roger-laptop NetworkManager: <debug> [1200451812.200075] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_701_noserial'). 
Jan 15 21:50:12 roger-laptop NetworkManager: <debug> [1200451812.200270] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_701_noserial_usbraw'). 
Jan 15 21:50:59 roger-laptop kernel: [42506.148000] scsi 3:0:0:0: rejecting I/O to dead device
Jan 15 21:50:59 roger-laptop last message repeated 2 times
Jan 15 21:51:03 roger-laptop hald: unmounted /dev/scd1 from '/media/My Disc' on behalf of uid 0
Jan 15 21:51:13 roger-laptop NetworkManager: <debug> [1200451869.584946] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_label_My_Disc'). 
Jan 15 21:51:17 roger-laptop NetworkManager: <debug> [1200451874.235254] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_PIONEER_DVR_112N_0_0'). 
Jan 15 21:51:20 roger-laptop NetworkManager: <debug> [1200451876.728433] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_2110_noserial_if0_bluetooth_hci_bluetooth_hci'). 
Jan 15 21:51:21 roger-laptop NetworkManager: <debug> [1200451881.184757] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_2110_noserial_if0_bluetooth_hci_bluetooth_hci_logicaldev_input'). 
Jan 15 22:03:20 roger-laptop -- MARK --
Jan 15 22:16:54 roger-laptop kernel: [44058.024000] ipw3945: Error sending cmd #07 to daemon: time out after 500ms.
Jan 15 22:18:16 roger-laptop /USR/SBIN/CRON[10697]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 15 22:44:15 roger-laptop -- MARK --
Jan 15 22:49:06 roger-laptop kernel: [45983.708000] ipw3945: Error sending cmd #07 to daemon: time out after 500ms.
Jan 15 22:49:15 roger-laptop kernel: [45985.204000] ipw3945: Error sending cmd #08 to daemon: time out after 500ms.
Jan 15 23:02:08 roger-laptop syslogd 1.4.1#21ubuntu3: restart.[/COLOR]

can anyone help me?  thanks

---

### Post by raffytaffy on 2008-01-15
Can you turn off the wireless and see if the problem continues? >ipw3945<

---

### Post by rogerxue on 2008-01-15
It seems the freese only happen at around 9-10 in the evening, I'll try to turn off the wireless tomorrow, thanks

---

### Post by freund on 2008-01-18
Also try openning a terminal and type "top" enter.
This will show the processes running. Keep it open and visible while you are working, and  when it freezes maybe it will show the renegade program that is causing the problem.

---

### Post by anthonyJC on 2008-01-18
it seems similar to my response to this [http://ubuntuforums.org/showthread.php?t=670943&highlight=freezing](http://ubuntuforums.org/showthread.php?t=670943&highlight=freezing). Your hdd is being spun down by bios and this is causing the freeze.

---

### Post by rogerxue on 2008-01-18
I increased memory to 2.5G, and the freese never happend again. So I think may be the freese happens only when the mem is fall? I use 1G mem before.

To anthonuJC: thanks fot the advice, I do turn on the hdd power saving, but I don't think it will freese me for more than an hour, and actrally when it freeses, I can hear the hdd spun.

I'll keep pose if anything happens, thanks everyone.

---

