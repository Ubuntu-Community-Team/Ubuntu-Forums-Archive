---
title: "An IR blaster/transmitter/emitter LIRC USB-UIRT question."
date: 2016-08-18
forum: General Help
---

### Post by gilsr on 2016-08-18
Just curious if anyone has gotten the above combination to work dependably.  Ubuntu 16.04, LIRC, USB-UIRT.  Note: not concerned about sending from remote to the transceiver, just blasting. If I get a yes, I'll ask for more help, but for now, a positive response will keep me going.

Edit:
Ironically, I get it working a few minutes after posting above. Here is my hardware.conf file. Seems funny that I was concerned about the blaster and wound up commenting it out and all that matters is the remote. By the way the remote works also, at least when tested with irw.


```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="USB-UIRT"
REMOTE_MODULES=""
REMOTE_DRIVER="usb_uirt_raw"
#REMOTE_DRIVER="uirt2_raw"
REMOTE_DEVICE="/dev/irblaster"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
#TRANSMITTER="USB-UIRT2 : Motorola Cable box"
#TRANSMITTER_MODULES=""
#TRANSMITTER_DRIVER="uirt2_raw"
#TRANSMITTER_DRIVER="usb_uirt_raw"
#TRANSMITTER_DEVICE="/dev/ttyUSB0"
#TRANSMITTER_SOCKET="/run/lirc/lircd"
#TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
#TRANSMITTER_LIRCD_ARGS="-l -d /dev/ttyUSB0"

#Disable kernel support.
#Typically, lirc will disable in-kernel support for ir devices in order to
#handle them internally.  Set to false to prevent lirc from disabling this
#in-kernel support. 
#DISABLE_KERNEL_SUPPORT="true"

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"


# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

```
Notice that the device is /dev/irblaster.  It would be /dev/ttyUSB0 normally. Change the name to match the alias if you make one. I think you should using suggestion below.

make a file -
```

gksu gedit /etc/udev/rules.d/99-usb-serial.rules

```

and put something like this in it. This will keep the system from reassigning the USB device to a different port. i.e replace ttyUSB0 with ttyUSB1, thereby breaking things.
```

SUBSYSTEM=="tty", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="f850", SYMLINK+="irblaster"
```

---

