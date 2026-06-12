---
title: "webcam only works after hotplug although it is shown as device (ubuntu 15.04)"
date: 2015-09-19
forum: General Help
---

### Post by dieter-erich on 2015-09-19
Hi,
  I have some old webcams (mostly USB1.1) that are all showing up (under ubuntu 15.04) as devices. For example with:

'udevadm info --query=all --name=/dev/video0'


one shows up as:


P: /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/video4linux/video0
N: video0
S: v4l/by-id/usb-SQ_Tech_CO.__LTD._USB_2.0_PC_camera-video-index0
S: v4l/by-path/pci-0000:00:1d.7-usb-0:2:1.0-video-index0
E: COLORD_DEVICE=1
E: COLORD_KIND=camera
E: DEVLINKS=/dev/v4l/by-id/usb-SQ_Tech_CO.__LTD._USB_2.0_PC_camera-video-index$
E: DEVNAME=/dev/video0
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/video4linux/video0
E: ID_BUS=usb
E: ID_FOR_SEAT=video4linux-pci-0000_00_1d_7-usb-0_2_1_0
E: ID_MODEL=USB_2.0_PC_camera
E: ID_MODEL_ENC=USB\x202.0\x20PC\x20camera\x20
E: ID_MODEL_ID=930c
E: ID_PATH=pci-0000:00:1d.7-usb-0:2:1.0
E: ID_PATH_TAG=pci-0000_00_1d_7-usb-0_2_1_0
E: ID_REVISION=0100
E: ID_SERIAL=SQ_Tech_CO.__LTD._USB_2.0_PC_camera
E: ID_TYPE=generic
E: ID_USB_DRIVER=sq930x
E: ID_USB_INTERFACES=:ffffff:
E: ID_USB_INTERFACE_NUM=00
E: ID_V4L_CAPABILITIES=:capture:
E: ID_V4L_PRODUCT=USB 2.0 PC camera
E: ID_V4L_VERSION=2
E: ID_VENDOR=SQ_Tech_CO.__LTD.
E: ID_VENDOR_ENC=SQ\x20Tech\x20CO.\x2c\x20LTD.
E: ID_VENDOR_ID=2770
E: MAJOR=81
E: MINOR=0
E: SUBSYSTEM=video4linux
E: TAGS=:seat:uaccess:
E: USEC_INITIALIZED=660244

however, I can only access it (with camorama, cheese, or motion) after hotplugging it. That means, when I reboot from remote the webcam does not work any more until I come back and pull and push the usb plug! Suggestions are warmly welcome!
D-E

---

