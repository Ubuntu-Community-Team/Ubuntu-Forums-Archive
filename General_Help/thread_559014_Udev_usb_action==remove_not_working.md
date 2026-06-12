---
title: "Udev usb action==remove not working?"
date: 2007-09-24
forum: General Help
---

### Post by Ardaen on 2007-09-24
Okay, I wrote this udev rule to switch ALSA to use my usb headset when it is plugged in and back when it is unplugged. It works when I connect my headset, but not when I unplug it.

How do I get the ACTION=="remove" part to work? Why doesn't it work?

```
ATTR{product}=="Logitech USB Headset", GOTO="usb_headset_start"
GOTO="usb_headset_end"

LABEL="usb_headset_start"

ACTION=="add", RUN+="/usr/bin/sudo -u #1000 /usr/bin/asoundconf set-default-card Headset"
ACTION=="remove", RUN+="/usr/bin/sudo -u #1000 /usr/bin/asoundconf set-default-card CK804"

LABEL="usb_headset_end"
```

---

### Post by Ardaen on 2007-10-04
Okay well, I guess using the attr{product} only works for connecting the device.

I ran the command udevmonitor command:
```
udevmonitor --udev --environment
```
Which showed udev events when I connected and disconnected my headset.
```
UDEV  [1191530985.608057] remove   /class/input/input13/event1 (input)
UDEV_LOG=3
ACTION=remove
DEVPATH=/class/input/input13/event1
SUBSYSTEM=input
SEQNUM=2956
MAJOR=13
MINOR=65
PHYSDEVPATH=/devices/pci0000:00/0000:00:02.0/usb1/1-6/1-6:1.3
PHYSDEVBUS=usb
PHYSDEVDRIVER=usbhid
UDEVD_EVENT=1
ID_VENDOR=Logitech
ID_MODEL=Logitech_USB_Headset
ID_REVISION=1013
ID_SERIAL=Logitech_Logitech_USB_Headset
ID_TYPE=hid
ID_BUS=usb
ID_PATH=pci-0000:00:02.0-usb-0:6:1.3
DEVNAME=/dev/input/event1
DEVLINKS=/dev/input/by-path/pci-0000:00:02.0-usb-0:6:1.3-event-
```
As you can see, this is an ACTION=remove event with a nice ID_MODEL string that I can use. So I assumed since this was being displayed with the --environment flag on udevmonitor I could access that string with ENV{}

This same ID_MODEL string appeared for both add and remove ACTION events, so I modified my rules file to look like this:
```
ENV{ID_MODEL}=="Logitech_USB_Headset", GOTO="usb_headset_start"
GOTO="usb_headset_end"

LABEL="usb_headset_start"

ACTION=="add", RUN+="/usr/bin/sudo -u #1000 /usr/bin/asoundconf set-default-card Headset"
ACTION=="remove", RUN+="/usr/bin/sudo -u #1000 /usr/bin/asoundconf set-default-card CK804"

LABEL="usb_headset_end"
```


I hope this is of some help to someone.

---

### Post by grof on 2008-01-24
Hello, I have the same problem with my ubuntu 7.10 and my USB headset. Please can you exactly explain how you do that?

I'm tried to write some udev rules but without any effects. It simply do not work. Can you explain me step-by-step instructions??

thanks

---

### Post by kayvan on 2008-06-04
Thanks, you just saved me a lot of time.

Using "udevmonitor --environment" and the hints on this page: [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

I created the following set of rules for my pair of external USB hard drives:

> # Ensure that USB disks are set up in the right way.

# My Backup drive should auto-mount to /media/backup when connected.
#
KERNEL=="sd*", SUBSYSTEMS=="scsi", ATTRS{vendor}=="ST330063", SYMLINK+="usb/daily%n"
ACTION=="add", KERNEL=="sd*", SUBSYSTEMS=="scsi", ATTRS{vendor}=="ST330063", RUN+="/bin/mkdir -p /media/backup"
ACTION=="add", KERNEL=="sd*", SUBSYSTEMS=="scsi", ATTRS{vendor}=="ST330063", PROGRAM="/lib/udev/vol_id -t %N", RESULT=="ext3", RUN+="/bin/mount /dev/%k /media/backup", OPTIONS="last_rule"
# 
# Now, umount it and remove the mount point when disconnecting.
#
ACTION=="remove", ENV{ID_VENDOR}=="ST330063", RUN+="/bin/umount -l /media/backup"
ACTION=="remove", ENV{ID_VENDOR}=="ST330063", RUN+="/bin/rmdir /media/backup", OPTIONS="last_rule"

# The secondary (offsite) backup should only create the mount point
# when connecting, I will manually mount it if I want. Remove the
# mount point when disconnecting.
#
KERNEL=="sd*", SUBSYSTEMS=="scsi", ATTRS{vendor}=="Maxtor", ATTRS{model}=="OneTouch", SYMLINK+="usb/offsite%n"
ACTION=="add", KERNEL=="sd*", SUBSYSTEMS=="scsi", ATTRS{vendor}=="Maxtor", ATTRS{model}=="OneTouch", RUN+="/bin/mkdir -p /media/offsite"
ACTION=="remove", ENV{ID_MODEL}=="OneTouch", RUN+="/bin/rmdir /media/offsite", OPTIONS="last_rule"

---

