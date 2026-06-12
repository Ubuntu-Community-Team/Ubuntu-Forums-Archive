---
title: "MSI windbox 14.04 non recoverable startup error"
date: 2014-09-16
forum: General Help
---

### Post by laurence91 on 2014-09-16
Hi, I posted this on the MSI forum also. Had a search but can't find a solution just a couple of other unresolved examples -

Boot repair file - [http://paste.Ubuntu.com/8345469/](http://paste.Ubuntu.com/8345469/)

This is an MSI windbox dc111 ms-b062.


I installed Ubuntu 14.04 via USB with the reccomended partioning and everything was working well for a few weeks. I packed up the unit to be shipped to another country... Two months later I plug it in for the first time and it turned on with the 'press f3 for recovery screen'. No USB keyboard works that I tried, nothing happens and even if you turn on the system and press f11 or delete etc you can't access BIOS or anything else for that matter the keyboard or any other usb devive is not getting power.

I plugged in a live USB stick with a clean Ubuntu install, if you kill the power supply then turn it on the memory stick would flash, this then allows me to power on the dc111 and it starts Ubuntu as normal with all files and customisation as before. If you don't kill the power supply before plugging in the USB live stick, it still has the f3 error.

I assumed this may be an error with GRUB or some part of the boot sequence so I ran Boot-repair which completed but said the Ubuntu boot files were far from the start of the disk ([http://paste.Ubuntu.com/8345469/](http://paste.Ubuntu.com/8345469/)) .

It reccomended adding in an extra partition, but I didn't fancy that so using gparted I wiped the disk and installed a fresh version of Ubuntu. 

Unfortunately this hasn't solved the issue, I can't think that the partitions are the issue as this is how it was set up and working well for weeks. Also the disk must be OK to work fine if you can get Ubuntu on.

 If you turn on the unit you get the nonrecoverable f3 error. I can still access Ubuntu by plugging in a live USB stick (unplugged from the power supply) but if I restart to try and access BIOS it always reverts to the f3 error.
Iv exhausted my knowledge... Does anybody have any ideas?

---

