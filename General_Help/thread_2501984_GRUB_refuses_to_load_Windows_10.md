---
title: "GRUB refuses to load Windows 10"
date: 2024-10-28
forum: General Help
---

### Post by fwilliams80 on 2024-10-28
Hi all,

Hoping for a bit of help.

I've dual booted Ubuntu with Windows 10 for years, never had any real issues.

I upgraded from 24.04 to 24.10 earlier this month, but since then GRUB fails to load Windows stating 'error: cannot load image'.

If I manually interrupt the boot process and select the Windows boot loader from the BIOS menu it works fine, only when trying to use GRUB does it fail.

Secure boot is disabled.
Running 'os-prober' correctly picks up the Windows EFI boot loader file bootmgfw.efi.
I've ran update-grub, made no difference.
I've ran grub-mkconfig, again no difference.

Hunted online for a solution and I've not found anything that relates to my exact issue.

Any help or pointers would be most appreciated.

Thanks.

---

### Post by grahammechanical on 2024-10-28
Just to make things clear for others who may be able to help - do you know that Windows fast startup is a form of hibernation and that Grub cannot read the Windows file system if Windows is hibernated? I have also heard that a Windows update will often turn fast startup back on.

We all experience those moments when we forget what we once knew so well and then wonder why what we were doing did not work out. We need to review the obvious.

Regards

---

### Post by Acharn on 2024-10-29
I've never dual-booted with Windows, but whenever I have a boot problem with Ubuntu I reach for the Boot-Repair Disk. I think it would repair your grub as well.

---

### Post by yancek on 2024-10-29
Curious as to why you would upgrade from a release that will be supported for 5 years to one that will only be supported for 9 months.  Was there new software available for 24.10 that was not available for 24.04?  Were you having problems with 24.04?

Did you do the upgrade in the standard way, apt upgrade, using the software manager?  Or did you do a new install from a usb over the previous install?

Do you have a menuentry for windows in the /boot/grub/grub.cfg file and what is it?  Have you checked since this problem that hibernation is off in windows?  If windows boots from the BIOS EFI entry then it should boot from grub if the files are not corrupted and fast boot/ hibernation are off.

If you run boot repair, it might be better to select the Create BootInfo Summary option and post the output here rather than trying repairs as there are a nunber of members here who are well versed on Grub and boot problems.  Also, just for informational purposes there is not point in running update-grub AND grub-mkconfig as all the update-grub stub does IS run grub-mkconfig.  You can see this if you simply open the /usr/sbin/update-grub file.

---

### Post by fwilliams80 on 2024-11-21
Apologies for the late response.  I managed to resolve this with the Boot Repair tool.  I don't really understand what it did differently than what I had tried manually which was to reinstall GRUB, my manual attempt did nothing but Boot Repair reinstalling it appears to have fixed it.

As for why I upgraded, well it shouldn't make any difference to the boot process but I needed a later kernel version for a network card and I like to keep Mesa as up to date as possible, as I game on this PC and try to use Linux now wherever possible.

Thanks for all the pointers, much appreciated.

---

