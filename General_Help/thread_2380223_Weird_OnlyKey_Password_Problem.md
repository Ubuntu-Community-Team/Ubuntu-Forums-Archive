---
title: "Weird OnlyKey Password Problem"
date: 2017-12-14
forum: General Help
---

### Post by 5aru on 2017-12-14
I've run into a problem where my OnlyKey doesn't seem to be typing in the correct keys for some parts of the stored passwords. This is only happening within the GUI and only on my system with both of my OnlyKeys on any USB port; so it's definitely not a defective key. It was originally working just a few days ago, and I don't recall changing anything that should have effected this. 

For example (Not actual passwords):[INDENT]The correct password would be:
Ggjsr2fwy*XL#3vNr<T}RE<Q/4+4YUV:vTBq:!!HA$zZBH3fK-"pZ

And the OnlyKey is giving me:
ggjsr2fwy8Xl33vNr<t]re<q/4=4yuV;vtBq;11ha4zZBh3fk-'pZ
[/INDENT]

lsusb -v
```

Bus 001 Device 029: ID 16c0:0486 Van Ooijen Technische Informatica Teensyduino RawHID
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x16c0 Van Ooijen Technische Informatica
  idProduct          0x0486 Teensyduino RawHID
  bcdDevice            1.00
  iManufacturer           1 Teensyduino
  iProduct                2 Keyboard/RawHID
  iSerial                 3 4294967295
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           66
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      85
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      28
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
Device Status:     0x0000
  (Bus Powered)


```

cat /etc/default/keyboard
```

# KEYBOARD CONFIGURATION FILE

# Consult the keyboard(5) manual page.

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""

BACKSPACE="guess"


```

setxkbmap -print -verbose 10
```

Setting verbose level to 10
locale is C
Trying to load rules file ./rules/evdev...
Trying to load rules file /usr/share/X11/xkb/rules/evdev...
Success.
Applied rules from evdev:
rules:      evdev
model:      pc105
layout:     us
Trying to build keymap using the following components:
keycodes:   evdev+aliases(qwerty)
types:      complete
compat:     complete
symbols:    pc+us+inet(evdev)
geometry:   pc(pc105)
xkb_keymap {
    xkb_keycodes  { include "evdev+aliases(qwerty)"    };
    xkb_types     { include "complete"    };
    xkb_compat    { include "complete"    };
    xkb_symbols   { include "pc+us+inet(evdev)"    };
    xkb_geometry  { include "pc(pc105)"    };
};


```

I'm running KDE, although I've tried XFCE4 as well and I am having the same issue. Nonetheless, I've checked the keyboard settings in the respective GUIs as well and both of them are set to pc105 us (I've attached screenshots of the setup on KDE). My Keyboard on my laptop runs just find, and I'm not having any trouble with it. I've tried plugging in a USB keyboard and it's not having problems either. If anyone has any ideas about what I could try or what might be causing this, help would be greatly appreciated. :D

---

