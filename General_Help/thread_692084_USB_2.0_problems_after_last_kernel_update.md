---
title: "USB 2.0 problems after last kernel update"
date: 2008-02-09
forum: General Help
---

### Post by rvega_arg on 2008-02-09
Hi everybody... i'm having problems to print with my HP lasjerjet 1020 after the last update.

At booting time i'm getting this message (4 time before continue):

   usb 2-1: device descriptor read/64, error -110

then if i unplug and plug my printer i can see the following errors:


[   51.376000] usb 2-2: new high speed USB device using ehci_hcd and address 5
[   61.080000] eth0: no IPv6 routers present
[   66.496000] usb 2-2: device descriptor read/64, error -110
[   81.720000] usb 2-2: device descriptor read/64, error -110
[   81.940000] usb 2-2: new high speed USB device using ehci_hcd and address 6
[   97.064000] usb 2-2: device descriptor read/64, error -110
[  112.288000] usb 2-2: device descriptor read/64, error -110
[  112.504000] usb 2-2: new high speed USB device using ehci_hcd and address 7
[  117.524000] usb 2-2: device descriptor read/8, error -110
[  122.648000] usb 2-2: device descriptor read/8, error -110
[  122.868000] usb 2-2: new high speed USB device using ehci_hcd and address 8
[  127.888000] usb 2-2: device descriptor read/8, error -110
[  133.008000] usb 2-2: device descriptor read/8, error -110
[ 5664.856000] usb 2-2: new high speed USB device using ehci_hcd and address 9
[ 5679.968000] usb 2-2: device descriptor read/64, error -110
[ 5695.188000] usb 2-2: device descriptor read/64, error -110
[ 5695.404000] usb 2-2: new high speed USB device using ehci_hcd and address 10
[ 5710.520000] usb 2-2: device descriptor read/64, error -110
[ 5725.740000] usb 2-2: device descriptor read/64, error -110
[ 5725.964000] usb 2-2: new high speed USB device using ehci_hcd and address 11
[ 5730.992000] usb 2-2: device descriptor read/8, error -110
[ 5736.112000] usb 2-2: device descriptor read/8, error -110
[ 5736.328000] usb 2-2: new high speed USB device using ehci_hcd and address 12
[ 5741.356000] usb 2-2: device descriptor read/8, error -110
[ 5746.484000] usb 2-2: device descriptor read/8, error -110


i don't have idea what can be the problem... my usb mouse works without problems. 

I tried to use only the printer (without the usb mouse) but the problem is the same.

Some ideas????? :(

NOTE: my printer was working really nice before the last update. I think the las update was something about a new kernel version (2.6.22-14-generic) and some changes in hpijs i don't remember exactly.

[Ubuntu Gutsy - 32bits | HP Pavilion dv6000]

---

### Post by rvega_arg on 2008-02-09
i solve my problem.... really strange BTW...



i just unplug my printer, i restart the printer and dmsg shows:
..
[ 7773.560000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 22 if 0 alt 0 proto 2 vid 0x03F0 pid 0x2B17
[ 7773.560000] usbcore: registered new interface driver usblp
[ 7773.560000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[ 7814.292000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: removed
[ 7814.824000] audit(1202573741.998:4):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=8585 profile="/usr/sbin/cupsd"
[ 7814.880000] audit(1202573741.998:5):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=8588 profile="/usr/sbin/cupsd"
...


Then everything started to work fine again. :confused:

At least is working.

---

