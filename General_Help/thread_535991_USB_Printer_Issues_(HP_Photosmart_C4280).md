---
title: "USB Printer Issues (HP Photosmart C4280)"
date: 2007-08-27
forum: General Help
---

### Post by BreakfastSamurai on 2007-08-27
Hey everyone.  I've dug through the forums to find an answer to my problem,  and I'm still perplexed and in need of some assistance.  

For some reason,  my USB printer is not even being registered by the USB subsystem.  Take a look at the kernel output immediately after plugging it into my USB port:  

[252003.461258] usb 4-6: device not accepting address 41, error -71
[252009.398225] usb 4-6: new high speed USB device using ehci_hcd and address 42
[252009.509989] usb 4-6: device descriptor read/64, error -71
[252009.725570] usb 4-6: device descriptor read/64, error -71
[252009.941168] usb 4-6: new high speed USB device using ehci_hcd and address 43
[252010.052961] usb 4-6: device descriptor read/64, error -71
[252010.268560] usb 4-6: device descriptor read/64, error -71
[252010.484153] usb 4-6: new high speed USB device using ehci_hcd and address 44
[252010.891397] usb 4-6: device not accepting address 44, error -71


It will continue pushing up the stack looking for (and not accepting) an address all the way until it finally gives up and times out.  

I've also installed the newest version of the HPLIP drivers (2.7.7 as of this posting) from [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/),  using the installation utility.   While HPLIP did install without issue,  obviously the low level problem with the USB address not being accepted is standing in the way of getting this working.

This issue does not arise with any other USB device (in the same slot or otherwise) that I own.  Everything else works flawlessly.

If anyone knows what's going on,  I would be most gracious,  and I apologize if this issue has been addressed and solved before.  


// Breakfast Samurai

---

### Post by Caydel on 2007-09-15
Hmmm, I am trying to use an external hard drive and am getting very similar errors:

[ 6028.840000] usb 3-2: new full speed USB device using ohci_hcd and address 7
[ 6032.028000] usb 3-2: device descriptor read/64, error -110
[ 6047.320000] usb 3-2: device descriptor read/64, error -110
[ 6047.612000] usb 3-2: new full speed USB device using ohci_hcd and address 8
[ 6050.800000] usb 3-2: device descriptor read/64, error -110
[ 6066.092000] usb 3-2: device descriptor read/64, error -110
[ 6066.384000] usb 3-2: new full speed USB device using ohci_hcd and address 9
[ 6076.792000] usb 3-2: device not accepting address 9, error -110
[ 6076.980000] usb 3-2: new full speed USB device using ohci_hcd and address 10
[ 6087.388000] usb 3-2: device not accepting address 10, error -110

This worked just fine on a fresh install of Ubuntu. However, after upgrading all the packages to their latest versions, I began getting these errors. I read this may be due to a bug in the latest kernel, but I am not exactly sure.

Perhaps someone could shed osme light on these issues?

---

