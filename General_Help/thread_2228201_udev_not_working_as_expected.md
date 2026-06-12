---
title: "udev not working as expected"
date: 2014-06-06
forum: General Help
---

### Post by ELMIT on 2014-06-06
I got a no-name tablet, which I want to connect to my Ubuntu 13.10, and just now upgraded to 14.04 box.

I can connect this tablet to my old EeePC without any settings and lsusb will tell me the line:

> Bus 003 Device 117: ID 0bb4:0c03 High Tech Computer Corp.

On my desktop, however, it does not show up!

Even I have added the line to /etc/udev/rules.d/51-android.rules:
> SUBSYSTEM=="usb", ATTRS{idVendor}=="0bb4", ATTRS{idProduct}=="0c03", MODE="0666", GROUP="plugdev"

Of course, I added the command:

$ sudo service udev restart
udev stop/waiting
udev start/running, process 15160


If I plug in another device, I see with tail -f /var/log/syslog immediatley:

> Jun  6 18:44:32 Ronald-Desktop kernel: [ 8040.643845] usb 2-3.7: new high-speed USB device number 16 using ehci-pci
Jun  6 18:44:32 Ronald-Desktop kernel: [ 8040.748894] usb 2-3.7: New USB device found, idVendor=0bb4, idProduct=0ca2
Jun  6 18:44:32 Ronald-Desktop kernel: [ 8040.748902] usb 2-3.7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jun  6 18:44:32 Ronald-Desktop kernel: [ 8040.748907] usb 2-3.7: Product: Android Phone
Jun  6 18:44:32 Ronald-Desktop kernel: [ 8040.748911] usb 2-3.7: Manufacturer: HTC
Jun  6 18:44:32 Ronald-Desktop kernel: [ 8040.748915] usb 2-3.7: SerialNumber: HT117RX20614
Jun  6 18:44:32 Ronald-Desktop kernel: [ 8040.750363] usb-storage 2-3.7:1.0: USB Mass Storage device detected
Jun  6 18:44:32 Ronald-Desktop kernel: [ 8040.750552] scsi8 : usb-storage 2-3.7:1.0
Jun  6 18:44:32 Ronald-Desktop mtp-probe: checking bus 2, device 16: "/sys/devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3.7"
Jun  6 18:44:32 Ronald-Desktop mtp-probe: bus: 2, device: 16 was not an MTP device
Jun  6 18:44:33 Ronald-Desktop kernel: [ 8041.750887] scsi 8:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
Jun  6 18:44:33 Ronald-Desktop kernel: [ 8041.751550] sd 8:0:0:0: Attached scsi generic sg4 type 0
Jun  6 18:44:33 Ronald-Desktop kernel: [ 8041.757745] sd 8:0:0:0: [sdd] Attached SCSI removable disk


Nothing however, if I plug in that tablet!

Recap: EeePC shows the device, pc doesn't. Other devices are shown on pc though.

Any ideas?

---

### Post by varunendra on 2014-06-07
The title of your thread is misleading and so you may not get proper help from right people. Udev rules come into play when a device ID is detected by the system, it does not do the job of _detecting_ a device itself.

Your problem is that the device is not being detected by the system, not that udev is not working.

If syslog is not showing the device, the problem maybe with the connection interface - usb or its drivers, besides some other compatibility issues that I can't guess right now.

I see that your example device was being probed to check if it was an MTP device. There used to be some bug with MTP support in Ubuntu due to which MTP devices did not work properly or not detected at all. I just vaguely remember this since I never dealt with such devices/threads myself, just noticed a few. Not sure if your problem may be a similar one.

Is there some 'Mode' setting in the tablet for its connection interface? Does it have a 'Storage' mode?
What kind of device does it show up as in the EeePC, and which version of Ubuntu does it have?

And I think you should request a mod (using "Report Post" button below your post) to correct the thread title to reflect the correct problem, for example - "Tablet connected via USB not detected in 14.04"

---

### Post by ELMIT on 2014-06-07
I changed the cable again and then it was detected on both, the Eeepc, still running 12.10 and desktop 14.04. 

However, it is not always detected though. It needs to plugin a couple of times till it is detected again.

---

### Post by varunendra on 2014-06-07
Maybe a "low-power-usb-port" issue then? If it disappears during file transfers, or some other high traffic activity, it is almost certainly a low power/signal issue. Using a better quality and/or shorter USB cable, or a different USB port may help in such cases (usually the backside usb ports are better on older motherboards).

---

