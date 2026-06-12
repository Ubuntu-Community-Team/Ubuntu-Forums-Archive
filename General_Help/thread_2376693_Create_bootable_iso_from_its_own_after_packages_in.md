---
title: "Create bootable iso from its own after packages installation"
date: 2017-11-05
forum: General Help
---

### Post by soujiro0725 on 2017-11-05
Hi.  I am trying to create a bootable image stored in an USB flash drive.
But the image needs to be customized.  More specifically, I install an Ubuntu image in a machine (or virtualbox/vmware) and install various packages like for instance for machine learning.  Then, I would like to create an image for that.

I have already tried with Ubuntu 17.10, which is installed on a physical machine (not virtual).  It has a disk utility software by default, so I tried "create disk image". 
It raises an error 

```

Error unmounting /dev/mm..... Command-line `umount "/dev/mm....." exited with non-zero exit status 32: umount: /:target is busy.
(udisks-error-quark, 14)

```

It seems to me, I cannot create an image from its own.

Could anyone help me out how to solve this problem?

---

### Post by TheFu on 2017-11-05
Welcome to the forums.

I've never touched 17.10.

There are 100+different solutions for this question.

I make a backup of all the installed packages and my settings (HOME directory), then do a normal install to a USB device.  Then put my HOME onto it (from outside), then take the list of installed packages and install those into the newly installed USB drive.  There is a little program, aptik, which does just this stuff.  I've never used it, but suspect it might be useful for an end user.
[http://ubuntuhandbook.org/index.php/2017/01/aptik-backup-ppa-installed-apps-users-data/](http://ubuntuhandbook.org/index.php/2017/01/aptik-backup-ppa-installed-apps-users-data/)

There are some complexities around dealing with the UUIDs for each partition that might need to be addressed inside the /etc/fstab if you do not do the install onto the specific USB disk.  If you do install to the USB disk directly, the UUID stuff is handled as part of the installation. Also, if you don't perform the installation, then the booting _stuff_ needs to be manually handled.  How that happens depends on whether the specific computer used is UEFI or legacy BIOS boot.  That means there isn't any universal installation that works for every possible computer you might insert the USB drive into.  Most of my systems use legacy BIOS, but the computer I'm typing on now doesn't support that method of boot. It only supports UEFI booting.  

There might be a way to support both booting methods, but I don't know how to create that. Clearly, it is possible since the Ubuntu installation ISO files do support this. I wasn't able to quickly find a way to do this now. 

BTW, USB storage isn't the best way to run Linux systems.  There are often queuing issues, but if that is all you can do, then it is best to use a fast USB3 storage device over a USB2 device.  It is always best to install Linux onto the internal SATA disk or an external eSATA disk. The commands that the SATA controller supports is vastly superior to that which a USB connection provides.

I have a desire to have booth ChromiumOS and Ubuntu (encrypted) installed to the same disk for travel purposes.  Don't know if this is possible anywhere, much less on my UEFI-only hardware.

Good luck to you.  I'll need some luck here,myself.

---

### Post by yancek on 2017-11-05
If you want to create a bootable iso file from an installed system, I would suggest you try either Systemback or Pinguy Builder.  I haven't tried either on 17.10 but they both work as expected with earlier versions of Ubuntu.

---

### Post by soujiro0725 on 2017-11-06
Thank you for your information.
I googled myself and clonezilla is also an option, maybe?  I have never used it so no sure.

---

### Post by soujiro0725 on 2017-11-06
I am wondering if there will be compatibility problems due to hardware differences.
For example, let's say, I have machine A that has all required packages installed, then created an ISO file from it.  If I install the ISO into a machine B whose hardware components are different from those of machine A.  
I am only guessing that each package requires some sort of drivers (or middleware)  specifically for hardware architecture.

---

### Post by TheFu on 2017-11-06
There are lots of different solutions. Try it. Does it work? It might work fine for your needs, but not work for some other situations. Whether your situation/HW cares or not is something we cannot answer.

You can't put 64-bit onto a 32-bit device. You can do the opposite.

Linux discovers hardware at boot and only really weird hardware differences matter - GPUs if you use proprietary drivers, HW-RAID cards, stuff like that.  Common NIC differences, common SATA controller, USB controller and most other common things are not an issue.  I have pulled HDDs from 1 machine and put it into another, booted and been happy more than a few times.  Linux isn't Windows.

A 64-bit Intel and a 64-bit AMD CPU just doesn't matter.

And there is still the legacy boot verses UEFI boot issue.  Clonezilla won't make a clone from a UEFI system boot on a legacy bios boot machine. It just won't.

---

### Post by C.S.Cameron on 2017-11-06
> **soujiro0725 said:**
> I am wondering if there will be compatibility problems due to hardware differences.
For example, let's say, I have machine A that has all required packages installed, then created an ISO file from it.  If I install the ISO into a machine B whose hardware components are different from those of machine A.  
I am only guessing that each package requires some sort of drivers (or middleware)  specifically for hardware architecture.

As long as you don't install any proprietary drivers you should be ok. Out of the box, Ubuntu works on many different machines.

---

### Post by soujiro0725 on 2017-11-15
PinguyBuilder worked, and it fits my need perfectly.  Thanks guys!

---

### Post by C.S.Cameron on 2017-11-16
Thank you for sharing what worked.

---

