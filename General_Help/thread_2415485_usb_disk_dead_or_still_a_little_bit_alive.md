---
title: "usb disk: dead or still a little bit alive?"
date: 2019-03-26
forum: General Help
---

### Post by matrooswolf on 2019-03-26
Hi everybody,

I have a usb 3TB disk that suddenly went dead. Is there a way to revive it and still get data from it?

It doesn't show up if I simply plug it in. But strangely ```
dsmeg
```gives```
38.238185] EXT4-fs (mmcblk0p1): mounted filesystem with ordered data mode. Opts: (null)
[ 1530.052177] usb 1-1: new high-speed USB device number 5 using xhci_hcd
[ 1530.221222] usb 1-1: New USB device found, idVendor=1058, idProduct=0827
[ 1530.221233] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[ 1530.221240] usb 1-1: Product: My Passport 0827
[ 1530.221246] usb 1-1: Manufacturer: Western Digital
[ 1530.221252] usb 1-1: SerialNumber: 5758423144363537504E5444
[ 1530.266453] usb-storage 1-1:1.0: USB Mass Storage device detected
[ 1530.266912] scsi host3: usb-storage 1-1:1.0
[ 1530.267145] usbcore: registered new interface driver usb-storage
[ 1530.270281] usbcore: registered new interface driver uas
[ 1531.296866] scsi 3:0:0:0: Direct-Access     WD       My Passport 0827 1021 PQ: 0 ANSI: 6
[ 1531.297486] scsi 3:0:0:1: Enclosure         WD       SES Device       1021 PQ: 0 ANSI: 6
[ 1531.299684] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 1531.300690] scsi 3:0:0:1: Attached scsi generic sg3 type 13
[ 1531.304845] sd 3:0:0:0: [sdb] Spinning up disk...
[ 1532.320193] .
[ 1539.338746] scsi 3:0:0:1: Failed to get diagnostic page 0x1
[ 1539.338765] scsi 3:0:0:1: Failed to bind enclosure -19
[ 1539.338829] ses 3:0:0:1: Attached Enclosure device
[ 1540.352075] .
[ 1541.376232] .
[ 1542.400193] .
[ 1543.424048] .
[ 1544.448210] .
[ 1545.472206] .
[ 1546.496098] .
[ 1547.520025] .
[ 1548.544113] .
[ 1549.568100] .
[ 1550.592076] .
[ 1551.616209] .
[ 1552.640094] .
[ 1553.664089] .
[ 1554.688119] .
[ 1586.284691] usb 1-1: reset high-speed USB device number 5 using xhci_hcd
[ 1586.433903] ready
[ 1766.449251] sd 3:0:0:0: timing out command, waited 180s
[ 1946.465965] sd 3:0:0:0: timing out command, waited 180s

