---
title: "Ubuntu 13.04 Beta 2. Screen brightness does not decrease."
date: 2013-04-16
forum: General Help
---

### Post by t430 on 2013-04-16
Hi,

I tried Ubuntu 13.04 Beta 2 through USB Boot, and found that the brightness toggle does not work. 

I have a Thinkpad T430. I think its an issue with Kernel Version 3.8.

All works fine with Ubuntu 12.04.2. 

Tried CentOS 6.4 and it works fine with the stock kernel, but not with the kernel version 3.8.

Anyone else having same issue?

---

### Post by jerrylamos on 2013-04-16
Ubuntu Raring never remembers brightness setting, always boots to Max bright.  Ouch.  Manual Systems Settings > brightness > move the slider always required.  Acer Aspire 5253 widescreen 15": notebook.  Anyone know of a cli or exec I could issue on every boot?  

Thanks....

---

### Post by t430 on 2013-04-16
Hi Jerry,

Thanks for the update. What I was trying to say is, the Function + "-" Button decreases the brightness and the "+" increases it. But thats not working.

---

### Post by Toz on 2013-04-16
Yes, something appears to have changed in the kernel 3.8 series. Have you tried the **acpi_backlight=vendor** kernel boot parameter? See the link in my signature for instructions on how to temporarily (and permanently) use kernel boot parameters.

---

