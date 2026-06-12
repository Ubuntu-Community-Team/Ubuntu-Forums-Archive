---
title: "Help with LVM/strange error"
date: 2007-05-11
forum: General Help
---

### Post by karamba_kid on 2007-05-11
I upgraded my laptop from edgy to feisty not to long ago.  I'm using logical volumes and the upgrade seemed to go alright except when it was asking about something I hit enter before I could even see what it was saying.  The laptop boots okay and the logical volumes mount fine.  but when I use the eject command to eject the cdrom drive I get some strange error message. 

alex@arbutus:~$ eject
dm_task_set_name: Device /dev/mapper/vg0-root not found
dm_task_set_name: Device /dev/mapper/vg0-home not found
dm_task_set_name: Device /dev/mapper/vg0-usr not found

Then the cdrom tray opens like it's supposed to.  The errors just annoy me to the point where I am considering a reinstall if I cannot fix it some other way.  Please help me.

---

### Post by TimP on 2007-06-04
I get the same message on LVM volumes created with Breezy, reformatted with Feisty.

---

