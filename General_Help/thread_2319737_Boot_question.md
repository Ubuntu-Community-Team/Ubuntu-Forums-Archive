---
title: "Boot question"
date: 2016-04-06
forum: General Help
---

### Post by terranz on 2016-04-06
Here's the background:  At work I have Ubuntu installed on an external HDD (been doing this for quite a while) and boot from it.  I work in various computer labs so I can take everything with me and for the software that will only run on windows I have virtualbox with a virtual PC that I put a standard work software image on.

My problem is that for this month I'm in a new lab where the staff PC is one of the new lease which is an HP 800 G2 (all in one) and the BIOS refuses to see my USB HDD and thus I cannot boot from it.

Can I boot from a USB flash disk and use the system installed on my USB HDD?  I will be rotated out of this lab at the end of the month but as these PCs are the new lease they will spread to all other labs and the lease cycle is 3 years.

* to add/edit, the HDD is perfectly viewable once the system is loaded in-case that wasn't clear.  I'm writing this from portable Firefox on the NTFS partition of that drive.

---

### Post by yancek on 2016-04-06
Is the Ubuntu installed on your external hard drive an MBR or UEFI install?
Are the new computers in your lab MBR or UEFI?
If the new machines don't see your hard drive, I don't know why they would see a flash drive.  Only way to find out is to try.  

> * to add/edit, the HDD is perfectly viewable once the system is loaded in-case that wasn't clear.

If your usb drive is not recognized in the BIOS how would it be recognized when the machine is booted and booted to what OS?

---

### Post by terranz on 2016-04-06
The PCs' BIOS does recognise USB flash disks and I've read on the HP support forum someone found their hard disk was seen by the BIOS at boot time if it was formatted as fat32 which isn't a great solution.  I've posted at HP support but have yet to get a reply.
Being new PCs they are capable of both UEFI and MBA but are currently set to UEFI which has never been an issue as this problem didn't exist on the previous 2 or 3 models since we switched to HP before the "G2".

Once you're booted it's no longer to BIOS doing the recognising of a USB device.  It's the operating system taking care of that.

---

### Post by oldfred on 2016-04-06
Your new systems are sure to be UEFI.
And you old install is probably BIOS.
You would have to go into UEFI, probably turn off UEFI Secure boot as BIOS boot is not secure boot. You may also have to turn on allow booting from USB. That also is not considered secure and many UEFI have that off by default.

While this is about a flash drive, any external drive would be the same.
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode)
A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode
[http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506](http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506)
[http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/](http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/)
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

---

### Post by sudodus on 2016-04-07
You can explore what that HP computer can boot from USB with a persistent live drive made with mkusb. One possibility is the have a USB pendrive, that can boot directly and in that system add a menuentry for chainloading into your current USB hard disk drive.
> mkusb/persistent: In a separate menu window you can choose between a GUID partition table, GPT, and an old style MSDOS partition table. Normally GPT is recommended, but many HP computers need an MSDOS partition table to boot directly from USB.

See this link: [mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent) (and of course also the links already posted by oldfred).
Look also at this one about chainloading: [Installation/FromUSBStick#Chainloading](https://help.ubuntu.com/community/Installation/FromUSBStick#Chainloading)

As oldfred has already written, if your USB hard disk drive in installed in BIOS mode, you must set the computer to boot in the same mode, BIOS alias CSM alias legacy alias ...

While this might be an acceptable work-around during this month, I suggest that for the future you create a new portable system, that will work in UEFI mode and if possible boot directly in the company's new computers.

---

### Post by terranz on 2016-04-07
chainloading, yes that's what I was asking for but I couldn't for the life of me remember the term.  Thank you for pointing me in the right direction.

For anyone else who may see this and be stuck with an HP 800 G2 or any HP G2
I have enabled boot from USB
I have toggled legacy boot and secure boot and neither option saw my USB HDD
I have a question in with HP after reading a similar forum thread on their site.  My question there is now 4 days without answer
My Ubuntu install is UEFI as the previous lease made this the only option so I had to go through that one.

---

### Post by him610 on 2016-04-07
This is just a thought, but how does your external USB HDD get its power?

---

