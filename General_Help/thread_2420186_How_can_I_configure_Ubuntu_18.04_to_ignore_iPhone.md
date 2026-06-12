---
title: "How can I configure Ubuntu 18.04 to ignore iPhone ?"
date: 2019-05-31
forum: General Help
---

### Post by takeawaydave on 2019-05-31
I want Ubuntu 18.04 to ignore my iPhone when I connect it to the USB Port. I want to connect it instead to a VM.
When I plug iPhone in to USB I see these  messages:

```
[59859.566267] usb 1-1: new high-speed USB device number 37 using xhci_hcd
[59859.715427] usb 1-1: New USB device found, idVendor=05ac, idProduct=12a8
[59859.715430] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[59859.715431] usb 1-1: Product: iPhone
[59859.715433] usb 1-1: Manufacturer: Apple Inc.
[59859.715434] usb 1-1: SerialNumber: 778f290f8013bc4435f59820d421ae270a484709
[59859.750781] ipheth 1-1:4.2: Apple iPhone USB Ethernet device attached
[59859.763002] ipheth 1-1:4.2 enp0s20f0u1c4i2: renamed from eth0
[59859.801730] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u1c4i2: link is not ready
[59859.802252] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u1c4i2: link is not ready

```
Device is not ready nor do I want it to be.

I then try to take control of the device using VMware Workstation and get this message:

> The specified device is in use by process:13799 /usr/sbin/usbmuxd on the host operating system. Continuing will detach the device from the host operating system.

I click OK however the iPhone does not get connected to the guest.

Shortly later the same appears:

> The specified device is in use by process:13941 /usr/sbin/usbmuxd on the host operating system. Continuing will detach the device from the host operating system.

However if I click OK the guest doesn't quite freeze but slows down so much it's not responsive for 3-4 minutes. Once the guest is responsive again the iPhone is not available on VMware Workstation for passing through to guest.

I have tried setting up udev rules to prevent mounting of the particular vendorid, productid pair however this did not work for me - I'd try again however not sure of whether this is actually an approach that can work.

Help really appreciated.

If I then disconnect and reconnect the iPhone it restarts.

---

### Post by takeawaydave on 2019-05-31
Tried uninstalling usbmuxd to see if this might get around the problem however both guest and iphone restart when trying to connect.

Tried setting up a udev rule again as per:

[https://www.linuxquestions.org/questions/blog/kingbeowulf-74138/qemu-usb-passthrough-with-specifics-for-iphone-37830/](https://www.linuxquestions.org/questions/blog/kingbeowulf-74138/qemu-usb-passthrough-with-specifics-for-iphone-37830/)

Same result though both guest and iPhone are restarted.

---

### Post by takeawaydave on 2019-05-31
Tried the following: [https://www.insanelymac.com/forum/topic/326555-vmware-cant-connect-iphone/](https://www.insanelymac.com/forum/topic/326555-vmware-cant-connect-iphone/)

However still behaves the same. Phone reboots on disconnect and guest restarts.

---

### Post by takeawaydave on 2019-06-04
Any one know anything about what I could try?

---

### Post by yancek on 2019-06-05
I'm not sure I'm understanding the problem.  You have Ubuntu as a host system with sum other OS running in VMWare, is that right?  Are you saying that after booting Ubuntu and then starting whichever OS you have in VMWare and then plugging in the iphone, it still attaches to the Ubuntu host?

 [QUOTEThe specified device is in use by process:13799 /usr/sbin/usbmuxd on the  host operating system. Continuing will detach the device from the host  operating system][/QUOTE]

If you do this, I would think you would need to plug the iphone in again to attache to the guest?

Did you do the udev rule option or the gvfs option suggested in the link you posted, or both?

---

