---
title: "Question about harddrive: Can I do this..."
date: 2007-01-12
forum: General Help
---

### Post by Oki on 2007-01-12
_... without risking of loosing data?_

1.Open the /etc/fstab and add a # argument i front of a SATA harddrive witch are in use, but as an backup drive. 
2.Run the sudo mount -a
3.Then turn of the power – _but only for this disk_ (meaning: Ubuntu will not be powered of). 


In Windows you will need a USB disk for doing this, so I am wondering if I can do this also with a SATA disk – in Linux? And yes, I am thinking about giving the disk a psu for itself(via wires that is). 

Thank you for any help - and sorry if this is a dumb question

---

### Post by broughcut on 2007-01-12
I am the person who spent hours wondering why commented out drives in fstab weren't automounting, so, you know, take all this with a grain of salt...

shouldn't you unmount the drive first before editing fstab?

sudo umount /dev/sata - or whatever

if it is busy and can not be unmounted, boot in recovery mode, umount it as root from the command line, edit the fstab, and then reboot into Ubuntu.

That's how I would do it. I don't believe you can lose data by messing with fstab, you may make the operating system unbootable but I think this can usually be fixed by booting up in recovery mode and correcting the errors in fstab with nano. I suppose you could lose data if you turn off a busy drive, so unmount it first.

---

### Post by brt on 2007-01-12
No.

If you do it like this the drive will still be mountet.

If you want to unmount a partition just use:

```
sudo umount /dev/<device-name>
```

or

```
sudo umount /path/to/mountpoint
```

if /dev/<device-name> -> /path/to/mountpoint mapping is still present in fstab otherwise this will not work.

* hint *

if its not unmounting instead reports a "Device is busy"-Error, maybe you  have to move out of the mounted directory, eg. if your mountpath is /media/bluedisk and you are currently in /media/bluedisk just type ```
cd ..
``` or ```
cd
``` to move out...

usually i just right-click on the drive-icon on the desktop an choose eject. but this only works with dynamically mounted volumes (mounted as user not fstab or root). this is what happens usually if you plugin in a drive when you are logged into a gnome-session.

---

### Post by Oki on 2007-01-12
So the answer is; if you unmont a disk, even using SATA, then you can turn of the power with no problems. 

That is so cool - am I right, that you cant do that in Winodws?

(I know of hot swap - for you need hardware for this).

---

### Post by tagra123 on 2007-01-12
Check on ebay

USB 2.0 To SATA / IDE Adapter Cable +Power Adapter ISXB

Can backup anything

My friend has one of these and it is very good for portable backups.  Just like a usb drive but with any spare ide or sata drive.

---

### Post by brt on 2007-01-12
> **Oki said:**
> (I know of hot swap - for you need hardware for this).

afaik, most of modern sata controllers support hotswapping.

at anytime you could also try to use hdparm to turn of your drive:

```
sudo hdparm -Y /dev/<device-name>
```

but it may not work with every drive/controller

---

