---
title: "mceusb, lirc not working with xhci in Ubuntu 13.10"
date: 2014-02-01
forum: General Help
---

### Post by sanu2 on 2014-02-01
I'm running into issues with getting my mceusb IR transmitter/receiver working in ubunutu 13.10. The issue seems to be xhci. It works on a machine that has the bios option of turning off xhci, and having the usb ports switch to ehci.  Unfortunately, my Intel Haswell NUC 4520 does not have this option in BIOS and i'm stuck with xhci. Tried unbinding the xhci driver, at which point all ports (usb3 and usb2) stop working. I was hoping that ehci would take over.

Basically when I run lirc, it creates the devices, but neither mode2, nor irw give any output. 
Has anyone else run into this issue? Can somebody please help?


Output of dmesg:
 3600.642121] usb 2-4: new full-speed USB device number 7 using xhci_hcd
[ 3600.660737] usb 2-4: New USB device found, idVendor=0471, idProduct=0815
[ 3600.660748] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3600.660753] usb 2-4: Product: eHome Infrared Transceiver
[ 3600.660757] usb 2-4: Manufacturer: Philips
[ 3600.660760] usb 2-4: SerialNumber: PH00ZHKE
[ 3600.662162] Registered IR keymap rc-rc6-mce
[ 3600.662389] input: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:14.0/usb2/2-4/2-4:1.0/rc/rc3/input15
[ 3600.662518] rc3: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:14.0/usb2/2-4/2-4:1.0/rc/rc3
[ 3600.662706] input: MCE IR Keyboard/Mouse (mceusb) as /devices/virtual/input/input16
[ 3600.662966] rc rc3: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[ 3600.662979] xhci_queue_intr_tx: 2 callbacks suppressed
[ 3600.838055] mceusb 2-4:1.0: Registered Philips eHome Infrared Transceiver with mce emulator interface version 1
[ 3600.838065] mceusb 2-4:1.0: 2 tx ports (0x0 cabled) and 2 rx sensors (0x0 active)

The only clue that something is wrong here is "xhci_queue_intr_tx: 2 callbacks suppressed"

uname -a:
Linux htpc 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:17:04 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

/etc/lirc/hardware.conf:
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="mceusb"
REMOTE_DEVICE="/dev/lirc1"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Motorola Cable box"
TRANSMITTER_MODULES="lirc_dev mceusb"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
TRANSMITTER_LIRCD_ARGS=""

---

