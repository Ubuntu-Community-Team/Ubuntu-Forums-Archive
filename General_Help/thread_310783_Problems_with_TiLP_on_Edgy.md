---
title: "Problems with TiLP on Edgy"
date: 2006-12-01
forum: General Help
---

### Post by ProN00b on 2006-12-01
hi, i am having problems getting tilp to work on Edgy Eft.
i am getting those errors and there is no /dev/tiusb0, solutions for creating /dev/tiusb0 with mknod that i found on this forums create it, but don't change the error.

i tested the cable on a different computer positively on windows.

lsusb -v|grep -i texas shows, so the cable should be connected correctly
```

Bus 003 Device 003: ID 0451:e001 Texas Instruments, Inc. GraphLink
  idVendor           0x0451 Texas Instruments, Inc.
  iManufacturer           1 Texas Instruments

```

From /var/log/messages
```

Dec  2 02:00:25 nerv kernel: [17180057.328000] usb 3-2: usbfs: interface 0 claimed by usbfs while 'tilp' sets config #1

```

after getting those errors in tilp
```

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
tifiles :   calc type: V200
ticalcs : settings:
ticalcs :   calc type: V200
ticables: Found <SilverLink>.
ticables: err: usb_set_configuration (could not set config 1: Device or resource busy)

```

---

### Post by ProN00b on 2006-12-02
bump

---

### Post by ProN00b on 2006-12-02
just for the archive, the solution was installing tiglusb kernel module from [http://lpg.ticalc.org/prj_usb/linux_install.html](http://lpg.ticalc.org/prj_usb/linux_install.html) manually (yes, it errored on compiling, but commenting out the conflicting lines worked (wtf haxx)).
then doing a insmod tiglusb.ko and a make devices;sh devices

---