```

So the disk is recognized, WD, with serial number and all, but then goes dead.

I don't know what 'failed to get diagnostic page' of 'failed to bind enclosure' mean...

Anybody any ideas? All help would be greatly appreciated...

---

### Post by TheFu on 2019-03-26
Did the disk actually spin up or not?  If you touch the enclosure, does it feel like it is spinning?

Install **smartmontools**, then run **smartctl -t short /path/to/device**  ... which was /dev/sdb in your post above.  That can change.  A short test will take between 1 and 120 minutes.  After that finishes, we have to ask for the test data.  **smartctl -a /path/to/device** will show it.  Post that data as you've done done using code tags.

Some USB controllers need special options to smartctl.  
If your BIOS doesn't have SMART enabled, you need to change that setting.

SMART data will provide some facts to say if the disk, the controller, or the cable is causing issues.  But it isn't perfect and 22% of the time, disks don't work without anything wrong showing in the SMART data.

---

### Post by matrooswolf on 2019-03-26
The disk does not seem to be spinning.

```
smartctl -t short /path/to/device
``` gives: no such device. (I replaced with the correct path).

dsmeg now give this: an I/O error on sector 0
It stops after spinning up disk...

```
[ 8812.654865] usb 2-1: USB disconnect, device number 2
[ 8812.790535] sd 3:0:0:0: [sdb] Synchronizing SCSI cache
[ 8812.830039] print_req_error: I/O error, dev sdb, sector 0
[ 8812.838013] print_req_error: I/O error, dev sdb, sector 0
[ 8813.014026] sd 3:0:0:0: [sdb] Synchronize Cache(10) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 8882.826450] usb 1-1: new high-speed USB device number 6 using xhci_hcd
[ 8882.995627] usb 1-1: New USB device found, idVendor=1058, idProduct=0827
[ 8882.995637] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[ 8882.995644] usb 1-1: Product: My Passport 0827
[ 8882.995650] usb 1-1: Manufacturer: Western Digital
[ 8882.995656] usb 1-1: SerialNumber: 5758423144363537504E5444
[ 8882.996647] usb-storage 1-1:1.0: USB Mass Storage device detected
[ 8883.000402] scsi host3: usb-storage 1-1:1.0
[ 8884.023308] scsi 3:0:0:0: Direct-Access     WD       My Passport 0827 1021 PQ: 0 ANSI: 6
[ 8884.023739] scsi 3:0:0:1: Enclosure         WD       SES Device       1021 PQ: 0 ANSI: 6
[ 8884.025855] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 8884.026377] ses 3:0:0:1: Attached Enclosure device
[ 8884.027491] ses 3:0:0:1: Attached scsi generic sg3 type 13
[ 8884.029208] sd 3:0:0:0: [sdb] Spinning up disk...

