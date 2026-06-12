---
title: "VMWare Server and USB thumbdrives"
date: 2007-10-31
forum: General Help
---

### Post by pmgeahan on 2007-10-31
I'm running VMware Server 1.0.4 build-56528 on an up-to-date Gutsy install, Dell XPS 710.  

I'm running several virtual machines with no issues.  Floppy, CD, sound, everything works great - except for USB devices.  The VMware server instance doesn't recognize USB drives when they're plugged in.  Gutsy sees them and mounts them with no problems.  The Vmware instance doesn't recognize them in Removable Drives->USB Devices.

Can anyone offer a suggestion as to what the issue may be?

---

### Post by Admoseley on 2007-10-31
check this out.. I'm running Ubuntu 7.10 with the exact same problem as yours with Vmware 1.04. I finally found a solution.


[http://communities.vmware.com/thread/108796](http://communities.vmware.com/thread/108796)

SOLVED

Please open the following file: /etc/init.d/mountdevsubfs.sh by following command - gksudo gedit /etc/init.d/mountdevsubfs.sh

Find the following lines:
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb


Unmark them so that look like this:
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb


Restart and your usb devices will be recognised

---

### Post by fjgaude on 2007-10-31
You know these four lines weren't commented out in Feisty... at least I don't think. Why would they, the programmers, comment out these lines. I see no downside, even if you are not using vm stuff.

---

### Post by pmgeahan on 2007-11-02
> **Admoseley said:**
> check this out.. I'm running Ubuntu 7.10 with the exact same problem as yours with Vmware 1.04. I finally found a solution.

That is perfect.  Solution worked great.  Thanks a ton!

---

### Post by doug-M on 2008-04-18
I tried the above solution and didn't have any luck.

I notice someone also responded to the vmware thread referenced and said it didn't work for them either.

The USB devices work fine in the Ubuntu host but VMware does not show them as devices in the VM -> Removable devices -> USB devices.

Ubuntu 7.10
VMWare Server 1.0.4
Guest: Windows XP and WIndows Server 2003R2

If anyone has more suggestions on what to do or how to debug I would love to hear them.

---

### Post by mygoogoo on 2008-04-21
I am also experiencing this issue and have tried two different methods to no avail.

System:
VMWare Server 1.0.5 build-80187
Guest system: Windows XP
Ubuntu 7.10 Gutsy

1. I tried this method found here:

[http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=2&docTypeID=DT_KB_1_1&dialogID=59222291&stateId=0%200%2059220408]("http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=2&docTypeID=DT_KB_1_1&dialogID=59222291&stateId=0%200%2059220408")

To work around this issue, mount USBFS to /proc/bus/usb.

To do this while the host  is running, execute the following command as root:
mount -t usbfs none /proc/bus/usb

You need to power cycle the virtual machines after the mount command to have access to available USB devices.

To configure the host to mount USBFS automatically on bootup, add the  following line in the /etc/fstab file:

usbfs  /proc/bus/usb  usbfs  auto  0  0
 
If this line is already present in /etc/fstab, it likely has the noauto option set in the options column (4th column). Change this to auto.

2. I also tried method mentioned in topic: ex:

Find the following lines:
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

Unmark them so that look like this:
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Restart and your usb devices will be recognised.

3. I also removed from BIOS, USB 2.0 support, and left the standard USB support for ver 1.0, just for the sake of testing it.

USB devices are fine within Ubuntu. Unfortunately USB not working in VMWare, and this seems to be an issue with quite a few people from what I understand. Hopefully someone has a solution.

Your help is greatly appreciated.

Thank you.

---

