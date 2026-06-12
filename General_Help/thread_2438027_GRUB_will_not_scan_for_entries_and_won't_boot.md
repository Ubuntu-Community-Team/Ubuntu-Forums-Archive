---
title: "GRUB will not scan for entries and won't boot"
date: 2020-03-04
forum: General Help
---

### Post by Geoff_Lane on 2020-03-04
Folks,

Fiddling between an external and an internal drive I have messed up the grub boot loaded for my laptop.

Previously it booted 3 O/Ss as follows;
Ubuntu - main system
Windows10 - if I really have to
Fedora - practicing.

GRUB menu disappeared, had to repair using Windows Macrium Reflect to reset the boot.

Booting back into Ubuntu using a rescue disk I reinstall grub onto correct drive, says all successful but when I run update-grub I just get the following;

```
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Adding boot menu entry for EFI firmware configuration
done

```

Doesn't report any of my systems.

Any advice appreciated as using Grub Emergency Boot image to get into system.

Geffers

---

### Post by oldfred on 2020-03-04
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Fedora install defaults to LVM, and standard Ubuntu does not have the LVM drivers, so you many need to install those into Ubuntu, mount the LVM using LVM tools & then run sudo update-grub.
Some similar with Windows. Windows 10 updates will turn fast start up back on. So you have to boot into Windows and turn off fast start up, so os-prober can find it.If UEFI install, you can boot Windows & Fedora directly from UEFI.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by Geoff_Lane on 2020-03-04
> **oldfred said:**
> May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)



Tried that - all it told me was it failed to remove some grub2 files. after that machine wouldn't boot so used Macrium reflect to repair boot sector - again.

So now Windows10 boots fine and Ubuntu boots using the Grub Emergency Boot image on a USB stick.

Geffers  :rolleyes:

---

### Post by oldfred on 2020-03-04
Best not to try to run a repair before someone reviews report.
Boot-Repair often works as it just reinstalls grub, but sometimes makes it worse.

I would still like to see the requested report.

---

### Post by Geoff_Lane on 2020-03-04
> **oldfred said:**
> Best not to try to run a repair before someone reviews report.
Boot-Repair often works as it just reinstalls grub, but sometimes makes it worse.

I would still like to see the requested report.

All resolved - didn't use any tools.  Wondering why it wasn't probing I inspected the /etc/grub.d files.

30_os_prober and 10_linux did not have the executable permissions set.  I altered these and update-grub found everything.

I intentionally did alter these files before it went wrong to try and tidy up the GRUB menu - just wanted default entries.

I have no idea why the default entries didn't show up anyway plus why should that stop a new version of grub installing properly.

Ah well, all working again.

Geffers

---

### Post by oldfred on 2020-03-04
I almost always turn off os-prober as I have multiple installs & it takes forever to scan all the partitions.
I add only the installs that I am still booting or experimenting with manually into 40_custom.
You can create a backup of grub.cfg and copy boot stanzas from there into 40_custom.

Read the beginning, but then jump to end & work backwards.
[https://ubuntuforums.org/showthread.php?t=2076205](https://ubuntuforums.org/showthread.php?t=2076205)
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