### Post by redmcg2 on 2014-02-04
I ran in to this issue. Details and a patch are here (scroll to bottom of link):
[https://patchwork.linuxtv.org/patch/21648/](https://patchwork.linuxtv.org/patch/21648/)

You'll find instructions on how to get the linux source code, compile just the mceusb module and load your new module here:
[http://www.hack-job.org/uncategorized/recompile-a-kernel-module-example-mceusb-c/](http://www.hack-job.org/uncategorized/recompile-a-kernel-module-example-mceusb-c/)

This will fix mceusb working with a xhci usb hub (at least it did for me).

---

### Post by sanu2 on 2014-02-06
Thanks for your reply redmcg2. I applied the patch and recompiled the module. The "xhci_queue_intr_tx: 2 callbacks suppressed" errors are gone. Unfortunately, this didnt entirely work for my setup. Increased the debug level on the module and I see a "Error: urb status = -71" message in dmesg when I load the module.

dmesg output:

[ 2229.017025] mceusb: module verification failed: signature and/or required key missing - tainting kernel
[ 2229.017883] mceusb 2-7:1.0: mceusb_dev_probe called
[ 2229.017885] mceusb 2-7:1.0: acceptable interrupt outbound endpoint found
[ 2229.017886] mceusb 2-7:1.0: acceptable interrupt inbound endpoint found
[ 2229.018543] Registered IR keymap rc-rc6-mce
[ 2229.018597] input: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:14.0/usb2/2-7/2-7:1.0/rc/rc2/input17
[ 2229.018650] rc2: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:14.0/usb2/2-7/2-7:1.0/rc/rc2
[ 2229.019005] input: MCE IR Keyboard/Mouse (mceusb) as /devices/virtual/input/input18
[ 2229.019102] rc rc2: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[ 2229.019105] mceusb 2-7:1.0: Flushing receive buffers
[ 2229.019106] mceusb 2-7:1.0: receive request called (size=0x10)
[ 2229.019109] mceusb 2-7:1.0: receive request complete (res=0)
[ 2229.019111] mceusb 2-7:1.0: receive request called (size=0x2)
[ 2229.019112] mceusb 2-7:1.0: receive request complete (res=0)
[ 2229.019158] mceusb 2-7:1.0: setup answer received 0 bytes
[ 2229.019160] mceusb 2-7:1.0: Error: urb status = -71
[ 2229.032898] mceusb 2-7:1.0: receive request called (size=0x3)
[ 2229.032905] mceusb 2-7:1.0: receive request complete (res=0)
[ 2229.048973] mceusb 2-7:1.0: receive request called (size=0x2)
[ 2229.048989] mceusb 2-7:1.0: receive request complete (res=0)
[ 2229.064977] mceusb 2-7:1.0: receive request called (size=0x2)
[ 2229.064991] mceusb 2-7:1.0: receive request complete (res=0)
[ 2229.080948] mceusb 2-7:1.0: receive request called (size=0x2)
[ 2229.080964] mceusb 2-7:1.0: receive request complete (res=0)
[ 2229.096946] mceusb 2-7:1.0: receive request called (size=0x2)
[ 2229.096962] mceusb 2-7:1.0: receive request complete (res=0)
[ 2229.112957] mceusb 2-7:1.0: receive request called (size=0x2)
[ 2229.112973] mceusb 2-7:1.0: receive request complete (res=0)
[ 2229.128960] mceusb 2-7:1.0: receive request called (size=0x2)
[ 2229.128974] mceusb 2-7:1.0: receive request complete (res=0)
[ 2229.144992] mceusb 2-7:1.0: receive request called (size=0x2)
[ 2229.145006] mceusb 2-7:1.0: receive request complete (res=0)
[ 2229.160997] mceusb 2-7:1.0: receive request called (size=0x3)
[ 2229.161012] mceusb 2-7:1.0: receive request complete (res=0)
[ 2229.176984] mceusb 2-7:1.0: receive request called (size=0x3)
[ 2229.176997] mceusb 2-7:1.0: receive request complete (res=0)
[ 2229.201085] mceusb 2-7:1.0: Registered Philips eHome Infrared Transceiver with mce emulator interface version 1
[ 2229.201094] mceusb 2-7:1.0: 2 tx ports (0x0 cabled) and 2 rx sensors (0x0 active)
[ 2229.201159] usbcore: registered new interface driver mceusb

Output of lsusb -vv
Bus 002 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        16
  idVendor           0x0471 Philips (or NXP)
  idProduct          0x0815 eHome Infrared Receiver
  bcdDevice            0.00
  iManufacturer           1 Philips
  iProduct                2 eHome Infrared Transceiver
  iSerial                 3 PH00ZHKE
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               0
Device Status:     0x0001
  Self Powered

---

### Post by Matt Devo on 2014-04-20
Sanu2, I have a patch that should fix this, sent you a PM regarding testing it

---

### Post by Matt Devo on 2014-04-27
For anyone else who might need this, here's the patch (against 3.14.1): [http://pastebin.com/REqHTekE](http://pastebin.com/REqHTekE)

it's currently in the process of being reviewed/accepted into the kernel source

---

### Post by flaterichd on 2014-04-28
Sorry had to reply here, as private messages do not allow so much text :)


Unfortunately it didn't work :(

Tried all USB ports, removed all other devices etc. Still getting loads of urb status -71 messages with module debug enabled. Without patch I only get 1 urb status method, similarly to log in third post of the thread.

```
[ 1212.065219] mceusb 3-13:1.0: Error: urb status = -71
[ 1212.065256] mceusb 3-13:1.0: Error: urb status = -71
[ 1212.065336] mceusb 3-13:1.0: Error: urb status = -71
[ 1212.065415] mceusb 3-13:1.0: Error: urb status = -71
[ 1212.065495] mceusb 3-13:1.0: Error: urb status = -71

```


output of lsusb -vv

```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x8087 Intel Corp.
  idProduct          0x8000 
  bcdDevice            0.04
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              12
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts             8
  wHubCharacteristic 0x0009
    Per-port power switching
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood        0 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.13
  iManufacturer           3 Linux 3.13.0-24-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1d.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x02
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0507 highspeed power suspend enable connect
   Port 2: 0000.0100 power
Device Status:     0x0001
  Self Powered


Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x8087 Intel Corp.
  idProduct          0x8008 
  bcdDevice            0.04
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x0009
    Per-port power switching
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood        0 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.13
  iManufacturer           3 Linux 3.13.0-24-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1a.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x02
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0507 highspeed power suspend enable connect
   Port 2: 0000.0100 power
Device Status:     0x0001
  Self Powered


Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0003 3.0 root hub
  bcdDevice            3.13
  iManufacturer           3 Linux 3.13.0-24-generic xhci_hcd
  iProduct                2 xHCI Host Controller
  iSerial                 1 0000:00:14.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           31
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
        bMaxBurst               0
Hub Descriptor:
  bLength              12
  bDescriptorType      42
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  bHubDecLat          0.0 micro seconds
  wHubDelay             0 nano seconds
  DeviceRemovable    0x00
 Hub Port Status:
   Port 1: 0000.02a0 5Gbps power Rx.Detect
   Port 2: 0000.02a0 5Gbps power Rx.Detect
   Port 3: 0000.02a0 5Gbps power Rx.Detect
   Port 4: 0000.02a0 5Gbps power Rx.Detect
   Port 5: 0000.02a0 5Gbps power Rx.Detect
   Port 6: 0000.02a0 5Gbps power Rx.Detect
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength           15
  bNumDeviceCaps          1
  SuperSpeed USB Device Capability:
    bLength                10
    bDescriptorType        16
    bDevCapabilityType      3
    bmAttributes         0x02
      Latency Tolerance Messages (LTM) Supported
    wSpeedsSupported   0x0008
      Device can operate at SuperSpeed (5Gbps)
    bFunctionalitySupport   3
      Lowest fully-functional device speed is SuperSpeed (5Gbps)
    bU1DevExitLat          10 micro seconds
    bU2DevExitLat         512 micro seconds
Device Status:     0x0001
  Self Powered


Bus 003 Device 005: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x058f Alcor Micro Corp.
  idProduct          0x6362 Flash Card Reader/Writer
  bcdDevice            1.29
  iManufacturer           1 Generic
  iProduct                2 Mass Storage Device
  iSerial                 3 058F312D81B
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)


Bus 003 Device 018: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        16
  idVendor           0x0471 Philips (or NXP)
  idProduct          0x0815 eHome Infrared Receiver
  bcdDevice            0.00
  iManufacturer           1 Philips
  iProduct                2 eHome Infrared Transceiver
  iSerial                 3 PH00GK3D
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               0
Device Status:     0x0001
  Self Powered


Bus 003 Device 019: ID 04f2:0402 Chicony Electronics Co., Ltd Genius LuxeMate i200 Keyboard
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x04f2 Chicony Electronics Co., Ltd
  idProduct          0x0402 Genius LuxeMate i200 Keyboard
  bcdDevice            1.65
  iManufacturer           1 Chicony
  iProduct                2 USB Keyboard
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
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
          wDescriptorLength      65
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
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
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
          wDescriptorLength     146
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)


Bus 003 Device 006: ID 15c2:0034 SoundGraph Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x15c2 SoundGraph Inc.
  idProduct          0x0034 
  bcdDevice            0.12
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.01
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     121
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
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      50
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.13
  iManufacturer           3 Linux 3.13.0-24-generic xhci_hcd
  iProduct                2 xHCI Host Controller
  iSerial                 1 0000:00:14.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts            14
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x60
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0103 power enable connect
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
   Port 9: 0000.0503 highspeed power enable connect
   Port 10: 0000.0303 lowspeed power enable connect
   Port 11: 0000.0100 power
   Port 12: 0000.0100 power
   Port 13: 0000.0303 lowspeed power enable connect
   Port 14: 0000.0100 power
Device Status:     0x0001
  Self Powered

```

---

### Post by flaterichd on 2014-04-28
Ok, I managed to get this to work, thanks to Matt!

You definitely need kernel 3.14.1 (or above?) for this patch to work.

I installed it using this guide: [http://www.yourownlinux.com/2014/04/install-upgrade-to-linux-kernel-3-14-1-in-linux.html](http://www.yourownlinux.com/2014/04/install-upgrade-to-linux-kernel-3-14-1-in-linux.html).

---

### Post by Matt Devo on 2014-04-28
yes, definitely need 3.14+ for the patch to work.  Glad to help!

---

### Post by flaterichd on 2014-04-29
Ok I have created a DKMS package for easy installation of the patched mceusb kernel module.

Here are the steps needed to install the patched module.

PLEASE NOTE
I only tested this on my media center box (trusty 64 bit), so it can hardly be considered "production", also upgrading to unsupported kernel could bring all sorts of problems and bugs. 
DO AT YOUR OWN RISK :)

Step 1: [install kernel 3.14.1]("http://www.yourownlinux.com/2014/04/install-upgrade-to-linux-kernel-3-14-1-in-linux.html") and reboot
```

mkdir -p /tmp/kern && cd /tmp/kern
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-headers-3.14.1-031401_3.14.1-031401.201404141220_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-headers-3.14.1-031401-generic_3.14.1-031401.201404141220_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-image-3.14.1-031401-generic_3.14.1-031401.201404141220_amd64.deb
sudo dpkg -i linux-headers-3.14.1-*.deb linux-image-3.14.1-*.deb
sudo reboot

```

Step 2: install patched mceusb kernel module from [ppa]("https://launchpad.net/~tikhonov/+archive/fixes/+packages") and restart
```

sudo apt-add-repository ppa:tikhonov/fixes
sudo apt-get update
sudo apt-get install mceusb-dkms
sudo reboot

```

Step 3: optional, if you are using nvidia proprietary driver. Kernel 3.14 [screws it up]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates/+bug/1289440"), so you need to install version 331, which contains a fix.
```

sudo apt-get install nvidia-331-updates
sudo reboot

```

---

### Post by sanu2 on 2014-04-30
Thanks for the fix Matt! It worked :)
Thanks for the dkms flaterichd. As you suggested, I had to update to kernel 3.14 to get it to work.

