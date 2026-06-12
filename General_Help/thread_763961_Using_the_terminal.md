---
title: "Using the terminal"
date: 2008-04-23
forum: General Help
---

### Post by jacoblyles on 2008-04-23
Hi all. 

How do I access thumb drives and cd-rom drives in the terminal? In windows, these drives would be assigned a drive letter such as A:\

Thanks,
Jacob

---

### Post by smartboyathome on 2008-04-23
It would be in /media. Depends on the type of media for the name of the folder in /media. For example, a partition might be named disk-#.

---

### Post by LaRoza on 2008-04-23
> **jacoblyles said:**
> Hi all. 

How do I access thumb drives and cd-rom drives in the terminal? In windows, these drives would be assigned a drive letter such as A:\

Thanks,
Jacob

As stated, they are in /media. They are named by their disk label also. If you have a Casio camera and connect it to the computer with a USB cable, there will be something like /media/CASIO (or whatever the camera calls itself)

---

### Post by az on 2008-04-23
Cdroms and USB drives will be mounted in media if gnome-volume-manager is running, which is the default for a standard ubuntu installation.  If you are running in recovery mode or if you are running a minimal installation, this is not the case and you need to mount the device by hand.

You can mount a device anywhere you like.

look at the log messages as you plug in the device.  The kernel will detect the device and you will see a message in /var/log/messages.

If the device you just plugged in is /dev/sdc, and it only has one partition on it, you can mount it like this:

sudo mount /dev/sdc1 /mnt

You can even mount it as a folder in your current directory:

mkdir usb
sudo mount /dev/sdc1 usb


to unmount it, 

sudo umount /dev/sdc1

or 

sudo umount usb

---

### Post by K.Mandla on 2008-04-23
Moved to General Help.

---

