---
title: "Can't access this USB stick - lsusb found it!"
date: 2018-01-20
forum: General Help
---

### Post by Sparks27 on 2018-01-20
This is an 8 GB USB storage stick, which I might have badly deleted somehow in the past - can't remember really - and I plug it in and it doesn't show in Disks nor in GParted. This is what lsusb says about it. I found it by plugging it in and out....

Have I lost it or can it be saved and formatted back to normal? 

```

Bus 001 Device 017: ID 0000:0000  
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice           11.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
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
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255


```

---

### Post by oldos2er on 2018-01-20
What file system is on it? Sounds as though it might not have been properly unmounted at some point.

---

### Post by rbmorse on 2018-01-20
If you just want to wipe whatever is on there now, reformat and restore the device to use, the package mkusb will be useful.  It's in repository.

---

### Post by Sparks27 on 2018-01-22
**mkusb** can't find the stick. I think **gparted** and **disks** would have found it first. They can't. 

[IMG]https://3.bp.blogspot.com/-us-MiE53-PA/WmYw0driawI/AAAAAAAAAAQ/RpRX4NS5TvkLt-wVLqpLr5Px9wopygatgCLcBGAs/s1600/151664762538586331.png[/IMG]

we're talking about the zeros-and-no-name device, device012



@oldos2er what do you mean by filesystem? like ext4, ntfs, fat32? It must have been one of those. I've used it to install some Linux version, and I think I did some kind of hard deletion on it after this. Like erase the whole disk and fill it with zeros, I don't know really...



Also, tried it on Windows too. I can't access it there too. When I plug it in, Windows make the characteristic sound that something has been plugged in. Then I run into the famously googled problem "usb shows up in **devices and printers** but not **my computer**" :( Devices and printers recognize it as usb storage device.

---

### Post by Sparks27 on 2018-01-28
Is my USB stick dead forever? :(

---

### Post by sudodus on 2018-01-28
You can try according to this list, that works for USB pendrives as well as memory cards,

- On some pendrives and on many memory cards there is a small mechanical switch for write protection, that can toggle between read/write and read-only. You might have set it read-only without intention.

- Reboot the computer and try again to restore or wipe the first megabyte with mkusb.

- Disconnect other USB devices. Sometimes USB devices can disturb the function for each other.

- Try other USB ports, and/or other card adapters.

- Try another computer.

- Try another operating system (Windows, MacOS) in another computer.

- If you still cannot wipe the first megabyte of the drive, or the drive is read-only, it is probably damaged beyond repair. There is a limit, when you have to accept that the pendrive is damaged beyond repair, at least with tools available to normal users like you and me.

There are more tips at [this link](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

---

