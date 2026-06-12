---
title: "Importing from camera: &quot;could not claim the usb device&quot;"
date: 2008-05-06
forum: General Help
---

### Post by Stanver on 2008-05-06
I just tried to import some pictures from my Canon A80, using F-Stop.
F-stop saw the A80 (which communicates by PTP, does not mount like a disk). But upon initiating the download I got an error message: "could not claim the usb device". Similar difficulty with digiKam. I do not have such trouble with other USB devices.

Did some spelunking in the bug reports, which turned up bug #205767: [Hardy Heron Beta] can't import photos from Canon A540.

That thread gives a workaround: issue the command "sudo chown -R :plugdev /dev/bus/usb" . This works because the USB device is in fact given the wrong owner upon mounting (should be plugdev, is given root).

I find this greatly annoying because I must now type that silly command in a terminal every time I want to import some pictures.

My question: does anyone know a more permanent and convenient solution? System is Kubuntu 8.04 release version, not beta, on 32-bit Intel.

Thanks.

---

### Post by smcleish on 2008-05-17
I had the same problem on upgrade to 8.04 and solved it based on instructions in [http://ubuntuforums.org/showthread.php?p=4916040#post4916040](http://ubuntuforums.org/showthread.php?p=4916040#post4916040)

Even when the camera gave this error, I could still find it:

```
$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 006: ID 04a9:30b1 Canon, Inc. PowerShot S70 (normal mode) / PowerShot S70 (PTP mode)
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

This gives the vendor ID (04a9 in my case) and model ID (30b1 ditto) that are used to make a change in /etc/udev/rules.d/40-permissions.rules. Open this file to edit:

```
$ sudo gedit /etc/udev/rules.d/40-permissions.rules
```

and then find the section between 

```
LABEL="usb_serial_start"
```

and

```
LABEL="usb_serial_end"
```

In this section add the lines:

```
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="30b1", \
					MODE="0666", GROUP="plugdev"
```

(using your IDs from the lsusb output). This mounts as world read-writable, to restrict access to plugdev group only, use MODE="0660".

Hope this works for you too!

---

### Post by Stanver on 2008-05-17
This works! Even if it is more like a work-around than a generic solution, since one would have to hack this config file for every single type of non-disk USB device that you'd ever want to plug in. Hopefully the Ubuntu people will come up with a more permanent solution.

But: it works, so thank you!

---

### Post by User101 on 2008-06-23
Thanks, smcleish, it works. =D>

Now, if there were only some way to specify "any vendor, any product"...

---

### Post by dnile on 2008-06-26
Thank you worked for me as well!!

---

### Post by Timbers2k on 2009-02-18
Are they ever going to fix this problem? I just did a fresh install of 8.10 for my daughter and had this same issue. On my gentoo box there is a 70-libgphoto2.rules files that gets installed with libgphoto that includes a buttload of rules for cameras. Why doesn't Ubuntu use this same system?

---

