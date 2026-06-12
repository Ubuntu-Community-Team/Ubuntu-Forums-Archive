---
title: "ACPI=force"
date: 2008-06-21
forum: General Help
---

### Post by sandman2600 on 2008-06-21
When I cold boot my laptop, this is displayed:  "No DMI BIOS year, ACPI=force is required to enable ACPI"

 Incidentally, when I click on the "shutdown" icon from the desktop to turn off the laptop, it does not shut down completely, instead, it hangs at the "Ubuntu" logo....

How do I enable the "acpi=force" command??:confused:

---

### Post by lisati on 2008-06-21
This is one way:

From the terminal (on the System->Accessories->Terminal menu) type in ```
sudo gedit /boot/grub/menu.lst
```Scroll down to where it says > # defoptions=quiet splashChange it to read ```
# defoptions=quiet splash acpi=force
```Save the file, leave the editor, type in ```
sudo update-grub
``` and restart your system.

Hope this helps.

---

### Post by sandman2600 on 2008-06-21
Thanks much!!     Shuts down perfectly now:)

---

