---
title: "Cheese Error: No device found even with camera connected"
date: 2024-07-29
forum: General Help
---

### Post by jnagy2 on 2024-07-29
I have a USB UVC 1.1 webcam that I had been using on Ubuntu 18.04 without issue however after upgrading to Ubuntu 20.04 the camera is suddenly not being recognized by cheese. The camera has not changed and works both on MacOS, Windows and even within several other Ubuntu applications (guvcview, VLC, webcamoid, xawtv, ffplay). I have verified the camrea is present with `lsusb -t` and `sudo lshw`. I am using kernel version `5.4.0-190-generic x86_64`. dmesg doesn't log any errors when I try to open cheese.

The exact errors I am recieving when running cheese through the command line are below.
```

user@machine:~$ cheese
** Message: 09:07:38.247: cheese-application.vala:214: Error during camera setup: No device found


(cheese:75828): cheese-CRITICAL **: 09:07:38.255: cheese_camera_device_get_name: assertion 'CHEESE_IS_CAMERA_DEVICE (device)' failed

(cheese:75828): GLib-CRITICAL **: 09:07:38.255: g_variant_new_string: assertion 'string != NULL' failed

(cheese:75828): GLib-CRITICAL **: 09:07:38.255: g_variant_ref_sink: assertion 'value != NULL' failed

(cheese:75828): GLib-GIO-CRITICAL **: 09:07:38.255: g_settings_schema_key_type_check: assertion 'value != NULL' failed

(cheese:75828): GLib-CRITICAL **: 09:07:38.255: g_variant_get_type_string: assertion 'value != NULL' failed

(cheese:75828): GLib-GIO-CRITICAL **: 09:07:38.255: g_settings_set_value: key 'camera' in 'org.gnome.Cheese' expects type 's', but a GVariant of type '(null)' was given

(cheese:75828): GLib-CRITICAL **: 09:07:38.255: g_variant_unref: assertion 'value != NULL' failed

** (cheese:75828): CRITICAL **: 09:07:38.255: cheese_preferences_dialog_setup_resolutions_for_device: assertion 'device != NULL' failed

```

---

### Post by ActionParsnip on 2024-07-29
Boot with the camera detatched and run:
```

lsusb

```
Then connect the camera, wait a second or so, then run:
```

dmesg | tail; lsusb

```

What is the full output please?

---

### Post by jnagy2 on 2024-07-29
```

user@machine:~$ lsusb
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 2109:0813 VIA Labs, Inc. USB3.0 Hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 2109:2813 VIA Labs, Inc. USB2.0 Hub
Bus 003 Device 004: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 003 Device 003: ID 17ef:608d Lenovo Lenovo USB Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

user@machine:~$ dmesg | tail; lsusb
[  202.141631] usb 4-5.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  202.141633] usb 4-5.3: Product: EvertzAV
[  202.141635] usb 4-5.3: Manufacturer: Evertz
[  202.141637] usb 4-5.3: SerialNumber: 8679370003
[  202.256311] mc: Linux media interface: v0.10
[  202.318597] videodev: Linux video capture interface: v2.00
[  202.320588] usbcore: registered new interface driver snd-usb-audio
[  202.382114] uvcvideo: Found UVC 1.10 device EvertzAV (0836:4722)
[  202.383872] usbcore: registered new interface driver uvcvideo
[  202.383874] USB Video Class driver (1.1.1)
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0836:4722 TrekStor 
Bus 004 Device 002: ID 2109:0813 VIA Labs, Inc. USB3.0 Hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 2109:2813 VIA Labs, Inc. USB2.0 Hub
Bus 003 Device 004: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 003 Device 003: ID 17ef:608d Lenovo Lenovo USB Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Note that the 'TrekStor' item is the camera.

---

### Post by ActionParsnip on 2024-07-29
If you search online for the USB ID you may find guides.

---

### Post by jnagy2 on 2024-07-29
I am expecting it to come up as an Evertz product and when I look up the vendor ID 0x0836 at [https://usb.org/sites/default/files/vendor_ids051920_0.pdf](https://usb.org/sites/default/files/vendor_ids051920_0.pdf), it shows that 0x0836 should map to Evertz and 0x1e68 to TrekStor. I am not sure why Ubuntu is mixing these 2 up or whether this would cause an issue for cheese.

---

### Post by jnagy2 on 2024-07-31
Looking at dmesg, it prints out the following. Does anyone know what either the error -19 or 'config error' means?

```

[  +0.800001] usb 4-6: new SuperSpeed Gen 1 USB device number 91 using xhci_hcd
[  +0.024531] usb 4-6: LPM exit latency is zeroed, disabling LPM.
[  +0.000791] usb 4-6: New USB device found, idVendor=0836, idProduct=4722, bcdDevice= 0.00
[  +0.000002] usb 4-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  +0.000002] usb 4-6: Product: EvertzAV
[  +0.000001] usb 4-6: Manufacturer: Evertz
[  +0.000001] usb 4-6: SerialNumber: 8679370003
[  +0.026678] uvcvideo: Found UVC 1.10 device EvertzAV (0836:4722)
[  +4.242409] usb 4-6: cannot submit urb (err = -19)
[  +0.000148] usb 4-6: cannot submit urb 0, error -19: no device
[  +1.009408] usb 4-6: USB disconnect, device number 91
[  +0.272053] usb 4-6: new SuperSpeed Gen 1 USB device number 92 using xhci_hcd
[  +0.020618] usb 4-6: LPM exit latency is zeroed, disabling LPM.
[  +0.000767] usb 4-6: New USB device found, idVendor=0836, idProduct=4722, bcdDevice= 0.00
[  +0.000005] usb 4-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  +0.000003] usb 4-6: Product: EvertzAV
[  +0.000003] usb 4-6: Manufacturer: Evertz
[  +0.000004] usb 4-6: SerialNumber: 8679370003
[  +0.026716] uvcvideo: Found UVC 1.10 device EvertzAV (0836:4722)
[  +0.013505] usb usb4-port6: config error

```

---

