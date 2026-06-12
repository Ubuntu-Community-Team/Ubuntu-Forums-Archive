---
title: "TI89 in linux"
date: 2006-07-20
forum: General Help
---

### Post by sc30317 on 2006-07-20
Is there a way that one could connect a ti89 in linux, and see the files/transfer files to and fro the device? TI explorer is for windows, can you use that in wine?  Does anyone know?

---

### Post by thunderduck3141 on 2006-07-20
yes, it works in wine

---

### Post by sc30317 on 2006-07-20
with the USB drivers?

---

### Post by Pinoy915 on 2007-09-22
I've installed tilp from the repositories on Feisty 64. I tried to connect with my Ti-89 Titanium but it won't connect. I'm trying to connect using a mini USB to USB cable(like the ones you use for digital cameras) and I'm always getting this error:

ticables: err: usb_set_configuration (could not set config 1: Device or resource busy).

[PHP]carlo@carlo-desktop:~$ sudo tilp 
tilp    : TiLP - Version 6.80, (C) 1999-2005 Romain Lievin
tilp    : THIS PROGRAM COMES WITH ABSOLUTELY NO WARRANTY
tilp    : PLEASE READ THE DOCUMENTATION FOR DETAILS
tilp    : built on Mar 22 2007 00:11:53
tilp    : initialized in command line mode.
tilp    : Configuration file not found, use default values. You can create one by the 'File|Save config' command menu.
tilp    : err: msg_box: Information, Configuration file not found, use default values. You can create one by the 'File|Save config' command menu.

tilp    : setlocale: <en_US.UTF-8>
tilp    : bindtextdomain: </usr/share/locale/>
tilp    : textdomain: <tilp>
ticables: ticables library version 3.9.6
ticables: setlocale: <en_US.UTF-8>
ticables: bindtextdomain: </usr/share/locale>
ticables: textdomain: <libticables>
ticables: built for __LINUX__ target.
ticables: checking resources:
ticables:   IO_API: found at compile time (HAVE_TERMIOS_H)
ticables:   IO_ASM: not found at compile time (HAVE_ASM_IO_H).
ticables:   IO_TIPAR: found at compile time (HAVE_LINUX_TICABLE_H)
ticables:   IO_TISER: found at compile time (HAVE_LINUX_TICABLE_H)
ticables:   IO_TIUSB: found at compile time (HAVE_LINUX_TICABLE_H)
ticables:   IO_LIBUSB: found at compile time (HAVE_LIBUSB)
ticables: quick search for parallel/serial ports:
ticables:   serial port found at 0x2f8
ticables:   parallel port found at 0x378
ticables:   serial port found at 0x3f8
ticables:   serial port found at 0x9c08
ticables:   serial port found at 0x9c10
ticables: search for all ports:
ticables:   /dev/parport0 at 0x378
ticables:   /dev/ttyS0 at 0x3f8
ticables:   /dev/ttyS1 at 0x2f8
ticables:   /dev/ttyS2 at 0x9c08
ticables:   /dev/ttyS3 at 0x9c10
ticables: getting method from resources (automatic):
ticables:   check for tty usability:
ticables:     node /dev/ttyS0: exists
ticables:     permissions/user/group: -rw-rw---- root dialout
ticables:     is user can r/w on device: yes
ticables: mapping I/O...
ticables: registering cable...
ticables: list of settings:
ticables:   cable: GrayLink
ticables:   port: serial port #2
ticables:   method: direct access (api)
ticables:   device name: /dev/ttyS1
ticables:   delay value: 10
tifiles : tifiles library version 0.6.6
tifiles : setlocale: <en_US.UTF-8>
tifiles : bindtextdomain: </usr/share/locale>
tifiles : textdomain: <libtifiles>
tifiles : settings:
tifiles :   calc type: TI92
ticalcs : ticalcs library version 4.6.1
ticalcs : setlocale: <en_US.UTF-8>
ticalcs : bindtextdomain: </usr/share/locale>
ticalcs : textdomain: <libticalcs>
tifiles : settings:
tifiles :   calc type: TI92
ticalcs : settings:
ticalcs :   calc type: TI92
tilp    : initialized in GTK+ mode.
tilp    : scanning plug-ins... Done !
tilp    : scanning registry... Done !
ticables: getting method from resources (automatic):
ticables:   check for tiusb usability:
ticables:     using devfs: no
ticables:     node /dev/tiusb0: does not exists
ticables:     => you will have to create the node.
ticables:   warning: can't use IO_TIUSB
ticables:   check for lib-usb usability:
ticables:     usb filesystem (/proc/bus/usb): mounted
ticables:     node /proc/bus/usb/devices: exists
ticables:     permissions/user/group: -rw-r--r-- root root
ticables:     is user can r/w on device: yes
ticables: mapping I/O...
ticables: registering cable...
ticables: list of settings:
ticables:   cable: SilverLink
ticables:   port: USB port #1
ticables:   method: user mode (ioctl)
ticables:   device name: /dev/tiusb0
ticables:   delay value: 10
tifiles : settings:
tifiles :   calc type: TI89t
ticalcs : settings:
ticalcs :   calc type: TI89t
ticables: Found <TI89 Titanium>.
ticables: err: usb_set_configuration (could not set config 1: Device or resource busy).
[/PHP]

---

### Post by Pinoy915 on 2007-09-24
I take it that this program does not work with Ti-89 Titanium version.

---

### Post by Pinoy915 on 2007-09-29
Anyone know of any other alternative? I just want to be able to send programs to the calculator through USB.

---

### Post by bravemenrun333 on 2008-06-08
tilp2 (install with synaptic) works like a charm for me on ubuntu 8.04 with ti-89 titanium, BUT: i have tu run it with

```
sudo tilp
```

it detects my device and also the cable type, port and all. very nice!

---

