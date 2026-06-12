---
title: "OWFS owserver - DS9490 bus master not found"
date: 2021-08-18
forum: General Help
---

### Post by silvaphoenix on 2021-08-18
Hi,
I'm looking for some help setting up a DS9490 bus master in owserver.
I've installed owserver in Kubuntu 18.04 from the repository, version 3.1p5.
Running with the command owserver -u --debug gives the error message
<LIBUSB_ERROR_ACCESS> Could not open the USB bus master. Is there a problem with permissions?
DEFAULT: ow_usb_msg.c: (188) <LIBUSB_ERROR_ACCESS> Could not open the USB bus master. Is there a problem with permissions?
DEBUG: ow_ds9490.c: (297) Cannot open USB device 5:1
CONNECT: ow_ds9490.c: (312) No USB DS9490 bus master found
DEFAULT: owlib.c: (208) Cannot open USB bus master
DEFAULT: owlib.c: (52) No valid 1-wire buses found
DEBUG: ow_exit.c: (17) Exit code = 1
Running as root
DEBUG: ow_usb_msg.c: (200) <LIBUSB_ERROR_NOT_FOUND> Could not release kernel module
CONNECT: ow_usb_msg.c: (207) <LIBUSB_ERROR_BUSY> Failed to set configuration on USB DS9490 bus master at 1:5
DEBUG: ow_usb_msg.c: (233) Did not successfully open DS9490 1:5 -- permission problem?
DEBUG: ow_ds9490.c: (297) Cannot open USB device 5:1
CONNECT: ow_ds9490.c: (312) No USB DS9490 bus master found
DEFAULT: owlib.c: (208) Cannot open USB bus master
CONNECT: ow_usb_msg.c: (246) <LIBUSB_ERROR_NOT_FOUND> Release interface (USB) failed
DEBUG: ow_usb_msg.c: (250) <LIBUSB_ERROR_OTHER> Linux kernel driver reattach problem
Segmentation fault


The device is listed
Bus 001 Device 005: ID 04fa:2490 Dallas Semiconductor DS1490F 2-in-1 Fob, 1-Wire adapter

This is the same device as the DS9490, they share the same circuitry.

 Please can anyone help resolve this issue.
Thanks, Stephen

---

