---
title: "set permanent permission to /dev/sg2 etc"
date: 2015-06-02
forum: General Help
---

### Post by dieter-erich on 2015-06-02
Hi,
   I have a camera connected to USB and it shows up as "usbscsi:/dev/sg2                 USB Mass Storage raw SCSI". I can only access it as root. How can I change the permission permanently to get read (maybe also write) access as normal user? Best would be to get permanent access to /dev/sg2,3,4, etc, as I shall add more cameras.....
Thanks, D-E

---

### Post by TheFu on 2015-06-03
I don't know the answer, but have a few ideas.

What are the current permissions for that device and each of the partitions under it?  owner, group, and other?
It appears to be mounted as a disk, but could probably be mounted as an MTP device, which might have different permissions. I dunno.

If it is mounted via udev, perhaps creating a rule-based on the USB vendor tag with the desired permissions would work?  [http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)  Don't pay attention to all the effort around controlling the mount location. That is much easier to control by using disk labels or UUIDs in the fstab or with autofs.

I find it is easier to just pull the SDHC from the camera, myself. Plus it doesn't waste camera batteries just to transfer files.

---

### Post by dieter-erich on 2015-06-05
Hi, 
   thanks for the hints! I have now put "chown user:user /dev/sg1" into /etc/rc.local and it seems to work. At least I can now read from /dev/sg1 even after reboot. Don't know whether this is the best solution, though. I was rather wondering whether one could add user to a group that has access rights but, again, I do not know how to do that....

---

### Post by TheFu on 2015-06-05
> **dieter-erich said:**
> Hi, 
   thanks for the hints! I have now put "chown user:user /dev/sg1" into /etc/rc.local and it seems to work. At least I can now read from /dev/sg1 even after reboot. Don't know whether this is the best solution, though. I was rather wondering whether one could add user to a group that has access rights but, again, I do not know how to do that....

That solution is reckless.  While that might work today, what happens after you reboot and there is a different number of devices connected or they are discovered in a different order?  You may compromise the security of your system. 

I.e. - it is a bad idea.  That link is about modifying a file under /dev/udev/ ... so only THIS EXACT DEVICE gets mounted in the way you want not for any device "sg1".  Device locations change. That is why UUIDs and LABELs were created. Please use those instead.

---

### Post by dieter-erich on 2015-06-08
Hi, you are probably correct but this is the only way I figured out so far. I shall appreciate other ideas! How would I do this by using UUID and/or LABEL?

---

### Post by TheFu on 2015-06-08
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID) shows how to use UUIDs.  You'll have to check the fstab options so it is only mounted when actually plugged in.  Then you can use the fstab mount options to choose the owner, group and permissions.  [http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Oh - and wherever it says to use sudo gedit, please, please, please use **sudoedit** (1 word), which is completely safe to use unlike the other technique which can cause permissions issues.

---

### Post by dieter-erich on 2015-06-09
Thanks, but the problem is: these devices do not get any UUID! Both commands given in the links just show the UUID of the HDs BUT NOT of the cameras! So, for some reason these old cameras (including the memory cards in them) are not listed as UUID!

---

### Post by TheFu on 2015-06-09
Ah - then you'll have to create a rule in /etc/udev/

---

### Post by dieter-erich on 2015-09-19
Thanks for the hint, but can anybody please describe how to create such a rule?!

'udevadm info --query=all --name=/dev/sg2' reports:


P: /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/host6/target6:0:0/6:0:0:0/scsi_generic/sg2
N: sg2
E: DEVNAME=/dev/sg2
E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/host6/target6:0:0/6:0:0:0/scsi_generic/sg2
E: GPHOTO2_DRIVER=proprietary
E: ID_FOR_SEAT=scsi_generic-pci-0000_00_1d_1-usb-0_1_1_0-scsi-0_0_0_0
E: ID_GPHOTO2=1
E: ID_PATH=pci-0000:00:1d.1-usb-0:1:1.0-scsi-0:0:0:0
E: ID_PATH_TAG=pci-0000_00_1d_1-usb-0_1_1_0-scsi-0_0_0_0
E: MAJOR=21
E: MINOR=2
E: SUBSYSTEM=scsi_generic
E: TAGS=:seat:uaccess:
E: USEC_INITIALIZED=691589

---

