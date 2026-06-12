---
title: "Usb to serial , cannot fin ttyUSB* in \dev"
date: 2007-04-27
forum: General Help
---

### Post by soonsoon on 2007-04-27
Hi all

I am trying to use a usb to serial convertor in ubuntu, i have plug in the device and run a lsusb in the terminal, the device is detected, but i cannot find the ttyUSB* file in the dev.

Log from var\log\messages

[ 1247.508000] usb 1-2: new full speed USB device using uhci_hcd and address 5
[ 1247.680000] usb 1-2: configuration #1 chosen from 1 choice
 [ 1247.684000] ftdi_sio 1-2:1.0: FTDI USB Serial Device converter detected
[ 1247.684000] drivers/usb/serial/ftdi_sio.c: Detected FT232BM
[ 1247.684000] usb 1-2: FTDI USB Serial Device converter now attached to ttyUSB0
[ 1247.812000] usb 1-2: usbfs: interface 0 claimed by ftdi_sio while 'brltty' sets config #1
[ 1247.816000] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[ 1247.816000] ftdi_sio 1-2:1.0: device disconnected

Can some one help me or show me now to setup for usb to serial?

Regards

---

### Post by fiatguy85 on 2007-04-29
Removing the brltty (and possibly brltty-x11) package solves the problem.  This is a package for using a braille display for the blind.

---

### Post by soonsoon on 2007-04-30
Sorry, i am a fresh window convert so i do it do that?

---

### Post by gyterpena on 2007-05-07
sudo apitude remove brltty
Be carefull it will offer you to remove ubuntu-desktop as well pres n for that option. Second option should by 
only to remove brltty and leave ubuntu-desktop and some other packages.

---

### Post by jvdl on 2007-05-31
Hi,

I have the same problem: I connected a USB device and it doesn't show up as a /dev/ttyusb*. However, it does show up as four /dev/usbdev*.*_ep** devices?!?!

I then tried to remove the brltty as you suggested. I rebooted my pc but the effect is the same: usbdev instead of ttyusb. Why is this?? How can I get one ttyusb device instead of four usbdev devices???

By the way: I am using ubuntu feisty.

---

### Post by no_martini_no on 2007-07-05
Hi everybody.
I think I'm in a big problem after installing my usb-isdn modem driver in feisty:
In my /dev directory I can't find any of ttyUSB or ttyACM devices. But I already tried with (sudo) modprobe cdc-acm command to install the modules and it makes nothing.
Don't know what to do, thanks...

---

