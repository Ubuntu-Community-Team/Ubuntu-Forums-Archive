---
title: "USB Pen Drive will not work - Hardy"
date: 2008-05-07
forum: General Help
---

### Post by culturepunk on 2008-05-07
Hi everyone, I'm quite new to Ubuntu and was wondering if anyone could help with a problem I'm having.

I'm using hardy, and have just got myself a 8GB USB stick. Whatever I try I cant get it to come up correctly in Ubuntu. When I first got it I could write but not read from it. It works completely fine on my 2 Windows XP machines though.

Tonight I have copied all files off it onto my Windows XP machine then have tried using gparted to format the drive using FAT32 in Ubuntu, as I've read somewhere that this could help. I was then able to read/write files to it, on the Ubuntu machine. I then took it downstairs to the Windows XP machine and copied the files I wanted to transfer back onto it. On inserting it back in the Ubuntu machine it will now not read or write.

When I insert it, it comes up on the desktop for a few seconds showing the drive and files on it then disappears again. With the error message:

""disk" couldn't be found. Perhaps it has recently been deleted."

The drive works fine on both Windows XP machines still. If anyone can help with this that would be great.

---

### Post by culturepunk on 2008-05-07
*oops - My Net Going Slow - Triple Posted*

---

### Post by culturepunk on 2008-05-07
*oops - My Net Going Slow - Triple Posted*

---

### Post by culturepunk on 2008-05-07
I have just run the command, which it said on another topic on here to run:

dmesg | tail

and have the following result:

```
[ 2090.181381] sd 5:0:0:0: [sdg] Mode Sense: 43 00 00 00
[ 2090.181384] sd 5:0:0:0: [sdg] Assuming drive cache: write through
[ 2090.181391]  sdg: sdg1
[ 2090.278168] sd 5:0:0:0: [sdg] Attached SCSI removable disk
[ 2090.278227] sd 5:0:0:0: Attached scsi generic sg8 type 0
[ 2090.601147] usb 4-1: reset high speed USB device using ehci_hcd and address 10
[ 2105.707679] usb 4-1: device descriptor read/64, error -110
[ 2120.918188] usb 4-1: device descriptor read/64, error -110
[ 2121.134099] usb 4-1: reset high speed USB device using ehci_hcd and address 10
[ 2136.240615] usb 4-1: device descriptor read/64, error -110

```

```
[ 2172.699480] usb 4-1: new high speed USB device using ehci_hcd and address 11
[ 2187.805977] usb 4-1: device descriptor read/64, error -110
[ 2203.016462] usb 4-1: device descriptor read/64, error -110
[ 2203.232401] usb 4-1: new high speed USB device using ehci_hcd and address 12
[ 2218.338920] usb 4-1: device descriptor read/64, error -110
[ 2233.549429] usb 4-1: device descriptor read/64, error -110
[ 2233.765342] usb 4-1: new high speed USB device using ehci_hcd and address 13
[ 2244.169581] usb 4-1: device not accepting address 13, error -110
[ 2244.281537] usb 4-1: new high speed USB device using ehci_hcd and address 14
[ 2254.685778] usb 4-1: device not accepting address 14, error -110

```

