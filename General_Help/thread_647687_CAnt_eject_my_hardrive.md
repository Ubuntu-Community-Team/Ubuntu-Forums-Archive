---
title: "CAnt eject my hardrive"
date: 2007-12-22
forum: General Help
---

### Post by Mr.popo on 2007-12-22
When i rebooted my system after a very recent update, a shortcut to my external hp hardrive had been added to my desktop. WHen i try to delete the shortcut it says to eject it so i eject the hardrive and it says 'The volume 'HP Personal Media Drive' is not mounted'. so i mount the hardrive and the shortcut seems to duplicate itself. I eject the original one and all that happens is the new shortcut is ejected. 

Please can you tell me how to get rid of this

thanks

---

### Post by jken146 on 2007-12-22
edited out accidental weird double post.

---

### Post by jken146 on 2007-12-22
Press Alt+F2 and enter **gconf-editor** .  Then navigate to Apps > Nautilus > Desktop and untick the box labelled "show volumes on desktop".
This will stop all auto-mounted volumes appearing as icons on your desktop.

If you only want to stop *this* volume from appearing as a desktop icon, I suggest you edit /etc/fstab to change its mount point (change it to somewhere other than /media/xxx, /mnt/something is a good idea).

---

### Post by Mr.popo on 2007-12-22
Thanks for quick reply , but ctrl + F2 isnt a shortcut for me?

---

### Post by taurus on 2007-12-22
Then just open a terminal, Applications -> Accessories -> Terminal.

---

### Post by Mr.popo on 2007-12-22
SOrry but how do i access Nautilus  using the terminal

---

### Post by jken146 on 2007-12-22
Sorry -- I meant **Alt**+F2.  All it does it open a box from which you can run a single command, which is quite useful for starting GUI apps.

---

### Post by jken146 on 2007-12-22
> **Mr.popo said:**
> SOrry but how do i access Nautilus  using the terminal

You don't.  You type ```
gconf-editor
``` in the terminal.

---

### Post by Mr.popo on 2007-12-22
Alright cheers mate. Its now gone thanks to you :)

---

