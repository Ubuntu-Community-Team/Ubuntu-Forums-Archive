---
title: "USB drives not working"
date: 2007-09-21
forum: General Help
---

### Post by yellabelly on 2007-09-21
I just can't get USB drives to work with 7.10 on an ECS Elite K7S5A motherboard.
Also I have a scanner that used to work fine with Fedora that stopped working.

I've never managed to access a USB flash or USB external drive. USB isn't totally broken because a mouse works fine.
I bought a Belkin USB 4 port PCI card that I hoped would work after reading about Linux successes but that doesn't do any better.

The scanner hangs in Xsane.
The USB drives show the following message when plugged in.
>dmesg
Sep 21 12:35:37 dog kernel: [ 1610.925056] usb 4-2: new full speed USB device using ohci_hcd and address 4
Sep 21 12:35:38 dog kernel: [ 1611.129083] usb 4-2: configuration #1 chosen from 1 choice

>lsmod | grep usb
usb_storage            72322  1 
scsi_mod              142348  3 sbp2,libata,usb_storage
libusual               17936  1 usb_storage
usbhid                 26592  0 
hid                    27392  1 usbhid
usbcore               134280  6 usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd

but I never see and /dev/sd* devices for mounting. Should it automount?

lsusb will hang.

I've no error messages.

Any ideas? I've been searching USB problems for a long time and found no solution.

Thanks,

---

### Post by dcstar on 2007-09-21
> **yellabelly said:**
> I just can't get USB drives to work with 7.10 on an ECS Elite K7S5A motherboard.
...........
but I never see and /dev/sd* devices for mounting. Should it automount?
...........


If the automount options in Preferences-Removable Drives and Media-Storage are set, then yes.

I have seen USB issues where the power required from a particular device overloads the USB hub, so you might want to try removing any other USB devices and then closely monitoring the dmesg output as you plug in a drive.

---

### Post by Coburn on 2007-12-27
Running Dapper and trying to get an Epson CX5000 (the Wal-Mart version of the CX4800) to scan. I had it working fine on another box with everything the same.

XSane searches for a device and hangs.  lsusb was doing the same thing until I reinstalled some of the sane stuff and restarted.  There does not seem to be a "scanner" or "saned" module in /etc/init.d or lsmod at this point.

I think the only difference is that we added Kubuntu to this box a little while before trying to hook up the all-in-one.  It does have some of its own printing and scanning stuff, but it is mostly frontend.

So, basically, I am seeing very similar symptoms in my USB setup, and would like to know more about fixing them.

Very strange.

---

