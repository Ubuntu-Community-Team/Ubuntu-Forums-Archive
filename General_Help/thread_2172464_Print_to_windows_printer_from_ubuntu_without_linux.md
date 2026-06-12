---
title: "Print to windows printer from ubuntu without linux drivers ?"
date: 2013-09-05
forum: General Help
---

### Post by vikram_kapoor on 2013-09-05
So, I have a windows XP machine and has a printer "**Kyocera TASKalfa 180 GX**" installed and plugged into it.

Unfortunately, It doesn't have any print drivers for linux so is there a way I can print to it from another ubuntu (13.04) box over local area network ?

Anyone with a similar issue or some solution please ? Thanks.

Edit: I have samba on ubuntu. I can even see the printer but it asks for driver :(

---

### Post by mikewhatever on 2013-09-05
If  the OS does not recognise a printer because there is no driver, then there is no way to print to it. Sorry.

---

### Post by entw on 2013-09-05
Go to the [http://localhost:631/admin]("http://localhost:631/admin") and add the printer. Select the "Windows Printer via SAMBA" entry. Of course you need SAMBA to be installed on your system.

---

