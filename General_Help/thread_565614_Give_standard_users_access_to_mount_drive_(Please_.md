---
title: "Give standard users access to mount drive (Please help)"
date: 2007-10-02
forum: General Help
---

### Post by gavinjb on 2007-10-02
Hi,

I am trying to create an fstab mount point that is not reliant on the dev/sdb1 for my external drive, this to make it easier and stop errors when I plug my usb pen drive in first as currently I get an error complaining that it is not an ext3 drive, also as this is my backup drive I need it to mount to a specific mount point.

After reading from various forums I have created a udev rule (had problems as my drive gave me ATTRS and not SYSFS messages with udevinfo)

my rules is in /etc/udev/rules.d/10-local.rules and is as follows
```

BUS=="usb", ATTRS{serial}=="01BC0E47003A", KERNEL=="sd?1", NAME="%k", SYMLINK+="
usbdrive", GROUP="storage"

```

and my fstab entry is as follows
```

/dev/usbdrive    /media/usbdrive    auto defaults 0 0

```

all seems ok except my normal users cannot mount this, as per the info on how to do this [http://wiki.archlinux.org/index.php/Using_udev_to_map_multiple_entries_to_a_device](http://wiki.archlinux.org/index.php/Using_udev_to_map_multiple_entries_to_a_device) (only one which even works this far and does not give me rule errors) I have created a new group called storage and assigned my users to it, but all I get is permission denied ): 

Can someone please help, surely it cant be this difficult to get a specific drive to mount at a specific location (even Windows made this easy) and have normal users capable of mounting it rather than just root.

Thanks,


Gavin,

---

### Post by dannyboy79 on 2007-10-02
I am not familar with using udev but I can read that you have defaults as your fstab option for mounting. If you read the man pages on mount, defaults makes it such that normal users can not mount or unmount (nouser). You need to add, users to that so it would be:

rw,suid,dev,exec,noauto,users,async

INSTEAD of defaults

Also, the defaults have auto in it as a mount option, that means the system will attempt to mount if upon bootup which you stated that you don't want since it's removable hardware so you would want to have noauto but udev should stil mount it once you plug it in.

---

