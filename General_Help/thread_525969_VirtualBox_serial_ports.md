---
title: "VirtualBox serial ports"
date: 2007-08-14
forum: General Help
---

### Post by john8791 on 2007-08-14
I am running the latest VirtualBox (1.4).  The manual says serial ports can be set up in the guest.  I'm afraid the whole named pipe thing is a little over my head.  Has anyone had any luck with this?  I tried my USB-serial adaptor but that didn't work either.  I assume it doesn't work because there is nothing to map the USB port to?  Here is from the manual:

[COLOR="Red"][I]Starting with version 1.4, VirtualBox can provide several serial ports to the guest. Up
to 4 serial ports can be configured. The guest sees a standard 16450-type serial port.
Both receiving and transmitting data is supported. On a Windows host, the data is
sent and received through a named pipe; on a Linux host, a local domain socket is
used instead. You can configure whether VirtualBox acts as a server or as a client of
such a named pipe or local domain socket.
 [COLOR="Red"] Currently, you can attach only a single host application to the named pipe or lo-
cal domain socket associated with a particular serial port. The current configuration
method is through the generic configuration facility of VBoxManage. In the future,
this may be replaced with a more convenient mechanism.
  To configure a serial port use the following 6 commands:

VBoxManage setextradata "YourVM"
    "VBoxInternal/Devices/serial/0/Config/IRQ" 4
VBoxManage setextradata "YourVM"
    "VBoxInternal/Devices/serial/0/Config/IOBase" 0x3f8
VBoxManage setextradata "YourVM"
    "VBoxInternal/Devices/serial/0/LUN#0/Driver" Char
VBoxManage setextradata "YourVM"
    "VBoxInternal/Devices/serial/0/LUN#0/AttachedDriver/Driver" NamedPipe
VBoxManage setextradata "YourVM"
    "VBoxInternal/Devices/serial/0/LUN#0/AttachedDriver/Config/Location"[/I][/COLOR]
[/COLOR]
Thanks

---

### Post by Kalibur on 2007-08-15
MY Virtualbox on gutsy does have usb support but it works fine on fiesty below is the error if gives me when I go to settings which should allow me to configure or should I saw allow me to allocate usb ports.


[B]Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND).The service might be not installed on the host computer.


Result Code: 
0x80004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {0332de0e-ce75-461f-8c6f-0fa42616404a}[/B]

Please drop me a msg if your reply has a solution to this problem, I easily lose track of my movements around threads.  Thanx over and out

---

### Post by roadkilla on 2007-09-08
1. Create a group called usbusers
2. Add yourself to this group
3. Edit the file **/etc/udev/rules.d/40-permissions.rules** (for this, you must have administrative privileges)
    3.1 Search for the following lines

    ```
# USB devices (usbfs replacement)
    SUBSYSTEM=="usb_device",                    MODE="0664"
```

    3.2 Change them to the following

    ```
# USB devices (usbfs replacement)
    SUBSYSTEM=="usb_device", GROUP="usbusers", MODE="0664"


```
and then do
```
sudo /etc/init.d/udev restart
sudo /etc/init.d/vboxdrv setup

```


Cheers

---

### Post by john8791 on 2007-09-08
You're a genius!  I had tried the usbusers thing allready but never would have known  to run "vboxdrv setup".  Now my USB-serial converter works and I can talk to my Magellan GPS.

---

### Post by hethe on 2007-09-09
to roadkilla:

thank you so much  for your reply solve the problem which trouble me so lang

---

### Post by kcy29581 on 2007-11-01
More info for you guys:

[http://www.virtualbox.org/ticket/747](http://www.virtualbox.org/ticket/747)

Basically, in the file /etc/init.d/mountdevsubfs.sh you need to edit the lines:

```
#
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb

```to look like this (removing four #'s):

```
#
     # Magic to make /proc/bus/usb work
     #
     mkdir -p /dev/bus/usb/.usbfs
     domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
     ln -s .usbfs/devices /dev/bus/usb/devices
     mount --rbind /dev/bus/usb /proc/bus/usb
 
```

Then follow the steps on the Virtualbox wiki:

[http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04](http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04)

I know it say 7.04, but the steps apply to 7.10 as well.

After this, once you have Windows running in Virtualbox, you can right-click on the USB icon in the bottom-right corner and select what USB device you want to activate. I usually ensure that any storage devices are unmounted in Ubuntu first, otherwise data loss may occur.

---

