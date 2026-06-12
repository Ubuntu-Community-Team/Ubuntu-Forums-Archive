---
title: "Can't pair Dualshock 3 controller via bluettoth"
date: 2014-11-06
forum: General Help
---

### Post by El_Rodro on 2014-11-06
Hello,

I am following the instructions from [https://help.ubuntu.com/community/Sixaxis](https://help.ubuntu.com/community/Sixaxis) to use the PS3 controller, but i am unable to make it work.

The pairing with the USB cable goes fine, and it writes the BT controller mac address in the controller correctly. However, when doing the [COLOR=#333333][FONT=UbuntuMono]sixad --start[/FONT][/COLOR] the message to press the PS button apperar but when i do that, nothing happens.

Looking at the syslog, i see some odd lines there:

```
Nov  6 22:47:30 HTPC bluetoothd[3838]: Bluetooth daemon 4.101Nov  6 22:47:30 HTPC bluetoothd[3839]: Starting SDP server
Nov  6 22:47:30 HTPC bluetoothd[3839]: **Not enough free handles to register service**
Nov  6 22:47:30 HTPC bluetoothd[3839]: Bluetooth Management interface initialized
Nov  6 22:47:30 HTPC bluetoothd[3839]: Adapter /org/bluez/3838/hci0 has been enabled
Nov  6 22:47:30 HTPC bluetoothd[3839]: **Unknown command complete for opcode 19**
Nov  6 22:47:32 HTPC sixad-bin[3849]: started
Nov  6 22:47:32 HTPC sixad-bin[3849]: sixad started, press the PS button now

```

I googled for that error but i didn't get any meaningful results. I guess there's some easy fix for this, but it escapes my current knowledge. Any help will be appreciated!

Rodro

Some info about my setup:

```
rodro@HTPC:~$ uname -a
Linux HTPC 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


rodro@HTPC:~$ dpkg -s bluez
Package: bluez
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 2539
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Version: 4.101-0ubuntu13
Replaces: bluez-audio (<= 3.36-3), bluez-input, bluez-network, bluez-serial, bluez-utils (<= 3.36-3), udev (<< 170-1)
Depends: libc6 (>= 2.15), libdbus-1-3 (>= 1.1.1), libglib2.0-0 (>= 2.28.0), libreadline6 (>= 6.0), libudev1 (>= 183), libusb-0.1-4 (>= 2:0.1.12), sysv-rc (>= 2.88dsf-24) | file-rc (>= 0.8.16), module-init-tools, udev (>= 170-1), lsb-base, dbus, python3-dbus
Suggests: bluez-hcidump
Breaks: udev (<< 170-1)
Conflicts: bluez-audio (<= 3.36-3), bluez-utils (<= 3.36-3)
Conffiles:
 /etc/bluetooth/main.conf 4c5ea920c35ec67225e01832e3276516
 /etc/bluetooth/proximity.conf b75823a140e00905d41465c380bf89fe
 /etc/bluetooth/serial.conf 5dcc15dd1153ddebbd41612da9b642e5
 /etc/bluetooth/audio.conf 6bc1fef4f5fe083d34e953ec3dd70bfd
 /etc/bluetooth/input.conf 4bebcedeed8770b1aea07eefc5c35a52
 /etc/bluetooth/network.conf 0c7497c405b963382ff71789d0730abd
 /etc/bluetooth/rfcomm.conf 0a87d3eddd29683c1456688907e67b4f
 /etc/init.d/bluetooth 6381b89fd1996a2d827e0e81f553477a
 /etc/dbus-1/system.d/bluetooth.conf ab36f00296c5d1f7ce78db671fb4338a
 /etc/init/bluetooth.conf e6b0122c1e5cd56016859a0767a8cfcb
Description: Bluetooth tools and daemons
 This package contains tools and system daemons for using Bluetooth devices.
 .
 BlueZ is the official Linux Bluetooth protocol stack. It is an Open Source
 project distributed under GNU General Public License (GPL).
Homepage: http://www.bluez.org
Original-Maintainer: Debian Bluetooth Maintainers <pkg-bluetooth-maintainers@lists.alioth.debian.org>

```

The bluetooth is the onboard controller in a GA-H77N-Wifi mobo.

---

