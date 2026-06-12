---
title: "Dual-Boot Installation Woes / Grub 2"
date: 2014-12-08
forum: General Help
---

### Post by Sith Lord Kyle on 2014-12-08
Howdy.  I recently dual-booted my laptop with Ubuntu 14.04 and Windows 7.  However, every time I try to start Ubuntu from Grub, it ends at a purple screen and the fan kicks on high.  Windows, however, boots up fine.  I did the same installation process on my desktop with no issues, however; can boot into both easily.  The major difference between the two systems is that my laptop had Windows 8 pre-installed with EFI.  I presume this had something to do with it.  Though, I have turned secure boot off and made sure it wasn't installing in EFI mode when I did the Windows 7 and 14.04 installations.

I looked this up on Google and these forums, tried a variety of things such as boot-repair (which seemed to make things way worse), reinstalled Ubuntu to no avail, checked FSTAB, updated drivers through CHROOT in Live USB, reinstalled Grub, and wiped the GPT with fixdisk.

Wondering if anyone has any ideas on something else to try.

---

### Post by oldfred on 2014-12-08
With laptops it often is the video chip(s). What video chip?
Even Intel which works often need boot parameter to set things correctly.
Some also need other boot parameters.
What brand/model computer?

---

### Post by Sith Lord Kyle on 2014-12-08
Hey there.  It is an AMD APU.  The A-10 to be exact.  I tried nomodeset in Grub but that did nothing.  The laptop is a Lenovo G505s.

---

### Post by oldfred on 2014-12-08
When you installed Windows 7, did you install in UEFI mode?  If so it did not correctly convert drive from gpt to MBR partitioning. 
Or was this computer always Windows 7? They almost always use all 4 primary partitions. 

Do not know AMD and what video issues they may have.

Does live installer boot into live mode ok?

---

### Post by Sith Lord Kyle on 2014-12-09
Howdy again.  I do not believe it was installed in UEFI mode.  I usually try to avoid using it.  This computer was original pre-installed with Windows 8 but I removed it and installed Ubuntu 14.04.  Then now have dual-booted it.  However, the Ubuntu installation won't boot up... just a purple screen.  The Windows one works fine.

Live installer boots up fine.  I have been using it to make changes and try solutions, as well as CHROOT into my Ubuntu installation and update it.

---

### Post by oldfred on 2014-12-09
I thought AMD also used the same nomodeset that I use for nVida.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)


 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)

---

### Post by Sith Lord Kyle on 2014-12-10
In my first response I mentioned that nomodeset does nothing, unfortunately.

---

### Post by Sith Lord Kyle on 2014-12-13
Well, since no one seems to know how to fix this and I don't want to not use Ubuntu.  How do I check to see if either Windows or my non-booting Ubuntu installation are indeed installed as EFI?

---

### Post by oldfred on 2014-12-13
Post link to summary report.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Sith Lord Kyle on 2014-12-14
Sorry for the dumb question, but summary report from what?

---

### Post by oldfred on 2014-12-14
If you click on the link to Boot-Repair it offers to run a summary report to all the details of how your system is configured. 
We then can review that and see if any boot issues are there and if in UEFI or BIOS boot mode.
It will not tell us issues past booting or video issues.

---

### Post by Sith Lord Kyle on 2014-12-14
The boot-repair summary is here: [http://paste.ubuntu.com/9519504/]("http://paste.ubuntu.com/9519504/")

I looked through it and noticed one thing that says "Warning: extended partition does not start at a cylinder boundary.  DOS and Linux will interpret the contents differently."  As well as Grub having two Windows entries, which seems odd.  They are both for the same OS.

UPDATE:  So it seems to freeze at loading RAM disk.  I booted it from Grub's command line and that's where it gets stuck.

---

### Post by oldfred on 2014-12-14
If you run boot repair it copies the boot files from the Windows boot partition into the main install. Many users delete the small hidden in Windows normally boot partition as they do not know what it is. Then they cannot boot. Boot-Repair due to copyright cannot install those so it copies them. 
But then grub sees boot files in two partitions and adds boot stanzas for them

You are in BIOS boot mode. But Boot-Repair says secure boot may be on which in BIOS mode does not do anything and usually cannot be on if in BIOS boot mode. 

The cylinder error is from one of the older tools that Boot-Repair runs and does not apply. But your system should be in AHCI mode for the drives, not IDE nor RAID.

---

### Post by Sith Lord Kyle on 2014-12-15
The system is in AHCI mode, just checked that.  I do not have secure boot on, double-checked in BIOS.  Drives are switched to Legacy first.

Pretty interesting about how it handles Windows though.

And as I mentioned in my last post, the purple screen seems to freeze up when it starts to initialize RAM disk.

---

### Post by Sith Lord Kyle on 2014-12-15
Hey oldfred,

Thanks for your attempts at helping thus far.  I think I am going to give up on fixing Ubuntu on my laptop and just use that space as a secondary partition for Windows, which actually does work.  I already removed Grub and restored MBR.  I have wasted a week trying to fix this, with absolute no progress and wish to waste no more time.  My desktop is neatly dual-booted with no issues so I will use Ubuntu there.  Cheers.

While this is marked as "Solved" it is anything but.  Closed without working solution is more appropriate.

---

