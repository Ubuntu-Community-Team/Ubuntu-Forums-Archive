---
title: "Dual boot screen (GRUB ?) not showing. Starting Ubuntu instead"
date: 2023-08-12
forum: General Help
---

### Post by kndrik on 2023-08-12
Hello everyone,

I've had windows 11 installed on this computer for a while, and decided to install ubuntu about six months ago alongside it. I followed a guide to install it (from The Odin Project) and didn't get into any issue until recently.
When booting my computer, I normally get the motherboard splash screen, followed by what I think is called the dual-boot screen (GRUB ??) where Ubuntu is selected by default, and windows under.
However, I currently don't get any of this anymore (neither the MB logo screen nor the dual-boot one), and my computer either gets stuck on a black screen or directly boot on Ubuntu, without allowing me to select windows.

I've done some research online and came across a tutorial on the help section of the ubuntu website ; [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
I followed the guide by downloading and installing boot-repair, as well as creating a "Boot-Info Summary". Before going ahead and clicking on the "Recommended repair" button, I wanted to make sure I was not going to complicate things further, and hoped I could find some help here from more qualified and experienced people.

Here is the pastebin of the generated Boot-info summary : [https://paste.ubuntu.com/p/vmKVq7dQfN/](https://paste.ubuntu.com/p/vmKVq7dQfN/)

I hope I was able to explain my problem clearly enough, please let me know if I can add any necessary information or detail.

Thanks a lot!

---

### Post by MAFoElffen on 2023-08-12
I contribute to the 'boot-info' and 'boot-repair' scripts. Do not do the repair... Thank you for coming here first.

This is what I see. You are not having boot problems, per-say. Grub2 is working. You are booting successfully. The EFI boot files for Windows 11 are there, and Windows 11 is present in your Grub2 Boot Menu.

I have done dual-boot since 2005, using Grub, before Grub2. Being dual-boot, Grub2 should show the menu by default, even for a short time, but on your machine, you say it does not.

Boot process times have decreased significantly, so I do something to force Grub2 to always show the Boot menu, even if just for a moment. This is how i do that.

In BIOS, turn off any boot option that says "fastboot". This is important, that option will skip over processes that will allow you to get to a boot menu... And also skip processes to recognise USB devices.

From booted in Ubuntu, edit file /etc/default/grub with elevated previledges
```

sudo nano /etc/default/grub

```
Change these lines to this:
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=[COLOR=#ff0000]menu[/COLOR]
GRUB_TIMEOUT=[COLOR=#ff0000]5[/COLOR]
[COLOR=#ff0000]GRUB_RECORDFAIL_TIMEOUT=5[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="-- quiet splash"
GRUB_CMDLINE_LINUX=""

```
Save and exit. Then update grub to pick up the changes:
```

sudo update-grub

```

---

