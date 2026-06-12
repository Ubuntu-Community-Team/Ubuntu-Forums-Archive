---
title: "HP 1018 printing"
date: 2006-07-14
forum: General Help
---

### Post by Rever75 on 2006-07-14
Ok,
  I have been trying to get this to work. I have gone to this site [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) and download compile and installed the driver. I also have edited the udev rules to install the print firmware. I think I have the firmware loading but it does not seem to work. I get nothing printing. Any help would be great. I will post more details in a few.

This is what I get in dmesg....
> [17189496.476000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 21 if 0 alt 0 proto 2 vid 0x03F0 pid 0x4117
[17189520.108000] ppdev0: registered pardevice
[17189520.160000] ppdev0: unregistered pardevice


This is in tail /var/log/message....
> Jul 14 11:06:16 localhost kernel: [17189496.320000] usb 3-7: new high speed USB device using ehci_hcd and address 21
Jul 14 11:06:16 localhost kernel: [17189496.476000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 21 if 0 alt 0 proto 2 vid 0x03F0 pid 0x4117
Jul 14 11:06:16 localhost /sbin/foo2zjs-loadfw: loading HP LaserJet 1018 firmware /lib/firmware/sihp1018.dl to /dev/usblp0 ...
Jul 14 11:06:17 localhost /sbin/foo2zjs-loadfw: ... download successful.

When the firmware is loaded gnome-cups-manager does not find the printer. However when the firmware is not loaded... ie I remove the firmware so it cannot be loaded. I can find the printer but nothing works.

---

### Post by Titanio2006 on 2006-08-29
Switch off-and-on the printer, you should see something like this
in your /var/log/messages:

kernel: usb 3-2: new full speed USB device using address 8
kernel: drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 8 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0517
/etc/hotplug/usb/hplj1018: loading HP LaserJet 1018 firmware /usr/share/foo2zjs/firmware/sihp1018.dl to /dev/usb/lp0 ...
/etc/hotplug/usb/hplj1018: ... download successful.

Then set up your printer queue by running system-config-printer-gui:
1. click New, and Forward.
2. Enter a name and description.
3. Queue-type: Locally Connected, /dev/usb/lp0
4. Choose HP LaserJet 1018
5. Finish, and print a test page!

this info is in linuxprinting.org or something like that.
worked for me after a day in google ](*,) 

Greetings from Chile.
Titanio

---

### Post by IronArjen on 2007-03-26
I switched the printer on and off, removed the install from my print manager, installed again and guess.......YES it works!

---

### Post by 1212jtraceur on 2007-09-10
Thank you, Titanio2006, for the switch off-and-on tip. I was just about to give up on getting my 1018 to work under Ubuntu.

---

