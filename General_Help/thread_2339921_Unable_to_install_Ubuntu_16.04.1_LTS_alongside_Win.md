---
title: "Unable to install Ubuntu 16.04.1 LTS alongside Windows 10.1"
date: 2016-10-14
forum: General Help
---

### Post by jaunvl on 2016-10-14
Please I desperately need help. After being a Windows user for a very long time I have this past year been introduced to Linux, specifically Ubuntu, at the beginning of this year. Linux and Ubuntu i sgreat and at the moment I cant work without it. The only reason why I sometime still use Windows is to edit my Word docs etc. I have recently purchased a new HP Envy x360 laptop which has Windows 10.1 preinstalled. The first thing I did when I got the laptop was to install Ubuntu alongside Windows with no luck. The installation process goes quite far but just before it is finish I get a pop up window error which says the following: 'grub-efi-amd64-signed failed to install into /target/. Without GRUB boot loader, the installed system will not boot'. Please can someone help me as at the moment it seems I have bought this laptop which is actually useless.

Thank you very much

---

### Post by reese1379 on 2016-10-14
At boot access the BIOS and change boot options to legacy support, then reinstall Ubuntu.

---

### Post by RobGoss on 2016-10-14
> **reese1379 said:**
> At boot access the BIOS and change boot options to legacy support, then reinstall Ubuntu.

This may not be the case if the OP machine is** UEFI / Legcay, **then he would need to make sure he installs Ubuntu in [B]UEFI

[/B]

---

### Post by RobGoss on 2016-10-14
Hello and welcome, Are you able to boot into Windows? It may be that you have installed Ubuntu in the wrong boot mode. I'm not really sure why you're getting that message but you can begin with this

Create a boot repair summary [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and post the results back here so other users may also assist you using the code tags

If you choose to reinstall Ubuntu try the following

The newest machine these days are **UEFI / Legacy,** if you have a new machine and it has** UEFI**  and Windows is install in **UEFI** then you will need to install Ubuntu the same way

Turn off** secure boot,** disable** fast startup. **Seeing you are using Windows you might want to check that partition that you installed Ubuntu on and if it's there I would just delete it and leave it as unallocated space then run the live Ubuntu installer and choose that partition with the unallocated space to install Ubuntu on

**NOTE: **Word to the wise, before you delete anything please make sure you have a recovery disk and backup just in case anything goes wrong it's better to be safe then sorry

I also came across this thread that may implicate what may be causing that error you're getting [https://ubuntuforums.org/showthread.php?t=2322918](https://ubuntuforums.org/showthread.php?t=2322918)

---

### Post by Hewjr100 on 2016-10-14
RobGoss FYI on my system, see specs below, when I turned off uefi windows did not boot.  For whatever reason I can install windows uefi or legacy but once done I cannot switch uefi/legacy.  So in my case I switched to legacy and reinstalled windows, shrunk disk, turned off fast boot, and then rebooted with ubuntu usb.  Also when I tried ubuntu in uefi during install it more or less "forces" you to disable uefi, apparently when installing codecs there is an issue with uefi authentication.

Henry

PS  jaunvl nice piece of hardware, probably newer bios with licensing restrictions.  I hope to by the same laptop for christmas:D

---