Seems there is some kind of read error... :( anyone any ideas?

---

### Post by culturepunk on 2008-05-08
Cany anyone help with this?

---

### Post by danevans29 on 2008-07-24
I am having a similar problem.  My pen drive / DVD-RW / USB external drive don't mount any longer (they worked fine after Hardy upgrade, but then recently stopped working).

Here are my outputs:

```

dan@dan:~$ dmesg|grep usb
[   15.243227] usbcore: registered new interface driver usbfs
[   15.243255] usbcore: registered new interface driver hub
[   15.253716] usbcore: registered new device driver usb
[   15.273741] usb usb1: configuration #1 chosen from 1 choice
[   15.376943] usb usb2: configuration #1 chosen from 1 choice
[   15.480861] usb usb3: configuration #1 chosen from 1 choice
[   15.584789] usb usb4: configuration #1 chosen from 1 choice
[   15.946302] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   15.993046] usb 4-1: configuration #1 chosen from 1 choice
[   16.076528] usb usb5: configuration #1 chosen from 1 choice
[   16.257707] usb 5-7: new high speed USB device using ehci_hcd and address 2
[   16.430650] usb 5-7: configuration #1 chosen from 1 choice
[   16.433382] usb 4-1: USB disconnect, address 2
[   29.447544] usbcore: registered new interface driver gspca
[  228.342795] usb 2-1: new low speed USB device using uhci_hcd and address 2
[  228.369893] usb 2-1: configuration #1 chosen from 1 choice
[  228.482475] usbcore: registered new interface driver hiddev
[  228.488203] input: USB Mouse as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input9
[  228.495547] input,hidraw0: USB HID v1.10 Mouse [USB Mouse] on usb-0000:00:1d.1-1
[  228.495575] usbcore: registered new interface driver usbhid
[  228.495582] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[ 3100.067313] usb 5-7: USB disconnect, address 2
[ 3100.214593] usb 5-7: new high speed USB device using ehci_hcd and address 4
[ 3100.356780] usb 5-7: unable to read config index 0 descriptor/all
[ 3100.356791] usb 5-7: can't read configurations, error -71
[ 3100.453406] usb 5-7: new high speed USB device using ehci_hcd and address 5
[ 3100.536679] usb 5-7: device descriptor read/64, error -71
[ 3100.736677] usb 5-7: configuration #1 chosen from 1 choice
[ 8135.440724] usb 5-2: new high speed USB device using ehci_hcd and address 6
[ 8135.572786] usb 5-2: configuration #1 chosen from 1 choice
[ 8135.846802] usbcore: registered new interface driver libusual
[ 8135.884007] usbcore: registered new interface driver usb-storage
[ 8135.884354] usb-storage: device found at 6
[ 8135.884358] usb-storage: waiting for device to settle before scanning
[ 8137.980908] usb-storage: device scan complete
[ 8168.314094] usb 5-2: reset high speed USB device using ehci_hcd and address 6
[ 8168.404578] usb 5-2: device descriptor read/64, error -71
[ 8168.571527] usb 5-2: device descriptor read/64, error -71
[ 8168.690583] usb 5-2: reset high speed USB device using ehci_hcd and address 6
[ 8168.772971] usb 5-2: device descriptor read/64, error -71
[ 8168.894810] usb 5-2: device descriptor read/64, error -71
[ 8168.987911] usb 5-2: reset high speed USB device using ehci_hcd and address 6
[ 8169.247392] usb 5-2: device not accepting address 6, error -71
[ 8169.301065] usb 5-2: reset high speed USB device using ehci_hcd and address 6
[ 8169.546881] usb 5-2: device not accepting address 6, error -71
[ 8169.546934] usb 5-2: USB disconnect, address 6
[ 8169.658815] usb 5-2: new high speed USB device using ehci_hcd and address 7
[ 8169.747909] usb 5-2: device descriptor read/64, error -71
[ 8169.885770] usb 5-2: device descriptor read/64, error -71
[ 8170.049839] usb 5-2: new high speed USB device using ehci_hcd and address 8
[ 8170.143325] usb 5-2: device descriptor read/64, error -71
[ 8170.276504] usb 5-2: device descriptor read/64, error -71
[ 8170.383038] usb 5-2: new high speed USB device using ehci_hcd and address 9
[ 8170.630516] usb 5-2: device not accepting address 9, error -71
[ 8170.683870] usb 5-2: new high speed USB device using ehci_hcd and address 10
[ 8170.921973] usb 5-2: device not accepting address 10, error -71
dan@dan:~$ dmesg | tail
[ 8169.658815] usb 5-2: new high speed USB device using ehci_hcd and address 7
[ 8169.747909] usb 5-2: device descriptor read/64, error -71
[ 8169.885770] usb 5-2: device descriptor read/64, error -71
[ 8170.049839] usb 5-2: new high speed USB device using ehci_hcd and address 8
[ 8170.143325] usb 5-2: device descriptor read/64, error -71
[ 8170.276504] usb 5-2: device descriptor read/64, error -71
[ 8170.383038] usb 5-2: new high speed USB device using ehci_hcd and address 9
[ 8170.630516] usb 5-2: device not accepting address 9, error -71
[ 8170.683870] usb 5-2: new high speed USB device using ehci_hcd and address 10
[ 8170.921973] usb 5-2: device not accepting address 10, error -71
dan@dan:~$ 

```

Any help?

---

### Post by danevans29 on 2008-08-09
I'm having the same problem:

```
[149334.952687] usb 5-2: new high speed USB device using ehci_hcd and address 30
[149335.064615] usb 5-2: device descriptor read/64, error -71
[149335.280477] usb 5-2: device descriptor read/64, error -71
[149335.496343] usb 5-2: new high speed USB device using ehci_hcd and address 31
[149335.608282] usb 5-2: device descriptor read/64, error -71
[149335.824132] usb 5-2: device descriptor read/64, error -71
[149336.039993] usb 5-2: new high speed USB device using ehci_hcd and address 32
[149336.447717] usb 5-2: device not accepting address 32, error -71
[149336.559667] usb 5-2: new high speed USB device using ehci_hcd and address 33
[149336.967387] usb 5-2: device not accepting address 33, error -71
[149511.528479] usb 5-2: new high speed USB device using ehci_hcd and address 34
[149511.639848] usb 5-2: device descriptor read/64, error -71
[149511.859713] usb 5-2: device descriptor read/64, error -71
[149512.075574] usb 5-2: new high speed USB device using ehci_hcd and address 35
[149512.187510] usb 5-2: device descriptor read/64, error -71
[149512.403365] usb 5-2: device descriptor read/64, error -71
[149512.619229] usb 5-2: new high speed USB device using ehci_hcd and address 36
[149513.026955] usb 5-2: device not accepting address 36, error -71
[149513.138914] usb 5-2: new high speed USB device using ehci_hcd and address 37
[149513.546623] usb 5-2: device not accepting address 37, error -71

```

```
Bus 005 Device 014: ID 046d:0896 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

The only listing I get is for my built-in webcam.  Nothing mounts any more.  After upgrading to Hardy everything worked fine, then everything stopped mounting.  Not sure if this has to do with some auto update but it's really annoying.

---

### Post by danevans29 on 2008-08-09
I found a workaround form the time being.  By disabling USB 2.0 and reverting to 1.1 (I think) I am able to mount my drives now, but only at low speed.  This is accomplished by:

```
sudo modprobe -r ehci_hcd
```

To undo this and go back to normal:

```
sudo modprobe ehci_hcd
```

Not a perfect solution, but at least I can access my pen drive, external drive, etc.

---

