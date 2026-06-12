---
title: "With 3.13 kernel, keyboard intermittently doesn't work at login screen"
date: 2014-07-12
forum: General Help
---

### Post by james_mcl on 2014-07-12
Some time ago, I installed linux-headers-generic-lts-trusty and linux-image-generic-lts-trusty on my Precise laptop. Using these to boot into kernel 3.13, although the keyboard works OK at the Grub screen, when I get to the login screen I frequently cannot enter my password or in fact do anything with the keyboard - all button presses are ignored.

("frequently" is, I'd estimate, on approximately one half of startups. If I'm rebooting, or booting up again just after a shutdown, this problem *seems* to occur less frequently than when I'm booting up at start-of-day.)

My "workaround" for a while was to drop back to 3.11; however as support for this on Precise nears end of life ([https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)) this won't be an option for much longer, so I need to either drop back to 3.2 or find a fix/better workaround.

The laptop is a Lenovo Z560 Ideapad. I don't know if the laptop's keyboard is using any sort of internal PS/2 port, so I don't know if this has anything to do with PS/2 keyboard support becoming modular in 3.13 (see [https://www.archlinux.org/news/linux-313-warning-ps2-keyboard-support-is-now-modular/](https://www.archlinux.org/news/linux-313-warning-ps2-keyboard-support-is-now-modular/)). There are a couple of other reasons why I don't think the workarounds on that page would work:

1.) They involve a module called atkbd. lsmod on 3.11 does not show any such module.
2.) I'm getting the impression - although I can't find it stated unambiguously - that the "earlymodules" kernel commandline parameter is supported on Arch Linux but not Ubuntu (not sure whether distro-specific kernel builds or Grub alterations would be the underlying cause of that.)

Can anyone suggest anything, whether workarounds, explanations or troubleshooting steps?

Thanks,

James McLaughlin.

---

### Post by james_mcl on 2014-07-13
Some of the information from hwinfo. Can someone tell me whether this means my laptop's keyboard is PS/2, USB or other? (or how to find out if this doesn't provide the necessary info)

  I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
  N: Name="AT Translated Set 2 keyboard"
  P: Phys=isa0060/serio0/input0
  S: Sysfs=/devices/platform/i8042/serio0/input/input4
  U: Uniq=
  H: Handlers=sysrq kbd event4 
  B: PROP=0
  B: EV=120013
  B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
  B: MSC=10
  B: LED=7

  P: /devices/platform/i8042/serio0/input/input4
  E: DEVPATH=/devices/platform/i8042/serio0/input/input4
  E: EV=120013
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_INPUT_KEYBOARD=1
  E: ID_PATH=platform-i8042-serio-0
  E: ID_PATH_TAG=platform-i8042-serio-0
  E: ID_SERIAL=noserial
  E: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
  E: LED=7
  E: MODALIAS=input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw
  E: MSC=10
  E: NAME="AT Translated Set 2 keyboard"
  E: PHYS="isa0060/serio0/input0"
  E: PRODUCT=11/1/1/ab41
  E: PROP=0
  E: SUBSYSTEM=input
  E: UDEV_LOG=3
  E: USEC_INITIALIZED=3696529

  P: /devices/platform/i8042/serio0/input/input4/event4
  N: input/event4
  S: input/by-path/platform-i8042-serio-0-event-kbd
  E: DEVLINKS=/dev/input/by-path/platform-i8042-serio-0-event-kbd
  E: DEVNAME=/dev/input/event4
  E: DEVPATH=/devices/platform/i8042/serio0/input/input4/event4
  E: DMI_VENDOR=LENOVO
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_INPUT_KEYBOARD=1
  E: ID_PATH=platform-i8042-serio-0
  E: ID_PATH_TAG=platform-i8042-serio-0
  E: ID_SERIAL=noserial
  E: MAJOR=13
  E: MINOR=68
  E: SUBSYSTEM=input
  E: UDEV_LOG=3
  E: USEC_INITIALIZED=3724948
  E: XKBLAYOUT=gb
  E: XKBMODEL=pc105

07: None 00.0: 0900 Keyboard controller
  [Created at misc.251]
  Unique ID: rdCR.9N+EecqykME
  Hardware Class: unknown
  Model: "Keyboard controller"
  I/O Port: 0x60 (rw)
  I/O Port: 0x64 (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

52: PS/2 00.0: 10800 Keyboard
  [Created at input.161]
  Unique ID: c3zD.+49ps10DtUF
  Hardware Class: keyboard
  Model: "AT Translated Set 2 keyboard"
  Vendor: 0x0001 
  Device: 0x0001 "AT Translated Set 2 keyboard"
  Compatible to: int 0x0211 0x0001
  Device File: /dev/input/event4
  Device Files: /dev/input/event4, /dev/input/by-path/platform-i8042-serio-0-event-kbd
  Device Number: char 13:68
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