### Post by pqwoerituytrueiwoq on 2013-04-16
to get my backlight to behave i had to use this in my boot line (as of the 3.7 kernel)
[FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash _**acpi_osi='!Windows 2012**'_"[/FONT]

---

### Post by Scoobin on 2013-04-16
My Brightness & Lock setting doesn't even have a slider!!!

---

### Post by serdotlinecho on 2013-04-16
Add acpi_backlight=vendor in /etc/default/grub.

```
$ gksu gedit /etc/default/grub
```

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor" **<---Here**
```

Save and close gedit, next:

```
sudo update-grub
sudo reboot
```

---

### Post by t430 on 2013-04-17
Hi All,

Sincere thanks for all your replies. Just goes to show how helpful the ubuntu community is. :)

On 13.04, I noticed another issue - Battery drains out much faster. I guess I better wait for the final version of 13.04. I recently bought the thinkpad and dont want to mess it up.

Till then, I am using 12.04.2. Thats one OS (perhaps the only OS)  where the battery usage is same as windows.

Only if Lenovo would release BIOS/Firmware updates that could be applied through linux...specifically the Ubuntu OS.

Thank you all once again.

---

### Post by ft_ on 2013-04-17
Did you explore powertop to investigate this ?

I own a X220 (i5 2520m / HD3000) laptop. The power usage is very good (roughly 10h with 94mWh battery with common wifi internet and backlight usage). No tweaks.

---

### Post by t430 on 2013-04-17
Hi ft_,

I am currently using jupiter and it works mighty fine. Thanks to Jupiter, the battery lasts about the same on Ubuntu as it does on Windows.

---

### Post by robertoaguiarlima on 2013-04-20
This solution work's for me.
My laptop is Dell Vostro 3650

Thank you!

---

### Post by mc4man on 2013-04-20
> **jerrylamos said:**
> Ubuntu Raring never remembers brightness setting, always boots to Max bright.  Ouch.  Manual Systems Settings > brightness > move the slider always required.  Acer Aspire 5253 widescreen 15": notebook.  Anyone know of a cli or exec I could issue on every boot?  

Thanks....
Unless there is a hardware/kernel  issue that System Settings panel does work & stay persistent but - 
The slider is used to set the default brightness for both Ac & battery but those settings are not the same. 
(The "Dim screen to save Power" is only for battery & doesn't affect the default login brightness setting for battery

So you need to set as desired for both Ac & battery separately though the same slider is used to do so.
(Ac brightness is set while on Ac, battery brightness is set while on battery

---

### Post by Rob Sayer on 2013-04-21
> **ft_ said:**
> Did you explore powertop to investigate this ?

I own a X220 (i5 2520m / HD3000) laptop. The power usage is very good (roughly 10h with 94mWh battery with common wifi internet and backlight usage). No tweaks.

Thanks for the tip on powertop.  Just installed it.

I've had video/power management issues running 12.04 on my atom 2600/cedarview netbook.  As of now, I'm eagerly awaiting 13.04 official (tried it and the video worked much better but I don't have the linux recovery skills to deal with alpha or beta OS issues).

I was going to suggest the acpi_backlight=vendor argument as well, but it's in the grub file and I don't know of a way to do the same thing with an install usb/cd.  Which means actual installation unless there is some way to test that.

---

### Post by brunomicas on 2013-05-01
> **serdotlinecho said:**
> Add acpi_backlight=vendor in /etc/default/grub.

```
$ gksu gedit /etc/default/grub
```

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor" **<---Here**
```

Save and close gedit, next:

```
sudo update-grub
sudo reboot
```

I tried add acpi_backlight=vendor but didn't work in my Asus K55VJ-SX098H with Ubuntu 13.04
Any other suggestion?

thanks

---

### Post by kevpan815 on 2013-05-01
> **brunomicas said:**
> I tried add acpi_backlight=vendor but didn't work in my Asus K55VJ-SX098H with Ubuntu 13.04
Any other suggestion?

thanks

Message Reported for continuing to talk about 13.04 in the Ubutu + 1 Sub-Forum! As Cariboo907 said: It's time to move all 13.04 Discussions to a different Forum. Ubuntu +1 currently means 13.10 Discussions Only!

---

### Post by mc4man on 2013-05-01
> **kevpan815 said:**
> Message Reported for continuing to talk about 13.04 in the Ubutu + 1 Sub-Forum! As Cariboo907 said: It's time to move all 13.04 Discussions to a different Forum. Ubuntu +1 currently means 13.10 Discussions Only!
For users affected who can't 'fix' thru available settings this either still exists in 13.10 or has been fixed with newer kernel, ect.
Either way still valid info/discussion
(as do many current 13.04 issues/interests

---

### Post by Bucky Ball on 2013-05-01
*Thread moved to **General Help***

As Raring is now released it is no longer Ubuntu+1, Saucy is, so moved to **General Help**. Good luck.

---

### Post by Tiago Cruz on 2013-05-07
> **serdotlinecho said:**
> Add acpi_backlight=vendor in /etc/default/grub.[/CODE]

Worked here, Dell Vostro Ubuntu 13.04 x86_64

Tks!!

---

### Post by BachuArg on 2013-05-17
> **serdotlinecho said:**
> Add acpi_backlight=vendor in /etc/default/grub.

Thanks!
Worked perfectly in my Samsung nc210 Netbook

---

### Post by dk0r on 2013-06-07
> **serdotlinecho said:**
> Add GRUB_CMDLINE_LINUX="acpi_backlight=vendor" in /etc/default/grub.

This worked on a Lenovo Helix but the brightness indicator is flakey and does not update according to the screens actual brightness level.

---

### Post by haywarc on 2013-06-27
[QUOTE=serdotlinecho;12606489]

```

GRUB_CMDLINE_LINUX="acpi_backlight=vendor" **<---Here**
```

This worked perfectly on my Acer aspire v5-571. Thanks :D

---

### Post by ph_wu2 on 2013-08-29
Actually - using a t430(i) my results in battery usage are way better compared to windows using tlp ( [http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html](http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html) ), even if I limit the battery charge to 80% in order to extend the batterys life... tlp replaces and extends the power management and is highly cunfigureable.

---

### Post by robin.weinhold on 2013-10-18
Worked for my Ubuntu System with Apple 23" Cinema Display HD.

OS: Ubuntu 13.10 (final)
GPU: Nvidia GeForce 9400 GT
Display: Apple 23" Cinema Display HD

Issue occured after installing the nVidia Dirvers.

Thanks a lot.

---

