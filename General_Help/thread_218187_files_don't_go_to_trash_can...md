---
title: "files don't go to trash can.."
date: 2006-07-18
forum: General Help
---

### Post by nismohasan on 2006-07-18
like the topic says, when i delete a file it does not go into the trash can on my gnome panal (says its still empty)

however when i look at $HOME/.Trash/ there files i've deleted are there..

how can i fix this?

---

### Post by nik on 2006-07-18
See if it helps to remove the tray icon (applet?) and then add i t again.

---

### Post by nismohasan on 2006-07-18
> **nik said:**
> See if it helps to remove the tray icon (applet?) and then add i t again.

i've tried that, didnt work :confused:

---

### Post by adam.tropics on 2006-07-18
If you have admin status when you deleted them, perhaps they got put in the root account trash. See if that's empty.... In a terminal do...

sudo ls /root/.Trash

It will list any files there if there are any.

---

### Post by nismohasan on 2006-07-18
> **adam.tropics said:**
> If you have admin status when you deleted them, perhaps they got put in the root account trash. See if that's empty.... In a terminal do...

sudo ls /root/.Trash

It will list any files there if there are any.

i think the error was due to a bad kernel.. had updated to 2.6.17.5 with a patchset today updated to 2.6.17.6 with beyond2.2 patch and it fixed files not going to the trash :)

cheers

---

### Post by piller on 2006-08-18
The trash-applet still does not work for me, using ubuntu-desktop-6.06.1 liveCD.  Any ideas on how to fix?

---

### Post by orb9220 on 2006-08-18
Is home on seprate partition? I was confused to with same issue until I saw I  had a seprate trash called home .Trash-root and a plain just .Trash.

---

