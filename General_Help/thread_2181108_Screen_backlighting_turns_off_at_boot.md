---
title: "Screen backlighting turns off at boot?"
date: 2013-10-16
forum: General Help
---

### Post by roeland2 on 2013-10-16
Hello! First of all, let me say I am brand new to Ubuntu. I recently purchased an Acer C7 Chromebook. After two hours of hating ChromeOS I ubuntu'd the laptop and it runs surprisingly well, apart from a few things.
Occasionally when booting, or when closing the lid and leaving the laptop for a while, the screen brightness gets automatically turned to the absolute zero. That is, the backlighting is turned off (I can still slightly see the pixels if I shine a light on my screen, so it's not turned off altogether). I tried disabling autodimming after figuring it only happened when disconnected from a power adapter, but no luck so far. Does anyone know what I'm doing wrong?

---

### Post by varunendra on 2013-10-17
Hello roeland2, and Welcome to the forums ! :)

> **roeland2 said:**
> Occasionally when booting, or when closing the lid and leaving the laptop for a while, the screen brightness gets automatically turned to the absolute zero.

Doesn't it turn back on when you move the pointer or press a key? Or if you try the brightness keys (if your chromebook has those)? Because if these bring back the backlight, then it is a power management issue with different solution.

But if it doesn't come back, then you may try some boot parameters with Grub 2, especially "acpi_osi=" or "acpi_osi=linux" as mentioned here : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

You may also find some helpful tips in the [Backlight Troubleshooting]("https://wiki.ubuntu.com/Kernel/Debugging/Backlight") wiki, especially, this section : [https://wiki.ubuntu.com/Kernel/Debugging/Backlight#Disabling_the_ACPI_backlight_driver](https://wiki.ubuntu.com/Kernel/Debugging/Backlight#Disabling_the_ACPI_backlight_driver)

You may try Boot-Repair to easily try some of these parameters in permanent mode, as mentioned here : [https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation](https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation)

---

