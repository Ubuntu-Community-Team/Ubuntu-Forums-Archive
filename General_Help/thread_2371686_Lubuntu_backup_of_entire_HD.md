---
title: "Lubuntu backup of entire HD?"
date: 2017-09-17
forum: General Help
---

### Post by ra7411 on 2017-09-17
I've got a laptop I run Lubuntu 16.04 on. I want to backup the entire o/s disk so if it refuses to boot after an update (like it did today) I can just do a restore that will make bootable again. It's a 32 bit i386 machine.

fsarchiver would be great, clonezilla would be ok, but I'm having no luck finding the right versions for this machine.

Thanks for any help.

---

### Post by dragonfly41 on 2017-09-18
> [COLOR=#000000] I'm having no luck finding the right versions for this machine.[/COLOR][COLOR=#000000]
[/COLOR]
Assuming that you have a 32bit LiveUSB available (and it is a *persistent *installation)
you can download and install onto LiveUSB Clonezilla 32 bits from here ...

[http://clonezilla.org/downloads/download.php?branch=alternative](http://clonezilla.org/downloads/download.php?branch=alternative)

selecting CPU architecture as i386.   

Or even look in Software Centre (via LiveUSB) for correct version to install.

You will need another drive to receive the cloned Lubuntu image.

Instead of clonezilla you could also explore using rsync so that only differences are backed up.

Another useful package to install is LuckyBackup which uses rsync.

---

### Post by mastablasta on 2017-09-18
another option is redobackup, uses the same program in the background as clonezilla, but it has a nice GUI and is really easy to use.

---

### Post by Autodave on 2017-09-18
I'm with mastablasta on using Redo. Very easy with a nice GUI.

---

