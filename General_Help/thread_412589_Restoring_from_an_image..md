---
title: "Restoring from an image."
date: 2007-04-18
forum: General Help
---

### Post by insane_alien on 2007-04-18
Hey there, i'm in a bit of a bind. recently i backed up my HDD using dd_recue (the command options were if=/dev/sda of=/disk/backup.img) so it was the whole drive into an image file on my usb drive. now, due to many cumulative mistakes on my part everything is borked. i tried restoring the image with dd and it didn't work. something about havng a partition table outside the drive (???)

now, i'm probably doing something obviously wrong but i can't see it. is there a way to get this working or am i completely borked. (i also have a windows drive thats doing the same thing.)

---

### Post by viper on 2007-04-18
As far as the windows drive goes try the recovery console by booting with the xp disk and use the fix mbr command.

---

### Post by insane_alien on 2007-04-18
yeah i tried that one. thats what got me from a blinking underscore to a 'Invalid Partition Table' error. the data seems to be there. just not accessible.

---

