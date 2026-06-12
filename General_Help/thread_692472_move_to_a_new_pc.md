---
title: "move to a new pc"
date: 2008-02-09
forum: General Help
---

### Post by jtmedin on 2008-02-09
We are trying to move to a new pc with a new hard drive. Problem is we would like to NOT reinstall the os & all the other programs. Used to use partition magic to copy the old hd to the new hd. Then windows would complain & we would have to use their cd while they fixed some things & finally get moved to the new hd. That no longer works :-(. Anyone got any better ideas? TIA

---

### Post by nemarasu on 2008-02-09
This will depend on the type of disk you have (IDE / SATA). If the drive is installed you can try one of the following...

this if for IDE:

dd if='/dev/hda' of='/dev/hdb'

This is for SATA

dd if='/dev/sda' of='/dev/sdb'

That should copy everything from your main hardrive to the new one and it should be bootable as well.

Or you can read this article for an even easier way:

[http://lifehacker.com/software/backup-utilities/copy-and-paste-your-entire-hard-drive-with-two-clicks-with-gparted-296850.php]("http://lifehacker.com/software/backup-utilities/copy-and-paste-your-entire-hard-drive-with-two-clicks-with-gparted-296850.php")

---