```

---

### Post by TheFu on 2019-03-26
What command did you try, exactly?

Regardless, without any data, your guess is as good as mine.

---

### Post by Autodave on 2019-03-26
I would try another port first.  Then, another cable.  Then try it on another machine.

---

### Post by TheFu on 2019-03-26
> **Autodave said:**
> I would try another port first.  Then, another cable.  Then try it on another machine.

Excellent ideas. Try the front USB panels and the rear ones.  If it is a laptop, try USB2 on the left and right side. Often, these go through different controllers.

Best case would be that it has a bad cable.

---

### Post by dragonfly41 on 2019-03-26
> [COLOR=#000000]I have a usb 3TB disk that suddenly went dead.[/COLOR]

Does this usb drive have an external power source?

---

### Post by matrooswolf on 2019-03-27
Hi,

I've tried all this to rule nothing out, changed usb port, computer, tried another disk on the same port, other cables... All works normal, except for the disk. It's powered by usb, no other source.

Strange thing is that the disk is recognized correctly by dsmeg, but doesn't show up. Light is blinking also. But that's it.

Was wondering if there was some way to still access the disk. I don't understand the errors that dsmeg gives....

---

### Post by dragonfly41 on 2019-03-27
I used this search pattern in google and found quite a few hits ..

```
WD My Passport NEAR Ubuntu NEAR Failed to get diagnostic page
```

"NEAR" is a google search operator in advanced search.

This WD My Passport device uses encryption.

Here is just one of many links from google search.

[https://askubuntu.com/questions/1098436/wd-my-passport-usb-drive-not-recognized](https://askubuntu.com/questions/1098436/wd-my-passport-usb-drive-not-recognized)

---

### Post by matrooswolf on 2019-03-31
Hi, 
The disk doesn't use encryption, I've reformated in ext4. There are indeed many links, and I've read a few of them, but I don't seem to find something that answers my question why the disk is recognized by the system, but is not showing up in Disks or Nemo.

There's an I/O error on sector 0 it says, but what does it mean, and is there a way to fix that?

---

### Post by Autodave on 2019-03-31
Generally, that means that you are probably not going to be able to recover anything from it.

If you are not worried about recovery, then the next thing that I would do is to try and reformat it: you might be able to and get some more use out of it.  If Linux won't format it, try Windows and NTFS first.

---

### Post by ubfan1 on 2019-03-31
Try a USB Y connector, to get power from two USB ports.  If the disk is really not spinning up, it might be freed up with a tap, say from a pencil with an eraser on the end.  Be ready to copy everything off the disk if you can get it spinning again.  Then check with WD about replacement -- might be a known problem with certain disks (it has happened before).

---

### Post by Autodave on 2019-03-31
Sorry: I forgot about it not spinning.  Try what ubfan1 suggested.  I also have gotten them to spin trying the following:

First, without power to it, try tapping it on the edges.  Don't slam it, but it will take a bit of a knock, ON THE EDGE, without hurting anything.
Second: with it powered, try twisting the drive.  You would/could hold it flat on the desk and rotate it back and forth quickly.

---

### Post by him610 on 2019-03-31
You could remove the external drive and install it in a desktop-type computer, if available, to see if you can get it to spin up.

---

### Post by matrooswolf on 2019-04-01
I got the disk spinning again with tapping on it and turning it around a bit, so that worked. But it sizzled out after a minute or so. And it still didn't show up in /media/username/

It's still under warranty, so I can have it replaced. WD is actually very easy on that. But it would be nice to recover some of the info if possible of course, before sending it in...

---

### Post by Autodave on 2019-04-01
Unless you can get it spinning and keep it spinning, you will not recover anything.  At this point, you have nothing to lose.  Try tapping, twisting again.  Can you open the case and make sure that all connections are tight?  (Please don't open it if that voids your warranty.)

---

### Post by rbmorse on 2019-04-01
Long shot, but it's worked for me (occasionally) in the past:  remove the drive, place inside a plastic freezer bag and put the bag in the freezer for about 4 hours or so. 

If the drive is recognized after this it will probably quit again when it warms up, so be quick about pulling critical data off the device.

---

### Post by matrooswolf on 2019-04-01
I'll try tapping and twisting again, and some incantations probably, but I'm not going to open it, as I have to send it back to get a replacement disk. Would love to though...

---

### Post by TheFu on 2019-04-01
Inside the USA, removal of the "Void if removed" does NOT invalidate the warranty.  The FTC found that condition to be illegal.
 [https://www.digitaltrends.com/computing/ftc-warranty-stickers-illegal/](https://www.digitaltrends.com/computing/ftc-warranty-stickers-illegal/)
 [https://www.ftc.gov/news-events/press-releases/2018/04/ftc-staff-warns-companies-it-illegal-condition-warranty-coverage](https://www.ftc.gov/news-events/press-releases/2018/04/ftc-staff-warns-companies-it-illegal-condition-warranty-coverage)

Obviously, other legal jurisdictions will have different rules.

A non-spinning disk could be a controller or power in the controller failure, so if you pull the disk out of the external USB case, then it might be possible to directly connect it internally via SATA and pull the data off.  Or use some other USB adaptor with the HDD.  

If you had a backup, this would be a minor inconvenience, not a data loss incident or any reason to worry about shipping any personal data to some company for a refurbish replacement.  I use encryption on portable devices, including USB storage.  Really should use encryption on all storage just for my piece of mind, should a disk in warranty fail.  I'd have no problem sending a LUKS encrypted disk to the vendor.  Between regular storage and virtual storage on disk, I'd rather not send that data unencrypted anywhere.

---

### Post by matrooswolf on 2019-04-02
Well, I think I'll give up. RIP.

I can hear and feel it spinning for about a minute when I give it a tap, but then it dies. When I put my ear on it, I also can hear a kind of click inside, three, four times before it dies...

---

### Post by dragonfly41 on 2019-04-02
A last resort is to place the drive in a separate external USB drive container (compatible with your drive) - importantly with its own dedicated power supply.  Sometimes there is insufficient power available from PC USB ports.  This is not wasted cost since you can use the USB container later to hold a backup drive.

This [video clip]("https://www.grc.com/sr/whatitdoes.htm") explains about failing disks but unfortunately SpinRite only works on Windows.

---