---

### Post by tstack77 on 2014-06-26
This is an awesome find! Unfortunately I upgraded to kernel 3.15.1 to address this issue before finding this fix. I tried flaterichd's ppa patch but it throws an error. What do I need to do to make this patch work for a newer kernel? Or how do manually apply the patch (previous link broken)?

Thanks

```
The following NEW packages will be installed:
  mceusb-dkms
0 upgraded, 1 newly installed, 0 to remove and 27 not upgraded.
Need to get 16.9 kB of archives.
After this operation, 86.0 kB of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/tikhonov/fixes/ubuntu/](http://ppa.launchpad.net/tikhonov/fixes/ubuntu/) trusty/main mceusb-dkms al             l 3.14.1tikhonov0 [16.9 kB]
Fetched 16.9 kB in 0s (36.7 kB/s)
Selecting previously unselected package mceusb-dkms.
(Reading database ... 179238 files and directories currently installed.)
Preparing to unpack .../mceusb-dkms_3.14.1tikhonov0_all.deb ...
Unpacking mceusb-dkms (3.14.1tikhonov0) ...
Setting up mceusb-dkms (3.14.1tikhonov0) ...
Loading new mceusb-3.14.1tikhonov0 DKMS files...
First Installation: checking all kernels...
Building only for 3.15.1-031501-generic
Building for architecture x86_64
Building initial module for 3.15.1-031501-generic
Error! Bad return status for module build on kernel: 3.15.1-031501-generic (x86_             64)
Consult /var/lib/dkms/mceusb/3.14.1tikhonov0/build/make.log for more information             .
```

