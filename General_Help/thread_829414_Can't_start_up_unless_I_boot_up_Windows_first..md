---
title: "Can't start up unless I boot up Windows first."
date: 2008-06-14
forum: General Help
---

### Post by kaldor on 2008-06-14
If I have the PC shut down, I need to boot Windows up and restart. If I shut down, I can't boot it up. This is what happens:

[http://www.youtube.com/watch?v=QCH9MUJOnh0](http://www.youtube.com/watch?v=QCH9MUJOnh0)

---

### Post by JC Cheloven on 2008-06-14
Sorry, the final message can't be read from the youtube video. What does it say? 

As far as I can see, the first time you get into GRUB command line. Anyway could you please post the exact messages from the computer?

---

### Post by spiderbatdad on 2008-06-14
It looks like your menu.lst is corrupted or you have recovery mode set as the default. I can't read the screen either, though.

You should have a backup of menu.lst (created when the original was overwritten.) I would remove the current one and rename the backup. The next time an update to the kernel occurs, go with the default option to keep the present menu.lst rather than selecting to go with the package maintainers version.

---

