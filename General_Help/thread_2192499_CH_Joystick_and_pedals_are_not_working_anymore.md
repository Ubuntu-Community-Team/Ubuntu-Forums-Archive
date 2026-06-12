---
title: "CH Joystick and pedals are not working anymore"
date: 2013-12-08
forum: General Help
---

### Post by MikeCyber on 2013-12-08
Hi
after installing 13.04 my CH joystick and pedals are not working anymore! Holy cow there's always something broken...

/dev/input/event13
   bustype : BUS_USB
   vendor  : 0x68e
   product : 0xf2
   version : 256
   name    : "CH PRODUCTS CH PRO PEDALS USB "
   phys    : "usb-0000:00:14.0-3.3/input0"
   uniq    : ""
   bits ev : EV_SYN EV_ABS

/dev/input/event14
   bustype : BUS_USB
   vendor  : 0x68e
   product : 0xff
   version : 256
   name    : "CH PRODUCTS CH FLIGHT SIM YOKE U"
   phys    : "usb-0000:00:14.0-3.4/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_ABS EV_MSC


michael@michael-Ubuntu:/lib/udev/rules.d$ cat 99*
#USB devices
#SUBSYSTEM=="usb", ATTRS{idVendor}=="c251", ATTRS{idProduct}=="2202", MODE="0666"
#SUBSYSTEM=="usb", ATTRS{idVendor}=="28de", ATTRS{idProduct}=="2202", MODE="0666"
#SUBSYSTEM=="usb", ATTRS{idVendor}=="28de", ATTRS{idProduct}=="1101", MODE="0666"
#SUBSYSTEM=="usb", ATTRS{idVendor}=="28de", ATTRS{idProduct}=="1051", MODE="0666"
# Oculus HID Sensor naming and permissioning
#KERNEL=="hidraw*", SUBSYSTEM=="hidraw", ATTRS{idVendor}=="2833", MODE="0666"
#my ch sticks
KERNEL=="event*", ATTRS{idProduct}=="00f2", ATTRS{idVendor}=="068e", MODE="0666"
KERNEL=="event*", ATTRS{idProduct}=="00ff", ATTRS{idVendor}=="068e", MODE="0666"

#SUBSYSTEM=="usb", ATTRS{idVendor}=="068e", ATTRS{idProduct}=="00f2", MODE="0666"
#SUBSYSTEM=="usb", ATTRS{idVendor}=="068e", ATTRS{idProduct}=="00ff", MODE="0666"
michael@michael-Ubuntu:/lib/udev/rules.d$ 


Thanks for help

---

