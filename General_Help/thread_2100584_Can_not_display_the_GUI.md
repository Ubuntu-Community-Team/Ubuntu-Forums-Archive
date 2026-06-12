---
title: "Can not display the GUI"
date: 2013-01-02
forum: General Help
---

### Post by frhs on 2013-01-02
I press [ Ctrl+Alt+F5 ]to go to the Text View. and then I input the command [ startx ],[SIZE="4"] and then I just can see the desk-background, I can not see the Programs launcher, can not see the States Column(menu, network states, time, shut down or restart).[/SIZE]

I just can return to the text view, and press Ctrl+Alt+Del to restart the computer, and waiting for system reload the GUI.

My System is Ubuntu 12.10, Kernel Linux 3.5.0-21-generic, GNOME 3.6.0.

And how can I fix this problem?

Thank you very much if the answers is helpful.

---

### Post by dino99 on 2013-01-02
you can try:

- boot without "splash" on the boot line, to see the verbose comments (simply select the boot line into grub menu, hit E to edit it, remove "splash" from the line, then hit ctrl+c to continue booting

- boot in recovery mode (hold "shift" key down to the bios end process on a single OS system to see the grub menu), then select repair.

note: as it seems to be a graphic driver issue, it could help to know: which card/chipset is used, which driver is installed and is it 32 or 64 install

---

### Post by frhs on 2013-01-02
> **dino99 said:**
> you can try:

- boot without "splash" on the boot line, to see the verbose comments (simply select the boot line into grub menu, hit E to edit it, remove "splash" from the line, then hit ctrl+c to continue booting

- boot in recovery mode (hold "shift" key down to the bios end process on a single OS system to see the grub menu), then select repair.

note: as it seems to be a graphic driver issue, it could help to know: which card/chipset is used, which driver is installed and is it 32 or 64 installAh... Excuse me, Actully I can boot the computer and Enter Gui Successfully. It Just Can't Display the Gui after I Entered the text view.

---

### Post by frhs on 2013-01-02
> **frhs said:**
> Ah... Excuse me, Actully I can boot the computer and Enter Gui Successfully. It Just Can't Display the Gui after I Entered the text view.

Can't Find the Program Lancher. And Can't fine any Program Icon.

---

### Post by rnerwein on 2013-01-02
> **frhs said:**
> Ah... Excuse me, Actully I can boot the computer and Enter Gui Successfully. It Just Can't Display the Gui after I Entered the text view.
hi
this looks like your display-manger freezed. have you tried some magic keys.
and for reboot i think it's better to use: sudo reboot not CTRL+ALT+DEL
cheers

---

