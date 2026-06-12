---
title: "floppy mount"
date: 2004-12-13
forum: General Help
---

### Post by Sorin Paliga on 2004-12-13
Floppy does not mount. Workaround: format the floppy, then it will mount automatically, but upon attempting to use it again, it does not unmount, display says 'busy with an application' or something similar. After restart, the same story.
Question: how can I make a floppy mount, effectively use it, take it out, insert another floppy, use it, etc. etc.
Usually, if not formatted, upon attempting to open floppy, message is 'unknown file system' or something similar.
Is there anyone who may help? 
It is OK with CD's though, not with MAC OS hfs and hfs+ systems, even if the hfs supprt was apt-get'ed. The floppy unit worked OK with MDK 10.1, replaced by Ubuntu.

---

### Post by ploum on 2004-12-13
I think your are in the wrong forum.

Tips : when something is "used" by another application, you can find which application with the "lsof" command.

sudo apt-get install lsof (you have to install it ;-) )
lsof /dev/fd0  (if /dev/fd0 is the floppy)

Then kill the software.

If you don't see anything, it's maybe fam. Then :
"killall famd" 
will allow you to umount the floppy.

---

### Post by Sorin Paliga on 2004-12-14
[QUOTE=ploum]I think your are in the wrong forum.

Which one is appropriate?

Tips : when something is "used" by another application, you can find which application with the "lsof" command.

sudo apt-get install lsof (you have to install it ;-) )
lsof /dev/fd0  (if /dev/fd0 is the floppy)

Then kill the software.

If you don't see anything, it's maybe fam. Then :
"killall famd" 
will allow you to umount the floppy.[/QUOTE]

I shall try that, just that this does not solve the problem, as the message is anyway incorrect: there is no other app in use, it WAS floppy formatter.
Rephrasing: how can I ALWAYS make a floppy fully functional, without any other headache?

---

