---
title: "Flickering since one week"
date: 2024-08-22
forum: General Help
---

### Post by thierryroncalli on 2024-08-22
I have a DELL XPS 13 9340 (New Version) and I have installed Ubuntu 22.04. One week ago, I notice some screen flickering (horizontal colored lines appear when moving the mouse).
I have reformated the hard drive and installed a dual boot Windows & Ubuntu (in order to check the issue with Windows). The problem disappears. But today fllickering appears again when using Ubuntu. I have no problem with Windows. If I boot my computer with the Ubuntu USB key, the problem disappears.
I suspect that an update version of Ubuntu is installed and produces this flickering.
Many thanks for your help.

---

### Post by eenuep on 2024-08-28
[COLOR=#0C0D0E][FONT=-apple-system]Had the same issue on my XPS 13 9340 with Ubuntu 24.04 (kernel 6.8.0-41-generic).[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]The issue is fixed by upgrading to the oem kernel:[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]sudo apt install linux-oem-24.04[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]The fix is planned to be fixed in "6.8.0-45.45 or later".[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Source: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2062951/comments/70](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2062951/comments/70)[/FONT][/COLOR]

---

