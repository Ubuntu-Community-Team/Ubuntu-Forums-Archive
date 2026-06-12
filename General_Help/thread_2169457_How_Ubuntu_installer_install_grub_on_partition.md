---
title: "How Ubuntu installer install grub on partition"
date: 2013-08-22
forum: General Help
---

### Post by leonardo4 on 2013-08-22
Hi guys, i need to make the same things that ubuntu installer make the grub installation on a partition. My problem is that i need to recognize the /boot partition (formatted in ext3) where grub is installed with another bootloader. I tried some distro but only ubuntu installer make it right. I also tried to install grub with blocklist with grub-install --force /dev/sdaXY in /boot and my notebook freeze when it power on (it power on some led and freeze after power on display). Now i ask to someone more expert than me how ubuntu installer install the bootloader.

*My disk use GPT.
This is my partition scheme:

```

[COLOR=#555555][FONT=Monaco]Number  Start (sector)    End (sector)  Size       Code  Name[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]   1              40          409639   200.0 MiB   EF00  [/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]   2          409640        16034639   7.5 GiB     AF00  [/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]   3        16034640       651209551   302.9 GiB   AF00  [/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]   4       651210752       651892735   333.0 MiB   0700  (ext3 partition mounted as /boot)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]   5       651892736       976771071   154.9 GiB   0700  (ext4 Ubuntu partition)[/FONT][/COLOR]

```

How Ubuntu installer make this working?

---

### Post by oldfred on 2013-08-22
You are showing an efi partition ef00 and no bios_grub, so you are booting in UEFI mode?

You cannot have more than one install use the same /boot partition. You will get version conflicts on kernels & grub. Either you have to have a separate /boot for every install or for most desktops you do not need a separate /boot partition at all. 

If you have installed Ubuntu using your existing /boot you may have already corrupted it and will have to repair your other install. 
But reinstall Ubuntu without specifying the separate /boot.

---

