---
title: "qemu /dev/bus/usb permissions"
date: 2014-04-11
forum: General Help
---

### Post by jeremy22 on 2014-04-11
Hi,

I have an Acer C720 chromebook dual booting chrome and kubuntu with kernel 3.11.0-18-generic.
I have a WinXP image that I'd like to run under qemu in order to use my 
Timex RunTrainer 1.0 (TRT GPS watch) since the communication software (Device Agent) 
only runs on Windows and does not run under WINE, 
and I don't have time to reverse engineer the protocol. 
(The newer TRT's just show up as normal usb mass storage devices.)

I've tested running XP under qemu on this system and it works good enough for my purposes.
My problem is that I'm getting a permissions error:

libusbx: error [_get_usbfs_fd] libusbx couldn't open USB device /dev/bus/usb/002/006: Permission denied
libusbx: error [_get_usbfs_fd] libusbx requires write access to USB device nodes

I guess I could run my StartXP shell script as root, but is there a better way?

Thanks in advance.

---

### Post by frostschutz on 2014-04-11
you could probably chmod/chown the usb device (or write a udev rule to that effect)

but it's not unheard of to run KVM instances as root

---

### Post by jeremy22 on 2014-04-11
Anybody with experience writing udev rules?

dmesg reports:
[ 3974.322884] usb 2-2: USB disconnect, device number 10
[ 3977.165023] usb 2-2: new full-speed USB device number 11 using xhci_hcd
[ 3977.185620] usb 2-2: New USB device found, idVendor=0cc2, idProduct=d702
[ 3977.185629] usb 2-2: New USB device strings: Mfr=2, Product=3, SerialNumber=0
[ 3977.185634] usb 2-2: Product: Timex Ironman Run Trainer GPS Watch
[ 3977.185638] usb 2-2: Manufacturer: Timex Corporation
[ 3977.189424] hid-generic 0003:0CC2:D702.0007: hiddev0,hidraw0: USB HID v1.11 Device [Timex Corporation Timex Ironman Run Trainer GPS Watch] on usb-0000:00:14.0-2/input0

and the device appears in
# ls -l /dev/usb/hiddev0 
crw------- 1 root root 180, 0 Apr 11 19:01 /dev/usb/hiddev0

and under /dev/bus/usb/002/00?

I've tried the following rule which doesn't work.
I've tried both ATTR{idVendor} and SYSFS{idVendor}.
And I've done "udevadm control --reload; udevadm trigger"

# cat 25-TRT.rules 
# usb 2-2: New USB device found, idVendor=0cc2, idProduct=d702
# usb 2-2: New USB device strings: Mfr=2, Product=3, SerialNumber=0
# usb 2-2: Product: Timex Ironman Run Trainer GPS Watch
# usb 2-2: Manufacturer: Timex Corporation
# hid-generic 0003:0CC2:D702.0003: hiddev0,hidraw0: USB HID v1.11 Device [Timex Corporation Timex Ironman Run Trainer GPS Watch] on usb-0000:00:14.0-2/input0


ACTION=="add", SUBSYS=="usb", ATTR{idVendor}=="0x0cc2", ATTR{idProduct}=="0xd702", MODE="0660", GROUP="plugdev"

---

