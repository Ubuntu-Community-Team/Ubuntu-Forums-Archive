---
title: "gnokii configuration for Nokia 6230i on Ubuntu 16.04"
date: 2018-09-05
forum: General Help
---

### Post by danixeddu on 2018-09-05
Struggling to get **gnokii** to interface with my Nokia 6230i through USB Nokia cable. Got past the serial device "Permission Denied" by changing permissions "sudo chmod 777 /dev/ttyACM0" but then get either "Device or resource busy" or  "[COLOR=#ff0000][/COLOR]Initialization failed (6) - Telephone interface init failed: Function or connection type not supported by the phone or by the phone driver". Can anyone help understand what is missing? Is it an issue with the cdc-acm driver and compatibility with phonet on my particular Ubuntu build?

**gnokii --identify provides the following output:**

[INDENT]**[for connection = serial]**
GNOKII Version 0.6.31
LOG: debug mask is 0x1
Config read from file /home/****/.gnokiirc.
phone instance config:
model = AT
port = /dev/ttyACM0
connection = serial
initlength = default
serial_baudrate = 19200
serial_write_usleep = -1
handshake = software
require_dcd = 0
smsc_timeout = 10
rfcomm_channel = 0
sm_retry = 0
Initializing AT capable mobile phone ...
Serial device: opening device /dev/ttyACM0
[COLOR=#ff0000]Gnokii serial_open: open: Device or resource busy
Couldn't open ATBUS device: Device or resource busy
AT bus initialization failed (1)
Initialization failed (1)[/COLOR]
Serial device: closing device
Telephone interface init failed: Command failed.
Quitting.
Command failed.

**[for connection = phonet, dku2libusb, dlr3p, dku5, dku2, ****dau9p]**
[/INDENT]

[INDENT]GNOKII Version 0.6.31
LOG: debug mask is 0x1
Config read from file /home/danixeddu/.gnokiirc.
phone instance config:
model = AT
port = /dev/ttyACM0
connection = *phonet*
initlength = default
serial_baudrate = 19200
serial_write_usleep = -1
handshake = software
require_dcd = 0
smsc_timeout = 10
rfcomm_channel = 0
sm_retry = 0
Initializing AT capable mobile phone ...
[COLOR=#ff0000]Initialization failed (6)
Serial device: closing device
Telephone interface init failed: Function or connection type not supported by the phone or by the phone driver.[/COLOR]
Quitting.
Function or connection type not supported by the phone or by the phone driver.
[/INDENT]


**dmesg provides the following detail:**


[INDENT][23446.450136] usb 1-1.2: new full-speed USB device number 12 using ehci-pci
[23446.564904] usb 1-1.2: New USB device found, idVendor=0421, idProduct=0428
[23446.564907] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[23446.564908] usb 1-1.2: Product: Nokia 6230i
[23446.564910] usb 1-1.2: Manufacturer: Nokia
[23446.614562] cdc_acm 1-1.2:1.1: ttyACM0: USB ACM device
[/INDENT]

**gnokiirc config file looks like this (non #lines):**


[INDENT]
[global]
port = /dev/ttyACM0
model = AT
initlength = default
connection = phonet (also tried serial, dku2libusb, dlr3p, dku5, dku2, dau9p**)**
use_locking = yes
serial_baudrate = 19200
smsc_timeout = 10

[xgnokii]
allow_breakage = 0

[gnokiid]
bindir = /usr/local/sbin/

[connect_script]
TELEPHONE = 12345678

[debuging]
debug = on
rlpdebug = off
xdebug = off

[phone_fake]
port = foobar
model = fake
connection = serial

[fake_driver]
sms_inbox = /tmp/sms

[/INDENT]

---

