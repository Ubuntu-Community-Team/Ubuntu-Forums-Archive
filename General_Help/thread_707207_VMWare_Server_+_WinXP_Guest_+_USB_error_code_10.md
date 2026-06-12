---
title: "VMWare Server + WinXP Guest + USB error code 10"
date: 2008-02-25
forum: General Help
---

### Post by frogotronic on 2008-02-25
Hello,

  I have an error when tyring to install USB devices in my WinXP Guest O/S in VMWare server.  The error code is "Error code 10: The Device cannot start" (courtesy of the windows O/S).  The Guest also complains that the USB controller is USB 1.1 (which it is not).

I've tried uninstalling and installing the USB controllers in the Guest

Any suggestions?

- CH

---

### Post by ambigiousop on 2008-05-16
I am having this same problem with Ubuntu 7.10 / VMware Server 1.0.5 / Windows Vista. Any luck? None of my USB flash drives work.

---

### Post by frogotronic on 2008-05-16
Hi,

I solved this problem.  Here goes:

1) Enable USB in Gutsy (which was disabled by default)

```
$ gedit /etc/init.d/mountdevsubfs.sh
```

Lines 42-45 get uncommented (remove the "#"), starting with
 #mkdir -p /dev/bus/usb/.usbfs.

Your file should look like this:

```
# Magic to make /proc/bus/usb work
	#
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
}
```

Save the file


2) Reboot

3) Start VMWare & your Guest O/S. Uninstall your USB devices, your USB hubs in your Guest WindowsXP O/S.  Unplug your USB devices.

4) Reinstall (re-detect) devices and your USB hubs should reinstall.  After they've installed, plug in your USB key (device) and it should re-install & work properly.

- CH

---

