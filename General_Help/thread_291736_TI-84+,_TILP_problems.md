---
title: "TI-84+, TILP problems"
date: 2006-11-02
forum: General Help
---

### Post by glaeven on 2006-11-02
I am running edgy on an i386 system.

I have a TI-84+ graphing calculator and i am trying to connect using TILP. I am sure the cable is a silverlink (usb), but i dont know anything about the different cables. when i start TILP, i have to go setup>communication. then i have to change the cable to silverlink, and the calc to 84+. when i hit ok, i get this:

> Msg: Unable to open/find a USB device.
Cause: Check that your cable is connected or not stalled. Check you rlibusb and usbfs, too.
System: Inappropriate ioctl for device (errno = 25)


then i click to see the logfile and this is what comes up:

> *** TiLP logfile (/tmp/tilp_log.2OP2HT) ***

tilp    : TiLP - Version 6.80, (C) 1999-2005 Romain Lievin
tilp    : THIS PROGRAM COMES WITH ABSOLUTELY NO WARRANTY
tilp    : PLEASE READ THE DOCUMENTATION FOR DETAILS
tilp    : built on Jun 21 2006 15:08:54
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
ticables:   IO_ASM: found at compile time (HAVE_ASM_IO_H).
ticables:   IO_TIPAR: found at compile time (HAVE_LINUX_TICABLE_H)
ticables:   IO_TISER: found at compile time (HAVE_LINUX_TICABLE_H)
ticables:   IO_TIUSB: found at compile time (HAVE_LINUX_TICABLE_H)
ticables:   IO_LIBUSB: found at compile time (HAVE_LIBUSB)
ticables: quick search for parallel/serial ports:
ticables:   parallel port found at 0x378
ticables:   serial port found at 0x3f8
ticables:   parallel port found at 0x778
ticables: search for all ports:
ticables:   /dev/parport0 at 0x378
ticables:   /dev/ttyS0 at 0x3f8
ticables:   /dev/ttyS1 at 0x1838
ticables:   /dev/ttyS2 at 0x3e8
ticables:   /dev/ttyS3 at 0x2e8
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
ticables:     node /dev/tiusb0: exists
ticables:     permissions/user/group: -rw-rw-rw- root root
ticables:     is user can r/w on device: yes
ticables:     module: not loaded
ticables:     => check the module exists (either as module, either as built-in)
ticables:     => add an entry into your modutils file to automatically load it
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
tifiles :   calc type: TI84+
ticalcs : settings:
ticalcs :   calc type: TI84

i cant really tell whats wrong. any ideas?

---

### Post by jsandys on 2006-11-03
It looks like you are trying to use the tiusb module.  According to the TiLP web site, you should be using TiLP2 which uses libusb.

[http://lpg.ticalc.org/prj_tilp/news.html](http://lpg.ticalc.org/prj_tilp/news.html)

Adding modules to the kernel is beyond my expertise.
 
Did you get TiLP from the Ubuntu repository?  If so someone should backport TiLP2, because it uses a usb library instead of a kernel module.

---

