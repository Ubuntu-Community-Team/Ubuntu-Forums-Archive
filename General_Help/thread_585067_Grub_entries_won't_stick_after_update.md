---
title: "Grub entries won't stick after update"
date: 2007-10-21
forum: General Help
---

### Post by Roarden on 2007-10-21
Hi all,

Upon installing gutsy, it didn't automatically recognize my XP partition, so I had to edit menu.lst to add it.  This has worked fine until I update, as every time I update ubuntu, grub for some reason 'resets' back to the entries without my XP entry and I need to manually enter it again.

Is there any way I can stop this from happening?

Thanks for any help!

---

### Post by joze7205 on 2007-10-22
I have had similar problems with my pure:dyne-linux. I guess that "update-grub" runs when the system gets updated.

My advice to you is to add the XP entry in the menu.lst-file before the line

### BEGIN AUTOMAGIC KERNELS LIST

or after the line

### END DEBIAN AUTOMAGIC KERNELS LIST

Hopefully the the update won't touch them there. It works for me.

---

