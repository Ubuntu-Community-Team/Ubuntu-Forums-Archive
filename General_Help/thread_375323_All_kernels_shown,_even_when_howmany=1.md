---
title: "All kernels shown, even when howmany=1"
date: 2007-03-03
forum: General Help
---

### Post by stupidlongname on 2007-03-03
All the kernels I have installed are shown, even when howmany is set to 1 (with or without the # comment sign). Any ideas?

Uninstalling the older kernels would seem like an ok idea, but I have my boot menu set to load Windows by default, and don't want to change the config file each time I update Ubuntu.

I used both manual changing and GrubEd, and nothing solves this problem.

---

### Post by justifier on 2007-03-03
I am guessing that you are talking about the GRUB menu ?

If so you could edit the menu.lst file, in the /boot directory and just remove them, though you have to be carefull as it can make your computer unbootable, if you want help with what to delete paste it to a pastbin or something, with numberd lines and i can tell you which ones to delete

the directory is /boot/grub/menu.lst

---

### Post by igknighted on 2007-03-03
Put windows above the *******begin debian automagic kernel list****** line, then set default 0 and you shouldn't have an issue with updates in the future (unless it does a complete re-write, I don't know for sure... but its worth a shot).

---

