---
title: "Any way to get /dev/cdrom to point to /dev/dvd?"
date: 2007-02-04
forum: General Help
---

### Post by Rich78 on 2007-02-04
Is there any way to get my DVD drive to mount as /dev/cdrom?

It seems to mount as /dev/dvd which is fine but VirtualBox only lets me point to /dev/cdrom so it doesn't find the disk.

Thanks

---

### Post by SeanTater on 2007-02-04
try this:

```

ln -s /dev/dvd /dev/cdrom

```

---

### Post by Falcorian on 2007-02-04
So virtual box won't let you point to anything but /dev/cdrom? If it lets your point to something else you could try a link...

---

### Post by Rich78 on 2007-02-04
No VirtualBox has a drop down and only had /dev/cdrom.

I since got an email from InnoTek (the developers) and it seems I had to put:

export VBOX_CDROM=/dev/dvd

in the shell before launching VirtualBox, it stores this item for future use.

So all solved and working :)

---

### Post by fragos on 2007-02-04
My systems always provide both a cdrom and DVD mount point even if the only drive is a DVD.  I've two DVD drives and without any command line fenagling everything works as expected.  Example follows:

fragos@Geo:~$ ll /dev/dvd*
lrwxrwxrwx 1 root root 3 2007-02-04 16:11 /dev/dvd -> hdd
lrwxrwxrwx 1 root root 3 2007-02-04 16:11 /dev/dvdrw -> hdc
fragos@Geo:~$ ll /dev/cd*
lrwxrwxrwx 1 root root 3 2007-02-04 16:11 /dev/cdrom -> hdd
lrwxrwxrwx 1 root root 3 2007-02-04 16:11 /dev/cdrw -> hdc

---

### Post by Rich78 on 2007-02-05
It's not the system (Ubuntu) that doesn't, that works fine straight out of the box.  It's just the way VirtualBox seems to locate the devices.

By typing in that command line you're basically manually adding the available drive to the list in VirtualBox.

---

