---
title: "how do i uninstall this game!?"
date: 2008-05-30
forum: General Help
---

### Post by iwallet on 2008-05-30
i have installed postal fudge pack, but now i wish to remove it...
how do i do this?! please help!!! :)

---

### Post by bwhite82 on 2008-05-30
How did you install it?

---

### Post by ibuclaw on 2008-05-30
If Postal installed itself in an isolated folder, then just removing the folder should do!

By UNIX standards, all "alien" software should install itself into the **/opt** directory.

Although, if you are unsure, this command should find it in the terminal:
```
cd / && find -type d -iname "*postal*" 2>/dev/null
```

Although, make sure that it is the **right** directory first!!


Regards
Iain

---

### Post by iwallet on 2008-05-31
thanks! ive deleted the folder, and im pretty sure its uninstalled!! i was running out of memory!!

---

