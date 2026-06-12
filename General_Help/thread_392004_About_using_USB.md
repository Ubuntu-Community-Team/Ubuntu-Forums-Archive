---
title: "About using USB"
date: 2007-03-24
forum: General Help
---

### Post by qmemo on 2007-03-24
Hi all, I would Like to know how to add a USB Group so I would give permissions to certain users.

what raised it is this > This from Virtual Box Help >  If USB is not working on your Linux host, make sure that the current user has permission to access the USB filesystem (usbfs), which VirtualBox relies on to retrieve valid information about your host's USB devices.
As usbfs is a virtual filesystem, a chmod on /proc/bus/usb has no effect. The permissions for usbfs can therefore only be changed by editing the /etc/fstab file.
For example, most Linux distributions have a user group called usb or similar, of which the current user must be a member. To give all users of that group access to usbfs, make sure the following line is present:
# 85 is the USB group
none     /proc/bus/usb     usbfs      devgid=85,devmode=664    0    0
Replace 85 with the group ID that matches your system (search /etc/group for "usb" or similar). Alternatively, if you don't mind the security hole, give all users access to USB by changing "664" to "666".
The various distributions are very creative from which script the usbfs filesystem is mounted. Sometimes the command is hidden in unexpected places. For SuSE 10.0 the mount command is part of the udev configuration file /etc/udev/rules.d/50-udev.rules. As this distribution has no user group called usb, you may e.g. use the vboxusers group which was created by the VirtualBox installer. Since group numbers are allocated dynamically, the following example uses 85 as a placeholder. Modify the line containing (a linebreak has been inserted to improve readability)
DEVPATH="/module/usbcore", ACTION=="add",
    RUN+="/bin/mount -t usbfs usbfs /proc/bus/usb"
and add the necessary options (make sure that everything is in a single line):
DEVPATH="/module/usbcore", ACTION=="add",
    RUN+="/bin/mount -t usbfs usbfs /proc/bus/usb -o devgid=85,devmode=664"
Debian Etch has the mount command in /etc/init.d/mountkernfs.sh. Since that distribution has no group usb, it is also the easiest solution to allow all members of the group vboxusers. Modify the line 
domount usbfs usbdevfs /proc/bus/usb -onoexec,nosuid,nodev
so that it contains 
domount usbfs usbdevfs /proc/bus/usb -onoexec,nosuid,nodev,devgid=85,devmode=664
As usual, replace the 85 with the actual group number which should get access to USB devices.
Other distributions do similar operations in scripts stored in the /etc/init.d directory.


Thanks in Advance

---

### Post by dommyOZ on 2007-06-02
Did you ever get a reply to this quetsion? Or find out how to do it??

---

