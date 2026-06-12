---
title: "upgraded to Edgy, USB drives now slow"
date: 2006-11-07
forum: General Help
---

### Post by tlacuache on 2006-11-07
I upgraded to Edgy last week and everything has been going great. Last night, however, I plugged in one of my flash drives and noticed that file copies were orders of magnitude slower than they should have been.

I looked in /var/log/messages and saw this:

...
usb 3-2: new full speed USB device using ohci_hcd and address 4
usb 3-2: not running at top speed; connect to a high speed hub
usb 3-2: configuration #1 chosen from 1 choice
scsi3 : SCSI emulation for USB Mass Storage devices
  Vendor: LEXAR     Model: JUMPDRIVE PRO     Rev: 1000
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sda: 2030592 512-byte hdwr sectors (1040 MB)
sda: Write Protect is off
SCSI device sda: 2030592 512-byte hdwr sectors (1040 MB)
sda: Write Protect is off
 sda: sda1
sd 3:0:0:0: Attached scsi removable disk sda
sd 3:0:0:0: Attached scsi generic sg0 type 0
...

So I'm trying to get to the root of the "not running at top speed; connect to a high speed hub" message. I'm plugging it in to the back of my PC like I always have, and it used to run much faster. I tested with a couple of different removable USB storage devices with the same results in /var/log/messages every time.

lsmod |grep usb lists:
...
usbhid                 45152  0 
usbcore               134912  4 usbhid,ehci_hcd,ohci_hcd
...

Any ideas?

I'm running a AMD Athlon XP 2100+ (1733 MHz), 710556 kB of physical ram, SiS 740 chipset motherboard.

Thanks,

Seth Grover
[email]sethdgrover@gmail.com[/email]

---

### Post by Merkwurdigliebe on 2006-11-09
Try these and post what you get:

lspci | grep -i usb

lsusb

I have this issue too.  My machine is falling back to 12 Mb/s on all external USB drives, after "upgrading" to 6.10.  It has worked fine with 6.06 and still works fine in XP 64.  Disks are fine, they work on another AMD machine (and four other PC's and a Mac) and they work on this one if I reboot into XP 64.

I made a couple of new kernels and have gotten a little closer.  I couldn't even mount any USB drives at first.  Now they mount, but they crawl.

I suspect a custom Ubuntu or Debian patch, because the machine does fine when booted to the Centos 4.4 install CD.  

I wish these Debian guys would quit piddling in the kernel.  I never have these problems with distributions that use vanilla kernels.

---

### Post by tlacuache on 2006-11-09
Here's something I did that (temporarily) has fixed my problem.

I unplugged my USB drive, and rmmod'ed ehci_hcd and ohci_hcd. Then, I modprobed ehci_hcd again. I plugged in my drive, and it was back up to full speed! However, my mouse didn't work. Then I modprobed ohci_hcd, and my mouse worked... and the USB was still fast!

I tried adding a file in /etc/modprobe.d/ to make sure they load up in this order, but after rebooting it's slow again. So right now my (somewhat unsatisfactory) solution has been to manually rmmod then modprobe these drivers again, then things are okay.

Hmmmm....

---

### Post by phantoap on 2006-11-10
I just installed Edgy and have the same problem.  
That rmmod/modprobe ohci/ehci fix worked for me, too.  A little cumbersome, but I'm just glad I can get usb running at high speed when I really need it.  
thanks

---

