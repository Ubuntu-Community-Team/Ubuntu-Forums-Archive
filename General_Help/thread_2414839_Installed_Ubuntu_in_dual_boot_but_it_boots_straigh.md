---
title: "Installed Ubuntu in dual boot but it boots straight to Win 8.1"
date: 2019-03-15
forum: General Help
---

### Post by ilpadro on 2019-03-15
Pretty much as the title says. I made a small partition for ubuntu (about 7gb) on my C: drive (being it the only one I can use considered I'm on a laptop). Installed it, everything was good. But unfortunately, after reboot it went straight to Windows. I tried running boot-repair with a live USB, but after reboot, straight to Windows again. Here's the pastebin from boot-repair:
[http://paste.ubuntu.com/p/h9yc7HYP79/](http://paste.ubuntu.com/p/h9yc7HYP79/)
Also, in the BIOS, nothing regarding ubuntu shows up.

Hope you can help me sort things out!

---

### Post by jeremy31 on 2019-03-15
Check BIOS for OS Boot manager option or trust EFI file

---

### Post by ilpadro on 2019-03-15
Here's what the BIOS shows:
[ATTACH=CONFIG]282801[/ATTACH][ATTACH=CONFIG]282802[/ATTACH]

there's "Select an UEFI file as trusted" but requires me to enable Secure Boot.

---

### Post by jeremy31 on 2019-03-15
See if you can enable Secure Boot and set \EFI\ubuntu\shimx64.efi to trusted, then disable Secure Boot later.  You might need to set a password in Bios to set the UEFI as trusted

---

### Post by westie457 on 2019-03-15
> [COLOR=#000000]there's "Select an UEFI file as trusted" but requires me to enable Secure Boot.[/COLOR]

No it doesn't, if you enable Secure Boot sooner or later Ubuntu will fail the security checks and will not boot.

You have got to set a Supervisor Password to enable the greyed out options.
Set the password, does not need to be complicated just easy for you to remember and can be cleared afterwards.
Select an UEFI files as trusted and follow the prompts - usually selecting the suggested item each time. When finished hit F10 to save the changes and reboot.

If after all this it still boots into Windows you will need to change some settings inside Windows to turn off Fast startup.

Let us know what happens.

---

### Post by yancek on 2019-03-15
> I made a small partition for ubuntu (about 7gb)

I'm surprised it installed without error.  When I installed 18.04 I believe the installer indicated a minimum of 7-8GB required to install.  TAke a look at the Ubuntu minimum requirements page.  If you do get it to boot it wont work very long as the partition will easily fill and become unbootable.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by ilpadro on 2019-03-16
> **jeremy31 said:**
> See if you can enable Secure Boot and set \EFI\ubuntu\shimx64.efi to trusted, then disable Secure Boot later.  You might need to set a password in Bios to set the UEFI as trusted

Ok done that, asked me to write something as description and not knowing what, I wrote something random. However, on reboot, again, straight to windows. Tried to disable fast startup but to no avail.

> **westie457 said:**
> No it doesn't, if you enable Secure Boot sooner or later Ubuntu will fail the security checks and will not boot.

You have got to set a Supervisor Password to enable the greyed out options.
Set the password, does not need to be complicated just easy for you to remember and can be cleared afterwards.
Select an UEFI files as trusted and follow the prompts - usually selecting the suggested item each time. When finished hit F10 to save the changes and reboot.

If after all this it still boots into Windows you will need to change some settings inside Windows to turn off Fast startup.

Let us know what happens.

Well, from the screenshot you can clearly see that Supervisor Passoword is "Set", also because that was the only way to disable Secure Boot.

> **yancek said:**
> I'm surprised it installed without error.  When I installed 18.04 I believe the installer indicated a minimum of 7-8GB required to install.  TAke a look at the Ubuntu minimum requirements page.  If you do get it to boot it wont work very long as the partition will easily fill and become unbootable.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Well I tried to make a bigger partition, but for some reason, even having enough free space, windows wouldn't let me. That's why it's so small

Edit: never mind, I'm stupid, forgot to check boot priority and in fact there was a new optipn. Looks now it's fixed, so than you all for your time and help

---

### Post by yancek on 2019-03-16
> Well I tried to make a bigger partition, but for some reason, even having enough free space, windows wouldn't let me. That's why it's so small


Windows 10 usually limits the decrease in size of the primary system partition, usually to about half.  I don't know what you used/tried to use on windows but you certainly should have been able to create a partition larger than 7GB for Ubuntu.  It's not going to work long at that size.  Are you confusing unallocated space with free space inside your windows partition(s)?  You should have been able to use Disk Management to reduce the size of the C:\ partition.  If you decide you want to keep Ubuntu, it would probably be simpler to reduce the windows system partition and re-install Ubuntu.

---

### Post by ilpadro on 2019-03-16
> **yancek said:**
> Windows 10 usually limits the decrease in size of the primary system partition, usually to about half.  I don't know what you used/tried to use on windows but you certainly should have been able to create a partition larger than 7GB for Ubuntu.  It's not going to work long at that size.  Are you confusing unallocated space with free space inside your windows partition(s)?  You should have been able to use Disk Management to reduce the size of the C:\ partition.  If you decide you want to keep Ubuntu, it would probably be simpler to reduce the windows system partition and re-install Ubuntu.

I have only one partition, the C: drive, where Windows resides. I had about 60 GB of available space on it, so I tried to shrink it to have 10 GB of unallocated space, but Windows Disk Manager gave me an error saying there was insufficient memory. So I tried 7 GB and it worked. Don't know what I did wrong to be honest.

---

### Post by yancek on 2019-03-16
Your boot repair output actually shows that you have 5 partitions, 3 are windows, one is the vfat EFI partition used by both windows and Ubuntu and the 5th is your Ubuntu OS partition.  You can't have a functional Linux system on an ntfs filesystem which is why the additional partition (sda5) was created with a Linux filesystem (ext4) for Ubuntu.  Use it while you can but understand that once you start adding software or data to the Ubuntu partition and it begins to fill up the partition and it will stop booting.  You only have about 350MB of free space now.  Your only alternative will be to shrink the windows partition to add space for Ubuntu but this may not be possible as windows needs a certain amount of free space to run well and you may need another drive since your windows system partition is almost full.

---

