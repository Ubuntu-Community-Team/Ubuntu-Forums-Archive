---
title: "boot into usb?"
date: 2008-04-14
forum: General Help
---

### Post by agim on 2008-04-14
I have a computer that I am working with that does not support booting into a usb device. Will I be able to make it boot into the usb if I use either the ubuntu livecd or super grub?
Thanks.

---

### Post by agim on 2008-04-15
bump

---

### Post by kutjara on 2008-04-15
> **agim said:**
> I have a computer that I am working with that does not support booting into a usb device. Will I be able to make it boot into the usb if I use either the ubuntu livecd or super grub?
Thanks.

Whether or not a computer will boot from a USB device is a feature of the BIOS. If the BIOS doesn't support USB booting, you won't be able to enable the feature via Ubuntu or grub.

---

### Post by agim on 2008-04-16
thanks

---

### Post by UnixBASHparty on 2008-04-16
I must say, GRUB is essentially an OS(with what one could call drivers).  Are USB drivers included with GRUB, because if that were true it should be able to boot USB.  Much like it can boot ext2(as ext2 isn't directly supported by the BIOS.  I seem to remember on Debian, GRUB detected my external hard-drive and added the option to boot DOS from it(Not that it would work as I don't think DOS would detect the USB).

Edit:  Note this debian computer is from 1998 and only has USB 1.1, so there is NO BIOS support(not even for mice ps/2 emulation).

---

### Post by kutjara on 2008-04-16
> **UnixBASHparty said:**
> I must say, GRUB is essentially an OS(with what one could call drivers).  Are USB drivers included with GRUB, because if that were true it should be able to boot USB.  Much like it can boot ext2(as ext2 isn't directly supported by the BIOS.  I seem to remember on Debian, GRUB detected my external hard-drive and added the option to boot DOS from it(Not that it would work as I don't think DOS would detect the USB).

Edit:  Note this debian computer is from 1998 and only has USB 1.1, so there is NO BIOS support(not even for mice ps/2 emulation).

I had a bit of a google about this to see if it's possible, and found this HOWTO:

[http://gentoo-wiki.com/HOWTO_Install_Gentoo_from_USB_stick_using_GRUB](http://gentoo-wiki.com/HOWTO_Install_Gentoo_from_USB_stick_using_GRUB)

It took the guy four days to get working, and that was on a machine that supported booting from a USB drive.

I don't think GRUB has access to the machine's USB drivers at such an early stage in the boot process. It simply looks at the devices mounted by the BIOS, scans them for bootable OSes, and adds them to the list of things it can boot.

I'm not sure how it recognized your old external drive. All I can think of is that GRUB added the entry for that drive when the whole system was up and running (complete with USB support). If you tried to boot from the drive at startup, however, GRUB would try to hand over to the unavailable USB drivers and the boot would fail.

---

### Post by bodhi.zazen on 2008-04-16
If you BIOS does not support booting to USB devices, first thing is to try to update the bios to a newer version that does.

If that fails, you may be able to do this by making a small /boot partition on your hard drive. The boot partition does not need to be much larger then 512 Mb and will house your kernel and initrd (which will mount the USB drive).

Install the OS onto the usb device, but, and during the installation, mount the boot partition at /boot.

---

### Post by agim on 2008-04-16
isn't updating the bios kind of dangerous

---

### Post by kutjara on 2008-04-16
> **agim said:**
> isn't updating the bios kind of dangerous

It can be, but often it's the only way of fixing certain problems or enabling certain features.

I've updated countless BIOSes over the years and never had a problem, but there's always a first time, so I can't guarantee there won't be any problems. It's firmly in the realm of Murphy's Law: if something can go wrong, it will.

---

### Post by UnixBASHparty on 2008-04-17
Since I don't think the USB thing will ever work directly, I propose a new idea.  You could install GRUB on a floppy disk along with /boot/(kernel and grub config files) and could mount the USB drive as / after the drivers are loaded.  That should involve editing the fstab along with grub.1st; however, that is fairly straightforward.

> **kutjara said:**
> It can be, but often it's the only way of fixing certain problems or enabling certain features.

I've updated countless BIOSes over the years and never had a problem, but there's always a first time, so I can't guarantee there won't be any problems. It's firmly in the realm of Murphy's Law: if something can go wrong, it will.

Oh yes it will, and it has happened to me.  I booted onto the DOS/bio-update utility floppy, and the next thing, booooom(a tranformer blew on the pole).  Luckily this particular model had a backup bios(dual bios).

Just remember to hook it up to an UPS just to be safe.

> **kutjara said:**
> 
I don't think GRUB has access to the machine's USB drivers at such an early stage in the boot process. It simply looks at the devices mounted by the BIOS, scans them for bootable OSes, and adds them to the list of things it can boot.


Well I do know that drivers like ext2 are included with GRUB.  I wonder if there is a list of such drivers.  I also know it could book off of my SCSI system; however, I think the SCSI card had some sort of BIOS patch.

---

### Post by djhk on 2008-06-13
To boot Ubuntu from a USB drive, I used Plop [http://www.plop.at/en/bootmanager.html]("http://www.plop.at/en/bootmanager.html")
Plop contains support for USB drives.
The Plop boot floppy will boot Grub on the USB drive.
You need to have Grub on the USB drive.
The Ubuntu installation had a Grub entry for HD(1,0).This worked fine when the USB drive was connected to the install system.
Plop has the USB drive as HD0. You need to add an entry to Grub for the Plop boot. I used HD(0,0).
The new entry allows Ubuntu to be booted from the USB drive on a system with a bias that has no USB support.:)

---

