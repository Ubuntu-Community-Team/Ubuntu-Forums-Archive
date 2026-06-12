---
title: "Screen is Fully Dimmed During Bootup"
date: 2013-05-30
forum: General Help
---

### Post by johnny907 on 2013-05-30
After fresh 12.04 install my screen was stuck at 1024X768 and Unity only worked in 2D.  I fixed those problems by [COLOR=#000000]a simple grub edit, but now m[/COLOR][COLOR=#000000]y screen goes fully dim while booting Ubuntu. I can get the brightness to full by using pressing [/COLOR]*function + brightness keys, but the keys are reversed. for example: + brightness = - brightness, and - brightness = + brightness. That is also the only way adjust screen brightness at all. The brightness settings in '[I]Brightness & Lock' do not work at all. I am hoping for a fix that will solve this issue and not affect my screen resolution and 3D functionality as aforementioned.*[/I]


This was my grub fix
[COLOR=#000000]:[/COLOR]

[COLOR=#000000]1. gksudo gedit /etc/default/grub[/COLOR]


2. 
[COLOR=#000000][COLOR=#000000]GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian
[B]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[/B]GRUB_CMDLINE_LINUX=""[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]

3.[/COLOR][/COLOR][I][COLOR=#000000]

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=trueGRUB_TIMEOUT=10GRUB_ DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [FONT=Verdana]acpi_osi=[/FONT]"**
GRUB_CMDLINE_LINUX=""
[/COLOR]
[COLOR=#000000]
[/COLOR][COLOR=#000000]4. [/COLOR][COLOR=#000000][I]sudo update-grub
[/I][/COLOR][/I][COLOR=#000000]


[/COLOR]

---

