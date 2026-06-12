---
title: "usb drive not recognized?"
date: 2015-12-29
forum: General Help
---

### Post by garyed on 2015-12-29
running ubuntu studio 14.04 : 
I have a usb stick that was working fine but I wanted to clean it & reformat it & make it a bootable live 14.04. I did some experimenting with the dd command to clean it & now I can not even get fdisk to recognize the drive. I have other usb drives that work fine so i know it's this one usb stick that is the problem. I guess it's possible the drive is just bad but more than likely it was the dd command that I used & I'm not even sure which code I tried. When I do fdisk -l with the stick in, the terminal locks up after it prints to the screen & it won't let me do any more commands unless I close the terminal & reopen it. When I do fdisk -l without the stick in then everything runs normally.   Gparted will not work either. Any ideas?

---

### Post by Al1000 on 2015-12-29
Hi Gary,

```
history | grep dd
```...should remind you what dd command(s) you used.

Re Gparted; in this order:

1) Boot up computer,

2) Plug in the offending USB

3) Open GParted

What happens? Is the USB listed in GParted?

Ideally you would want to select the USB, click on the Device tab in GParted, and select "Create Partition Table."

I assume there's no data on the USB that you want to try to salvage.

---

### Post by garyed on 2015-12-29
This looks like the command I used:> sudo dd if=/dev/zero of=/dev/sdd bs=1k count=2048 but it could have been something a little different because i also tried the command as root so it will not show up in history.
 /dev/sdd was my working usb stick at the time.

Since I issued whatever dd command, Gparted will not run with the usb stick inserted. If I remove it then it runs fine. It acts like a bad HD does but I can't believe one command can break a usb drive instead of just deleting everything.

---

### Post by garyed on 2015-12-30
Is there any other reason besides a bad usb stick that it will not show up in fdisk or gparted?
This is assuming the usb slot is working with all other usb sticks when they are plugged in.

---

### Post by yancek on 2015-12-30
With the usb stick plugged in reboot and check the BIOS to see if it shows up.  If not, it is probably bad.

---

### Post by sudodus on 2015-12-30
You have wiped the partition table. It *should* work well to use ***gparted*** to create a new partition table and after that partitions with file systems. But the USB stick must be recognized as a mass storage device, /dev/sdx, where x is a drive letter, for example [COLOR="#0000CD"]d[/COLOR] as in /dev/sd[COLOR="#0000CD"]d[/COLOR] in your dd command line.

Run the following commands:

```
sudo lsblk -fm
```

and

```
sudo parted -ls
```

and post the results in a reply.

Try in different USB ports, if possible also in different computers. That dd command does not destroy a USB stick. I have used it hundreds of times (under the hood of ***mkusb***). But a USB stick can break without any warning, so maybe it just happened during or right after that operation.

---

### Post by garyed on 2015-12-30
> **sudodus said:**
> You have wiped the partition table. It *should* work well to use ***gparted*** to create a new partition table and after that partitions with file systems. But the USB stick must be recognized as a mass storage device, /dev/sdx, where x is a drive letter, for example [COLOR="#0000CD"]d[/COLOR] as in /dev/sd[COLOR="#0000CD"]d[/COLOR] in your dd command line.

Run the following commands:

```
sudo lsblk -fm
```

and

```
sudo parted -ls
```

and post the results in a reply.

Try in different USB ports, if possible also in different computers. That dd command does not destroy a USB stick. I have used it hundreds of times (under the hood of ***mkusb***). But a USB stick can break without any warning, so maybe it just happened during or right after that operation.


Those commands will not work with the usb stick inserted. They just hang until i pull the stick out & then they work. I have other usb sticks that work in the same slot so i think the flash drive just went bad coincidentally. I even tried it on another computer running a different version of Ubnuntu & the same thing happens.

---

### Post by matt_symes on 2015-12-30
Hi

Open a terminal and type

```
tail -f /var/log/syslog
```

Plug the USB stick in, wait 10 seconds and post the output that tail followed into your next post.

Kind regards

---

