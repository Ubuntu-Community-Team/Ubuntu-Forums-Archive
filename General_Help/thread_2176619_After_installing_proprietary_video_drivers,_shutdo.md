---
title: "After installing proprietary video drivers, shutdown works but reboot doesn't"
date: 2013-09-25
forum: General Help
---

### Post by colinzealknows on 2013-09-25
[COLOR=#333333][FONT=UbuntuRegular]Running 12.04 here.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Initially telling the computer to shutdown or restart via GUI would make it get stuck on the screen with Ubuntu and the dots. The fan was running, screen still on but nothing really happening. I would just hold the power button until it turned off, to actually shut it down. Tried adding the "acpi=force" to grub but that didn't really do anything.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I read some tips that the problem could be with the video drivers, so I installed the proprietary drivers for my card (Radeon 7770 HD) and voilà, shutdown works perfectly now. Restarting, however, still doesn't: now there's no Ubuntu screen, but the machine is still turned on, and it stays like that indefinitely.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Saw somewhere that I could add "reboot=efi" to grub, tried that and it didn't work as well.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]My machine is a 4-year old Dell XPS 430, not sure if this information is relevant or not, but there you go.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I appreciate the help.[/FONT][/COLOR]

---

