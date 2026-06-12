---
title: "USB key can't automount with Compiz running"
date: 2007-11-07
forum: General Help
---

### Post by therealbrewer on 2007-11-07
I have a USB key that won't automount. Tried everything suggested in as many places as I could find. The only thing that worked was

 ```
sudo modprobe -r ehci_hcd
```

but of course that turns off USB2.0

Then, because Mathematica doesn't like Compiz, I temporarily used

```
sudo metacity --replace
```

and to my surprise, the USB key automounted!

When I later did

```
sudo compiz --replace
```

the key unmounted!

What's going on???

---

### Post by Ultimadlamer on 2007-11-07
I'm not sure myself, however on my system, there's this thing called "Hald" (short for HAL Daemon, I believe) that manages the automounting of everything from CDs to flash drives to memory cards in my media card reader.

I've been told in one of my threads that it is the cause of freezes, and Compiz is something that i do have in common.  Perhaps the problems are related?  I don't know, I'm new to this linux thing.

---

### Post by therealbrewer on 2007-11-08
bump

---

### Post by therealbrewer on 2007-11-08
here is some more info:

```
$ gnome-volume-manager -n 2>&1 | tee gvm.log
```

gives this:

```
manager.c/647: setting[0]: bool: autobrowse = 1
manager.c/647: setting[1]: bool: autoburn = 1
manager.c/642: setting[2]: string: autoburn_audio_cd_command = serpentine
manager.c/642: setting[3]: string: autoburn_data_cd_command = nautilus --no-desktop burn:
manager.c/647: setting[4]: bool: autoipod = 1
manager.c/642: setting[5]: string: autoipod_command = rhythmbox
manager.c/647: setting[6]: bool: autokeyboard = 0
manager.c/642: setting[7]: string: autokeyboard_command = 
manager.c/647: setting[8]: bool: automount_drives = 1
manager.c/647: setting[9]: bool: automount_media = 1
manager.c/647: setting[10]: bool: automouse = 0
manager.c/642: setting[11]: string: automouse_command = 
manager.c/647: setting[12]: bool: autoopen = 0
manager.c/642: setting[13]: string: autoopen_path = .autoopen:autoopen
manager.c/647: setting[14]: bool: autophoto = 1
manager.c/642: setting[15]: string: autophoto_command = gnome-volume-manager-gthumb %h
manager.c/647: setting[16]: bool: autopalmsync = 0
manager.c/642: setting[17]: string: autopalmsync_command = gpilotd-control-applet
manager.c/647: setting[18]: bool: autoplay_cda = 1
manager.c/642: setting[19]: string: autoplay_cda_command = sound-juicer -d %d
manager.c/647: setting[20]: bool: autoplay_dvd = 1
manager.c/642: setting[21]: string: autoplay_dvd_command = totem %m
manager.c/647: setting[22]: bool: autoplay_vcd = 1
manager.c/642: setting[23]: string: autoplay_vcd_command = totem %m
manager.c/647: setting[24]: bool: autopocketpc = 0
manager.c/642: setting[25]: string: autopocketpc_command = multisync
manager.c/647: setting[26]: bool: autoprinter = 0
manager.c/642: setting[27]: string: autoprinter_command = gnome-cups-add hal://%h
manager.c/647: setting[28]: bool: autorun = 0
manager.c/642: setting[29]: string: autorun_path = .autorun:autorun:autorun.sh
manager.c/647: setting[30]: bool: autotablet = 0
manager.c/642: setting[31]: string: autotablet_command = 
manager.c/656: settings[32]: float: percent_threshold = 0.050000
manager.c/656: settings[33]: float: percent_used = 0.010000
manager.c/3306: gvm_user_active_at_console: check-foreground-console returned with 0
manager.c/2538: Device added: /org/freedesktop/Hal/devices/usb_device_781_8185_000136167
manager.c/3306: gvm_user_active_at_console: check-foreground-console returned with 0
manager.c/2538: Device added: /org/freedesktop/Hal/devices/usb_device_781_8185_000136167_if0
manager.c/3306: gvm_user_active_at_console: check-foreground-console returned with 0
manager.c/2538: Device added: /org/freedesktop/Hal/devices/usb_device_781_8185_000136167_usbraw
manager.c/3306: gvm_user_active_at_console: check-foreground-console returned with 0
manager.c/2538: Device added: /org/freedesktop/Hal/devices/usb_device_781_8185_000136167_if0_scsi_host
manager.c/3306: gvm_user_active_at_console: check-foreground-console returned with 0
manager.c/2538: Device added: /org/freedesktop/Hal/devices/usb_device_781_8185_000136167_if0_scsi_host_scsi_device_lun0
manager.c/3306: gvm_user_active_at_console: check-foreground-console returned with 0
manager.c/2538: Device added: /org/freedesktop/Hal/devices/usb_device_781_8185_000136167_if0_scsi_host_scsi_device_lun0_scsi_generic
```

Then

```
 sudo udevmonitor -e | tee udev.log
```

gives this:

```
udevmonitor will print the received events for:
UDEV the event which udev sends out after rule processing
UEVENT the kernel uevent

UEVENT[1194553271.391802] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-6 (usb)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6
SUBSYSTEM=usb
SEQNUM=2838
MAJOR=189
MINOR=517
DEVTYPE=usb_device
PHYSDEVBUS=usb
DEVICE=/proc/bus/usb/005/006
PRODUCT=781/8185/125
TYPE=0/0/0
BUSNUM=005
DEVNUM=006

UEVENT[1194553271.391914] add      /class/usb_endpoint/usbdev5.6_ep00 (usb_endpoint)
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep00
SUBSYSTEM=usb_endpoint
SEQNUM=2839
MAJOR=254
MINOR=12
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb

UEVENT[1194553271.398236] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0 (usb)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
SUBSYSTEM=usb
SEQNUM=2840
DEVTYPE=usb_interface
PHYSDEVBUS=usb
DEVICE=/proc/bus/usb/005/006
PRODUCT=781/8185/125
TYPE=0/0/0
INTERFACE=8/6/80
MODALIAS=usb:v0781p8185d0125dc00dsc00dp00ic08isc06ip50

UEVENT[1194553271.398308] add      /class/scsi_host/host7 (scsi_host)
ACTION=add
DEVPATH=/class/scsi_host/host7
SUBSYSTEM=scsi_host
SEQNUM=2841
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host7

UEVENT[1194553271.398339] add      /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2842
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553271.398370] add      /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2843
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553271.398397] add      /class/usb_device/usbdev5.6 (usb_device)
ACTION=add
DEVPATH=/class/usb_device/usbdev5.6
SUBSYSTEM=usb_device
SEQNUM=2844
MAJOR=189
MINOR=517
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb

UDEV  [1194553271.606783] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-6 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6
SUBSYSTEM=usb
SEQNUM=2838
MAJOR=189
MINOR=517
DEVTYPE=usb_device
PHYSDEVBUS=usb
DEVICE=/proc/bus/usb/005/006
PRODUCT=781/8185/125
TYPE=0/0/0
BUSNUM=005
DEVNUM=006
UDEVD_EVENT=1
DEVNAME=/dev/5-6

UDEV  [1194553271.613371] add      /class/usb_endpoint/usbdev5.6_ep00 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep00
SUBSYSTEM=usb_endpoint
SEQNUM=2839
MAJOR=254
MINOR=12
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep00

UDEV  [1194553271.844713] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
SUBSYSTEM=usb
SEQNUM=2840
DEVTYPE=usb_interface
PHYSDEVBUS=usb
DEVICE=/proc/bus/usb/005/006
PRODUCT=781/8185/125
TYPE=0/0/0
INTERFACE=8/6/80
MODALIAS=usb:v0781p8185d0125dc00dsc00dp00ic08isc06ip50
UDEVD_EVENT=1

UDEV  [1194553271.852023] add      /class/scsi_host/host7 (scsi_host)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/scsi_host/host7
SUBSYSTEM=scsi_host
SEQNUM=2841
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host7
UDEVD_EVENT=1

UDEV  [1194553271.983749] add      /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2842
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep81

UDEV  [1194553271.993468] add      /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2843
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep02

UDEV  [1194553272.157656] add      /class/usb_device/usbdev5.6 (usb_device)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_device/usbdev5.6
SUBSYSTEM=usb_device
SEQNUM=2844
MAJOR=189
MINOR=517
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb
UDEVD_EVENT=1
USB_BUS=005
USB_DEV=006
DEVNAME=/dev/bus/usb/005/006

UEVENT[1194553276.397243] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host7/target7:0:0/7:0:0:0 (scsi)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host7/target7:0:0/7:0:0:0
SUBSYSTEM=scsi
SEQNUM=2845
PHYSDEVBUS=scsi
MODALIAS=scsi:t-0x00

UEVENT[1194553276.397301] add      /class/scsi_disk/7:0:0:0 (scsi_disk)
ACTION=add
DEVPATH=/class/scsi_disk/7:0:0:0
SUBSYSTEM=scsi_disk
SEQNUM=2846
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host7/target7:0:0/7:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd

UDEV  [1194553276.979933] remove   /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
UDEV_LOG=3
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2847
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep81

UEVENT[1194553276.980040] remove   /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2848
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553276.980076] add      /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2849
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553276.980107] add      /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2850
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UDEV  [1194553276.985723] remove   /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
UDEV_LOG=3
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2848
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep02

UEVENT[1194553277.560380] remove   /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2851
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553277.560449] remove   /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2852
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553277.560506] add      /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2853
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553277.560542] add      /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2854
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553278.138327] remove   /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2855
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553278.138390] remove   /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2856
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553278.138439] add      /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2857
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553278.138471] add      /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2858
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553278.716804] remove   /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2859
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553278.716828] remove   /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2860
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553278.716837] add      /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2861
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553278.716846] add      /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2862
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553279.292422] remove   /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2863
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553279.292445] remove   /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2864
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553279.292454] add      /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2865
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553279.292463] add      /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2866
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UDEV  [1194553279.432217] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host7/target7:0:0/7:0:0:0 (scsi)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host7/target7:0:0/7:0:0:0
SUBSYSTEM=scsi
SEQNUM=2845
PHYSDEVBUS=scsi
MODALIAS=scsi:t-0x00
UDEVD_EVENT=1

UDEV  [1194553279.435571] add      /class/scsi_disk/7:0:0:0 (scsi_disk)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/scsi_disk/7:0:0:0
SUBSYSTEM=scsi_disk
SEQNUM=2846
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host7/target7:0:0/7:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd
UDEVD_EVENT=1

UDEV  [1194553279.436809] add      /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2849
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep81

UDEV  [1194553279.438465] add      /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2850
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep02

UDEV  [1194553279.440339] remove   /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
UDEV_LOG=3
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2851
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep81

UDEV  [1194553279.461407] remove   /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
UDEV_LOG=3
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2852
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep02

UDEV  [1194553279.463120] add      /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2853
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep81

UDEV  [1194553279.474227] add      /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2854
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep02

UDEV  [1194553279.475694] remove   /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
UDEV_LOG=3
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2855
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep81

UDEV  [1194553279.480570] remove   /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
UDEV_LOG=3
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2856
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep02

UDEV  [1194553279.482636] add      /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2857
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep81

UDEV  [1194553279.523664] add      /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2858
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep02

UDEV  [1194553279.525782] remove   /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
UDEV_LOG=3
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2859
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep81

UDEV  [1194553279.527226] remove   /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
UDEV_LOG=3
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2860
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep02

UDEV  [1194553279.529695] add      /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2861
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep81

UDEV  [1194553279.531916] add      /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2862
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep02

UDEV  [1194553279.533730] remove   /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
UDEV_LOG=3
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2863
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep81

UDEV  [1194553279.535165] remove   /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
UDEV_LOG=3
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2864
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep02

UDEV  [1194553279.546005] add      /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2865
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep81

UDEV  [1194553279.547416] add      /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2866
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep02

UEVENT[1194553279.867894] remove   /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2867
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553279.867925] remove   /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2868
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553279.867934] add      /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2869
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553279.867943] add      /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2870
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UDEV  [1194553279.870061] remove   /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
UDEV_LOG=3
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2867
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep81

UDEV  [1194553279.871527] remove   /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
UDEV_LOG=3
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2868
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep02

UDEV  [1194553279.873435] add      /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2869
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep81

UDEV  [1194553279.875036] add      /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2870
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep02

UEVENT[1194553280.443939] remove   /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2871
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553280.443962] remove   /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2872
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553280.443977] add      /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2873
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UEVENT[1194553280.443986] add      /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2874
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage

UDEV  [1194553280.446897] remove   /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
UDEV_LOG=3
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2871
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep81

UDEV  [1194553280.448353] remove   /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
UDEV_LOG=3
ACTION=remove
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2872
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep02

UDEV  [1194553280.450439] add      /class/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep81
SUBSYSTEM=usb_endpoint
SEQNUM=2873
MAJOR=254
MINOR=13
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep81

UDEV  [1194553280.451887] add      /class/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/usb_endpoint/usbdev5.6_ep02
SUBSYSTEM=usb_endpoint
SEQNUM=2874
MAJOR=254
MINOR=14
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0
PHYSDEVBUS=usb
PHYSDEVDRIVER=usb-storage
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.6_ep02

UEVENT[1194553280.772065] add      /block/sdb (block)
ACTION=add
DEVPATH=/block/sdb
SUBSYSTEM=block
SEQNUM=2875
MINOR=16
MAJOR=8
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host7/target7:0:0/7:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd

UEVENT[1194553280.774723] add      /block/sdb/sdb1 (block)
ACTION=add
DEVPATH=/block/sdb/sdb1
SUBSYSTEM=block
SEQNUM=2876
MINOR=17
MAJOR=8
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host7/target7:0:0/7:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd

UEVENT[1194553280.774760] add      /class/scsi_device/7:0:0:0 (scsi_device)
ACTION=add
DEVPATH=/class/scsi_device/7:0:0:0
SUBSYSTEM=scsi_device
SEQNUM=2877
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host7/target7:0:0/7:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd

UEVENT[1194553280.774784] add      /class/scsi_generic/sg2 (scsi_generic)
ACTION=add
DEVPATH=/class/scsi_generic/sg2
SUBSYSTEM=scsi_generic
SEQNUM=2878
MAJOR=21
MINOR=2
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host7/target7:0:0/7:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd

UDEV  [1194553280.824998] add      /class/scsi_device/7:0:0:0 (scsi_device)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/scsi_device/7:0:0:0
SUBSYSTEM=scsi_device
SEQNUM=2877
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host7/target7:0:0/7:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd
UDEVD_EVENT=1

UDEV  [1194553280.878300] add      /class/scsi_generic/sg2 (scsi_generic)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/scsi_generic/sg2
SUBSYSTEM=scsi_generic
SEQNUM=2878
MAJOR=21
MINOR=2
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host7/target7:0:0/7:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd
UDEVD_EVENT=1
DEVNAME=/dev/sg2

UDEV  [1194553282.241535] add      /block/sdb (block)
UDEV_LOG=3
ACTION=add
DEVPATH=/block/sdb
SUBSYSTEM=block
SEQNUM=2875
MINOR=16
MAJOR=8
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host7/target7:0:0/7:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd
UDEVD_EVENT=1
DEVTYPE=disk
ID_VENDOR=Generic
ID_MODEL=STORAGE_DEVICE
ID_REVISION=1.25
ID_SERIAL=Generic_STORAGE_DEVICE_000136167-0:0
ID_SERIAL_SHORT=000136167
ID_TYPE=disk
ID_INSTANCE=0:0
ID_BUS=usb
ID_PATH=pci-0000:00:1d.7-usb-0:6:1.0-scsi-0:0:0:0
DEVNAME=/dev/sdb
DEVLINKS=/dev/disk/by-id/usb-Generic_STORAGE_DEVICE_000136167-0:0 /dev/disk/by-path/pci-0000:00:1d.7-usb-0:6:1.0-scsi-0:0:0:0

UDEV  [1194553283.612577] add      /block/sdb/sdb1 (block)
UDEV_LOG=3
ACTION=add
DEVPATH=/block/sdb/sdb1
SUBSYSTEM=block
SEQNUM=2876
MINOR=17
MAJOR=8
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host7/target7:0:0/7:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd
UDEVD_EVENT=1
DEVTYPE=partition
ID_VENDOR=Generic
ID_MODEL=STORAGE_DEVICE
ID_REVISION=1.25
ID_SERIAL=Generic_STORAGE_DEVICE_000136167-0:0
ID_SERIAL_SHORT=000136167
ID_TYPE=disk
ID_INSTANCE=0:0
ID_BUS=usb
ID_PATH=pci-0000:00:1d.7-usb-0:6:1.0-scsi-0:0:0:0
ID_FS_USAGE=filesystem
ID_FS_TYPE=vfat
ID_FS_VERSION=FAT16
ID_FS_UUID=2CA7-4A44
ID_FS_UUID_ENC=2CA7-4A44
ID_FS_LABEL=USB STICK
ID_FS_LABEL_ENC=USB\x20STICK
ID_FS_LABEL_SAFE=USB_STICK
DEVN
```