### Post by garyed on 2015-12-30
```

$ tail -f /var/log/syslog
Dec 30 17:22:20 gary-gig kernel: [ 3325.400387] usb 3-10: new low-speed USB device number 21 using xhci_hcd
Dec 30 17:22:20 gary-gig kernel: [ 3325.415228] usb 3-10: New USB device found, idVendor=046d, idProduct=c05a
Dec 30 17:22:20 gary-gig kernel: [ 3325.415239] usb 3-10: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Dec 30 17:22:20 gary-gig kernel: [ 3325.415241] usb 3-10: Product: USB Optical Mouse
Dec 30 17:22:20 gary-gig kernel: [ 3325.415241] usb 3-10: Manufacturer: Logitech
Dec 30 17:22:20 gary-gig kernel: [ 3325.415375] usb 3-10: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
Dec 30 17:22:20 gary-gig kernel: [ 3325.417340] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.0/input/input28
Dec 30 17:22:20 gary-gig kernel: [ 3325.417610] hid-generic 0003:046D:C05A.0010: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:14.0-10/input0
Dec 30 17:22:20 gary-gig mtp-probe: checking bus 3, device 21: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-10"
Dec 30 17:22:20 gary-gig mtp-probe: bus: 3, device: 21 was not an MTP device
Dec 30 17:24:35 gary-gig kernel: [ 3460.376032] usb 3-1: new high-speed USB device number 22 using xhci_hcd
Dec 30 17:24:35 gary-gig kernel: [ 3460.565930] usb 3-1: New USB device found, idVendor=058f, idProduct=9380
Dec 30 17:24:35 gary-gig kernel: [ 3460.565940] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Dec 30 17:24:35 gary-gig kernel: [ 3460.565945] usb 3-1: Product: Mass Storage Device
Dec 30 17:24:35 gary-gig kernel: [ 3460.565948] usb 3-1: Manufacturer: Alcor Micro
Dec 30 17:24:35 gary-gig mtp-probe: checking bus 3, device 22: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1"
Dec 30 17:24:35 gary-gig mtp-probe: bus: 3, device: 22 was not an MTP device
Dec 30 17:24:35 gary-gig kernel: [ 3460.611359] usb-storage 3-1:1.0: USB Mass Storage device detected
Dec 30 17:24:35 gary-gig kernel: [ 3460.611396] scsi6 : usb-storage 3-1:1.0
Dec 30 17:24:35 gary-gig kernel: [ 3460.611434] usbcore: registered new interface driver usb-storage
Dec 30 17:24:36 gary-gig kernel: [ 3461.611831] scsi 6:0:0:0: Direct-Access     Generic  USB Flash Disk   7.76 PQ: 0 ANSI: 2
Dec 30 17:24:36 gary-gig kernel: [ 3461.612341] sd 6:0:0:0: Attached scsi generic sg4 type 0
Dec 30 17:24:36 gary-gig kernel: [ 3461.613121] sd 6:0:0:0: [sdd] 3115008 512-byte logical blocks: (1.59 GB/1.48 GiB)
Dec 30 17:24:36 gary-gig kernel: [ 3461.613325] sd 6:0:0:0: [sdd] Write Protect is off
Dec 30 17:24:36 gary-gig kernel: [ 3461.613335] sd 6:0:0:0: [sdd] Mode Sense: 03 00 00 00
Dec 30 17:24:36 gary-gig kernel: [ 3461.613518] sd 6:0:0:0: [sdd] No Caching mode page found
Dec 30 17:24:36 gary-gig kernel: [ 3461.613523] sd 6:0:0:0: [sdd] Assuming drive cache: write through
Dec 30 17:24:36 gary-gig kernel: [ 3461.615998] sd 6:0:0:0: [sdd] No Caching mode page found
Dec 30 17:24:36 gary-gig kernel: [ 3461.616009] sd 6:0:0:0: [sdd] Assuming drive cache: write through
Dec 30 17:25:07 gary-gig kernel: [ 3492.407981] usb 3-1: reset high-speed USB device number 22 using xhci_hcd
Dec 30 17:25:07 gary-gig kernel: [ 3492.596282] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803cfc10480
Dec 30 17:25:07 gary-gig kernel: [ 3492.596297] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803cfc104c0


```

I ran the code first & after 10 seconds inserted the usb flash drive so the first 5 or 10 lines are before the flash drive was inserted. I have 3 internal HD's in the computer.

---

