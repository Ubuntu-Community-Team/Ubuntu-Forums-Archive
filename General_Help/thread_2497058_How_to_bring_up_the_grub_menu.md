---
title: "How to bring up the grub menu"
date: 2024-04-21
forum: General Help
---

### Post by alansecker on 2024-04-21
I cannot get into the grub menu.
I have tried booting up while holding down the left shift key or the Esc key but that always takes me to the BIOS screen.
The kernel is 5.15.0-105-generic.

---

### Post by Bashing-om on 2024-04-21
alansecker; Hey -

Is this a UEFI system ?
Then it is a escape key that grub looks for. But there is only a 2 second window of opportunity.
As soon as the firmware splash screen clears - spam (depress/release rapidly) the escape key.

[INDENT]hope this helps
[/INDENT]

---

### Post by ajgreeny on 2024-04-21
In order to see the grub menu it is much easier to show it every boot but for only 2 seconds by editing as root /etc/default/grub changing the config lines as shown.
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```
You may say you don't need the menu at every boot but for 2 seconds it is worth it in my opinion, particularly if you need to boot to recovery mode or a different kernel than usual.

---

