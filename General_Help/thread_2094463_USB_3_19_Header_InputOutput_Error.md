---
title: "USB 3 19 Header Input/Output Error"
date: 2012-12-13
forum: General Help
---

### Post by lakerssuperman on 2012-12-13
I have two different machines with USB 3.0.  One has native support and the other has an add in card.  When using the rear ports on either the motherboard with native support or the ports on the back of the USB 3.0 add in card I have no issues.  Both machines are running Ubuntu 12.10 Gnome Remix with all the latest updates.

The problem occurs when I use the front USB ports that plug into the 19 pin header.  With these ports I randomly get input/output splice errors and random disk mounting and unmounting during transfers.  At first I thought it was a bad header on the machine with the native support until I tried it on the other machine with the add in card and got the same results.

I tried two different USB 3.0 drives and a few USB 2.0 drives.  The USB 3.0 drives give me errors, but the USB 2.0 drives transfer fine.  Anyone else have this issue? Anyone know how to fix it?  Thanks guys.

---

### Post by Rexilion on 2012-12-14
Perhaps provide output from 'dmesg'.

> My USB3 is not working!

Is kind of generic... and unspecified.

---

### Post by lakerssuperman on 2012-12-14
You're right, "my USB isn't working" is very generic and unhelpful, but I didn't say that.  I describe a specific set of behaviors that  I have obvserved on two different machines when utilizing front USB 3 ports hooked into a 19 pin header.  I also noted that I get a specific error under these conditions on two different machines with two different pieces of hardware and was only asking if someone else has experienced similar issues as that feels like a software issue more than a hardware one.

I don't mean to sound smarmy as you are trying to help and, yes I didn't post dmesg, but I also didn't go full noob and simply say my USB wasn't working.

Thank you for taking the time to read and post a tip.  Have a nice day.

---

### Post by Rexilion on 2012-12-14
I made that remark as intention to notify you that your problem and it's description lack detail. It was in no way intended to offend.

It still get's me no further than the previous conclusion: USB3 does not work. You mention random errors, but you don't post them. You used different types of hardware, but didn't mention their names.

If you post the output of 'sudo dmesg', I will know.

---

### Post by lakerssuperman on 2012-12-14
Fair enough.  My initial point, though, was simply to illustrate that my front USB 3 ports on two different machines with two different internal configurations both drop transfers and report "Splice: input/output error" while the back USB 3 ports work fine.  I don't think it's tied to a specific piece of hardware since it's reproducable on a different machine.

I am not at the machine that has the issue.  I will post the dmseg output later when I get home.  Thanks.

---

### Post by lakerssuperman on 2012-12-14
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1050352](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1050352)

This seems like it might be relevant, although it doesn't have a solution attached to it.

---

### Post by lakerssuperman on 2012-12-14
Here is the dmesg output when the drive experiences an input/output error and the drive mounts and then remounts.

76.437710]  sdc: sdc1
[   76.441103] sd 10:0:0:0: [sdc] No Caching mode page present
[   76.441115] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[   76.441122] sd 10:0:0:0: [sdc] Attached SCSI disk
[   76.915451] EXT4-fs (sdc1): recovery complete
[   76.915457] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[   78.785585] usb 9-1: USB disconnect, device number 5
[   78.786367] JBD2: Error -5 detected when updating journal superblock for sdc1-8.
[   78.786470] Aborting journal on device sdc1-8.
[   78.786480] JBD2: Error -5 detected when updating journal superblock for sdc1-8.
[   78.786497] journal commit I/O error
[   78.800279] EXT4-fs error (device sdc1): ext4_put_super:886: Couldn't clean up the journal
[   78.800285] EXT4-fs (sdc1): Remounting filesystem read-only
[   79.030132] usb 9-1: new SuperSpeed USB device number 6 using xhci_hcd
[   79.047762] usb 9-1: Parent hub missing LPM exit latency info.  Power management will be impacted.
[   79.051481] usb 9-1: New USB device found, idVendor=174c, idProduct=5106
[   79.051490] usb 9-1: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[   79.051497] usb 9-1: Product: AS2105
[   79.051502] usb 9-1: Manufacturer: ASMedia
[   79.051507] usb 9-1: SerialNumber:      WD-WCATR0028632
[   79.053854] scsi11 : usb-storage 9-1:1.0
[   81.466853] usb 9-1: USB disconnect, device number 6

---

### Post by lakerssuperman on 2012-12-14
I'm seeing a lot of bugs and errors reported when I Google this.  It seems that LPM is messing up and the ASMedia controllers can be problematic.  I don't see any clear work arounds this as of yet.

---

### Post by lakerssuperman on 2012-12-14
Did some more digging.  Apparently, this has to do with the U1/U2 states specified by the USB 3 controller.  Certain controllers report this information incorrectly and messes up the LPM state setting.  The 3.6 kernel has the fixes.  I installed the 3.6.3 kernel from the mainline repo and I have not had any disconnects with my USB 3 drive and consistently high read and write speeds.

---

### Post by dcstar on 2012-12-15
> **lakerssuperman said:**
> 
........
The problem occurs when I use the front USB ports that plug into the 19 pin header.
........

USB3 has different hardware specs to USB2, if the header and front ports are only USB2 certified then there is no guarantee that it will work reliably with the higher USB3 data rates and power requirements.

USB3 cable extenders are now on the market because old USB2 extenders do not work with USB3.

---

### Post by lakerssuperman on 2012-12-15
I'm not sure why it was just the front ports, maybe with the header connection the LPM comes into play whereas the back ports it doesn't.  Either way, running the 3.6.3 kernel has resolved the issues.  I've read that some of the new USB 3 stuff in this kernel may be backported to the 3.5 kernel series, but it is definitely in this kernel which I got from the mainline ppa.

---

