---
title: "Unable to get into boot manager after installing Ubuntu"
date: 2022-04-05
forum: General Help
---

### Post by jboey on 2022-04-05
Full discloser - I'm a dummy. I recently got interested in linux and did successful installations of the latest version of Ubuntu LTS on a Toshiba laptop and an iMac. Also installed 34 bit Peppermint on another Toshiba laptop.

All were >10 yeards old. I went ahead and did a full installation of Ubuntu on my own 2008 MBP. This did not go well. Basically it takes eight minutes or more to start and the computer is not usuable. I tried to get into boot manager by hitting the option key when starting the computer but don't see boot options. The only thing I see is an hard drive Icon with "EFI boot" text underneath the icon.

At this point I'm at sea and would greatly appreciate any suggestions. Thanks all in advance

Jim

---

### Post by Impavidus on 2022-04-05
What are the specs of those laptops? You may need one of the light flavours, Xubuntu or Lubuntu. They are better suited for computers with less RAM.

---

### Post by grahammechanical on 2022-04-05
> the computer is not usuable.

Please describe "not usable."

Does that mean that you get to a login screen and from there to a desktop environment? If you can get to a Ubuntu Desktop use Activities>Software & Updates>Additional Drivers tab. Is a proprietary video driver installed? If not, install one from the drivers tab. If one is already installed, de-activate it from the Drivers tab and reboot.

Regards

---

### Post by yancek on 2022-04-06
Is "MBP" a Mac?  If when using the options key you see something related to "EFI", the question is did you install Ubuntu in EFI mode?  If you don't resolve this problem, you could try going to the site below and downloading and running boot repair and posting the resulting link here so that we have more information.  Use the 2nd option explained on that page and only use the Create BootInfo Summary option..  Do NOT try any repair options. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by dech-03 on 2022-04-06
Based on recent experience with an iMac; I needed to hover over the UEFI boot option then press the Control key (circling arrow appears);then click the active mouse button.   Somewhere in System Prefs. you can change the preferred boot option "Start up disk"?  Apple devices seem to get "confused" when different startups have been attempted and take much longer to boot so re-setting NV RAM is probably advisable - that's Cmd + Option + P + R simultaneously on Monterey OS and I think that goes back many years.

---

