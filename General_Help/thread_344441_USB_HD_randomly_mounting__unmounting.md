---
title: "USB HD randomly mounting / unmounting"
date: 2007-01-22
forum: General Help
---

### Post by m.musashi on 2007-01-22
I have a hard drive that does not fit in my small case that I am using externally (I purchased one of those hd enclosures). I have it connected via usb port. When I turn it on, it will mount and then a few seconds later seemingly unmounts - I get an error about unsafe removal or a device. It does this over and over, mounting and unmounting. I want to use gparted to reformat it and use it to store back up images of my install but until I can resolve this I can't do anything.

Has anyone else experienced this or know of a solution?

Thanks.

---

### Post by La muerte del DIos on 2007-02-14
I have the same issue but with a Samsung YP mp3 player, please help us.

---

### Post by dcstar on 2007-02-14
> **La muerte del DIos said:**
> I have the same issue but with a Samsung YP mp3 player, please help us.

You both should run this in a terminal:
```
dmesg
```
and post the output when the problems occur.

---

### Post by m.musashi on 2007-02-14
> **dcstar said:**
> You both should run this in a terminal:
```
dmesg
```
and post the output when the problems occur.

Okay, did that. It printed more stuff than the terminal would hold (even scrolling all the way to the top never got to the beginning) but most of it looked unrelated to I'm just posting the bottom portion. Hope that is what is important.
```
[17342212.836000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17342418.520000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17342418.520000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17342894.588000] usb 2-2: new high speed USB device using ehci_hcd and address 12
[17342894.724000] usb 2-2: configuration #1 chosen from 1 choice
[17342894.724000] scsi11 : SCSI emulation for USB Mass Storage devices
[17342894.724000] usb-storage: device found at 12
[17342894.724000] usb-storage: waiting for device to settle before scanning
[17342897.516000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17342897.516000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17342899.724000] usb-storage: device scan complete
[17342899.728000]   Vendor: ST320082  Model:             4LJ2  Rev: 3.01
[17342899.728000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17342899.728000] SCSI device sdc: 390721968 512-byte hdwr sectors (200050 MB)
[17342899.732000] sdc: Write Protect is off
[17342899.732000] sdc: Mode Sense: 00 38 00 00
[17342899.732000] sdc: assuming drive cache: write through
[17342899.732000] SCSI device sdc: 390721968 512-byte hdwr sectors (200050 MB)
[17342899.736000] sdc: Write Protect is off
[17342899.736000] sdc: Mode Sense: 00 38 00 00
[17342899.736000] sdc: assuming drive cache: write through
[17342899.736000]  sdc: sdc1 sdc2 sdc3
[17342899.756000] sd 11:0:0:0: Attached scsi disk sdc
[17342899.756000] sd 11:0:0:0: Attached scsi generic sg2 type 0
[17342900.048000] NTFS-fs warning (device sdc1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[17342900.368000] NTFS volume version 3.1.
[17342901.444000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17342911.956000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17342911.956000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17343118.128000] usb 2-2: USB disconnect, address 12
[17343119.376000] usb 2-2: new high speed USB device using ehci_hcd and address 13
[17343119.508000] usb 2-2: configuration #1 chosen from 1 choice
[17343119.508000] scsi12 : SCSI emulation for USB Mass Storage devices
[17343119.508000] usb-storage: device found at 13
[17343119.508000] usb-storage: waiting for device to settle before scanning
[17343120.648000] usb 2-2: USB disconnect, address 13
[17343122.400000] usb 2-2: new high speed USB device using ehci_hcd and address 14
[17343122.532000] usb 2-2: configuration #1 chosen from 1 choice
[17343122.532000] scsi13 : SCSI emulation for USB Mass Storage devices
[17343122.532000] usb-storage: device found at 14
[17343122.532000] usb-storage: waiting for device to settle before scanning
[17343124.816000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17343124.816000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17343127.532000] usb-storage: device scan complete
[17343127.532000]   Vendor: ST320082  Model:             4LJ2  Rev: 3.01
[17343127.532000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17343127.536000] SCSI device sdc: 390721968 512-byte hdwr sectors (200050 MB)
[17343127.536000] sdc: Write Protect is off
[17343127.536000] sdc: Mode Sense: 00 38 00 00
[17343127.536000] sdc: assuming drive cache: write through
[17343127.540000] SCSI device sdc: 390721968 512-byte hdwr sectors (200050 MB)
[17343127.540000] sdc: Write Protect is off
[17343127.540000] sdc: Mode Sense: 00 38 00 00
[17343127.540000] sdc: assuming drive cache: write through
[17343127.540000]  sdc: sdc1 sdc2 sdc3
[17343127.548000] sd 13:0:0:0: Attached scsi disk sdc
[17343127.548000] sd 13:0:0:0: Attached scsi generic sg2 type 0
[17343128.152000] NTFS-fs warning (device sdc1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[17343128.392000] NTFS volume version 3.1.
[17343128.600000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17343198.520000] usb 2-2: USB disconnect, address 14
[17343200.020000] usb 2-2: new high speed USB device using ehci_hcd and address 15
[17343200.156000] usb 2-2: configuration #1 chosen from 1 choice
[17343200.156000] scsi14 : SCSI emulation for USB Mass Storage devices
[17343200.156000] usb-storage: device found at 15
[17343200.156000] usb-storage: waiting for device to settle before scanning
[17343201.740000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17343201.740000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17343202.048000] usb 2-2: USB disconnect, address 15
```
Thanks for the help.

