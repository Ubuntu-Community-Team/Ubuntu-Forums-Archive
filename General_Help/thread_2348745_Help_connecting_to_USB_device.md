---
title: "Help connecting to USB device"
date: 2017-01-06
forum: General Help
---

### Post by padraignotlad-x on 2017-01-06
Hello,

I'm trying to connect to a USB device.  I used to connect using /dev/ttyACM0.  But I updated the firmware, and now the device shows "RaceFlight One" where it used to say /dev/ttyACM0.  I keep getting the following message in the software...  "Are udev rules installed correctly? See docs for instructions".  The instructions say....
[COLOR=#b22222]*Linux requires udev rules to allow write access to USB devices for users. An example shell command to acheive this on Ubuntu is shown here:*[/COLOR]

[COLOR=#b22222]*(echo '# DFU (Internal bootloader for STM32 MCUs)'*[/COLOR]
[COLOR=#b22222]* echo 'SUBSYSTEM=="usb", ATTRS{idVendor}=="0483", ATTRS{idProduct}=="df11", MODE="0664", GROUP="plugdev"') | sudo tee /etc/udev/rules.d/45-stdfu-permissions.rules > /dev/null*[/COLOR]
[COLOR=#b22222]*This assigns the device to the plugdev group(a standard group in Ubuntu). To check that your account is in the plugdev group type groups in the shell and ensure plugdev is listed. If not you can add yourself as shown (replacing <username> with your username):*[/COLOR]

[COLOR=#b22222][I]sudo usermod -a -G plugdev <username>

[/I][/COLOR]I have updated the idVendor and idProduct to reflect what is listed below.  Still won't connect.

Below is what I get from dmesg.  Does anyone know what I need to do to the UDEV rules to make this work again?

[   25.606859] usb 1-1.2.2: Product: RaceFlight FC
[   25.606863] usb 1-1.2.2: Manufacturer: RaceFlight
[   25.606868] usb 1-1.2.2: SerialNumber: 308A396D3136
[   25.608148] input: RaceFlight RaceFlight FC as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/0003:0483:5742.0005/input/input22
[   25.608529] hid-generic 0003:0483:5742.0005: input,hidraw4: USB HID v1.11 Device [RaceFlight RaceFlight FC] on usb-0000:00:1a.0-1.2.2/input0
[  776.190570] usb 1-1.2.2: USB disconnect, device number 10
[  858.567007] usb 1-1.2.2: new full-speed USB device number 11 using ehci-pci
[  858.662246] usb 1-1.2.2: New USB device found, idVendor=0483, idProduct=5742
[  858.662257] usb 1-1.2.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  858.662263] usb 1-1.2.2: Product: RaceFlight FC
[  858.662267] usb 1-1.2.2: Manufacturer: RaceFlight
[  858.662272] usb 1-1.2.2: SerialNumber: 308A396D3136
[  858.665472] input: RaceFlight RaceFlight FC as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2.2/1-1.2.2:1.0/0003:0483:5742.0006/input/input23
[  858.665876] hid-generic 0003:0483:5742.0006: input,hidraw4: USB HID v1.11 Device [RaceFlight RaceFlight FC] on usb-0000:00:1a.0-1.2.2/input0
[ 1283.346377] usb 1-1.2.2: USB disconnect, device number 11

Using Ubuntu Gnome 16.04 LTS x64.
Thanks!

---

### Post by padraignotlad-x on 2017-01-07
Bump, anyone?

---

### Post by dstaron on 2017-07-04
No help in this forum? I'm looking for help connecting also.

---

### Post by wildmanne39 on 2017-07-04
Please start your own thread with a descriptive title in the New to Ubuntu or General section.

Thanks

---

