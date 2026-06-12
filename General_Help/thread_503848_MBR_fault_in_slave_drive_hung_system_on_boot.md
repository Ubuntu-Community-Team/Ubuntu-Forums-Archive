---
title: "MBR fault in slave drive hung system on boot"
date: 2007-07-18
forum: General Help
---

### Post by dwasifar on 2007-07-18
I have a friend running Feisty, for whom I am the primary technical support.  The machine is configured with a small drive (40GB) as the boot and system drive and a larger drive (200GB) for media storage, at /dev/hda and /dev/hdb respectively.

Recently the system refused to boot, reporting an MBR fault.  Naturally I assumed this was the fault of the boot drive, but investigation showed it to be a problem with the storage drive at /dev/hdb.  Removing this drive from the system and from /etc/fstab resulted in normal boot.  The suspect drive was then installed in a USB enclosure, where it was recognized by my system with no problem.  All files and directories were present.

To solve the problem quickly, I simply copied the contents of the suspect drive over to a different drive and installed that in the machine.  After that, I used GParted to create a new disklabel and partition on the suspect drive.  (I'm not sure I trust it, though.  This was a so-called "refurb" drive bought from woot.com, so I don't know its full history.)

I am wondering if this problem could have been solved in the short term more directly.  Is there a way I could have forced an update in place to the MBR on this drive without interfering with the data on it or removing it from the machine?

---

### Post by phidia on 2007-07-18
Well presented question!

We are talking about /dev/hdb right? Or that's how the system saw the drive? Being that it was in a usb enclosure and therefore connected through the usb bus puts another wrinkle in it, but normally the only drive that gets a MBR is the primary or first drive in bios boot order. 

Unless someone changed the bios boot order and tried to do an OS install I don't see how the drive would have mbr issues or create them.

---

### Post by dwasifar on 2007-07-18
> **phidia said:**
> Well presented question!

We are talking about /dev/hdb right? Or that's how the system saw the drive? Being that it was in a usb enclosure and therefore connected through the usb bus puts another wrinkle in it, but normally the only drive that gets a MBR is the primary or first drive in bios boot order. 

Unless someone changed the bios boot order and tried to do an OS install I don't see how the drive would have mbr issues or create them.

When it caused the problem, it was at /dev/hdb - mounted inside the computer case, connected to the motherboard primary IDE channel, and set as slave.  Not in a USB enclosure.  That came later.  I had no problems mounting it later as a USB device; at that point it came up as /dev/sdh, but that was on a different machine.

I can see why you were confused though.  I should have said, "The suspect drive was THEN installed in a USB enclosure..."

There was nothing changed in the bios boot order.  (I know because I built this machine myself.)  

I am at a loss to explain it too.  I imagine that at some point this drive WAS a boot drive for something, before it was "refurbished" and resold.  But I can't imagine why an MBR would survive the drive being wiped for resale, nor why it would cause trouble with the drive in a non-primary position.

---

### Post by dwasifar on 2007-07-19
I'm bumping this up just in case someone else sees it and can explain it.

---