---

### Post by basszero on 2014-07-30
I first I got excited when I saw the patch got integrated in 3.16. I tried back patching JUST mceusb.c to 3.15.6 (the only delta from 3.15 to 3.16 is the patch mentioned here) and I still get the "urb status = -71" error. Perhaps there is something else in 3.16 that makes this work?

---

### Post by bdoe-att on 2014-08-24
I, too, am affected by this bug, and as far as I know, there is no way to disable xHCI in my system BIOS.

I am currently running Ubuntu 14.04.1 (Trusty) Server Edition with kernel 3.13.0-34-generic.

I just tried updating to the 3.14 kernel following the instructions here, and the installation basically threw up all over the place, leading to a kernel panic.

```
xbmc@Leo:/tmp/kern$ sudo dpkg -i linux-headers-3.14.1-*.deb linux-image-3.14.1-*.deb[sudo] password for xbmc: 
Selecting previously unselected package linux-headers-3.14.1-031401.
(Reading database ... 101464 files and directories currently installed.)
Preparing to unpack linux-headers-3.14.1-031401_3.14.1-031401.201404141220_all.deb ...
Unpacking linux-headers-3.14.1-031401 (3.14.1-031401.201404141220) ...
Selecting previously unselected package linux-headers-3.14.1-031401-generic.
Preparing to unpack linux-headers-3.14.1-031401-generic_3.14.1-031401.201404141220_amd64.deb ...
Unpacking linux-headers-3.14.1-031401-generic (3.14.1-031401.201404141220) ...
Selecting previously unselected package linux-image-3.14.1-031401-generic.
Preparing to unpack linux-image-3.14.1-031401-generic_3.14.1-031401.201404141220_amd64.deb ...
Done.
Unpacking linux-image-3.14.1-031401-generic (3.14.1-031401.201404141220) ...
Setting up linux-headers-3.14.1-031401 (3.14.1-031401.201404141220) ...
Setting up linux-headers-3.14.1-031401-generic (3.14.1-031401.201404141220) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.14.1-031401-generic /boot/vmlinuz-3.14.1-031401-generic
Error! Bad return status for module build on kernel: 3.14.1-031401-generic (x86_64)
Consult /var/lib/dkms/nvidia-304/304.117/build/make.log for more information.
Setting up linux-image-3.14.1-031401-generic (3.14.1-031401.201404141220) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.14.1-031401-generic /boot/vmlinuz-3.14.1-031401-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.14.1-031401-generic /boot/vmlinuz-3.14.1-031401-generic
Error! Bad return status for module build on kernel: 3.14.1-031401-generic (x86_64)
Consult /var/lib/dkms/nvidia-304/304.117/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.14.1-031401-generic /boot/vmlinuz-3.14.1-031401-generic
update-initramfs: Generating /boot/initrd.img-3.14.1-031401-generic
Killed
update-initramfs: failed for /boot/initrd.img-3.14.1-031401-generic with 137.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 137
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.14.1-031401-generic.postinst line 1025.
dpkg: error processing package linux-image-3.14.1-031401-generic (--install):
 subprocess installed post-installation script returned error exit status 2
```
At this point, the system locked up. Thankfully, when I rebooted, the old kernel was still intact, so it booted just fine, and everything seems to be running normally.

Does anyone know if kernel 3.14 will eventually make it to Trusty (I only install LTS releases for my server), or if a fix for mceusb with xHCI will come to the 3.13 kernel? Or am I just stuck between a rock and a hard place?

---

