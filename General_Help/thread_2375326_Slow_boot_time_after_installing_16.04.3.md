---
title: "Slow boot time after installing 16.04.3"
date: 2017-10-23
forum: General Help
---

### Post by suicideking on 2017-10-23
[COLOR=#242729][FONT=Arial]Background: Brand new Asus Gaming laptop with i7 and 16GB RAM. Has a Samsung 960 NVME. Would boot Win10 to the desktop in 4 seconds from power on.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Installed Ubuntu Gnome 16.04.3 and was taking over a minute to boot with Grub timeout set to 1 second and Windows as primary (used grub customizer).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Tried turning off fast boot and turned off superfetch service.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]How I fixed it: In the bios, the boot order had Ubuntu listed first, Windows second. I changed it to Windows first, that fixed it.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The side effect is now I have to hit ESC to bring up boot order if I want to boot Ubnuntu. I'll also have to use grub customizer again to set Ubuntu as primary.

Curious if there are other fixes for this that will allow the Grub menu to run?[/FONT][/COLOR]

---

