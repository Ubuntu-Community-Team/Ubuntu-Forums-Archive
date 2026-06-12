---
title: "Disable write cache for USB?"
date: 2007-06-25
forum: General Help
---

### Post by ss0007 on 2007-06-25
Hi ,
I wanted to disable the write caching for my USB drive(Sony Ericssion phone). It seems Ubuntu writes to cache for large files and I have to wait impatiently for the drive write operations.So , Is there any idea to disable write caching? 

Also, Googling the search ,I discovered to use this command ...
```
sudo hdparm -W 0 /dev/sdc1
```

But , using that results in following error, 
```
/dev/sdc1:
 setting drive write-caching to 0 (off)
 HDIO_DRIVE_CMD(setcache) failed: Invalid argument
```

Is there any way to solve the issue ?

---

### Post by grahams on 2007-06-25
I don't think there is currently a way to change parameters of USB devices with hdparm. However using the write cache of your drive should increase performance. I would not try to turn it off unless you're running some sort of mission critical server app were data integrity is vital.

---

### Post by ss0007 on 2007-06-25
Actually need not to be a mission critical , my Sony ericssion phone connects as USB mass storage drive.
Whenever I write some data around 50mb , the progress dialog disappears imm. Hence when I unmount , a dialog is displayed, saying "Writing data to device .. " and this is displayed for >20min for 50MB file !!!. Hence, I wanted to stop caching and see whether it stuck at any file.

---

### Post by grahams on 2007-06-26
Wow 20 mins for 50MB is very slow even if it's running at USB 1.1 speeds. Do you get the same poor performance when writing to other USB devices?

The modern kernels ubuntu uses should provide very fast USB speeds via async I/O. 

type lsmod |grep usb and make sure you have both ehci_usb and uhci_hcd loaded. One of them is for high speed USB and if it's missing it may account for the slow performance. 

My output looks like this
usbcore               134280  3 ehci_hcd,uhci_hcd

If everything looks good, try the device on another system or OS to make sure it's not a device issue.

---

### Post by mbeierl on 2007-06-26
The mount options you want (in /etc/fstab) are "sync,dirsync" to write synchronously to the device.  For example, my mount is:
```

/dev/sdb1                                               /media/usb              vfat user,sync,dirsync          0 0

```

---

### Post by Spartakan on 2007-10-04
Thought I'd continue this thread rather than start a new one -  I have exactly the same problem with my Sony Ericsson W880i. When mounted its entry in /etc/mtab looks like this:

```

/dev/sdb1 /media/PHONE\040CARD vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0

```

In fact currently, the unmount seems to have timed out (with a message like 'you seem to have mounted the device from the command line' - which I hadn't), so I'm left with my phone saying it can't be disconnected, and nothing in /etc/mtab

lsusb still shows my phone though:
```
Bus 004 Device 005: ID 0fce:e068 Sony Ericsson Mobile Communications AB 
```

The output from lsmod includes
```
usbcore               134280  11 ndiswrapper,usb_storage,libusual,cdc_ether,usbnet,cdc_acm,usbhid,hci_usb,ehci_hcd,uhci_hcd

```

What's the best next step? Is there a way to force a disconnect, or am I stuck with removing the cable?

Thanks

---

### Post by gatewayasteroid on 2007-10-04
> **ss0007 said:**
> Hi ,
I wanted to disable the write caching for my USB drive(Sony Ericssion phone). It seems Ubuntu writes to cache for large files and I have to wait impatiently for the drive write operations.So , Is there any idea to disable write caching? 

Also, Googling the search ,I discovered to use this command ...
```
sudo hdparm -W 0 /dev/sdc1
```

But , using that results in following error, 
```
/dev/sdc1:
 setting drive write-caching to 0 (off)
 HDIO_DRIVE_CMD(setcache) failed: Invalid argument
```

Is there any way to solve the issue ?

Not a good idea for a FAT filesystems:

[http://groups.google.com/group/linux.kernel/msg/8d1591196c0ae15e](http://groups.google.com/group/linux.kernel/msg/8d1591196c0ae15e)

---

### Post by Murz on 2008-05-12
> **gatewayasteroid said:**
> Not a good idea for a FAT filesystems:

[http://groups.google.com/group/linux.kernel/msg/8d1591196c0ae15e](http://groups.google.com/group/linux.kernel/msg/8d1591196c0ae15e)
Maybe exists another method to disable write caching on removable drives?
I very often needs to quickly remove USB Flash drive and have no time to waiting when 'sync' command write all buffer to device.
Better for me is lower write perfomance and quick remove (without sync).

---

