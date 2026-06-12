---
title: "Problems with a usb device,  udev rules, and permissions"
date: 2020-02-17
forum: General Help
---

### Post by adrian-h on 2020-02-17
After 7 hours of getting nowhere, I think it best to ask for help.

I have a USB device that can receive satellite TV a DVB-S/2 decoder.

When I try to run a command line script to access it I get failed to access. 

```
a@plex780:~/longmynd$ ./longmynd -i 192.168.1.40 10000 742500 2000
Flow: main
      Status: Main Frequency=742500 KHz
              Main Symbol Rate=2000 KSymbols/s
              Using First Minitiouner detected on USB
              Main TS output to IP=192.168.1.40:10000
              Main Status output to FIFO=longmynd_main_status
              Main refers to TOP F-Type
Flow: Fifo Init

      Status: opened fifo ok
Flow: FTDI init
Flow: FTDI USB init
libusb: error [_get_usbfs_fd] libusb couldn't open USB device /dev/bus/usb/001/010: Permission denied
libusb: error [_get_usbfs_fd] libusb requires write access to USB device nodes.
ERROR: Unable to open device with VID and PID
       Is the USB cable plugged in?
ERROR: FTDI init
Flow: UDP Init

```

But if prefixed with sudo it runs OK.

```
a@plex780:~/longmynd$ sudo ./longmynd -i 192.168.1.40 10000 742500 2000
[sudo] password for a: 
Flow: main
      Status: Main Frequency=742500 KHz
              Main Symbol Rate=2000 KSymbols/s
              Using First Minitiouner detected on USB
              Main TS output to IP=192.168.1.40:10000
              Main Status output to FIFO=longmynd_main_status
              Main refers to TOP F-Type
Flow: Fifo Init
      Status: opened fifo ok
Flow: FTDI init
Flow: FTDI USB init
Flow: FTDI set mpsse mode
Flow: FTDI USB init
Flow: FTDI set mpsse mode
Flow: FTDI setup io
      Status: MPSSE Synched AA FA
Flow: FTDI nim reset
Flow: UDP Init
Flow: NIM init
Flow: STV0910 init
Flow: stv0910 init regs
      Status: STV0910 MID = 0x51, DID = 0x20
Flow: STV0910 set MCLK
Flow: Setup equlaizers 1
Flow: Setup carrier loop 1
Flow: Setup timing loop 1
Flow: Tuner init
Flow: Tuner cal lowpass
Flow: Tuner set freq
      Status: tuner:0, f_vco=0x2d5190, icp=0x2, f=0x0, n=0xc6,
              rdiv=0x1, p=0x1, freq=742500, cfhf=2331
Flow: LNA init 1
      Status: found new NIM with LNAs
Flow: LNA init 2
      Status: found new NIM with LNAs
Flow: STV0910 start scan
```


When I do a lsusb I get the following entry about the device:-

Bus 001 Device 010: ID 0403:6010 Future Technology Devices International, Ltd FT2232C Dual USB-UART/FIFO IC

In 
etc/udev/rules.d I have got the following file 53-minitiouner.rules  The contents of which is:-

```
# Install with `sudo cp minitiouner.rules /etc/udev/rules.d/`
#  then unplug and replug the minitiouner

# Minitiouner uses FT2232H/D default VID/PID, but it's own product string.
SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6010", ATTRS{product}=="USB <-> NIM tuner", MODE:="0666"
```

The system has been rebooted to reload the rules but to no effect.

I checked in   /dev and monitored for any devices that showed up when the device was plugged in and noticed 3 extra entries, these were: serial, ttyUSB0 and ttyUSB1

So I even tried adding the user to group "tty" and group "dialout" without success, I can still only access the USB device using sudo.

Can anyone explain where I am going wrong please.

Adrian

---

### Post by adrian-h on 2020-02-17
The issue was resolved with the help of a knowledgable radio ham

An extra line was put into the rule.

53-minitiouner.rules now becomes

```
# Install with `sudo cp minitiouner.rules /etc/udev/rules.d/`
#  then unplug and replug the minitiouner

# Minitiouner uses FT2232H/D default VID/PID, but it's own product string.
SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6010", ATTRS{product}=="USB <-> NIM tuner", MODE:="0666"
# Minitiouner Express uses different product string
SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6010", ATTRS{product}=="MiniTiouner-Express", MODE:="0666"
```

Looks like I need to learn more about udev rules, I may have found it if I used lsusb -v  as the output provided the following


```
Bus 001 Device 028: ID 0403:6010 Future Technology Devices International, Ltd FT2232C Dual USB-UART/FIFO IC
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0403 Future Technology Devices International, Ltd
  idProduct          0x6010 FT2232C Dual USB-UART/FIFO IC
  bcdDevice            7.00
  iManufacturer           1 FTDI
  iProduct                2 MiniTiouner-Express
  iSerial                 3 DA3EFKAB
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           55
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 

```

So in effect the search strings to apply the rules were not being met.

I live and learn, well until I forget.

Adrian

---

