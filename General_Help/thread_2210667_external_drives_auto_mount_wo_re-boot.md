---
title: "external drives auto mount w/o re-boot"
date: 2014-03-12
forum: General Help
---

### Post by keith14 on 2014-03-12
Hi,
I wanted to have both external HD and flash drives automatically detected (whether they were present on boot-up or not). I did the following:
(only showing external drive).
sudo fdisk -l
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001    c  W95 FAT32 (LBA)

I do not see this drive in media. ls /media -> keith
looked on line tried:
sudo mkdir /media/external
sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137
ls /media -> external  keith  usb  usb0  usb1  usb2     usb3  usb4  usb5  usb6  usb7

Yes now I see HD in /media/external.

Subsequent boot-ups I plug in the HD and get the following:   (don't know how to cut/paste pic in this window so will just remit the text)

Unable to mount Transcend
Device /dev/sdb1 is already mounted at /media/usb0

The HD is R/W via usb0, all is ok except the error pop-up box.
thanks,
Keith

---

### Post by tfrue on 2014-03-12
When you use the mount command, it's only valid per that sessions; so if you reboot, the previous mount command executed does not work.

You need to edit the /etc/fstab, as root, and that will solve your problem.

Here is a link to the fstab page:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

It's much better to mount device's by their UUID since it's a unique number assigned to every device, to find out a devices UUID (With the drive plugged in), type:
```

sudo blkid

```
and copy the UUID for that specific drive.

In short, open a terminal and type (I use vim as the text editor, but you can use nano or gedit. If you use gedit, type "gksu gedit /etc/fstab"):
"#" are used to comment code so you can write notes, known as comments, to yourself and to others.
```

sudo vim /etc/fstab
#External drive
UUID=<devices UUID> /media/external vfat uid=1000,gid=1000,utf8,dmask=0027,fmask=0137 0 0

```

Generally what I do is this:
```

#My general way of mounting external and flash drives
UUID=<devicesUUID> /path/to/directory auto defaults 0 0

```
This will automagically detect the FS type and use the default options, which the defaults options are: rw, suid, dev, exec, auto, nouser, and async.

After this, you will need to either do a system reboot or un-mount the drive, then unplug the drive, and finally plugging the drive back in.

Chris

---

### Post by keith14 on 2014-03-12
Hi Chris,
thanks for responce.
I only entered the mount command once. The error box comes up automatically once the drive is plugged in. /media maintained all the entries shown after the initial mount command. unbuntu just reassigned /media/external with /media/usb0. 
edited /etc/fstab to add:UUID=12DC-067E /media/external auto defaults 0 0
re-booted and got the message (whole screen) waiting answer to whether to continue w/o the specified drive not there. It wasn't and usually will not be.
I use fs commands and drive status in perl to select drives in win*. perl makes it easy to look at external drives. Using multiple pc's I try to keep on same page with scripts by dumping the content of common paths to external drives ($HOME/[bin/, profile, environ, _vimrc ...]. This is working with win* and looking to make this work in ubuntu. This info is stored on external drives in the respective pc's allocated space via script.
The usb ports are not constant, be nice to discern which ports are candidates for use and prompt the user if necessary (more than one choice).
I looked into lsusb also for common ground but not sure the connection B/W the report and media/usb[7:0] 
The goal is plug in drive, run perl script to locate suitable drives to use (will often only be one) and then dump files to the drive known source locations and or specified ones.
keith

---

### Post by ajgreeny on 2014-03-12
I think you need to change the fstab entry to 
UUID=12DC-067E /media/external [COLOR=#ff0000]no[/COLOR]auto defaults 0 0

That my be all that is needed.  See [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) for more details of fstab entries.

---

### Post by tfrue on 2014-03-12
You could do what ajgreeny said, but the "noauto" option is in the wrong place. You would actually put the "noauto" option like:
UUID=12DC-067E /media/external auto defaults,noauto 0 0

This way the system won't try and automount it at boot. Where he placed noauto is where the FS type goes.

/etc/fstab is laid out:

<device> <mount point> <File System type> <options> <dump> <pass>

Why don't you learn what each external drives UUID, since it won't matter what usb port you use, and have the perl script parse, or grep, the blkid command looking for the specific UUID, then dump to that drive? Just a thought...

Chris

---

### Post by Morbius1 on 2014-03-12
> Unable to mount Transcend
Device /dev/sdb1 is already mounted at /media/usb0
This hasn't come up in a while. The only utility that I know of that would mount to /media/usb0-7 is usbmount or something that has usbmount as a dependency.

Whatever you have in fstab concerning those usb devices will be ignored as long as that package is installed so unless you need it for some other reason remove it:
```
sudo apt-get remove usbmount
```

---

### Post by ajgreeny on 2014-03-12
> **tfrue said:**
> You could do what ajgreeny said, but the "noauto" option is in the wrong place. You would actually put the "noauto" option like:
UUID=12DC-067E /media/external auto defaults,noauto 0 0

This way the system won't try and automount it at boot. Where he placed noauto is where the FS type goes.

/etc/fstab is laid out:

<device> <mount point> <File System type> <options> <dump> <pass>

Why don't you learn what each external drives UUID, since it won't matter what usb port you use, and have the perl script parse, or grep, the blkid command looking for the specific UUID, then dump to that drive? Just a thought...

Chris
Thanks for the correction; I answered in a hurry and didn't stop to check, but I did notice the auto option which I knew was not needed.

Also I was unaware of the usbmount package, so thanks to Morbius for that info.

---

### Post by tfrue on 2014-03-12
No problem, ajgreeny! I've never heard of that either.

---

### Post by keith14 on 2014-03-21
Looking online for fsutil program for linux (ubuntu) I found [http://terasaur.org/item/show/fsutil-1-8/2061](http://terasaur.org/item/show/fsutil-1-8/2061) but not sure how to use same.

---

### Post by Morbius1 on 2014-03-21
And you want to install fsutil because ...................?

---

### Post by keith14 on 2014-03-21
ok I use lsusb but I don't know what drives are; example I plug in HD and it will auto mount to /media/usb0 . lsusb reports:
Bus 002 Device 005: ID 0a5c:5801 Broadcom Corp. BCM5880 Secure Applications Processor with fingerprint swipe sensor
Bus 002 Device 004: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 002 Device 006: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. JM20329 SATA Bridge
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Where is the idea that the HD is mounted under /media/usb0  ?

---

### Post by Morbius1 on 2014-03-22
> **keith14 said:**
> Where is the idea that the HD is mounted under /media/usb0  ?
From your original post:
> Unable to mount Transcend
Device /dev/sdb1 is already mounted at /media/usb0
To my knowledge the only thing that does that by default is the usbmount package.

---

