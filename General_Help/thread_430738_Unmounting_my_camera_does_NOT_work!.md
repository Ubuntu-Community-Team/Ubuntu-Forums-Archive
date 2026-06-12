---
title: "Unmounting my camera does NOT work!"
date: 2007-05-02
forum: General Help
---

### Post by dennis1200 on 2007-05-02
I have a Nikon D70 camera, complete with CF card. Whenever I transfer pics to the computer, which I do often, I plug in the camera, turn it on, and a NIKON D70 drive appears. I copy files to HD. So far, so good. But if I unmount the camera (usually using the Disk Mounter applet in my toolbar, but the same goes for right-click-->unmount volume), the camera can no longer read the files on the CF card. Clicking on the "preview" button just comes up with "Folder contains no images," which means that the data has been corrupted somehow. I can either unplug it first, and then turn if off, or turn it off and then unplug it (both after properly unmounting it), but the result is the same. All I'm doing is copy/paste, and I make sure the  unmount is complete before doing anything else. Any help?

---

### Post by dannyboy79 on 2007-05-02
please show me what this returns immediately after this weird occurance.

dmesg | tail

also, please also show me what this command returns WHEN the camera is plugged in and mounted

mount

also, 

lsusb

---

### Post by dennis1200 on 2007-05-02
Well, of course it worked fine this time (now I know what all those car drivers feel like when they take it into the shop)! I'll be sure to post that output when it does fail. For those interested, this is what (apparently correct) code looks like:
For mounting, I typed 'tail -n 30 /var/log/syslog', since dmesg didn't quite get it all. Here are those results:
```
May  2 17:09:34 laptop: [  756.528000] usb 2-2: new full speed USB device using ohci_hcd and address 2
May  2 17:09:34 laptop: [  756.740000] usb 2-2: configuration #1 chosen from 1 choice
May  2 17:09:35 laptop: [  757.436000] usbcore: registered new interface driver libusual
May  2 17:09:35 laptop: [  757.516000] Initializing USB Mass Storage driver...
May  2 17:09:35 laptop: [  757.516000] scsi0 : SCSI emulation for USB Mass Storage devices
May  2 17:09:35 laptop: [  757.520000] usbcore: registered new interface driver usb-storage
May  2 17:09:35 laptop: [  757.520000] USB Mass Storage support registered.
May  2 17:09:35 laptop: [  757.520000] usb-storage: device found at 2
May  2 17:09:35 laptop: [  757.520000] usb-storage: waiting for device to settle before scanning
May  2 17:09:40 laptop: [  762.524000] usb-storage: device scan complete
May  2 17:09:40 laptop: [  762.528000] scsi 0:0:0:0: Direct-Access     NIKON    D70              2.00 PQ: 0 ANSI: 2
May  2 17:09:40 laptop: [  762.592000] SCSI device sda: 2002896 512-byte hdwr sectors (1025 MB)
May  2 17:09:40 laptop: [  762.596000] sda: Write Protect is off
May  2 17:09:40 laptop: [  762.596000] sda: Mode Sense: 0f 00 00 00
May  2 17:09:40 laptop: [  762.596000] sda: assuming drive cache: write through
May  2 17:09:40 laptop: [  762.616000] SCSI device sda: 2002896 512-byte hdwr sectors (1025 MB)
May  2 17:09:40 laptop: [  762.624000] sda: Write Protect is off
May  2 17:09:40 laptop: [  762.624000] sda: Mode Sense: 0f 00 00 00
May  2 17:09:40 laptop: [  762.624000] sda: assuming drive cache: write through
May  2 17:09:40 laptop: [  762.624000]  sda: sda1
May  2 17:09:40 laptop: [  762.640000] sd 0:0:0:0: Attached scsi removable disk sda
May  2 17:09:40 laptop: [  762.656000] sd 0:0:0:0: Attached scsi generic sg0 type 0
May  2 17:09:41 xxxxx-xxxxxxx hald: mounted /dev/sda1 on behalf of uid 1000

```


Here is 'lsusb':
```
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 04b0:0405 Nikon Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 001 Device 001: ID 0000:0000 
```


And finally, syslog while unmounting (watching using tail -f /var/log/syslog)
```
May  2 17:18:06 laptop hald: unmounted /dev/sda1 from '/media/NIKON D70' on behalf of uid 1000
May  2 17:18:13 laptop kernel: [ 1275.080000] usb 2-2: USB disconnect, address 4

```

---

### Post by dennis1200 on 2007-05-05
Very stupid of me, and very obvious. The code is clean as a whistle. The deciding factor is whether I rename the folder before copying it. This means that the camera "preview" finds nothing in the default folder name, hence "folder contains no images". But the images are there. Silly me. 

Ubuntu was right all along!

And hooray for the recently announced [Dell-Canonical partnership]("http://www.linuxplanet.com/linuxplanet/newss/6383/1/")!

---

