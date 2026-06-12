---
title: "USB not mounted"
date: 2007-05-30
forum: General Help
---

### Post by arno77 on 2007-05-30
Hello.

I switched to Ubuntu 1 month ago and was really enthusiastic about it but since I upgraded Feisty to from 2.6.20-15 to 2.6.20-16 my USB sticks and (USB) external drives are not mounted any more. I receive the message "You are not privileged to mount volume 'name of drive'". Which is strange because I did not have this problem with earlier kernels. Has anybody similar problems? Or even better a solution? Would be great.

Arno

---

### Post by cas118 on 2007-06-04
It's to do with the fstab file. You've probably got a disk that isn't mounting properly.

I had the same problem, and put my resolution on [my blog]("http://ccgi.maxpower.plus.com/2007/06/04/ubuntu-704-fails-to-mount-usb-drive-after-kernal-upgrade/").

Hope it helps!

---

### Post by kdarkentity on 2007-06-04
is it an external hard drive?

---

### Post by arno77 on 2007-06-05
> **cas118 said:**
> It's to do with the fstab file. You've probably got a disk that isn't mounting properly.

I had the same problem, and put my resolution on [my blog]("http://ccgi.maxpower.plus.com/2007/06/04/ubuntu-704-fails-to-mount-usb-drive-after-kernal-upgrade/").

Hope it helps!

Thanks for your response and the link to your blog. Unfortunately, it seems not to be the same problem. I can't find back any errors after typing dmesg. dmesg gives a.o. the following:

[ 1861.528000] usb 4-3: USB disconnect, address 4
[ 1871.640000] usb 4-3: new high speed USB device using ehci_hcd and address 5
[ 1871.772000] usb 4-3: configuration #1 chosen from 1 choice
[ 1871.772000] scsi1 : SCSI emulation for USB Mass Storage devices
[ 1871.772000] usb-storage: device found at 5
[ 1871.772000] usb-storage: waiting for device to settle before scanning
[ 1876.772000] usb-storage: device scan complete
[ 1876.772000] scsi 1:0:0:0: Direct-Access     BSIX     2.0              4.00 PQ: 0 ANSI: 2
[ 1876.772000] SCSI device sda: 501759 512-byte hdwr sectors (257 MB)
[ 1876.776000] sda: Write Protect is off
[ 1876.776000] sda: Mode Sense: 00 00 00 00
[ 1876.776000] sda: assuming drive cache: write through
[ 1876.776000] SCSI device sda: 501759 512-byte hdwr sectors (257 MB)
[ 1876.776000] sda: Write Protect is off
[ 1876.776000] sda: Mode Sense: 00 00 00 00
[ 1876.776000] sda: assuming drive cache: write through
[ 1876.776000]  sda: sda1
[ 1876.780000] sd 1:0:0:0: Attached scsi removable disk sda
[ 1876.780000] sd 1:0:0:0: Attached scsi generic sg0 type 0
 
Maybe, I don't see the problem but anybody else does.

arno77

---

### Post by arno77 on 2007-06-05
> **kdarkentity said:**
> is it an external hard drive?

No, its a memory stick.

---

### Post by mfronzeo on 2007-06-06
I am having the same problem. I upgraded to fiesty fawn, but I didn't notice the problem until I did some auto updates a week or two ago.
There are a number of other posts regarding this and "cannot obtain lock on /media/.hal-mtab" problem (that I'm also having). Being a linux newbie, I'm slowly working my way through the fixes and will advise if I come up with anything.
Thanks,

---

