---
title: "What are these /etc/grub.d files?"
date: 2023-01-15
forum: General Help
---

### Post by sofasurfer on 2023-01-15
I have been messing with my 40_custom file. Somewhere along the line it got deleted when I deleted some grub menu entries with "grub customizer"  While looking for it I discovered that I now have a (1) 40_custom.save  (2) 40_custom.save.1  ( 3) a backup dir  (4) a bin dir  (5) a proxifiedScripts dir.

These were automatically created at the time I lost my 40_custom. Turns out someone who designed linux forsaw me and my 40_custom file was found in the mysterious new backup directory. 

Can someone offer a mild explanation for what created these files and directories?

Thanks

---

### Post by grahammechanical on 2023-01-15
> These were automatically created at the time I lost my 40_custom. Turns  out someone who designed linux forsaw me and my 40_custom file was found  in the mysterious new backup directory.

The developer of Grub Customizer, perhaps? Automatic backups is a thoughtful feature.

Regards

---

### Post by sofasurfer on 2023-01-15
I replaced my 40_custom menu and then ran <$ sudo update_grub>. This did not fix my problem. My grub menu showed no custom entries. Then I just found that grub customizer has a panel on the right side that lists the menu items that I removed. All I had to do was click them back into the menu and wahlah, good as new.
There sure is a lot to learn.

---

