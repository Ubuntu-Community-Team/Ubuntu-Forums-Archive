---
title: "[SOLVED] Switching to Runlevel - no prompts"
date: 2008-03-03
forum: General Help
---

### Post by MegaJim on 2008-03-03
When i switch runlevel instead of getting a login prompt (like on my laptop) i just get a blinking underscore, no amount of input will get me to a login prompt.

I can switch back to run level 7

any ideas?

---

### Post by Arthur Archnix on 2008-03-03
If you've added something like vga=791 to your grub boot line, try removing it and seeing if that fixes the problem.

If it does, then go here to apply a workaround: [http://ubuntuforums.org/showpost.php?p=3593878&postcount=8](http://ubuntuforums.org/showpost.php?p=3593878&postcount=8)

---

### Post by MegaJim on 2008-03-03
Wow, that worked, thanks very much ! :D

---

