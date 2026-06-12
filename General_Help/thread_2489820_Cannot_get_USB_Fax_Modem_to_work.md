---
title: "Cannot get USB Fax Modem to work"
date: 2023-08-10
forum: General Help
---

### Post by cscj01 on 2023-08-10
I have had my US Robotics USR5637 on a number of iterations of Ubuntu.  I am now on 22.04 and cannot get the system to recognize the device by assign an appropriate dev to it.  The status under Efax-gtk is Inactive.  Here is what I have found to date:```
$ lsusb
Bus 002 Device 003: ID 1058:25a3 Western Digital Technologies, Inc. Elements Desktop (WDBWLG)
Bus 002 Device 002: ID 0bda:0411 Realtek Semiconductor Corp. Hub
Bus 002 Device 004: ID 1058:25a3 Western Digital Technologies, Inc. Elements Desktop (WDBWLG)
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 013: ID 046d:0892 Logitech, Inc. C920 HD Pro Webcam
Bus 001 Device 012: ID 04b0:4001 Nikon Corp. LS 50 ED/Coolscan V ED
Bus 001 Device 010: ID 04b8:013a Seiko Epson Corp. GT-X820 [Perfection V600 Photo]
Bus 001 Device 008: ID 0baf:0303 U.S. Robotics USR5637 56K Faxmodem
Bus 001 Device 005: ID 0bda:5411 Realtek Semiconductor Corp. RTS5411 Hub
Bus 001 Device 003: ID 04b8:1194 Seiko Epson Corp. ET-8550 Series
Bus 001 Device 006: ID 534d:0021 MacroSilicon MS210x Video Grabber [EasierCAP]
Bus 001 Device 004: ID 1058:25a3 Western Digital Technologies, Inc. Elements Desktop (WDBWLG)
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 011: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 009: ID 048d:5702 Integrated Technology Express, Inc. ITE Device
Bus 001 Device 007: ID 046a:0011 Cherry GmbH G83 (RS 6000) Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```
$ lsusb -v -d 0baf:0303

Bus 001 Device 008: ID 0baf:0303 U.S. Robotics USR5637 56K Faxmodem
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0baf U.S. Robotics
  idProduct          0x0303 USR5637 56K Faxmodem
  bcdDevice            2.00
  iManufacturer           1 U.S.Robotics
  iProduct                2 USB Modem
  iSerial                10 0000002
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x0043
    bNumInterfaces          2
    bConfigurationValue     2
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              360mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              5 
      CDC Header:
        bcdCDC               10.01
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          1
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      CDC ACM:
        bmCapabilities       0x06
          sends break
          line coding and serial state
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              5 
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
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
```So, the system knows the modem is there, but it can't open it.  This always worked in previous versions of Ubuntu.  Any help would be appreciated.

---

### Post by TheFu on 2023-08-10
No clue, but some USB devices don't work through a USB hub. Try connecting it directly to a USB port on the computer.

---

### Post by cscj01 on 2023-08-10
The Fax modem is plugged into a usb port on the MB.  I have tried removing and reinserting, rebooting, etc.  I even removed britty.  No change.

---

### Post by TheFu on 2023-08-10
Is there a device file in /dev/ for the modem? Typically, ttyUSB0 would be seen.

What are the permissions on that file?
[https://askubuntu.com/questions/133235/how-do-i-allow-non-root-access-to-ttyusb0](https://askubuntu.com/questions/133235/how-do-i-allow-non-root-access-to-ttyusb0) has an example file and permissions.

I haven't had a fax/modem inside any of my computers since the 1990s. Switched to a Brother All-in-One machine over a decade ago to send faxes out. I don't ever receive faxes. If I did, I'd probably just ask them to ZIP encrypt the file and email it.  Anything more complex than that and 99% of the world freaks out.

---

### Post by cscj01 on 2023-08-10
No, there is no device file for the modem.

---

### Post by TheFu on 2023-08-10
That means a driver isn't loaded. You'll need to solve that first.
I'll ask some questions to clearly display my total ignorance.

Is this a win-modem or a proper modem with a real UART?  I remember winmodems not working under Linux.  People always got real modems with UARTs that were supported by the OS drivers.  Eventually, someone came up with a hack to use MS-Windows drivers under Linux. I never used those.

Someone on another forum for a different OS said to load the driver using 
**sudo modprobe cdc_acm**

The resulting device is seen:
**ls -l /dev/ttyACM***

then you'd just ensure the permissions for that device file are correct for the users you need to have access.  I suppose that would be a fax server daemon or your userid, but IDK.

---

### Post by cscj01 on 2023-08-11
> **TheFu said:**
> That means a driver isn't loaded. You'll need to solve that first.
I'll ask some questions to clearly display my total ignorance.

Is this a win-modem or a proper modem with a real UART?  I remember winmodems not working under Linux.  People always got real modems with UARTs that were supported by the OS drivers.  Eventually, someone came up with a hack to use MS-Windows drivers under Linux. I never used those.

Someone on another forum for a different OS said to load the driver using 
**sudo modprobe cdc_acm**

The resulting device is seen:
**ls -l /dev/ttyACM***

then you'd just ensure the permissions for that device file are correct for the users you need to have access.  I suppose that would be a fax server daemon or your userid, but IDK.

This is not a win-modem.  It has worked on all previous versions of Ubuntu going  back at least as far as 16.04 and possibly to 14.04 (I can't remember further back than 16.04).

I tried ```
sudo modprobe cdc_acm
``` and nothing was returned.

---

### Post by cscj01 on 2023-08-11
I don't know what this means, but I have two directories in /dev/serial labeled by_id and by_path.  There is one file in each directory.  In by_id, the file name is > usb-U.S.Robotics_USB_Modem_0000002-if00 and in by_path it is > pci-0000:00:14.0-usb-0:7.1:2.0  Maybe this will give you a clue.

---

### Post by TheFu on 2023-08-12
Point your modem control program at the usb-U.S.Robotics_USB_Modem_0000002-if00  symlink.  Did you look to see which device file that really points at?  What are the permissions?

Perhaps I missed it, but which OS and which kernel are being used?

---

### Post by cscj01 on 2023-08-12
I am running the following: > OS - Ubuntu 22.04.3;
Kernel 6.2.0-26-generac;
Version #26~22.04.1-Ubuntu SMP PREEMPT _DYNAMIC Thru Jul 13 16:27:29 UTC 2usb-U.S.Robotics_USB_Modem_0000002-if00 shows the following:> Type: Link to character device (inode/chardevice);
Link target:f ../../ttyACMO  It has the following permissions:> Owner: root with Read and write;
Group: dialout with Read and write;
Others: with None


I am a member of dialout.  ttyACMO does not exist anywhere in my system.

---

### Post by cscj01 on 2023-08-13
bump

---

### Post by HermanAB on 2023-08-15
I usually debug these things with low level utilities like dmesg, lsmod, lsusb etc.

Eg:
Unplug the modem
$ sudo dmesg
Look at the old messages
Plug the modem in
$ sudo dmesg
See what is newly reported
$ sudo lsusb
See what shows up
$ ls /dev
See which device nodes are reported
Etc…

---

### Post by TheFu on 2023-08-15
I like using multiple terminals and in one run **dmesg -w** which will show the tail of dmesg output as it arrives.

Besides what I've already posted, I know nothing specific about modem use.

---

