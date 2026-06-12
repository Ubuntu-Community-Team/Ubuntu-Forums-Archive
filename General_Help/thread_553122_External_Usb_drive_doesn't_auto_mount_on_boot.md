---
title: "External Usb drive doesn't auto mount on boot"
date: 2007-09-17
forum: General Help
---

### Post by CMNetworx on 2007-09-17
I have a somewhat different mounting problem..

I am running Ubuntu Fiesty Fawn 7.04
When I plug in my external usb drive, it will detect it and automatically mount it...

However, After I reboot, even though the drive is still plugged in, it does not mount it again..:mad:

My temporary fix is to simply unplug the usb cable and plug it back in, but this is getting kind of annoying..

Does anyone know a solution to this?
:confused:

---

### Post by raijinsetsu on 2007-09-17
The reason for this is simple:
When you're logged in, there is a Gnome/KDE service responsible for automounting a new USB drive. There is no way to use this during boot. I also don't believe these services support "cold plugging" of devices. "cold plugging" is when the device is plugged in before the system is running.

If you're a little linux saavy, you can change your fstab so that the external drive mounts on boot. But then, you run into trouble with permissions and so fourth.

My suggestion: check the settings for the Gnome/KDE service to see if you can get them to use cold-plugged devices.

*edit*
Also, are you sure that the device is just not showing up on your desktop? Sometimes things get auto-mounted, but the desktop doesn't get updated. Try checking out the /media/ directory to see if you're device is listed there.

---

### Post by Amazona aestiva on 2007-09-17
There is a feature in my BIOS menu called... (default is disabled for me)
Support boot from USB

So check your BIOS configuration. It might help.

---

### Post by CMNetworx on 2007-09-17
There have been no changes to the bios, and I don't need to actually boot from the usb drive, so Im ok there..

The wierd thing is I had a previous installation of ubuntu on this machine and had no trouble with this at all. The usb drive always showed up..

It is not visible in the /media/ folder, All I have are the 2 cdroms..

Here is my fstab..

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=eb63f7f0-387a-44ab-a586-cf7b0bf84cdd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=629faff1-9d92-4433-9688-a7c570320efe none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

The other thing that confuses me is that it seems the drive is actually /dev/sdb
if I type
fdisk -l /dev/sdb
I get 
> Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48640   390700768+   c  W95 FAT32 (LBA)

which is the correct drive..

I have attempted to mount this and discovered I do not know how to correctly use mount..

I am still baffled here, What would I enter into fstab to automatically mount the drive? I thought this didn't have to be done with usb devices..
or where would I tell the machine to look for drives that were plugged at boot?

---

### Post by raijinsetsu on 2007-09-17
That's very odd that an older version would cold-plug the drive, but the newer one won't.
I would do the following:
check the output of "grep /var/log/messages cold" and "grep /var/log/messages usb" for any errors in regards to a usb-hd...

---

### Post by CMNetworx on 2007-11-02
I looked into doing as you said
grep /var/log/messages usb

However it returns me with a message
grep: usb: No such file or director

So I tried
grep /var/log/messages\ usb
and the file is blank, Same with the messages cold file..

I looked in the /var/log folder and I have a few files that start with messages, and they are
messages
messages.0
messages1.gz
messages2.gz
messages3.gz

The compressed messages files have messages.0 in them and they all have a size to them..

BTW I have upgraded to 7.10 Gutsy and I still have the same issue..

---

### Post by jloveless on 2008-02-04
I realize that this thread goes back to May but I am having the same issue today on 7.10 with an HP PMD - basically an external USB drive. It isn't recognized at boot so I need to remove/reinsert. That works fine to mount the drive but it is annoying. How did you resolve this. please.

Many thanks.:confused:

---

### Post by conscious on 2008-02-05
I have the same problem with Ubuntu 7.10 running on an Acer laptop. The worst part is that unplugging and plugging the USB drive does not help. I have the auto-mounting turned on, and it works perfectly with the devices that are not plugged at boot time.

I'd be happy to provide more information. Just tell me what's needed.

EDIT: When booting Ubuntu with USB flash drive inserted (and only in this case), I get the following error message between the splash screen and login screen:
```
* Starting Bluetooth devices
[56.564000] usb-5-1: device not accepting address 4, error -110
[57.100000] usb-5-1: device not accepting address 5, error -110

```

I don't have any bluetooth devices on my laptop.

---

