---
title: "Udev help needed"
date: 2013-11-29
forum: General Help
---

### Post by peter.wieringa on 2013-11-29
Hi,

I've been struggling for a week a now to get a udev rule working. The syntax is correct (no errors in syslog) but the rule is not applied. I want to create a udev rule for this device:

```
looking at device '/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/ttyUSB0/tty/ttyUSB0':    KERNEL=="ttyUSB0"
    SUBSYSTEM=="tty"
    DRIVER==""


  looking at parent device '/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/ttyUSB0':
    KERNELS=="ttyUSB0"
    SUBSYSTEMS=="usb-serial"
    DRIVERS=="ftdi_sio"
    ATTRS{port_number}=="0"
    ATTRS{latency_timer}=="1"


  looking at parent device '/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0':
    KERNELS=="4-2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="ftdi_sio"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{interface}=="FT232R USB UART"


  looking at parent device '/devices/pci0000:00/0000:00:1d.2/usb4/4-2':
    KERNELS=="4-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{devpath}=="2"
    ATTRS{idVendor}=="0403"
    ATTRS{speed}=="12"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{busnum}=="4"
    ATTRS{devnum}=="2"
    ATTRS{configuration}==""
    ATTRS{bMaxPower}==" 90mA"
    ATTRS{authorized}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{maxchild}=="0"
    ATTRS{bcdDevice}=="0600"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{serial}=="A400fFkN"
    ATTRS{version}==" 2.00"
    ATTRS{urbnum}=="16"
    ATTRS{manufacturer}=="FTDI"
    ATTRS{removable}=="unknown"
    ATTRS{idProduct}=="6001"
    ATTRS{bDeviceClass}=="00"
    ATTRS{product}=="FT232R USB UART"


  looking at parent device '/devices/pci0000:00/0000:00:1d.2/usb4':
    KERNELS=="usb4"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{devpath}=="0"
    ATTRS{idVendor}=="1d6b"
    ATTRS{speed}=="12"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{authorized_default}=="1"
    ATTRS{busnum}=="4"
    ATTRS{devnum}=="1"
    ATTRS{configuration}==""
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{authorized}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{maxchild}=="2"
    ATTRS{bcdDevice}=="0305"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{serial}=="0000:00:1d.2"
    ATTRS{version}==" 1.10"
    ATTRS{urbnum}=="31"
    ATTRS{manufacturer}=="Linux 3.5.0-17-generic uhci_hcd"
    ATTRS{removable}=="unknown"
    ATTRS{idProduct}=="0001"
    ATTRS{bDeviceClass}=="09"
    ATTRS{product}=="UHCI Host Controller"


  looking at parent device '/devices/pci0000:00/0000:00:1d.2':
    KERNELS=="0000:00:1d.2"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{irq}=="18"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{broken_parity_status}=="0"
    ATTRS{class}=="0x0c0300"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{local_cpus}=="ff"
    ATTRS{device}=="0x27ca"
    ATTRS{msi_bus}==""
    ATTRS{local_cpulist}=="0-7"
    ATTRS{vendor}=="0x8086"
    ATTRS{subsystem_device}=="0x8179"


  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""



```

This my rule:

```
SUBSYSTEM=="tty", ATTRS{serial}=="A400fFkN", SYMLINK+="ziggo"
```

Additional info:

Distributor ID: Ubuntu
Description:    Ubuntu 12.10
Release:        12.10
Codename:     quantal


Thanks in advance !

---

### Post by peter.wieringa on 2013-12-03
update: still no luck. However, i did notice that when i run udevadm test ttyUSB0, i get:
 
cannot find device **/sys/**dev/ttyUSB0. (device is in /dev/ttyUSB0, i don't have a /sys/dev dir).

Do I have an incorrect path somewhere or is this normal behaviour ?

---

