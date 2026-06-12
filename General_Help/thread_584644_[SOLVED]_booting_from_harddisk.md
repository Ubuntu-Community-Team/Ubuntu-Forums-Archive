---
title: "[SOLVED] booting from harddisk"
date: 2007-10-21
forum: General Help
---

### Post by uroskriznar on 2007-10-21
I used to have a dual boot windows (hd0,0), Ubuntu (hd1,0). I took the harddisk with windows away. Whenever i update my system (new kernel and so on) the only harddisk (Ubuntu) is put back to hd1,0 so i have to edit grub manualy. It sais that the harddisk is not found or something like that. How can I solve this?

---

### Post by dcstar on 2007-10-21
> **uroskriznar said:**
> I used to have a dual boot windows (hd0,0), Ubuntu (hd1,0). I took the harddisk with windows away. Whenever i update my system (new kernel and so on) the only harddisk (Ubuntu) is put back to hd1,0 so i have to edit grub manualy. It sais that the harddisk is not found or something like that. How can I solve this?

If you look in your menu.lst file, there will be an entry set with the default disk ("**groot=**(hdx,y)", I think).

You may notice that it is probably set to the wrong hard disk, so every time you update the kernel it uses that setting and you have to manually change things.

If you correct it, all future kernel updates should boot up after install.

---

### Post by uroskriznar on 2007-10-21
I found this in the menu.lst

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

Do I just change to???

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

---

