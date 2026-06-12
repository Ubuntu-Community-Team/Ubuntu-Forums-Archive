---
title: "MTP not detecting phone"
date: 2013-02-24
forum: General Help
---

### Post by dave0109 on 2013-02-24
I've searched far and wide looking for answers on how to connect my phone (Motorola Razr XT890 running Android 4.0) to Ubuntu for transferring files.

I can sometimes get it to work using PTP mode, but it's very hit and miss.  I keep coming back to try MTP mode, but nothing happens and the device is not even listed.

All the help I've found, starts with running mtp-detect to get information about the attached device, but when I run that, there are no devices listed.

```
$ mtp-detect
libmtp version: 1.1.4

Listing raw device(s)
   No raw devices found.

```

I've tried adding the udev rules to open up the permissions, but that appears to have no effect with mtp-detect.  The only difference is that with dmesg, I can see usbcore registering the device for USB Mass Storage, which of course, doesn't work with Android 4.

```
[  435.864745] usb 2-1.3.2: new high-speed USB device number 7 using ehci_hcd
[  435.976972] usb 2-1.3.2: New USB device found, idVendor=22b8, idProduct=710f
[  435.976977] usb 2-1.3.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  435.976980] usb 2-1.3.2: Product: XT890
[  435.976983] usb 2-1.3.2: Manufacturer: Motorola
[  435.976985] usb 2-1.3.2: SerialNumber: XXXXXXX
[  436.017978] Initializing USB Mass Storage driver...
[  436.018263] scsi8 : usb-storage 2-1.3.2:1.0
[  436.018356] usbcore: registered new interface driver usb-storage
[  436.018357] USB Mass Storage support registered.
[  437.016415] scsi 8:0:0:0: CD-ROM            Motorola XT890            0001 PQ: 0 ANSI: 2
[  437.020109] sr1: scsi-1 drive
[  437.020261] sr 8:0:0:0: Attached scsi CD-ROM sr1
[  437.021815] sr 8:0:0:0: Attached scsi generic sg3 type 5

```

```
$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 06a3:8021 Saitek PLC Eclipse II Keyboard
Bus 002 Device 004: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 005: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 006: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 008: ID 22b8:710f Motorola PCS 

```

Any other thoughts on what I could try?

---

### Post by DeMus on 2013-02-24
Just to make sure, did you switch on the USB connection in your phone and set it to USB storage? I use Android 2.3.6 and I need to do that. Normally it is set to Charging only.
When you do that with the cable connected, the computer should see a new disc which it offers to mount.
I get the same results as you do, also the no RAW devices found, but with lsusb it is there.
Check to see if the USB connection in your phone is set to USB storage, or similar name in Android 4.

---

### Post by bro on 2013-02-24
There is a recent problem with newer android versions no longer automatically mounting properly. Have searched so far and wide as to install this ppa? [https://launchpad.net/~langdalepl/+archive/gvfs-mtp](https://launchpad.net/~langdalepl/+archive/gvfs-mtp) 

That solved it for me.

---

### Post by dave0109 on 2013-02-25
@DeMus - Android 4 no longer has the USB storage option.  There's only MTP or PTP.

@bro - no, I haven't seen that before.  Thanks, I shall check it out.

---

### Post by dave0109 on 2013-02-25
Alas, no joy...

```
$ mtp-detect
Error: Unable to open ~/.mtpz-data for reading.
libmtp version: 1.1.5

Listing raw device(s)
   No raw devices found.
```

---

### Post by davea88 on 2013-02-25
See
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/903422](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/903422)
The Langdalepl ppa has not worked for me, so far.

---

### Post by MoebusNet on 2013-02-26
This is the best general explanation I've found so far:

[http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access)

I have read that this will be addressed in Ubuntu 13.04 (fingers crossed)

---

### Post by 3rdalbum on 2013-02-26
Until 13.04, my father found it's easiest to do the following:

1. Set your Android phone/tablet to use a static IP address when connecting to your wifi
2. Install one of those FTP server apps on your phone
3. Connect to the FTP server on your phone, from your computer. Add a bookmark to the phone's FTP server.

Unfortunately, Linux's MTP support sucks. It's been terrible for a few years now and I'm sure it will still be terrible after 13.04, but at least Android phones should mount then.

---

### Post by clive littlewood on 2013-02-26
Hi

Try AIRDROID in the play store.

This connects your phone through a browser page.

You can then transfer files both ways between phone and PC.

Very secure and works a treat !!!!

Hope this helps

Clive

---

### Post by dave0109 on 2013-02-26
@davea88 - thanks, I'm watching with interest.

> **clive littlewood said:**
> Very secure and works a treat !!!!
Ahem, have you *seen* the permissions that app requires?! ;)

---

### Post by pulpo69 on 2013-02-27
another option [http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html](http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html)

---

### Post by dave0109 on 2013-03-11
Thanks for all the replies.  None of the above helped.  I did hack the rules for the libmtp install to recognise my phone's USB device codes, but that didn't help mtp-detect at all.

---

### Post by TheByteSmasher on 2013-03-24
Gvfs-mtp recently stopped working mounting my nexus 4 and nexus 7 following an Ubuntu GVFS update. It had worked flawlessly until then. The devices will connect in PTP mode but not MTP... Help? Ubuntu 12.10

---