Then

```
lshal
```

gives

```

Dumping 98 device(s) from the Global Device List:
-------------------------------------------------
udi = '/org/freedesktop/Hal/devices/computer'
  info.addons = {'hald-addon-cpufreq', 'hald-addon-acpi'} (string list)
  info.bus = 'unknown'  (string)
  info.callouts.add = {'hal-storage-cleanup-all-mountpoints'} (string list)
  info.capabilities = {'cpufreq_control'} (string list)
  info.interfaces = {'org.freedesktop.Hal.Device.SystemPowerManagement', 'org.freedesktop.Hal.Device.CPUFreq'} (string list)
  info.product = 'Computer'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer'  (string)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_argnames = {'num_seconds_to_sleep', 'num_seconds_to_sleep', '', '', '', 'enable_power_save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_execpaths = {'hal-system-power-suspend', 'hal-system-power-suspend-hybrid', 'hal-system-power-hibernate', 'hal-system-power-shutdown', 'hal-system-power-reboot', 'hal-system-power-set-power-save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_names = {'Suspend', 'SuspendHybrid', 'Hibernate', 'Shutdown', 'Reboot', 'SetPowerSave'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_signatures = {'i', 'i', '', '', '', 'i'} (string list)
  power_management.acpi.linux.version = '20070126'  (string)
  power_management.can_hibernate = true  (bool)
  power_management.can_suspend = true  (bool)
  power_management.can_suspend_hybrid = false  (bool)
  power_management.can_suspend_to_disk = true  (bool)
  power_management.can_suspend_to_ram = true  (bool)
  power_management.is_powersave_set = false  (bool)
  power_management.type = 'acpi'  (string)
  smbios.bios.release_date = '06/24/2005'  (string)
  smbios.bios.vendor = 'Hewlett-Packard'  (string)
  smbios.bios.version = '786C3 v01.09'  (string)
  smbios.chassis.manufacturer = 'Hewlett-Packard'  (string)
  smbios.chassis.type = 'Mini Tower'  (string)
  smbios.system.manufacturer = 'Hewlett-Packard'  (string)
  smbios.system.product = 'hp workstation xw4200'  (string)
  smbios.system.serial = 'USU44003J3'  (string)
  smbios.system.uuid = '439DC7EB-A217-D911-BBDA-0A9D4F040011'  (string)
  smbios.system.version = ''  (string)
  system.chassis.manufacturer = 'Hewlett-Packard'  (string)
  system.chassis.type = 'Mini Tower'  (string)
  system.firmware.release_date = '06/24/2005'  (string)
  system.firmware.vendor = 'Hewlett-Packard'  (string)
  system.firmware.version = '786C3 v01.09'  (string)
  system.formfactor = 'desktop'  (string)
  system.hardware.product = 'hp workstation xw4200'  (string)
  system.hardware.serial = 'USU44003J3'  (string)
  system.hardware.uuid = '439DC7EB-A217-D911-BBDA-0A9D4F040011'  (string)
  system.hardware.vendor = 'Hewlett-Packard'  (string)
  system.hardware.version = ''  (string)
  system.kernel.machine = 'i686'  (string)
  system.kernel.name = 'Linux'  (string)
  system.kernel.version = '2.6.22-14-386'  (string)
  system.product = 'hp workstation xw4200 '  (string)
  system.vendor = 'Hewlett-Packard'  (string)

udi = '/org/freedesktop/Hal/devices/acpi_CPU0'
  info.capabilities = {'processor'} (string list)
  info.category = 'processor'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Intel(R) Pentium(R) 4 CPU 3.00GHz'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU0'  (string)
  linux.acpi_path = '/proc/acpi/processor/CPU0'  (string)
  linux.acpi_type = 1  (0x1)  (int)
  linux.hotplug_type = 4  (0x4)  (int)
  processor.can_throttle = true  (bool)
  processor.number = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'
  alsa.device_file = '/dev/snd/timer'  (string)
  alsa.type = 'timer'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ALSA Timer Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'  (string)
  linux.device_file = '/dev/snd/timer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/timer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'  (string)
  linux.device_file = '/dev/sequencer2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/sequencer2'  (string)
  oss.device_file = '/dev/sequencer2'  (string)
  oss.type = 'sequencer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'  (string)
  linux.device_file = '/dev/sequencer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/sequencer'  (string)
  oss.device_file = '/dev/sequencer'  (string)
  oss.type = 'sequencer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'
  alsa.device_file = '/dev/snd/seq'  (string)
  alsa.type = 'sequencer'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ALSA Sequencer Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'  (string)
  linux.device_file = '/dev/snd/seq'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/seq'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'
  button.has_state = false  (bool)
  button.type = 'power'  (string)
  info.addons = {'hald-addon-keyboard'} (string list)
  info.capabilities = {'input', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Power Button (CM)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'  (string)
  input.device = '/dev/input/event5'  (string)
  input.product = 'Power Button (CM)'  (string)
  linux.device_file = '/dev/input/event5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/class/input/input5/event5'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  button.has_state = false  (bool)
  button.type = 'power'  (string)
  info.addons = {'hald-addon-keyboard'} (string list)
  info.capabilities = {'input', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Power Button (FF)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'  (string)
  input.device = '/dev/input/event4'  (string)
  input.product = 'Power Button (FF)'  (string)
  linux.device_file = '/dev/input/event4'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/class/input/input4/event4'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Macintosh mouse button emulation'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'  (string)
  input.device = '/dev/input/event0'  (string)
  input.product = 'Macintosh mouse button emulation'  (string)
  linux.device_file = '/dev/input/event0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/class/input/input0/event0'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'
  info.bus = 'pnp'  (string)
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'System Board'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0d'  (string)
  pnp.description = 'System Board'  (string)
  pnp.id = 'PNP0c01'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'
  info.bus = 'pnp'  (string)
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0c'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'
  info.bus = 'pnp'  (string)
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0b'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0003'
  info.bus = 'pnp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'APIC'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0003'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0a'  (string)
  pnp.description = 'APIC'  (string)
  pnp.id = 'PNP0003'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0700'
  info.bus = 'pnp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PC standard floppy disk controller'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0700'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:09'  (string)
  pnp.description = 'PC standard floppy disk controller'  (string)
  pnp.id = 'PNP0700'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  info.bus = 'pnp'  (string)
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08'  (string)
  pnp.description = '16550A-compatible COM port'  (string)
  pnp.id = 'PNP0501'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  info.capabilities = {'serial'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/class/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.physical_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0401'
  info.bus = 'pnp'  (string)
  info.linux.driver = 'parport_pc'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ECP printer port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0401'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:07'  (string)
  pnp.description = 'ECP printer port'  (string)
  pnp.id = 'PNP0401'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'
  info.bus = 'pnp'  (string)
  info.linux.driver = 'i8042 kbd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:06'  (string)
  pnp.description = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  pnp.id = 'PNP0303'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0f13'
  info.bus = 'pnp'  (string)
  info.linux.driver = 'i8042 aux'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PS/2 Port for PS/2-style Mice'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0f13'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:05'  (string)
  pnp.description = 'PS/2 Port for PS/2-style Mice'  (string)
  pnp.id = 'PNP0f13'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'
  info.bus = 'pnp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT-style speaker sound'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:04'  (string)
  pnp.description = 'AT-style speaker sound'  (string)
  pnp.id = 'PNP0800'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'
  info.bus = 'pnp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT Real-Time Clock'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:03'  (string)
  pnp.description = 'AT Real-Time Clock'  (string)
  pnp.id = 'PNP0b00'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'
  info.bus = 'pnp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT DMA Controller'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:02'  (string)
  pnp.description = 'AT DMA Controller'  (string)
  pnp.id = 'PNP0200'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'
  info.bus = 'pnp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Math Coprocessor'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:01'  (string)
  pnp.description = 'Math Coprocessor'  (string)
  pnp.id = 'PNP0c04'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0a08'
  info.bus = 'pnp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (PNP0a08)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0a08'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:00'  (string)
  pnp.id = 'PNP0a08'  (string)

udi = '/org/freedesktop/Hal/devices/platform_smsc47b397_1152'
  info.bus = 'platform'  (string)
  info.linux.driver = 'smsc47b397'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (smsc47b397.1152)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_smsc47b397_1152'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/smsc47b397.1152'  (string)
  platform.id = 'smsc47b397.1152'  (string)

udi = '/org/freedesktop/Hal/devices/platform_serial8250'
  info.bus = 'platform'  (string)
  info.linux.driver = 'serial8250'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (serial8250)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/serial8250'  (string)
  platform.id = 'serial8250'  (string)

udi = '/org/freedesktop/Hal/devices/platform_pcspkr'
  info.bus = 'platform'  (string)
  info.linux.driver = 'pcspkr'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (pcspkr)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/pcspkr'  (string)
  platform.id = 'pcspkr'  (string)

udi = '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'
  info.capabilities = {'input'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  info.product = 'PC Speaker'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'  (string)
  input.device = '/dev/input/event3'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  input.physical_device = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  input.product = 'PC Speaker'  (string)
  linux.device_file = '/dev/input/event3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/class/input/input3/event3'  (string)

udi = '/org/freedesktop/Hal/devices/platform_iTCO_wdt'
  info.bus = 'platform'  (string)
  info.linux.driver = 'iTCO_wdt'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (iTCO_wdt)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_iTCO_wdt'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/iTCO_wdt'  (string)
  platform.id = 'iTCO_wdt'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042'
  info.bus = 'platform'  (string)
  info.linux.driver = 'i8042'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (i8042)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042'  (string)
  platform.id = 'i8042'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  info.bus = 'serio'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1'  (string)
  serio.description = 'i8042 AUX port'  (string)
  serio.id = 'serio1'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  info.bus = 'serio'  (string)
  info.linux.driver = 'atkbd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 KBD port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0'  (string)
  serio.description = 'i8042 KBD port'  (string)
  serio.id = 'serio0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'
  info.addons = {'hald-addon-keyboard'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  info.product = 'AT Translated Set 2 keyboard'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'  (string)
  input.device = '/dev/input/event1'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  input.physical_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  input.product = 'AT Translated Set 2 keyboard'  (string)
  linux.device_file = '/dev/input/event1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/class/input/input1/event1'  (string)

udi = '/org/freedesktop/Hal/devices/platform_eisa_0'
  info.bus = 'platform'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (eisa.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_eisa_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/eisa.0'  (string)
  platform.id = 'eisa.0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_2652'
  info.bus = 'pci'  (string)
  info.linux.driver = 'ata_piix'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801FR/FRW (ICH6R/ICH6RW) SATA Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2652'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 143  (0x8f)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2'  (string)
  pci.product = '82801FR/FRW (ICH6R/ICH6RW) SATA Controller'  (string)
  pci.product_id = 9810  (0x2652)  (int)
  pci.subsys_product_id = 12296  (0x3008)  (int)
  pci.subsys_vendor = 'Hewlett-Packard Company'  (string)
  pci.subsys_vendor_id = 4156  (0x103c)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2652_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2652'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2652_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host2'  (string)
  scsi_host.host = 2  (0x2)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2652_scsi_host_scsi_device_lun0'
  info.bus = 'scsi'  (string)
  info.linux.driver = 'sd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2652_scsi_host'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2652_scsi_host_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 2  (0x2)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'ST380013AS'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'disk'  (string)
  scsi.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST380013AS_3JVCG72C'
  block.device = '/dev/sda'  (string)
  block.is_volume = false  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST380013AS_3JVCG72C'  (string)
  info.capabilities = {'storage', 'block'} (string list)
  info.category = 'storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2652_scsi_host_scsi_device_lun0'  (string)
  info.product = 'ST380013AS'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST380013AS_3JVCG72C'  (string)
  info.vendor = 'ATA'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/block/sda'  (string)
  storage.automount_enabled_hint = false  (bool)
  storage.bus = 'scsi'  (string)
  storage.drive_type = 'disk'  (string)
  storage.firmware_version = '3.20'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = false  (bool)
  storage.model = 'ST380013AS'  (string)
  storage.no_partitions_hint = false  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/pci_8086_2652_scsi_host_scsi_device_lun0'  (string)
  storage.partitioning_scheme = 'mbr'  (string)
  storage.physical_device = '/org/freedesktop/Hal/devices/pci_8086_2652_scsi_host_scsi_device_lun0'  (string)
  storage.removable = false  (bool)
  storage.removable.media_available = true  (bool)
  storage.removable.media_size = 80026361856  (0x12a1f16000)  (uint64)
  storage.requires_eject = false  (bool)
  storage.serial = '1ATA_ST380013AS_3JVCG72C'  (string)
  storage.size = 80026361856  (0x12a1f16000)  (uint64)
  storage.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_c5af2c40_5b2d_4e12_9769_1bed3eb298a8'
  block.device = '/dev/sda5'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 5  (0x5)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST380013AS_3JVCG72C'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST380013AS_3JVCG72C'  (string)
  info.product = 'Volume (swap)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_c5af2c40_5b2d_4e12_9769_1bed3eb298a8'  (string)
  linux.fstab.mountpoint = 'none'  (string)
  linux.fstab.options = 'sw'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/block/sda/sda5'  (string)
  storage.model = ''  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'swap'  (string)
  volume.fsusage = 'other'  (string)
  volume.fsversion = '2'  (string)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount_point = ''  (string)
  volume.num_blocks = 3020157  (0x2e157d)  (int)
  volume.partition.media_size = 80026361856  (0x12a1f16000)  (uint64)
  volume.partition.number = 5  (0x5)  (int)
  volume.partition.start = 78477428736  (0x12459e8800)  (uint64)
  volume.size = 1546320384  (0x5c2afa00)  (uint64)
  volume.uuid = 'c5af2c40-5b2d-4e12-9769-1bed3eb298a8'  (string)

udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'
  block.device = '/dev/sda2'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 2  (0x2)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST380013AS_3JVCG72C'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST380013AS_3JVCG72C'  (string)
  info.product = 'Volume'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/block/sda/sda2'  (string)
  storage.model = ''  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = ''  (string)
  volume.fsusage = ''  (string)
  volume.fsversion = ''  (string)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount_point = ''  (string)
  volume.num_blocks = 2  (0x2)  (int)
  volume.partition.media_size = 80026361856  (0x12a1f16000)  (uint64)
  volume.partition.number = 2  (0x2)  (int)
  volume.partition.start = 78477396480  (0x12459e0a00)  (uint64)
  volume.size = 1024  (0x400)  (uint64)
  volume.uuid = ''  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_6b447f49_24d5_4b7f_b24a_e3c760ef62f0'
  block.device = '/dev/sda1'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 1  (0x1)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST380013AS_3JVCG72C'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST380013AS_3JVCG72C'  (string)
  info.product = 'Volume (ext3)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_6b447f49_24d5_4b7f_b24a_e3c760ef62f0'  (string)
  linux.fstab.mountpoint = '/'  (string)
  linux.fstab.options = 'defaults,errors=remount-ro'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/block/sda/sda1'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  storage.model = ''  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ext3'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = '1.0'  (string)
  volume.ignore = true  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'acl', 'user_xattr', 'data='} (string list)
  volume.mount_point = '/'  (string)
  volume.num_blocks = 153276102  (0x922cec6)  (int)
  volume.partition.flags = {'boot'} (string list)
  volume.partition.label = ''  (string)
  volume.partition.media_size = 80026361856  (0x12a1f16000)  (uint64)
  volume.partition.number = 1  (0x1)  (int)
  volume.partition.scheme = 'mbr'  (string)
  volume.partition.start = 32256  (0x7e00)  (uint64)
  volume.partition.type = '0x83'  (string)
  volume.partition.uuid = ''  (string)
  volume.size = 78477364224  (0x12459d8c00)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = '6b447f49-24d5-4b7f-b24a-e3c760ef62f0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_2652_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2652_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2652_scsi_host_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/class/scsi_generic/sg1'  (string)
  scsi_generic.device = '/dev/sg1'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266f'
  info.bus = 'pci'  (string)
  info.linux.driver = 'ata_piix'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266f'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 138  (0x8a)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1'  (string)
  pci.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller'  (string)
  pci.product_id = 9839  (0x266f)  (int)
  pci.subsys_product_id = 12296  (0x3008)  (int)
  pci.subsys_vendor = 'Hewlett-Packard Company'  (string)
  pci.subsys_vendor_id = 4156  (0x103c)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_266f_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266f'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266f_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1/host0'  (string)
  scsi_host.host = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_266f_scsi_host_scsi_device_lun0'
  info.bus = 'scsi'  (string)
  info.linux.driver = 'sr'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266f_scsi_host'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266f_scsi_host_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1/host0/target0:0:0/0:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 0  (0x0)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'COMBO SOHC-4832K'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'cdrom'  (string)
  scsi.vendor = 'LITE-ON'  (string)

udi = '/org/freedesktop/Hal/devices/storage_model_COMBO_SOHC_4832K'
  block.device = '/dev/scd0'  (string)
  block.is_volume = false  (bool)
  block.major = 11  (0xb)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_COMBO_SOHC_4832K'  (string)
  info.addons = {'hald-addon-storage'} (string list)
  info.capabilities = {'storage', 'block', 'storage.cdrom'} (string list)
  info.category = 'storage'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266f_scsi_host_scsi_device_lun0'  (string)
  info.product = 'COMBO SOHC-4832K'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_model_COMBO_SOHC_4832K'  (string)
  info.vendor = 'LITE-ON'  (string)
  linux.fstab.mountpoint = '/media/cdrom0'  (string)
  linux.fstab.options = 'user,noauto'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/block/sr0'  (string)
  org.freedesktop.Hal.Device.Storage.method_argnames = {'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Storage.method_execpaths = {'hal-storage-eject', 'hal-storage-closetray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_names = {'Eject', 'CloseTray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_signatures = {'as', 'as'} (string list)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'scsi'  (string)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.dvdplusr = false  (bool)
  storage.cdrom.dvdplusrdl = false  (bool)
  storage.cdrom.dvdplusrw = false  (bool)
  storage.cdrom.dvdplusrwdl = false  (bool)
  storage.cdrom.dvdr = false  (bool)
  storage.cdrom.dvdram = false  (bool)
  storage.cdrom.dvdrw = false  (bool)
  storage.cdrom.hddvd = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.mo = false  (bool)
  storage.cdrom.mrw = true  (bool)
  storage.cdrom.mrw_w = true  (bool)
  storage.cdrom.read_speed = 8467  (0x2113)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.support_multisession = true  (bool)
  storage.cdrom.write_speed = 0  (0x0)  (int)
  storage.cdrom.write_speeds = {} (string list)
  storage.drive_type = 'cdrom'  (string)
  storage.firmware_version = 'OQK5'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = true  (bool)
  storage.model = 'COMBO SOHC-4832K'  (string)
  storage.no_partitions_hint = true  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266f_scsi_host_scsi_device_lun0'  (string)
  storage.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266f_scsi_host_scsi_device_lun0'  (string)
  storage.removable = true  (bool)
  storage.removable.media_available = false  (bool)
  storage.requires_eject = true  (bool)
  storage.size = 0  (0x0)  (uint64)
  storage.vendor = 'LITE-ON'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266f_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266f_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266f_scsi_host_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/class/scsi_generic/sg0'  (string)
  scsi_generic.device = '/dev/sg0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_2640'
  info.bus = 'pci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801FB/FR (ICH6/ICH6R) LPC Interface Bridge'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2640'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.0'  (string)
  pci.product = '82801FB/FR (ICH6/ICH6R) LPC Interface Bridge'  (string)
  pci.product_id = 9792  (0x2640)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e'
  info.bus = 'pci'  (string)
  info.linux.driver = 'Intel ICH'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.2'  (string)
  pci.device_class = 4  (0x4)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.2'  (string)
  pci.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller'  (string)
  pci.product_id = 9838  (0x266e)  (int)
  pci.subsys_product_id = 12296  (0x3008)  (int)
  pci.subsys_vendor = 'Hewlett-Packard Company'  (string)
  pci.subsys_vendor_id = 4156  (0x103c)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_playback_4'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'Intel ICH6 with AD1981B'  (string)
  alsa.device = 4  (0x4)  (int)
  alsa.device_file = '/dev/snd/pcmC0D4p'  (string)
  alsa.device_id = 'Intel ICH6 - IEC958'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.type = 'playback'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 - IEC958 ALSA Playback Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_playback_4'  (string)
  linux.device_file = '/dev/snd/pcmC0D4p'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC0D4p'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_3'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'Intel ICH6 with AD1981B'  (string)
  alsa.device = 3  (0x3)  (int)
  alsa.device_file = '/dev/snd/pcmC0D3c'  (string)
  alsa.device_id = 'Intel ICH6 - ADC2'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.type = 'capture'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 - ADC2 ALSA Capture Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_3'  (string)
  linux.device_file = '/dev/snd/pcmC0D3c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC0D3c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_2'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'Intel ICH6 with AD1981B'  (string)
  alsa.device = 2  (0x2)  (int)
  alsa.device_file = '/dev/snd/pcmC0D2c'  (string)
  alsa.device_id = 'Intel ICH6 - MIC2 ADC'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.type = 'capture'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 - MIC2 ADC ALSA Capture Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_2'  (string)
  linux.device_file = '/dev/snd/pcmC0D2c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC0D2c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_1'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'Intel ICH6 with AD1981B'  (string)
  alsa.device = 1  (0x1)  (int)
  alsa.device_file = '/dev/snd/pcmC0D1c'  (string)
  alsa.device_id = 'Intel ICH6 - MIC ADC'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.type = 'capture'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 - MIC ADC ALSA Capture Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_1'  (string)
  linux.device_file = '/dev/snd/pcmC0D1c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC0D1c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_playback_0'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'Intel ICH6 with AD1981B'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/pcmC0D0p'  (string)
  alsa.device_id = 'Intel ICH6'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.type = 'playback'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 ALSA Playback Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_playback_0'  (string)
  linux.device_file = '/dev/snd/pcmC0D0p'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC0D0p'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_0'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'Intel ICH6 with AD1981B'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/pcmC0D0c'  (string)
  alsa.device_id = 'Intel ICH6'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.type = 'capture'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 ALSA Capture Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_0'  (string)
  linux.device_file = '/dev/snd/pcmC0D0c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC0D0c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_oss_mixer__1'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 OSS Control Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_oss_mixer__1'  (string)
  linux.device_file = '/dev/mixer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/mixer'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'Intel ICH6 with AD1981B'  (string)
  oss.device_file = '/dev/mixer'  (string)
  oss.device_id = 'Intel ICH6'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  oss.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  oss.type = 'mixer'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_oss_pcm_0_0'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 OSS PCM Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_oss_pcm_0_0'  (string)
  linux.device_file = '/dev/dsp'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/dsp'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'Intel ICH6 with AD1981B'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/dsp'  (string)
  oss.device_id = 'Intel ICH6'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  oss.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_control__1'
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'Intel ICH6 with AD1981B'  (string)
  alsa.device_file = '/dev/snd/controlC0'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  alsa.type = 'control'  (string)
  info.capabilities = {'alsa'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 with AD1981B ALSA Control Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_control__1'  (string)
  linux.device_file = '/dev/snd/controlC0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/controlC0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_oss_pcm_0'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 OSS PCM Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_oss_pcm_0'  (string)
  linux.device_file = '/dev/audio'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/audio'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'Intel ICH6 with AD1981B'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/audio'  (string)
  oss.device_id = 'Intel ICH6'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  oss.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_266e_oss_pcm_1'
  info.capabilities = {'oss'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  info.product = 'Intel ICH6 OSS PCM Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_266e_oss_pcm_1'  (string)
  linux.device_file = '/dev/adsp'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/adsp'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'Intel ICH6 with AD1981B'  (string)
  oss.device = 1  (0x1)  (int)
  oss.device_file = '/dev/adsp'  (string)
  oss.device_id = 'Intel ICH6'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  oss.physical_device = '/org/freedesktop/Hal/devices/pci_8086_266e'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_244e'
  info.bus = 'pci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801 PCI Bridge'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_244e'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 1  (0x1)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0'  (string)
  pci.product = '82801 PCI Bridge'  (string)
  pci.product_id = 9294  (0x244e)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_265c'
  info.bus = 'pci'  (string)
  info.linux.driver = 'ehci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_265c'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 32  (0x20)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7'  (string)
  pci.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller'  (string)
  pci.product_id = 9820  (0x265c)  (int)
  pci.subsys_product_id = 12296  (0x3008)  (int)
  pci.subsys_vendor = 'Hewlett-Packard Company'  (string)
  pci.subsys_vendor_id = 4156  (0x103c)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'
  info.bus = 'usb_device'  (string)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_265c'  (string)
  info.product = 'EHCI Host Controller'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'  (string)
  info.vendor = 'Linux 2.6.22-14-386 ehci_hcd'  (string)
  linux.device_file = '/dev/usb5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb5'  (string)
  usb_device.bus_number = 5  (0x5)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 1  (0x1)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb5'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 8  (0x8)  (int)
  usb_device.product = 'EHCI Host Controller'  (string)
  usb_device.product_id = 0  (0x0)  (int)
  usb_device.serial = '0000:00:1d.7'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.speed_bcd = 294912  (0x48000)  (int)
  usb_device.vendor = 'Linux 2.6.22-14-386 ehci_hcd'  (string)
  usb_device.vendor_id = 0  (0x0)  (int)
  usb_device.version = 2.0 (2) (double)
  usb_device.version_bcd = 512  (0x200)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_781_8185_000136167'
  info.bus = 'usb_device'  (string)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'  (string)
  info.product = 'Cruzer Mini'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_781_8185_000136167'  (string)
  info.vendor = 'SanDisk Corporation'  (string)
  linux.device_file = '/dev/5-6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-6'  (string)
  usb_device.bus_number = 5  (0x5)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 293  (0x125)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 6  (0x6)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-6'  (string)
  usb_device.max_power = 70  (0x46)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Cruzer Mini'  (string)
  usb_device.product_id = 33157  (0x8185)  (int)
  usb_device.serial = '000136167'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.speed_bcd = 294912  (0x48000)  (int)
  usb_device.vendor = 'SanDisk Corporation'  (string)
  usb_device.vendor_id = 1921  (0x781)  (int)
  usb_device.version = 2.0 (2) (double)
  usb_device.version_bcd = 512  (0x200)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_781_8185_000136167_usbraw'
  info.capabilities = {'usbraw'} (string list)
  info.category = 'usbraw'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_781_8185_000136167'  (string)
  info.product = 'USB Raw Device Access'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_781_8185_000136167_usbraw'  (string)
  linux.device_file = '/dev/bus/usb/005/006'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb_device'  (string)
  linux.sysfs_path = '/sys/class/usb_device/usbdev5.6'  (string)
  usbraw.device = '/dev/bus/usb/005/006'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_781_8185_000136167_if0'
  info.bus = 'usb'  (string)
  info.linux.driver = 'usb-storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_781_8185_000136167'  (string)
  info.product = 'USB Mass Storage Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_781_8185_000136167_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0'  (string)
  usb.bus_number = 5  (0x5)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 293  (0x125)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 8  (0x8)  (int)
  usb.interface.description = 'Bulk-Only'  (string)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 80  (0x50)  (int)
  usb.interface.subclass = 6  (0x6)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 6  (0x6)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0'  (string)
  usb.max_power = 70  (0x46)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Mass Storage Interface'  (string)
  usb.product_id = 33157  (0x8185)  (int)
  usb.serial = '000136167'  (string)
  usb.speed = 480.0 (480) (double)
  usb.speed_bcd = 294912  (0x48000)  (int)
  usb.vendor = 'SanDisk Corporation'  (string)
  usb.vendor_id = 1921  (0x781)  (int)
  usb.version = 2.0 (2) (double)
  usb.version_bcd = 512  (0x200)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_781_8185_000136167_if0_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_781_8185_000136167_if0'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_781_8185_000136167_if0_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host7'  (string)
  scsi_host.host = 7  (0x7)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_781_8185_000136167_if0_scsi_host_scsi_device_lun0'
  info.bus = 'scsi'  (string)
  info.linux.driver = 'sd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_781_8185_000136167_if0_scsi_host'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_781_8185_000136167_if0_scsi_host_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/host7/target7:0:0/7:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 7  (0x7)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'unknown'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_781_8185_000136167_if0_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_781_8185_000136167_if0_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_781_8185_000136167_if0_scsi_host_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/class/scsi_generic/sg2'  (string)
  scsi_generic.device = '/dev/sg2'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'
  info.capabilities = {'usbraw'} (string list)
  info.category = 'usbraw'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'  (string)
  info.product = 'USB Raw Device Access'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'  (string)
  linux.device_file = '/dev/bus/usb/005/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb_device'  (string)
  linux.sysfs_path = '/sys/class/usb_device/usbdev5.1'  (string)
  usbraw.device = '/dev/bus/usb/005/001'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'
  info.bus = 'usb'  (string)
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-0:1.0'  (string)
  usb.bus_number = 5  (0x5)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 1  (0x1)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 8  (0x8)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 0  (0x0)  (int)
  usb.serial = '0000:00:1d.7'  (string)
  usb.speed = 480.0 (480) (double)
  usb.speed_bcd = 294912  (0x48000)  (int)
  usb.vendor = 'Linux 2.6.22-14-386 ehci_hcd'  (string)
  usb.vendor_id = 0  (0x0)  (int)
  usb.version = 2.0 (2) (double)
  usb.version_bcd = 512  (0x200)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_265b'
  info.bus = 'pci'  (string)
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_265b'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3'  (string)
  pci.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4'  (string)
  pci.product_id = 9819  (0x265b)  (int)
  pci.subsys_product_id = 12296  (0x3008)  (int)
  pci.subsys_vendor = 'Hewlett-Packard Company'  (string)
  pci.subsys_vendor_id = 4156  (0x103c)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'
  info.bus = 'usb_device'  (string)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_265b'  (string)
  info.product = 'UHCI Host Controller'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'  (string)
  info.vendor = 'Linux 2.6.22-14-386 uhci_hcd'  (string)
  linux.device_file = '/dev/usb4'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb4'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb4'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = 'UHCI Host Controller'  (string)
  usb_device.product_id = 0  (0x0)  (int)
  usb_device.serial = '0000:00:1d.3'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.speed_bcd = 4608  (0x1200)  (int)
  usb_device.vendor = 'Linux 2.6.22-14-386 uhci_hcd'  (string)
  usb_device.vendor_id = 0  (0x0)  (int)
  usb_device.version = 1.1 (1.1) (double)
  usb_device.version_bcd = 272  (0x110)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'
  info.capabilities = {'usbraw'} (string list)
  info.category = 'usbraw'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'  (string)
  info.product = 'USB Raw Device Access'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'  (string)
  linux.device_file = '/dev/bus/usb/004/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb_device'  (string)
  linux.sysfs_path = '/sys/class/usb_device/usbdev4.1'  (string)
  usbraw.device = '/dev/bus/usb/004/001'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'
  info.bus = 'usb'  (string)
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb4/4-0:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb4/4-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 0  (0x0)  (int)
  usb.serial = '0000:00:1d.3'  (string)
  usb.speed = 12.0 (12) (double)
  usb.speed_bcd = 4608  (0x1200)  (int)
  usb.vendor = 'Linux 2.6.22-14-386 uhci_hcd'  (string)
  usb.vendor_id = 0  (0x0)  (int)
  usb.version = 1.1 (1.1) (double)
  usb.version_bcd = 272  (0x110)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_265a'
  info.bus = 'pci'  (string)
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_265a'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2'  (string)
  pci.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3'  (string)
  pci.product_id = 9818  (0x265a)  (int)
  pci.subsys_product_id = 12296  (0x3008)  (int)
  pci.subsys_vendor = 'Hewlett-Packard Company'  (string)
  pci.subsys_vendor_id = 4156  (0x103c)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'
  info.bus = 'usb_device'  (string)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_265a'  (string)
  info.product = 'UHCI Host Controller'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'  (string)
  info.vendor = 'Linux 2.6.22-14-386 uhci_hcd'  (string)
  linux.device_file = '/dev/usb3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb3'  (string)
  usb_device.bus_number = 3  (0x3)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb3'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = 'UHCI Host Controller'  (string)
  usb_device.product_id = 0  (0x0)  (int)
  usb_device.serial = '0000:00:1d.2'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.speed_bcd = 4608  (0x1200)  (int)
  usb_device.vendor = 'Linux 2.6.22-14-386 uhci_hcd'  (string)
  usb_device.vendor_id = 0  (0x0)  (int)
  usb_device.version = 1.1 (1.1) (double)
  usb_device.version_bcd = 272  (0x110)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'
  info.capabilities = {'usbraw'} (string list)
  info.category = 'usbraw'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'  (string)
  info.product = 'USB Raw Device Access'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'  (string)
  linux.device_file = '/dev/bus/usb/003/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb_device'  (string)
  linux.sysfs_path = '/sys/class/usb_device/usbdev3.1'  (string)
  usbraw.device = '/dev/bus/usb/003/001'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial'
  info.bus = 'usb_device'  (string)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'  (string)
  info.product = 'Optical USB Mouse'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial'  (string)
  info.vendor = 'Logitech'  (string)
  linux.device_file = '/dev/3-1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb3/3-1'  (string)
  usb_device.bus_number = 3  (0x3)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 832  (0x340)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 3  (0x3)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb3/3-1'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Optical USB Mouse'  (string)
  usb_device.product_id = 49174  (0xc016)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.speed_bcd = 336  (0x150)  (int)
  usb_device.vendor = 'Logitech'  (string)
  usb_device.vendor_id = 1133  (0x46d)  (int)
  usb_device.version = 2.0 (2) (double)
  usb_device.version_bcd = 512  (0x200)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial_usbraw'
  info.capabilities = {'usbraw'} (string list)
  info.category = 'usbraw'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial'  (string)
  info.product = 'USB Raw Device Access'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial_usbraw'  (string)
  linux.device_file = '/dev/bus/usb/003/003'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb_device'  (string)
  linux.sysfs_path = '/sys/class/usb_device/usbdev3.3'  (string)
  usbraw.device = '/dev/bus/usb/003/003'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial_if0'
  info.bus = 'usb'  (string)
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0'  (string)
  usb.bus_number = 3  (0x3)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 832  (0x340)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 3  (0x3)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0'  (string)
  usb.max_power = 100  (0x64)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 49174  (0xc016)  (int)
  usb.speed = 1.5 (1.5) (double)
  usb.speed_bcd = 336  (0x150)  (int)
  usb.vendor = 'Logitech'  (string)
  usb.vendor_id = 1133  (0x46d)  (int)
  usb.version = 2.0 (2) (double)
  usb.version_bcd = 512  (0x200)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial_if0'  (string)
  info.product = 'Logitech Optical USB Mouse'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event2'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial_if0'  (string)
  input.physical_device = '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial_if0'  (string)
  input.product = 'Logitech Optical USB Mouse'  (string)
  linux.device_file = '/dev/input/event2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/class/input/input2/event2'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'
  info.bus = 'usb'  (string)
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb3/3-0:1.0'  (string)
  usb.bus_number = 3  (0x3)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb3/3-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 0  (0x0)  (int)
  usb.serial = '0000:00:1d.2'  (string)
  usb.speed = 12.0 (12) (double)
  usb.speed_bcd = 4608  (0x1200)  (int)
  usb.vendor = 'Linux 2.6.22-14-386 uhci_hcd'  (string)
  usb.vendor_id = 0  (0x0)  (int)
  usb.version = 1.1 (1.1) (double)
  usb.version_bcd = 272  (0x110)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2659'
  info.bus = 'pci'  (string)
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2659'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1'  (string)
  pci.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2'  (string)
  pci.product_id = 9817  (0x2659)  (int)
  pci.subsys_product_id = 12296  (0x3008)  (int)
  pci.subsys_vendor = 'Hewlett-Packard Company'  (string)
  pci.subsys_vendor_id = 4156  (0x103c)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'
  info.bus = 'usb_device'  (string)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2659'  (string)
  info.product = 'UHCI Host Controller'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'  (string)
  info.vendor = 'Linux 2.6.22-14-386 uhci_hcd'  (string)
  linux.device_file = '/dev/usb2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb2'  (string)
  usb_device.bus_number = 2  (0x2)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb2'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = 'UHCI Host Controller'  (string)
  usb_device.product_id = 0  (0x0)  (int)
  usb_device.serial = '0000:00:1d.1'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.speed_bcd = 4608  (0x1200)  (int)
  usb_device.vendor = 'Linux 2.6.22-14-386 uhci_hcd'  (string)
  usb_device.vendor_id = 0  (0x0)  (int)
  usb_device.version = 1.1 (1.1) (double)
  usb_device.version_bcd = 272  (0x110)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'
  info.capabilities = {'usbraw'} (string list)
  info.category = 'usbraw'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'  (string)
  info.product = 'USB Raw Device Access'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'  (string)
  linux.device_file = '/dev/bus/usb/002/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb_device'  (string)
  linux.sysfs_path = '/sys/class/usb_device/usbdev2.1'  (string)
  usbraw.device = '/dev/bus/usb/002/001'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'
  info.bus = 'usb'  (string)
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb2/2-0:1.0'  (string)
  usb.bus_number = 2  (0x2)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb2/2-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 0  (0x0)  (int)
  usb.serial = '0000:00:1d.1'  (string)
  usb.speed = 12.0 (12) (double)
  usb.speed_bcd = 4608  (0x1200)  (int)
  usb.vendor = 'Linux 2.6.22-14-386 uhci_hcd'  (string)
  usb.vendor_id = 0  (0x0)  (int)
  usb.version = 1.1 (1.1) (double)
  usb.version_bcd = 272  (0x110)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2658'
  info.bus = 'pci'  (string)
  info.linux.driver = 'uhci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2658'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0'  (string)
  pci.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1'  (string)
  pci.product_id = 9816  (0x2658)  (int)
  pci.subsys_product_id = 12296  (0x3008)  (int)
  pci.subsys_vendor = 'Hewlett-Packard Company'  (string)
  pci.subsys_vendor_id = 4156  (0x103c)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'
  info.bus = 'usb_device'  (string)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2658'  (string)
  info.product = 'UHCI Host Controller'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'  (string)
  info.vendor = 'Linux 2.6.22-14-386 uhci_hcd'  (string)
  linux.device_file = '/dev/usb1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb1'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb1'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = 'UHCI Host Controller'  (string)
  usb_device.product_id = 0  (0x0)  (int)
  usb_device.serial = '0000:00:1d.0'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.speed_bcd = 4608  (0x1200)  (int)
  usb_device.vendor = 'Linux 2.6.22-14-386 uhci_hcd'  (string)
  usb_device.vendor_id = 0  (0x0)  (int)
  usb_device.version = 1.1 (1.1) (double)
  usb_device.version_bcd = 272  (0x110)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'
  info.capabilities = {'usbraw'} (string list)
  info.category = 'usbraw'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'  (string)
  info.product = 'USB Raw Device Access'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'  (string)
  linux.device_file = '/dev/bus/usb/001/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb_device'  (string)
  linux.sysfs_path = '/sys/class/usb_device/usbdev1.1'  (string)
  usbraw.device = '/dev/bus/usb/001/001'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'
  info.bus = 'usb'  (string)
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb1/1-0:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb1/1-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 0  (0x0)  (int)
  usb.serial = '0000:00:1d.0'  (string)
  usb.speed = 12.0 (12) (double)
  usb.speed_bcd = 4608  (0x1200)  (int)
  usb.vendor = 'Linux 2.6.22-14-386 uhci_hcd'  (string)
  usb.vendor_id = 0  (0x0)  (int)
  usb.version = 1.1 (1.1) (double)
  usb.version_bcd = 272  (0x110)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2666'
  info.bus = 'pci'  (string)
  info.linux.driver = 'pcieport-driver'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2666'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.3'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.3'  (string)
  pci.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4'  (string)
  pci.product_id = 9830  (0x2666)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_14e4_1677'
  info.bus = 'pci'  (string)
  info.linux.driver = 'tg3'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2666'  (string)
  info.product = 'NetXtreme BCM5751 Gigabit Ethernet PCI Express'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_14e4_1677'  (string)
  info.vendor = 'Broadcom Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.3/0000:80:00.0'  (string)
  pci.device_class = 2  (0x2)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.3/0000:80:00.0'  (string)
  pci.product = 'NetXtreme BCM5751 Gigabit Ethernet PCI Express'  (string)
  pci.product_id = 5751  (0x1677)  (int)
  pci.subsys_product_id = 12296  (0x3008)  (int)
  pci.subsys_vendor = 'Hewlett-Packard Company'  (string)
  pci.subsys_vendor_id = 4156  (0x103c)  (int)
  pci.vendor = 'Broadcom Corporation'  (string)
  pci.vendor_id = 5348  (0x14e4)  (int)

udi = '/org/freedesktop/Hal/devices/net_00_11_0a_9d_4f_04'
  info.capabilities = {'net', 'net.80203'} (string list)
  info.category = 'net.80203'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_14e4_1677'  (string)
  info.product = 'Networking Interface'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_11_0a_9d_4f_04'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/class/net/eth0'  (string)
  net.80203.mac_address = 73192525572  (0x110a9d4f04)  (uint64)
  net.address = '00:11:0a:9d:4f:04'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'eth0'  (string)
  net.linux.ifindex = 2  (0x2)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_14e4_1677'  (string)
  net.physical_device = '/org/freedesktop/Hal/devices/pci_14e4_1677'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_2660'
  info.bus = 'pci'  (string)
  info.linux.driver = 'pcieport-driver'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2660'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0'  (string)
  pci.product = '82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1'  (string)
  pci.product_id = 9824  (0x2660)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2585'
  info.bus = 'pci'  (string)
  info.linux.driver = 'pcieport-driver'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82925X/XE PCI Express Root Port'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2585'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0'  (string)
  pci.product = '82925X/XE PCI Express Root Port'  (string)
  pci.product_id = 9605  (0x2585)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_10de_fd'
  info.bus = 'pci'  (string)
  info.linux.driver = 'nvidia'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2585'  (string)
  info.product = 'NV37GL [Quadro PCI-E Series]'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_fd'  (string)
  info.vendor = 'nVidia Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0'  (string)
  pci.device_class = 3  (0x3)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0'  (string)
  pci.product = 'NV37GL [Quadro PCI-E Series]'  (string)
  pci.product_id = 253  (0xfd)  (int)
  pci.subsys_product_id = 533  (0x215)  (int)
  pci.subsys_vendor = 'nVidia Corporation'  (string)
  pci.subsys_vendor_id = 4318  (0x10de)  (int)
  pci.vendor = 'nVidia Corporation'  (string)
  pci.vendor_id = 4318  (0x10de)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_2584'
  info.bus = 'pci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82925X/XE Memory Controller Hub'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2584'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.product = '82925X/XE Memory Controller Hub'  (string)
  pci.product_id = 9604  (0x2584)  (int)
  pci.subsys_product_id = 12296  (0x3008)  (int)
  pci.subsys_vendor = 'Hewlett-Packard Company'  (string)
  pci.subsys_vendor_id = 4156  (0x103c)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)


Dumped 98 device(s) from the Global Device List.
------------------------------------------------

```

