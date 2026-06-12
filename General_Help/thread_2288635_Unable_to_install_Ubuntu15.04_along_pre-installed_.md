---
title: "Unable to install Ubuntu15.04 along pre-installed windows 8, GRUB error"
date: 2015-07-28
forum: General Help
---

### Post by jeffa2 on 2015-07-28
Hi,

I'm trying to install [ubuntu-15.04-desktop-amd64.iso]("http://releases.ubuntu.com/15.04/ubuntu-15.04-desktop-amd64.iso")from usb on my Acer Aspire E5-571 laptop that has windows 8.1 pre-installed and windows fastboot has been disabled. I have made the usb install using [Universal-USB-Installer-1.9.6.1.exe]("http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer-1.9.6.1.exe") from pendrivelinux.com.

No mater what version of Ubuntu(14.02) I try to install it always fails at "unable to install GRUB in /dev/sda/" ( both with secure boot enabled and disabled as well ). Interestingly I got two different GRUB error screens by choosing "install along windows (attachment 1) " and other option(attachment 2) while installing Ubuntu. 



[ATTACH=CONFIG]263444[/ATTACH][ATTACH=CONFIG]263445[/ATTACH]

Can some any one please guide me on how I can fix the issue?

PS I'm trying to boot into pendrive from windows side by pressing restart while holding shift key to boot into EFI USB device. 

-
TIA

---

### Post by oldfred on 2015-07-28
Do not run any auto fix until someone reviews report.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Did you install in UEFI mode? If Windows is UEFI you really need to install in UEFI mode. And grub needs a bios_grub partition to install in BIOS mode, but may not have it and create error.

Do not reinstall using auto reinstall. I think it has been fixed with  15.04, so should be ok, but see caution in link in my signature.  Boot-Repair can convert a BIOS install to UEFI install by uninstalling grub-pc(BIOS) and installing grub-efi-amd64(UEFI).

If an Acer you will have issues booting in UEFI mode. You must enable trust in UEFI and one user posted details, but said it was a challenge for a new user.

      Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[URL="http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot"]http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot
[/URL]
 Details on password & trust setting:
[URL="http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi"]http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi


[/URL]

[URL="http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot"]
[/URL]

---

### Post by jeffa2 on 2015-07-29
> **oldfred said:**
> Do not run any auto fix until someone reviews report.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Did you install in UEFI mode? If Windows is UEFI you really need to install in UEFI mode. And grub needs a bios_grub partition to install in BIOS mode, but may not have it and create error.

Do not reinstall using auto reinstall. I think it has been fixed with  15.04, so should be ok, but see caution in link in my signature.  Boot-Repair can convert a BIOS install to UEFI install by uninstalling grub-pc(BIOS) and installing grub-efi-amd64(UEFI).

If an Acer you will have issues booting in UEFI mode. You must enable trust in UEFI and one user posted details, but said it was a challenge for a new user.

      Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[URL="http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot"]http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot
[/URL]
 Details on password & trust setting:
[URL="http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi"]http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi


[/URL]

[URL="http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot"]
[/URL]

Link for my Boot-info @ [pastebin]("http://paste.ubuntu.com/11959501/")

After that error the installer will crash, then it tries to capture the bug report and fails to send it. My windows was installed by the manufacturer so, I think it would be in UEFI mode.  

My BIOS Boot menu never shows the option to boot from EFI USB Device. So I boot to windows first and restart windows by holding shift key to select boot into EFI USB device. After that I check for "ls /sys/firmware/efi" folder from the terminal it does show its contents (config_table, fw_platform_size, runtime, systab, efivars, fw_vendor, runtime-map, vars folders are listed).  Does it confirm that I have booted into EFI mode from my pendrive to install ubunut?
[ATTACH=CONFIG]263459[/ATTACH][ATTACH=CONFIG]263460[/ATTACH]

 


A month ago I tried to install Fedora and Mint before trying Ubuntu all of them have reported the same error with GRUB
```
grub install error cannot open /boot/efi/ubuntu/shimx64.efi
```
[ATTACH=CONFIG]263461[/ATTACH]

---

### Post by oldfred on 2015-07-29
You have UEFI secure boot on, may be best to try with it off. Ubuntu does work with secure boot on, but once installed you cannot dual boot from grub menu. Grub for whatever reason will not boot Windows with secure boot on. Probably something in the chain of signed software is then not seen correctly. If you really want secure boot then you have to allows boot from UEFI.

You should have a setting in your UEFI that directly allows USB flash drive booting. Often with secure boot that is not allowed for security and you have to specifically turn it on. It may be one of those settings that you cannot get to until you set your UEFI password.
UEFI has a one time boot setting, and that may be what booting thru Windows is then using.

You are in UEFI mode, Boot-Repair reported this::
>  BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.

You get different screens base on the way you boot:

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI

      [/URL]
 Check UEFI boot mode
[ -d /sys/firmware/efi ] && echo EFI || echo Legacy


Rather than the auto fix from Boot-Repair go into its advanced options and choose the full un-install/reinstall of grub. Of course you do not have an old grub to un-install but it does more in the way of updates.

---

### Post by jeffa2 on 2015-07-29
> **oldfred said:**
> You have UEFI secure boot on, may be best to try with it off. Ubuntu does work with secure boot on, but once installed you cannot dual boot from grub menu. Grub for whatever reason will not boot Windows with secure boot on. Probably something in the chain of signed software is then not seen correctly. If you really want secure boot then you have to allows boot from UEFI.

You should have a setting in your UEFI that directly allows USB flash drive booting. Often with secure boot that is not allowed for security and you have to specifically turn it on. It may be one of those settings that you cannot get to until you set your UEFI password.
UEFI has a one time boot setting, and that may be what booting thru Windows is then using.

You are in UEFI mode, Boot-Repair reported this::


You get different screens base on the way you boot:

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI

      [/URL]
 Check UEFI boot mode
[ -d /sys/firmware/efi ] && echo EFI || echo Legacy


Rather than the auto fix from Boot-Repair go into its advanced options and choose the full un-install/reinstall of grub. Of course you do not have an old grub to un-install but it does more in the way of updates.

I went into Windows disk management to reformat the partition and gave it a try(with out even diabling the secure boot)... it worked this time :eek:

Only had to change the boot order to Ubuntu partition and now I can boot into either windows / Ubuntu.


oldfred, thanks for your support.

---

