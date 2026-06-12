---
title: "xubuntu 20.10 vs aspire 3 ryzen 3 laptop no boot"
date: 2021-03-27
forum: General Help
---

### Post by Sandgoose on 2021-03-27
"burnt" the xubuntu image to flash drive, several times, also tried mint variant both do the same thing   when I enable the boot text it gets to around  "a start job for monitoring of lvm2 mirrors, snaps etc, using deventd or process polling" and "start job is runnuing for wait for udev to complete device initilization"  after about 30 seconds it locks up requireing 7 second press on the power button.    friend seems to suggest its because the kernel in the distro iso is too old (3 years) and that hardware is too new, dive boots on other pc, any suggestions ?

---

### Post by CelticWarrior on 2021-03-27
Welcome.

I don't know about the kernel's age but the distro - 20.10 - with its 5.8 series kernel is new enough and should support a Ryzen 3. You may try 21.04 that's about to be released anyway. Indeed, for any Ryzen, the newer the better seems to be a rule.
That said the errors you mentioned don't seems related to the kernel support. They suggest issues with the drives. Make sure AHCI mode is selected in UEFI as some "RAID" modes aren't supported. Make sure Secure Boot is OFF and if there's any "OS Selection" type of setting then avoid any "Windows 8/10" reference.

---

### Post by Sandgoose on 2021-03-27
thanks for the response,   the kernel on the official live iso is still a version 4 kernel though right? I did try the daily build but I don't know if the live part of the image is still using an older kernel or not either way it still didn't work.  anyway just poking around the bios now, the device seem to be a WDC {C SM52- 128gb drive, SATA mode is AHCI,  there is a "security" tab which has a page full of settings, it states the "secure boot mode" is "standard" the system has no password but seems none of the settings on this page are interactive.  under "boot" tab the boot mode is UEFI and Secure boot is listed as "disabled" again these two settings seem none interactive,  I was thinking if it were secure boot it wouldnt' even get as far as It did ?  anyway seems like beta of 21.04 is due on april the 1st haha anything I can do until then ? I don't want to run windows 10

---

### Post by Sandgoose on 2021-03-28
bump also found this [https://old.reddit.com/r/linux4noobs/comments/iv6qf2/i_really_need_some_help_booting_my_acer_aspire_3/](https://old.reddit.com/r/linux4noobs/comments/iv6qf2/i_really_need_some_help_booting_my_acer_aspire_3/) actually seems to have gotten the live image boot to happen   "managed to solve the issue while trying to install other distributions, "just in case". It turns out that Mint, which is ubuntu based, actually displays a log of what it's doing during boot, instead of a useless throbber like ubuntu.  The problems comes from the nvme interface of the ssd, which seems to have a faulty default configuration on ubuntu.  Long story short, you just have to modify the grub command lines and it will work like a charm. Just replace "quiet splash" by "quiet splash nvme_core.default_ps_max_latency_us=5500 " and you are good to go ! "

---