---

### Post by dcstar on 2007-02-14
> **m.musashi said:**
> Okay, did that. It printed more stuff than the terminal would hold (even scrolling all the way to the top never got to the beginning) but most of it looked unrelated to I'm just posting the bottom portion. Hope that is what is important.
```
[17342212.836000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17342418.520000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17342418.520000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
.......
**[17343198.520000] usb 2-2: USB disconnect, address 14**
[17343200.020000] usb 2-2: new high speed USB device using ehci_hcd and address 15
[17343200.156000] usb 2-2: configuration #1 chosen from 1 choice
[17343200.156000] scsi14 : SCSI emulation for USB Mass Storage devices
[17343200.156000] usb-storage: device found at 15
[17343200.156000] usb-storage: waiting for device to settle before scanning
[17343201.740000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17343201.740000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
**[17343202.048000] usb 2-2: USB disconnect, address 15
```**
Thanks for the help.

These seem to be the problem, the USB bus is dropping off (for some reason) and then restarting.

If you get into your BIOS and change some of the current USB settings, then possibly things may get better (or worse.......)

I can only think that there is some incompatibility with your hardware and the kernel, this may be fixed in a newer kernel version but who can wait for such things........

The **setkeycodes** messages are another issue, I don't know if they are related but they seem to appear each time the USB bus resets, maybe because you have a USB keyboard?

I'm also wondering if your USB ports are capable of providing enough power for whatever you have plugged into them at the moment?

---

### Post by m.musashi on 2007-02-14
There aren't too many USB settings in the BIOS - just enable legacy support I think. The keyboard is USB but it's connected to the PS2 ports with an adapter so I don't think that's related. The drive does have external power so I would hope that is sufficient. This is a regular interal drive though. I just have it in an external enclosure. However, I don't think I ever had the same problem with a regular portable mini drive that runs on USB only, so maybe it is something to do with the drive or the case. I'll take a look but I'm not sure what to look for. As long as it turns on I figure it's working.

EDIT: Okay, I tried a different cable in a different port and it went about 5 min before the problem showed up. Before it only took about a minute. Maybe a coincidence, I don't know. However, since I still have the problem I'm guessing it's not cable or port related.

EDIT2: Just verified that the problem exists on an edgy laptop as well. I guess I should try it in windows and see what happens. However, it is sounding like a hardware problem.

---

### Post by slyboots on 2007-04-07
After some minutes remove my Ubuntu Edgy with all actualy updates my HDD from PC and connect next back with error msg unsafe device removal. 

Previously wasnt this issue occured by my pc, but now (without any changes in settings) is this issue occured. 

In windows isnt this issue. So i think it is linux SW problem. 

After geting ON the /Administration/Services/Hard Disk Tuning (hdparm) is no more this issue occured.

---

### Post by m.musashi on 2007-04-08
In my case I verified it's a hardware problem. The drive enclosure is defective. The USB connection won't work but the eSATA does.

---

