---
title: "ZTE modem udev rules HELP"
date: 2013-11-07
forum: General Help
---

### Post by Marcos_Cano on 2013-11-07
hello i've been trying to make a udev rule for a ZTE modem (that we use to send SMS) the problem i encounter is that sometimes when we plug the modem it does not assign the same ttyUSB(number) so our application won't start beacuase the name is not always the same.

so i came up with the idea of making a udev rule to to assign it a SYMLINK like "zte-modem%n" 

i can put the output of  lsusb or dmesg

my current udev rules does not work. 10-usb-serial.rules

[B]
KERNEL=="ttyUSB[0-4]*",SUBSYSTEM=="tty" ,ATTRS{serial}=="MF1900ZTED010000", SYMLINK+="codratel-USB%n ttyUSB%n"[/B]


the output of :
**"sudo udevadm info -a -p $(sudo udevadm info -q path -n /dev/ttyUSB3)"**


Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/ttyUSB3/tty/ttyUSB3':
    KERNEL=="ttyUSB3"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/ttyUSB3':
    KERNELS=="ttyUSB3"
    SUBSYSTEMS=="usb-serial"
    DRIVERS=="option1"
    ATTRS{port_number}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1':
    KERNELS=="2-1.1:1.1"
    SUBSYSTEMS=="usb"
    DRIVERS=="option"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="01"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1':
    KERNELS=="2-1.1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{devpath}=="1.1"
    ATTRS{idVendor}=="19d2"
    ATTRS{speed}=="480"
    ATTRS{bNumInterfaces}==" 4"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="16"
    ATTRS{configuration}=="ZTE Configuration"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{authorized}=="1"
    ATTRS{bmAttributes}=="c0"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{maxchild}=="0"
    ATTRS{bcdDevice}=="0000"
    ATTRS{avoid_reset_quirk}=="1"
    ATTRS{quirks}=="0x10"
    ATTRS{serial}=="MF1900ZTED010000"
    ATTRS{version}==" 2.00"
    ATTRS{urbnum}=="20126"
    ATTRS{manufacturer}=="ZTE,Incorporated"
    ATTRS{removable}=="removable"
    ATTRS{idProduct}=="0117"
    ATTRS{bDeviceClass}=="00"
    ATTRS{product}=="ZTE WCDMA Technologies MSM"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2/2-1':
    KERNELS=="2-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{devpath}=="1"
    ATTRS{idVendor}=="8087"
    ATTRS{speed}=="480"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="2"
    ATTRS{configuration}==""
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{authorized}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{maxchild}=="6"
    ATTRS{bcdDevice}=="0000"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{version}==" 2.00"
    ATTRS{urbnum}=="359"
    ATTRS{removable}=="fixed"
    ATTRS{idProduct}=="0024"
    ATTRS{bDeviceClass}=="09"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{devpath}=="0"
    ATTRS{idVendor}=="1d6b"
    ATTRS{speed}=="480"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{authorized_default}=="1"
    ATTRS{busnum}=="2"
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
    ATTRS{serial}=="0000:00:1d.0"
    ATTRS{version}==" 2.00"
    ATTRS{urbnum}=="114"
    ATTRS{manufacturer}=="Linux 3.5.0-37-generic ehci_hcd"
    ATTRS{removable}=="unknown"
    ATTRS{idProduct}=="0002"
    ATTRS{bDeviceClass}=="09"
    ATTRS{product}=="EHCI Host Controller"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0':
    KERNELS=="0000:00:1d.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{irq}=="23"
    ATTRS{subsystem_vendor}=="0x1028"
    ATTRS{broken_parity_status}=="0"
    ATTRS{class}=="0x0c0320"
    ATTRS{companion}==""
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{local_cpus}=="ff"
    ATTRS{device}=="0x1c26"
    ATTRS{uframe_periodic_max}=="100"
    ATTRS{enable}=="1"
    ATTRS{msi_bus}==""
    ATTRS{local_cpulist}=="0-7"
    ATTRS{vendor}=="0x8086"
    ATTRS{subsystem_device}=="0x04de"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

---

