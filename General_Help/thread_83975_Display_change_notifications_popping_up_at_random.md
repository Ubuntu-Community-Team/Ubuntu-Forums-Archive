---
title: "Display change notifications popping up at random"
date: 2005-10-30
forum: General Help
---

### Post by p0ltergeist on 2005-10-30
Under Kubuntu (KDE) on my Sony Vaio Laptop, I'm getting arbitrary display change notifications in the form of a large white box appearing right in the centre of my screen. It'll say things like: Brightness: 0% or Display: LCD Off, and it's very annoying. There must be a way to deactivate these notifications, and was hoping someone knew where to do this.

---

### Post by p0ltergeist on 2005-10-30
No one? :(

---

### Post by shinygerbil on 2005-10-30
Erm, I have no idea about Sony Vaio laptops, but looking at the options in System Settings (which are all greyed out), there's one check box which says "Report unhandled events using On Screen Display" - maybe unchecking this will help, if it's checked...

Steve

EDIT: You'll find it in:
KControl -> System Administration -> Sony Vaio Laptop
System Settings -> Laptops and Power -> Sony Vaio Laptop
depending on which you use :)

---

### Post by p0ltergeist on 2005-10-31
I have tried that, and it doesn't work. But I have taken a look into the KSystemLog and I'm constantly getting error messages saying 2 things:

[######,######] Asus ACPI: Error reading brightness

[######,######] Asus ACPI: Error reading LCD status

These are happening several times a second.

---

### Post by JuanFerS on 2006-01-10
Sorry to bring up an old thread, but I have the same problem...
Though my computer was showing just 3 messages:

Asus ACPI: Error reading LCD status
Display changed: LCD on
Display changed: LCD off

I fixed the "LCD Display status error" by editing the acpi4asus module and reloading it.

I edited this file: "asus_core.c"

        if (hotk->model != L3H) {
        /* We don't have to check anything if we are here */
-               if (!read_acpi_int(NULL, hotk->methods->lcd_status, &lcd))
/*             if (!read_acpi_int(NULL, hotk->methods->lcd_status, &lcd))
                        printk(KERN_WARNING "Asus ACPI: Error reading LCD status\n");
-
*/
                if (hotk->model == L2D)
                        lcd = ~lcd;

Compiled and installed.
I commented out those lines and the problem was fixed... 

I just need to fix the other 2 errors... if anyone has already fixed this any help would be appreciated.

---

### Post by PapaWiskas on 2006-02-08
If you are on a laptop, turn of KMILO, it is a utility for special keyboards and laptops like sony vaio etc....

You can find it under system settings in KDE.

---

