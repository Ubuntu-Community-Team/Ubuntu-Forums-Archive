---
title: "My laptop doesn’t boot after installing ubuntu"
date: 2024-01-23
forum: General Help
---

### Post by goreldeen on 2024-01-23
Hi, I’ve installed ubuntu on my 7 years old laptop because it’s more lightweight, but after some time, i booted the laptop and all what i see on screen is two tabs, one called Boot menu with only ubuntu as an option inside it, the second one is Application Menu with an option called Diagnostic Screen

When i choose ubuntu in the boot menu, it shows up again and nothing actually happens, and no matter what i did i cannot access the bios settings, please help im new to this

---

### Post by oldfred on 2024-01-23
What brand/model system? What video card/chip?

Did you install in UEFI boot mode with gpt partitioning, which has been the standard since 2012, or old BIOS/MBR mode?
How you boot install media is then how it installs.
And then in UEFI/BIOS settings the default boot mode must match how you installed.

Many systems use f2 to get into UEFI/BIOS. But if UEFI fast boot is on, you may not have time to press any key.
Then full shutdown and boot or a "cold" boot from total power down, may give you time to press correct key. Check your user manual.

Have you updated UEFI/BIOS firmware to latest from vendor? Older systems may have updates but not real current ones.

If specs or more lightweight, then a lightweight flavor of Ubuntu may be better. Like like Kubuntu which is more mid-weight but will work on many systems.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

### Post by goreldeen on 2024-01-24
Hi oldfred, thanks for the detailed reply

I actually managed to fix it
It turned out my laptop which is a Fujitsu lifebook model  AH532 has issues with ubuntu messing with boot stuff, the fix was to reset factory bios by removing the bios battery inside the motherboard

Also I’ve tried all what you told, none of them worked, again the Fujitsu lifebook laptops has specifically this issue, i knew that all thanks to someone’s thread here about it, Thanks again and have a great day!!

---

