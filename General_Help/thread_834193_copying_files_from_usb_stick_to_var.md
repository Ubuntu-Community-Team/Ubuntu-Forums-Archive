---
title: "copying files from usb stick to /var"
date: 2008-06-19
forum: General Help
---

### Post by gandalf458 on 2008-06-19
I'm having a bit of trouble getting my head around permissions. I have a laptop which I intend only to be used by me. I tried to copy from a usb drive to /var and was told I didn't have permission to create a new directory. Rather than using the command line to copy I would prefer to give myself create and delete access to /var. Can I do this?

Thanks G :)

---

### Post by Joeb454 on 2008-06-19
I'm sure you can :)

Though personally I wouldn't recommend it at all. As you don't want to use the command line, I would hit Alt+F2 and enter ```
gksudo nautilus
``` and copy the files graphically that way, though be extremely careful what you copy/delete etc. as root :)

---

### Post by gandalf458 on 2008-06-19
Thanks, Joe. I'll give that a go. Like your other blog! G :)

---

