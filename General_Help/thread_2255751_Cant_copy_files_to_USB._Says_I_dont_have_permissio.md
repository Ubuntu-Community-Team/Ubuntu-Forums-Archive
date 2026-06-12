---
title: "Cant copy files to USB. Says I dont have permission?"
date: 2014-12-07
forum: General Help
---

### Post by adambond on 2014-12-07
Im running Ubuntu 12.04  
Just plugged several USB sticks into the comp. Tried dragging files over to the USB. Says 'permission denied'. 

I tried lots of different files, and different kinds of files. I went into properties of all those files, and changed the permissions to all available options. No difference.
Still wont save any files to the USB sticks.

---

### Post by nerdtron on 2014-12-07
How do you mount the drives? Just clicking them on the left side of the file manager? You shouldn't have any issues on that.


> I tried lots of different files, and different kinds of files. I went  into properties of all those files, and changed the permissions to all  available options. No difference.

You can try launching the file manager as root.
Try "gksudo nautilus" on the terminal. It will ask for password and should open a nautilus window in root mode where you can do all the copying you want.
(just be careful on this mode).

---

### Post by adambond on 2014-12-07
I appreciate the work around. But what has caused this problem?

---

### Post by nerdtron on 2014-12-07
Probably incorrect permissions on the mounted drive. Are you willing to troubleshoot?
On the terminal post the outputs here:
```
id
lsblk
ls -lsa /media/[username]/*

```

---

### Post by adambond on 2014-12-07
I dont think its the USB, because ive tried several with this same result. 

Ok,
id
lsblk
ls -lsa /media/[username]/*
I did that. What am I looking for?

---

### Post by nerdtron on 2014-12-07
Type those command on the terminal while you have a USB plugged in. And replace the [username] with the username you use on your computer.

Since when did this happen?

---

### Post by adambond on 2014-12-07
First noticed it today.

heres what I get

---

### Post by nerdtron on 2014-12-07
Ok. so the 4GB USb is mounted on /media/usb0.

How do you open/mount USB drives? You don't have the same problems with the other drives such as the My Book?

Let's see the permissions on that, so run again:
```
 ls -lah /media/usb0
```

---

### Post by coffeecat on 2014-12-07
If your usb drive is mounted on /media/usb0, then that means that you may have installed the package usbmount which is not intended for GUI desktops. If you have installed usbmount, then uninstall it.

---

### Post by adambond on 2014-12-07
THANK YOU coffeecat! :)  yes, uninstalling 'usbmount' was the answer. :)  I had installed that about 2months ago because was having problems with things not mounting. 
Thank you to Nerdtron, for taking the time to help. :)

---

### Post by coffeecat on 2014-12-08
@adambond - I'm glad that worked. I really wish there was a large health warning for usbmount. You are not the first to find that usbmount breaks usb automounting in GUI systems, and I doubt you'll be the last, unfortunately. For others coming across this thread, usbmount is in the Universe repository and hence not an official Ubuntu package, maintained by volunteers. Although I suspect that I am being over-generous when I say maintained. The package description for usbmount says this:

> This package automatically mounts USB mass storage devices (typically
USB pens) when they are plugged in, and unmounts them when they are
removed. The mountpoints (/media/usb[0-7] by default), filesystem types
to consider, and mount options are configurable. When multiple devices
are plugged in, the first available mountpoint is automatically
selected. If the device provides a model name, a symbolic link
/var/run/usbmount/MODELNAME pointing to the mountpoint is automatically
created.

The script that does the mounting is called by the udev daemon.
Therefore, USBmount requires a 2.6 (or newer) Linux kernel.

Firewire devices are also supported by USBmount.

USBmount is intended as a lightweight solution which is independent of
a desktop environment. Users which would like an icon to appear when an
USB device is plugged in should use the pmount and hal packages
instead.

You have to read right to the end to see that it is not intended for GUI systems, and even then the wording is unclear. The reference to hal - which has long been deprecated - shows that this package belongs more in a museum than an Ubuntu repository. Whether or not it is of any use in sever installations, I have no idea.

TL;DR. Don't use usbmount. If you have installed it, uninstall it now. :wink:

---

### Post by adambond on 2014-12-08
Wow! Well, that says alot. 

I had a HD that I could not get mounted. USBMOUNT actually did solve that problem. But..... then a couple months later, has caused this problem. 

Thanks again. I hope someone can find some use from this thread. :KS

---

