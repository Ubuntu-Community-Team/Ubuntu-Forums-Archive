---
title: "ipod not mounted or recognized in dapper?"
date: 2007-01-28
forum: General Help
---

### Post by lime4x4 on 2007-01-28
My neice just got a ipod nano. I have her setup on ubuntu dapper.When ever she plugs the ipod into the usb port nothing happens and the only thing shown on the ipod is "Do Not Disconnect" which stays there for hours until she unplugs it.The ipod works fine when hooked up to a windows machine.From what i've read dapper should place an icon on here desktop whenever the ipod is connected. So any ideas where to start looking for the glitch as to why it's not being mounted?

---

### Post by rainwalker on 2007-01-28
Try installing Amarok, it's a REALLY nice audio player and it has iPod support as well. To learn more about it go to 
[http://en.wikipedia.org/wiki/Amarok_%28audio%29](http://en.wikipedia.org/wiki/Amarok_%28audio%29)

---

### Post by bettlebrox on 2007-01-29
Check to see if her userid a member of the plugdev group? You need to be a member of the group to mount iPods and other devices. Then you can go to the "removeable drives & media" settings dialog and set it like this screenshot and it should automount and start gtkpod:

[http://www.flickr.com/photos/timony/268864585/](http://www.flickr.com/photos/timony/268864585/)

---

### Post by lime4x4 on 2007-01-29
yes she is  a member of that group. I tried the gtkpod and amarok and both don't work.So how do i make sure that sbp2 module is loading?

---

### Post by bettlebrox on 2007-01-29
> **lime4x4 said:**
> yes she is  a member of that group. I tried the gtkpod and amarok and both don't work.So how do i make sure that sbp2 module is loading?
Disconnect the iPod and:

sudo modprobe sbp2

THen reconnect the iPod and see what happens. Look at the output of dmesg to see if the system recognises the iPod. U should see something like this:

```
Jan 29 00:58:56 localhost kernel: ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
Jan 29 00:58:56 localhost kernel: ieee1394: sbp2: Try serialize_io=0 for better performance
Jan 29 00:59:07 localhost kernel: usb 2-2: new high speed USB device using ehci_hcd and address 10
Jan 29 00:59:07 localhost kernel: usb 2-2: configuration #1 chosen from 2 choices
Jan 29 00:59:07 localhost kernel: scsi15 : SCSI emulation for USB Mass Storage devices
Jan 29 00:59:12 localhost kernel:   Vendor: Apple     Model: iPod              Rev: 1.62
Jan 29 00:59:12 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan 29 00:59:12 localhost kernel: SCSI device sdb: 7999487 512-byte hdwr sectors (4096 MB)
Jan 29 00:59:12 localhost kernel: sdb: Write Protect is off
Jan 29 00:59:12 localhost kernel: SCSI device sdb: 7999487 512-byte hdwr sectors (4096 MB)
Jan 29 00:59:12 localhost kernel: sdb: Write Protect is off
Jan 29 00:59:12 localhost kernel:  sdb: sdb1 sdb2
```
Also, type in mount to see if has been mounted. You will also need to have the gnome-volume-manager running (I presume your using Gnome?).

To make sure sbp2 is loaded at boot time, you can add it to /etc/modules .

---

### Post by Beamvr6 on 2007-01-29
Sorry for threadjacking but I had the same question and output of dmesg proves the borrowed iPod I am using is recognized. Banshee despite a recent version (0.11.4) with all plugins doesn't see it. Could this be cause my iPod has a Mac file system? Or something else wrong?

edit:

The iPod is visible as a device in Nautilus bit can't copy files from the iPod although the whole filesystem there is visible. Also Banshee will start when connecting the iPod first time after logout/login but does not see no iPod.

---

### Post by lime4x4 on 2007-01-29
well it's not being mounted

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)

and nothing shows up in dmesg either

---

### Post by bettlebrox on 2007-01-29
4x4: add sbp2 to your /etc/modules, reboot and try again.

beam: I don't use banshee so I'm not sure. But, I don't see any options in the Banshee menus for iPod support so maybe Ubuntu doesn't have it compiled in?

---

### Post by lime4x4 on 2007-01-29
it's already there. Don't know how i never added it.

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
sr_mod

---

### Post by Beamvr6 on 2007-01-30
> But, I don't see any options in the Banshee menus for iPod support so maybe Ubuntu doesn't have it compiled in?

There is a Banshee plugin for iPod support and after reading a lot on the forums I learned Banshee should work with iPod. I also learned that differences in file system cause problems, I am still interested however if a Mac formatted iPod can work with Ubuntu (6.0.6)?

TIA

---

### Post by bettlebrox on 2007-01-30
> **Beamvr6 said:**
> There is a Banshee plugin for iPod support and after reading a lot on the forums I learned Banshee should work with iPod. I also learned that differences in file system cause problems, I am still interested however if a Mac formatted iPod can work with Ubuntu (6.0.6)?

TIA
I don't have one with Apple's filesystem to test. But, you'll need either the hfs or hfsplus modules loaded to access a Mac formatted iPod.

---

### Post by bettlebrox on 2007-01-30
> **lime4x4 said:**
> it's already there. Don't know how i never added it.

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
sr_mod

Try rebooting your system with the iPod plugged in and see if it detects it.

 I do rem that the first time I tried to get a Linux system to see my iPod took a fair bit of work, but that was 2 or 3 years ago. With Ubuntu on my laptop I don't remember having to do too much work to get it to connect.

Also, I think the ieee1394 & ohci1394 modules need to be loaded too, but hotplug usually takes care of all that.

---

