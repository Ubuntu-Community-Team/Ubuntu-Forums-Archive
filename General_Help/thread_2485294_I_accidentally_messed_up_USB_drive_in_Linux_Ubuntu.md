---
title: "I accidentally messed up USB drive in Linux Ubuntu 22.04 LTS!"
date: 2023-03-25
forum: General Help
---

### Post by saddie2 on 2023-03-25
The USB 16 GB drive was infected with some Windows virus, I didn't want to plug it in, so I decided to
install Linux Ubuntu 22.04 LTS on my other computer and then I've formatted that same USB drive using Linux terminal commands (I don't remember which one).
I've chosen quick formatting and in that moment I wasn't aware if selected file system was ext4 or ext3 or something else.
Because of that file system the USB drive is unusable in Windows machines, so in the future I'm only going to use it in Linux environment.


But the main problem is that today that same usb drive is unrecognized when plugged in Linux Ubuntu? I've tried to search for it using commands but I can't find it.
In addition to that, I've also tried to check the situation using Windows machine, it seems that Windows recognizes that usb device has been plugged in, but when I click on it it's greyed out,
it can't be formatted etc.

Is there any chance that this USB drive will ever be usable again? I don't mind losing all the data, I want to format it in Linux or Windows but I can't find the way to do it?

I've tried ```
df -h
``` command and ```
gparted
``` but with no success ...

[https://postimg.cc/vgHVyxDZ](https://postimg.cc/vgHVyxDZ)
[https://postimg.cc/D4S4JVrV](https://postimg.cc/D4S4JVrV)
[https://postimg.cc/fJ00MNWm](https://postimg.cc/fJ00MNWm)
[https://postimg.cc/DW5Sxf5k](https://postimg.cc/DW5Sxf5k)
[https://postimg.cc/LhJJVp1w](https://postimg.cc/LhJJVp1w)
[https://postimg.cc/R6yVYWH8](https://postimg.cc/R6yVYWH8)
[IMG]https://postimg.cc/DW5Sxf5k[/IMG][IMG]https://postimg.cc/LhJJVp1w[/IMG][IMG]https://postimg.cc/R6yVYWH8[/IMG][IMG]https://postimg.cc/fJ00MNWm[/IMG]
[IMG]https://postimg.cc/D4S4JVrV[/IMG]
[IMG]https://postimg.cc/vgHVyxDZ[/IMG]

---

### Post by saddie2 on 2023-03-25
Links to images shown

---

### Post by ne29914 on 2023-03-25
Is this some virtual machine setup? It looks strange.

---

### Post by saddie2 on 2023-03-25
Yes it is virtual machine because I thought my USB port is not functioning, but now I'm sure that USB port is working 100% fine with other USB flash drives that I just got for testing purposes.

---

### Post by nimafanniasl on 2023-03-26
Hmm, have you tried gnome disks?

---

### Post by saddie2 on 2023-03-26
[[IMG]https://i.postimg.cc/HLHjyrnW/Screenshot-2023-03-26-133159.png[/IMG]]("https://postimg.cc/mPXbx27K")

When I click on three dots, all options are greyed out, it only allows "Power Off"?

---

### Post by tea for one on 2023-03-26
> **saddie2 said:**
> Is there any chance that this USB drive will ever be usable again? I don't mind losing all the data, I want to format it in Linux or Windows but I can't find the way to do it?
Open Gparted
Insert the disk
Gparted > Refresh Devices 
Select your target device
Device > Create Partition Table > msdos or gpt (user choice)

If that is successful, then you can create partition(s).

---

### Post by saddie2 on 2023-03-26
> **tea for one said:**
> Open Gparted
Insert the disk
Gparted > Refresh Devices 
Select your target device
Device > Create Partition Table > msdos or gpt (user choice)

If that is successful, then you can create partition(s).


Inside Gparted I've refreshed devices, but nothing changes, it doesn't want to show it in Gparted,
I've tried multiple times, it only shows /dev/sda (60.00 GiB).
At the same time in Gnome disks, it shows his name USB DISK 2.0 and the device name is /dev/sdb 
(see the screenshot)

[COLOR=#000000]When I click on three dots (in Gnome disks), all options are greyed out, it only allows "Power Off" (like in the post #6)?[/COLOR]

[[IMG]https://i.postimg.cc/htkrkWsQ/Screenshot-2023-03-26-141244.png[/IMG]]("https://postimg.cc/5XmLzrZf")

---

### Post by Holger_Gehrke on 2023-03-26
The first step should be finding out if it's found on the USB when connected. Use the 'lsusb' command for that, once before connecting the drive and a second time a few seconds after connecting it. 'lsusb' shows all the connected devices, so comparing the output of the two runs should tell you whether the drive is seen. If the drive is visible in 'lsusb' but isn't mounted automatically and can't be seen in Gnome disk or gparted or 'sudo parted -l' / 'sudo fdisk -l' or 'lsblk', then running 'journalctl -b 0' or 'sudo dmesg' and looking at the contents of the file /var/log/syslog might tell you something about the problem.

Holger

---

### Post by sudodus on 2023-03-26
You can analyze the problem according to [this link](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035) and if you are lucky, find a solution.

---

### Post by saddie2 on 2023-03-26
> **Holger_Gehrke said:**
> The first step should be finding out if it's found on the USB when connected. Use the 'lsusb' command for that, once before connecting the drive and a second time a few seconds after connecting it. 'lsusb' shows all the connected devices, so comparing the output of the two runs should tell you whether the drive is seen. If the drive is visible in 'lsusb' but isn't mounted automatically and can't be seen in Gnome disk or gparted or 'sudo parted -l' / 'sudo fdisk -l' or 'lsblk', then running 'journalctl -b 0' or 'sudo dmesg' and looking at the contents of the file /var/log/syslog might tell you something about the problem.

Holger


[https://paste.ubuntu.com/p/6mJp3ZTdkS/](https://paste.ubuntu.com/p/6mJp3ZTdkS/)

---

### Post by Holger_Gehrke on 2023-03-26
Hm, ... So lsusb sees it as a Kingston Platinum USB drive mini (does PNY buy from Kingston ?) ; fdisk and parted both don't see it, but lsblk sees a drive of size 0. 

'journalctl', not 'journal' ... the former shows a human-readable representation of the binary journal the system keeps, the latter is for people who want to keep a diary ;) . 

The dmesg output gets interesting from line 1928 onward: the device is recognized, the idVendor and idProduct are for a Kingston Platinum USB drive mini (so that's where lsusb pulled that name from; there's a list of vendor and product ids in /usr/share/misc/usb.ids) but then it gets treated as something with removable media with either no media inserted or with the media removed. 

This doesn't look good; might be the end of the line for this stick. I'd follow sudodus' tutorial - especially the part on installing and using mkusb - but I wouldn't get my hopes up. Flash-drives have a limited write count and at some point they just break.

Holger

---

### Post by saddie2 on 2023-03-26
Ok, thanks for your help Holger_Gehrke, appreciate it.
I will paste this just in case: ```
[COLOR=#111111][FONT=monospace]journalctl -b 0[/FONT][/COLOR]
```

[https://paste.ubuntu.com/p/SVjW2yQZKQ/](https://paste.ubuntu.com/p/SVjW2yQZKQ/)


Before I start doing complete steps from sudodus' tutorial ([https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035))
I will paste output of this command ```
lsusb -v
```

```
computer99@computer99-virtual-machine:~$ lsusb -v

Bus 001 Device 004: ID 13fe:4200 Kingston Technology Company Inc. Platinum USB drive mini
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x13fe Kingston Technology Company Inc.
  idProduct          0x4200 Platinum USB drive mini
  bcdDevice            1.00
  iManufacturer           1         
  iProduct                2 USB DISK 2.0
  iSerial                 3 90005BA465155916
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x0020
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              200mA
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
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0



```

---

