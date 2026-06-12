---
title: "Can't get to GRUB"
date: 2015-10-11
forum: General Help
---

### Post by bryson.christopher on 2015-10-11
Hi,

My system had a single install of Windows 10 on it, I downloaded the Ubuntu X64 15.04 ISO to a USB and done an install of Ubuntu alongside Windows 10.

The install went smooth and everything worked perfect with Ubuntu on a first test, however I couldn't boot to Windows 10. I got an error message to the effect of "/EndEntire ... file path: /ACPI ... error: cannot load image" which after some research I disabled Secure Boot within my BIOS and following this was able to select Windows Boot Loader from GRUB and load into Windows 10.

The problem I face now when starting my system is that it goes straight to Windows 10 and doesn't load GRUB. Within the BIOS the priority is still Ubuntu but this isn't the case. I used my install USB to access Ubuntu Live and run Boot Repair but the problem still remains.

Any thoughts on what I could do to resolve this?

Thanks,
Chris.

---

### Post by yancek on 2015-10-11
> I used my install USB to access Ubuntu Live and run Boot Repair but the problem still remains.

The boot repair has an option to Create BootInfo summary and without you posting that information here, all we can do is guess.  My guess, you installed one system using MBR and the other EFI but there are a number of other possibilities..  Posting the output should get you some help.

---