Then

```
dmesg
```

gives

```
[    0.000000] Linux version 2.6.22-14-386 (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 Sun Oct 14 22:36:54 GMT 2007 (Ubuntu 2.6.22-14.46-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff4000 (usable)
[    0.000000]  BIOS-e820: 000000003fff4000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000d0000000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe700
[    0.000000] Entering add_active_range(0, 0, 262132) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262132
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262132
[    0.000000] On node 0 totalpages: 262132
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32501 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00E9A10 checksum 0
[    0.000000] ACPI: RSDP 000E9A10, 0014 (r0 COMPAQ)
[    0.000000] ACPI: RSDT 3FFF4040, 0038 (r1 COMPAQ CPQ0063  20050624             0)
[    0.000000] ACPI: FACP 3FFF40EC, 0074 (r1 COMPAQ ALDERWD         1             0)
[    0.000000] ACPI: DSDT 3FFF4267, 191B (r1 COMPAQ     DSDT        1 MSFT  100000E)
[    0.000000] ACPI: FACS 3FFF4000, 0040
[    0.000000] ACPI: SSDT 3FFF5B82, 2D7F (r1 COMPAQ  PROJECT        1 MSFT  100000E)
[    0.000000] ACPI: APIC 3FFF4160, 0068 (r1 COMPAQ ALDERWD         1             0)
[    0.000000] ACPI: ASF! 3FFF41C8, 0063 (r32 COMPAQ ALDERWD         1             0)
[    0.000000] ACPI: MCFG 3FFF422B, 003C (r1 COMPAQ ALDERWD         1             0)
[    0.000000] ACPI: PM-Timer IO Port: 0xf808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:90000000)
[    0.000000] Built 1 zonelists.  Total pages: 260085
[    0.000000] Kernel command line: root=UUID=6b447f49-24d5-4b7f-b24a-e3c760ef62f0 ro quiet splash vga=795
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3000.303 MHz processor.
[   25.461780] Console: colour dummy device 80x25
[   25.462063] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   25.462383] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   25.480538] Memory: 1028172k/1048528k available (1929k kernel code, 19652k reserved, 877k data, 348k init, 131024k highmem)
[   25.480547] virtual kernel memory layout:
[   25.480548]     fixmap  : 0xfffa8000 - 0xfffff000   ( 348 kB)
[   25.480550]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   25.480551]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   25.480552]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   25.480553]       .init : 0xc03c0000 - 0xc0417000   ( 348 kB)
[   25.480554]       .data : 0xc02e25d5 - 0xc03bda04   ( 877 kB)
[   25.480555]       .text : 0xc0100000 - 0xc02e25d5   (1929 kB)
[   25.480558] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   25.480605] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   25.560557] Calibrating delay using timer specific routine.. 6005.58 BogoMIPS (lpj=12011162)
[   25.560579] Security Framework v1.0.0 initialized
[   25.560584] SELinux:  Disabled at boot.
[   25.560590] Mount-cache hash table entries: 512
[   25.560680] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   25.560687] monitor/mwait feature present.
[   25.560689] using mwait in idle threads.
[   25.560695] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   25.560697] CPU: L2 cache: 1024K
[   25.560700] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000
[   25.560708] Compat vDSO mapped to ffffe000.
[   25.560720] CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 04
[   25.560727] Checking 'hlt' instruction... OK.
[   25.577023] Early unpacking initramfs... done
[   25.861325] ACPI: Core revision 20070126
[   25.861363] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   25.864042] ENABLING IO-APIC IRQs
[   25.864205] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   26.008236] Booting paravirtualized kernel on bare hardware
[   26.008291] Time: 20:04:42  Date: 10/08/107
[   26.008308] NET: Registered protocol family 16
[   26.008374] EISA bus registered
[   26.008386] ACPI: bus type pci registered
[   26.009073] PCI: PCI BIOS revision 2.20 entry at 0xec3b8, last bus=128
[   26.009075] PCI: Using configuration type 1
[   26.009077] Setting up standard PCI resources
[   26.010317] ACPI: EC: Look up EC in DSDT
[   26.012153] ACPI: Interpreter enabled
[   26.012157] ACPI: (supports S0 S1 S3 S4 S5)
[   26.012178] ACPI: Using IOAPIC for interrupt routing
[   26.016924] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.016937] PCI: Probing PCI hardware (bus 00)
[   26.017416] PCI quirk: region f800-f87f claimed by ICH6 ACPI/GPIO/TCO
[   26.017420] PCI quirk: region fa00-fa3f claimed by ICH6 GPIO
[   26.017888] PCI: Transparent bridge - 0000:00:1e.0
[   26.017940] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.018224] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG1._PRT]
[   26.018353] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCX1._PRT]
[   26.018481] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCX4._PRT]
[   26.018609] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[   26.029409] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 14 15)
[   26.029509] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 14 15)
[   26.029606] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 14 15)
[   26.029702] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 14 15)
[   26.029799] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 14 15)
[   26.029896] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 14 15)
[   26.029993] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 14 15)
[   26.030090] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[   26.030177] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.030186] pnp: PnP ACPI init
[   26.030192] ACPI: bus type pnp registered
[   26.033146] pnp: PnP ACPI: found 14 devices
[   26.033149] ACPI: ACPI bus type pnp unregistered
[   26.033153] PnPBIOS: Disabled by ACPI PNP
[   26.033193] PCI: Using ACPI for IRQ routing
[   26.033196] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   26.587619] NET: Registered protocol family 8
[   26.587622] NET: Registered protocol family 20
[   26.587658] Time: tsc clocksource has been installed.
[   26.587685] pnp: 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[   26.587690] pnp: 00:0c: ioport range 0x400-0x41f has been reserved
[   26.587693] pnp: 00:0c: ioport range 0x420-0x43f has been reserved
[   26.587695] pnp: 00:0c: ioport range 0x440-0x45f has been reserved
[   26.587698] pnp: 00:0c: ioport range 0x460-0x47f has been reserved
[   26.587700] pnp: 00:0c: ioport range 0x480-0x48f has been reserved
[   26.587703] pnp: 00:0c: ioport range 0xf800-0xf81f has been reserved
[   26.587706] pnp: 00:0c: ioport range 0xf820-0xf83f has been reserved
[   26.587708] pnp: 00:0c: ioport range 0xf840-0xf85f has been reserved
[   26.587713] pnp: 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   26.587716] pnp: 00:0d: iomem range 0x100000-0x3fffffff could not be reserved
[   26.587719] pnp: 00:0d: iomem range 0xe8000-0xfffff could not be reserved
[   26.587722] pnp: 00:0d: iomem range 0xfec01000-0xffffffff could not be reserved
[   26.617966] PCI: Bridge: 0000:00:01.0
[   26.617968]   IO window: disabled.
[   26.617972]   MEM window: f1000000-f31fffff
[   26.617975]   PREFETCH window: e0000000-f01fffff
[   26.617979] PCI: Bridge: 0000:00:1c.0
[   26.617980]   IO window: disabled.
[   26.617984]   MEM window: disabled.
[   26.617987]   PREFETCH window: disabled.
[   26.617992] PCI: Bridge: 0000:00:1c.3
[   26.617993]   IO window: disabled.
[   26.617998]   MEM window: f0200000-f04fffff
[   26.618001]   PREFETCH window: disabled.
[   26.618005] PCI: Bridge: 0000:00:1e.0
[   26.618006]   IO window: disabled.
[   26.618010]   MEM window: disabled.
[   26.618013]   PREFETCH window: disabled.
[   26.618029] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   26.618035] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   26.618052] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   26.618069] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
[   26.618074] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   26.618084] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   26.618093] NET: Registered protocol family 2
[   26.655614] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.655678] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   26.656253] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   26.656388] TCP: Hash tables configured (established 131072 bind 65536)
[   26.656391] TCP reno registered
[   26.667721] checking if image is initramfs... it is
[   27.119200] Switched to high resolution mode on CPU 0
[   27.218562] Freeing initrd memory: 7096k freed
[   27.218887] audit: initializing netlink socket (disabled)
[   27.218898] audit(1194552282.192:1): initialized
[   27.218953] highmem bounce pool size: 64 pages
[   27.220713] VFS: Disk quotas dquot_6.5.1
[   27.220725] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   27.220805] io scheduler noop registered
[   27.220807] io scheduler anticipatory registered
[   27.220809] io scheduler deadline registered
[   27.220824] io scheduler cfq registered (default)
[   27.220901] Boot video device is 0000:01:00.0
[   27.220963] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   27.220997] assign_interrupt_mode Found MSI capability
[   27.221000] Allocate Port Service[0000:00:01.0:pcie00]
[   27.221067] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   27.221105] assign_interrupt_mode Found MSI capability
[   27.221107] Allocate Port Service[0000:00:1c.0:pcie00]
[   27.221136] Allocate Port Service[0000:00:1c.0:pcie02]
[   27.221210] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   27.221247] assign_interrupt_mode Found MSI capability
[   27.221250] Allocate Port Service[0000:00:1c.3:pcie00]
[   27.221278] Allocate Port Service[0000:00:1c.3:pcie02]
[   27.221402] isapnp: Scanning for PnP cards...
[   27.573025] isapnp: No Plug & Play device found
[   27.594983] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   27.595080] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.595746] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.596342] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   27.596499] input: Macintosh mouse button emulation as /class/input/input0
[   27.596575] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[   27.599707] serio: i8042 KBD port at 0x60,0x64 irq 1
[   27.599712] serio: i8042 AUX port at 0x60,0x64 irq 12
[   27.599867] mice: PS/2 mouse device common for all mice
[   27.599959] EISA: Probing bus 0 at eisa.0
[   27.599966] Cannot allocate resource for EISA slot 1
[   27.599988] EISA: Detected 0 cards.
[   27.600055] TCP cubic registered
[   27.600064] NET: Registered protocol family 1
[   27.600083] Using IPI Shortcut mode
[   27.600210]   Magic number: 15:266:93
[   27.600489] Freeing unused kernel memory: 348k freed
[   27.667860] input: AT Translated Set 2 keyboard as /class/input/input1
[   28.828168] AppArmor: AppArmor initialized<5>audit(1194552283.804:2):  type=1505 info="AppArmor initialized" pid=1309
[   28.838720] fuse init (API version 7.8)
[   28.843363] Failure registering capabilities with primary security module.
[   28.857104] ACPI: Processor [CPU0] (supports 8 throttling states)
[   29.368193] usbcore: registered new interface driver usbfs
[   29.368217] usbcore: registered new interface driver hub
[   29.368238] usbcore: registered new device driver usb
[   29.368952] USB Universal Host Controller Interface driver v3.0
[   29.369001] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
[   29.369011] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   29.369015] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   29.369134] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   29.369160] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00001440
[   29.369267] usb usb1: configuration #1 chosen from 1 choice
[   29.369293] hub 1-0:1.0: USB hub found
[   29.369299] hub 1-0:1.0: 2 ports detected
[   29.474798] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 18 (level, low) -> IRQ 19
[   29.474809] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   29.474813] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   29.474836] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   29.474864] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001460
[   29.474956] usb usb2: configuration #1 chosen from 1 choice
[   29.474982] hub 2-0:1.0: USB hub found
[   29.474988] hub 2-0:1.0: 2 ports detected
[   29.485101] SCSI subsystem initialized
[   29.490335] libata version 2.21 loaded.
[   29.576974] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 21 (level, low) -> IRQ 20
[   29.576984] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   29.576988] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   29.577010] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   29.577037] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00001480
[   29.577132] usb usb3: configuration #1 chosen from 1 choice
[   29.577159] hub 3-0:1.0: USB hub found
[   29.577165] hub 3-0:1.0: 2 ports detected
[   29.621802] FDC 0 is a post-1991 82077
[   29.680873] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 22 (level, low) -> IRQ 21
[   29.680885] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   29.680889] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   29.680912] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   29.680938] uhci_hcd 0000:00:1d.3: irq 21, io base 0x000014a0
[   29.681033] usb usb4: configuration #1 chosen from 1 choice
[   29.681060] hub 4-0:1.0: USB hub found
[   29.681066] hub 4-0:1.0: 2 ports detected
[   29.786160] tg3.c:v3.77 (May 31, 2007)
[   29.786184] ACPI: PCI Interrupt 0000:80:00.0[A] -> GSI 19 (level, low) -> IRQ 17
[   29.786194] PCI: Setting latency timer of device 0000:80:00.0 to 64
[   29.863772] eth0: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCI Express) 10/100/1000Base-T Ethernet 00:11:0a:9d:4f:04
[   29.863780] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   29.863783] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   29.864012] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
[   29.864023] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   29.864026] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   29.864056] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   29.864085] ehci_hcd 0000:00:1d.7: debug port 1
[   29.864090] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   29.864097] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xcfd00000
[   29.936508] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   29.936522] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.936627] usb usb5: configuration #1 chosen from 1 choice
[   29.936655] hub 5-0:1.0: USB hub found
[   29.936662] hub 5-0:1.0: 8 ports detected
[   30.040578] ata_piix 0000:00:1f.1: version 2.11
[   30.040596] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 17 (level, low) -> IRQ 22
[   30.040626] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   30.040690] scsi0 : ata_piix
[   30.040728] scsi1 : ata_piix
[   30.040787] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000114e0 irq 14
[   30.040790] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000114e8 irq 15
[   30.360363] ata1.00: ATAPI: LITE-ON COMBO SOHC-4832K, OQK5, max UDMA/44
[   30.464014] usb 3-1: new low speed USB device using uhci_hcd and address 3
[   30.532194] ata1.00: configured for UDMA/44
[   30.639147] usb 3-1: configuration #1 chosen from 1 choice
[   30.652455] usbcore: registered new interface driver hiddev
[   30.665306] input: Logitech Optical USB Mouse as /class/input/input2
[   30.665417] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.2-1
[   30.665428] usbcore: registered new interface driver usbhid
[   30.665431] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   30.699154] scsi 0:0:0:0: CD-ROM            LITE-ON  COMBO SOHC-4832K OQK5 PQ: 0 ANSI: 5
[   30.699216] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   30.851669] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 17
[   30.851700] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   30.851732] scsi2 : ata_piix
[   30.851777] scsi3 : ata_piix
[   30.851839] ata3: SATA max UDMA/133 cmd 0x00011810 ctl 0x0001182a bmdma 0x000114f0 irq 17
[   30.851842] ata4: SATA max UDMA/133 cmd 0x00011818 ctl 0x0001182e bmdma 0x000114f8 irq 17
[   31.127571] ata3.00: ATA-6: ST380013AS, 3.20, max UDMA/100
[   31.127575] ata3.00: 156301488 sectors, multi 16: LBA48 
[   31.143554] ata3.00: configured for UDMA/100
[   31.309469] scsi 2:0:0:0: Direct-Access     ATA      ST380013AS       3.20 PQ: 0 ANSI: 5
[   31.337556] sr0: scsi3-mmc drive: 0x/48x writer cd/rw xa/form2 cdda tray
[   31.337561] Uniform CD-ROM driver Revision: 3.20
[   31.337712] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   31.337960] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   31.337972] sd 2:0:0:0: [sda] Write Protect is off
[   31.337975] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.337991] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.338027] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   31.338037] sd 2:0:0:0: [sda] Write Protect is off
[   31.338039] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.338054] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.338058]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   31.342566] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   31.355257]  sda1 sda2 < sda5 >
[   31.373839] sd 2:0:0:0: [sda] Attached SCSI disk
[   31.573784] Attempting manual resume
[   31.573787] swsusp: Resume From Partition 8:5
[   31.573789] PM: Checking swsusp image.
[   31.574037] PM: Resume from disk failed.
[   31.609299] kjournald starting.  Commit interval 5 seconds
[   31.609309] EXT3-fs: mounted filesystem with ordered data mode.
[   40.956204] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.036679] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.753506] Real Time Clock Driver v1.12ac
[   41.778874] input: PC Speaker as /class/input/input3
[   41.783318] parport_pc 00:07: reported by Plug and Play ACPI
[   41.783373] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   41.802333] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[   41.802336]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[   41.802337]  you are certain that your <4>intel_rng: system has a functional
[   41.802339]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[   42.020540] iTCO_vendor_support: vendor-support=0
[   42.021534] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   42.021606] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0xf860)
[   42.021646] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   42.063712] Linux agpgart interface v0.102 (c) Dave Jones
[   42.478290] nvidia: module license 'NVIDIA' taints kernel.
[   42.750673] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   42.750683] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   42.750829] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   42.906624] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 21 (level, low) -> IRQ 20
[   42.906640] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   43.328005] intel8x0_measure_ac97_clock: measured 54915 usecs
[   43.328009] intel8x0: clocking to 48000
[   43.522120] lp0: using parport0 (interrupt-driven).
[   43.568881] smsc47b397: found SMSC LPC47B397-NC (base address 0x0480, revision 1)
[   43.599056] p4-clockmod: P4/Xeon(TM) CPU On-Demand Clock Modulation available
[   43.684385] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[   43.953553] EXT3 FS on sda1, internal journal
[   46.804338] No dock devices found.
[   46.900579] input: Power Button (FF) as /class/input/input4
[   46.904194] ACPI: Power Button (FF) [PWRF]
[   46.935588] input: Power Button (CM) as /class/input/input5
[   46.939159] ACPI: Power Button (CM) [PBTN]
[   48.895387] NET: Registered protocol family 10
[   48.895456] lo: Disabled Privacy Extensions
[   48.895490] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   49.831746] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   49.831751] tg3: eth0: Flow control is off for TX and off for RX.
[   49.832228] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   52.147466] ppdev: user-space parallel port driver
[   52.776619] audit(1194552309.345:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=6274 profile="/usr/sbin/cupsd"
[   52.890258] apm: BIOS not found.
[   65.146593] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   65.218497] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   65.237401] NFSD: starting 90-second grace period
[   66.012600] NET: Registered protocol family 17
[   66.162717] device eth0 entered promiscuous mode
[   66.162733] audit(1194552322.746:4): dev=eth0 prom=256 old_prom=0 auid=4294967295
[   68.842063] Failure registering capabilities with primary security module.
[   69.189608] Bluetooth: Core ver 2.11
[   69.189872] NET: Registered protocol family 31
[   69.189881] Bluetooth: HCI device and connection manager initialized
[   69.189887] Bluetooth: HCI socket layer initialized
[   69.254337] Bluetooth: L2CAP ver 2.8
[   69.254351] Bluetooth: L2CAP socket layer initialized
[   69.402374] Bluetooth: RFCOMM socket layer initialized
[   69.402600] Bluetooth: RFCOMM TTY layer initialized
[   69.402609] Bluetooth: RFCOMM ver 1.8
[   89.635159] eth0: no IPv6 routers present
[  140.623326] usb 5-6: new high speed USB device using ehci_hcd and address 3
[  140.762919] usb 5-6: configuration #1 chosen from 1 choice
[  141.315421] usbcore: registered new interface driver libusual
[  141.705680] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  141.706577] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  141.727044] Initializing USB Mass Storage driver...
[  141.727454] scsi4 : SCSI emulation for USB Mass Storage devices
[  141.727839] usb-storage: device found at 3
[  141.727842] usb-storage: waiting for device to settle before scanning
[  141.727985] usbcore: registered new interface driver usb-storage
[  141.728063] USB Mass Storage support registered.
[  146.721796] usb-storage: device scan complete
[  146.725199] scsi 4:0:0:0: Direct-Access     Generic  STORAGE DEVICE   1.25 PQ: 0 ANSI: 0
[  147.058646] sd 4:0:0:0: [sdb] 512000 512-byte hardware sectors (262 MB)
[  147.176638] usb 5-6: reset high speed USB device using ehci_hcd and address 3
[  147.756016] usb 5-6: reset high speed USB device using ehci_hcd and address 3
[  148.335483] usb 5-6: reset high speed USB device using ehci_hcd and address 3
[  148.914837] usb 5-6: reset high speed USB device using ehci_hcd and address 3
[  149.490252] usb 5-6: reset high speed USB device using ehci_hcd and address 3
[  150.069763] usb 5-6: reset high speed USB device using ehci_hcd and address 3
[  150.209598] sd 4:0:0:0: [sdb] Write Protect is off
[  150.209638] sd 4:0:0:0: [sdb] Mode Sense: 02 00 00 00
[  150.209663] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  150.545235] sd 4:0:0:0: [sdb] 512000 512-byte hardware sectors (262 MB)
[  150.546939] sd 4:0:0:0: [sdb] Write Protect is off
[  150.546968] sd 4:0:0:0: [sdb] Mode Sense: 02 00 00 00
[  150.546990] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  150.547038]  sdb: sdb1
[  150.551705] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  150.552089] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  529.633503] usb 5-6: USB disconnect, address 3
[  555.892240] usb 5-6: new high speed USB device using ehci_hcd and address 4
[  556.031783] usb 5-6: configuration #1 chosen from 1 choice
[  556.033059] scsi5 : SCSI emulation for USB Mass Storage devices
[  556.033453] usb-storage: device found at 4
[  556.033475] usb-storage: waiting for device to settle before scanning
[  561.027410] usb-storage: device scan complete
[  561.028419] scsi 5:0:0:0: Direct-Access     Generic  STORAGE DEVICE   1.25 PQ: 0 ANSI: 0
[  561.362560] sd 5:0:0:0: [sdb] 512000 512-byte hardware sectors (262 MB)
[  561.478474] usb 5-6: reset high speed USB device using ehci_hcd and address 4
[  562.065865] usb 5-6: reset high speed USB device using ehci_hcd and address 4
[  562.649263] usb 5-6: reset high speed USB device using ehci_hcd and address 4
[  563.232658] usb 5-6: reset high speed USB device using ehci_hcd and address 4
[  563.484439] usb 5-6: reset high speed USB device using ehci_hcd and address 4
[  564.067861] usb 5-6: reset high speed USB device using ehci_hcd and address 4
[  564.207714] sd 5:0:0:0: [sdb] Write Protect is off
[  564.207732] sd 5:0:0:0: [sdb] Mode Sense: 02 00 00 00
[  564.207741] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  564.544999] sd 5:0:0:0: [sdb] 512000 512-byte hardware sectors (262 MB)
[  564.659211] usb 5-6: reset high speed USB device using ehci_hcd and address 4
[  564.910947] usb 5-6: reset high speed USB device using ehci_hcd and address 4
[  565.494358] usb 5-6: reset high speed USB device using ehci_hcd and address 4
[  566.077761] usb 5-6: reset high speed USB device using ehci_hcd and address 4
[  566.661192] usb 5-6: reset high speed USB device using ehci_hcd and address 4
[  567.248592] usb 5-6: reset high speed USB device using ehci_hcd and address 4
[  567.384646] sd 5:0:0:0: [sdb] Write Protect is off
[  567.384661] sd 5:0:0:0: [sdb] Mode Sense: 02 00 00 00
[  567.384667] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  567.384676]  sdb: sdb1
[  567.719109] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  567.719228] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  651.549029] usb 5-6: USB disconnect, address 4
[  709.839407] usb 5-6: new high speed USB device using ehci_hcd and address 5
[  709.979617] usb 5-6: configuration #1 chosen from 1 choice
[  709.980932] scsi6 : SCSI emulation for USB Mass Storage devices
[  709.981334] usb-storage: device found at 5
[  709.981355] usb-storage: waiting for device to settle before scanning
[  714.974650] usb-storage: device scan complete
[  714.975655] scsi 6:0:0:0: Direct-Access     Generic  STORAGE DEVICE   1.25 PQ: 0 ANSI: 0
[  715.301579] sd 6:0:0:0: [sdb] 512000 512-byte hardware sectors (262 MB)
[  715.417641] usb 5-6: reset high speed USB device using ehci_hcd and address 5
[  715.993033] usb 5-6: reset high speed USB device using ehci_hcd and address 5
[  716.568501] usb 5-6: reset high speed USB device using ehci_hcd and address 5
[  717.147907] usb 5-6: reset high speed USB device using ehci_hcd and address 5
[  717.723315] usb 5-6: reset high speed USB device using ehci_hcd and address 5
[  718.302751] usb 5-6: reset high speed USB device using ehci_hcd and address 5
[  718.438546] sd 6:0:0:0: [sdb] Write Protect is off
[  718.438551] sd 6:0:0:0: [sdb] Mode Sense: 02 00 00 00
[  718.438554] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  718.766318] sd 6:0:0:0: [sdb] 512000 512-byte hardware sectors (262 MB)
[  718.882084] usb 5-6: reset high speed USB device using ehci_hcd and address 5
[  719.457503] usb 5-6: reset high speed USB device using ehci_hcd and address 5
[  720.032912] usb 5-6: reset high speed USB device using ehci_hcd and address 5
[  720.284660] usb 5-6: reset high speed USB device using ehci_hcd and address 5
[  720.864079] usb 5-6: reset high speed USB device using ehci_hcd and address 5
[  721.447498] usb 5-6: reset high speed USB device using ehci_hcd and address 5
[  721.586613] sd 6:0:0:0: [sdb] Write Protect is off
[  721.586621] sd 6:0:0:0: [sdb] Mode Sense: 02 00 00 00
[  721.586627] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  721.586633]  sdb: sdb1
[  721.920784] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  721.920869] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  854.532879] usb 5-6: USB disconnect, address 5
[ 1013.701775] usb 5-6: new high speed USB device using ehci_hcd and address 6
[ 1013.840861] usb 5-6: configuration #1 chosen from 1 choice
[ 1013.841814] scsi7 : SCSI emulation for USB Mass Storage devices
[ 1013.841980] usb-storage: device found at 6
[ 1013.841989] usb-storage: waiting for device to settle before scanning
[ 1018.837044] usb-storage: device scan complete
[ 1018.838188] scsi 7:0:0:0: Direct-Access     Generic  STORAGE DEVICE   1.25 PQ: 0 ANSI: 0
[ 1019.165441] sd 7:0:0:0: [sdb] 512000 512-byte hardware sectors (262 MB)
[ 1019.280223] usb 5-6: reset high speed USB device using ehci_hcd and address 6
[ 1019.744767] sd 7:0:0:0: [sdb] Write Protect is off
[ 1019.744789] sd 7:0:0:0: [sdb] Mode Sense: 02 00 00 00
[ 1019.744798] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1019.749138] sd 7:0:0:0: [sdb] 512000 512-byte hardware sectors (262 MB)
[ 1019.863489] usb 5-6: reset high speed USB device using ehci_hcd and address 6
[ 1020.443014] usb 5-6: reset high speed USB device using ehci_hcd and address 6
[ 1021.022268] usb 5-6: reset high speed USB device using ehci_hcd and address 6
[ 1021.597680] usb 5-6: reset high speed USB device using ehci_hcd and address 6
[ 1022.173098] usb 5-6: reset high speed USB device using ehci_hcd and address 6
[ 1022.748509] usb 5-6: reset high speed USB device using ehci_hcd and address 6
[ 1022.884370] sd 7:0:0:0: [sdb] Write Protect is off
[ 1022.884374] sd 7:0:0:0: [sdb] Mode Sense: 02 00 00 00
[ 1022.884377] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1022.884380]  sdb: sdb1
[ 1023.211327] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[ 1023.211441] sd 7:0:0:0: Attached scsi generic sg2 type 0
```

Then

```
ls -l /dev/sd*
```

gives

```
brw-rw---- 1 root disk    8,  0 2007-11-08 14:04 /dev/sda
brw-rw---- 1 root disk    8,  1 2007-11-08 14:05 /dev/sda1
brw-rw---- 1 root disk    8,  2 2007-11-08 14:04 /dev/sda2
brw-rw---- 1 root disk    8,  5 2007-11-08 14:04 /dev/sda5
brw-rw---- 1 root plugdev 8, 16 2007-11-08 14:21 /dev/sdb
brw-rw---- 1 root plugdev 8, 17 2007-11-08 14:21 /dev/sdb1
```

Then

```
id
```

gives

```
uid=1000(bill) gid=1000(bill) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(bill)
```

Then

```
id hal
```

gives

```
id: hal: No such user
```

Then

```
 id haldaemon
```

gives

```
uid=107(haldaemon) gid=114(haldaemon) groups=114(haldaemon),24(cdrom),25(floppy),46(plugdev),115(powerdev)
```

Finally,

```
uname -a
```

gives

```
Linux bill-desktop1 2.6.22-14-386 #1 Sun Oct 14 22:36:54 GMT 2007 i686 GNU/Linux
```

---

