---
title: "How to *completely* remove a broken module?"
date: 2008-06-09
forum: General Help
---

### Post by jreikes on 2008-06-09
Warning: I'm definitely still a big time Linux noob...

I tried to install gspca from the tar file.  On reboot, I see some error message about not being able to build the module go by on my screen.  I don't know what log file to find that error message in or I'd post it here.

I tried modprobe -r gspca, but I see that when I reboot, gspca still shows in lsmod.  So am I correct that modprobe -r only removes the module from memory, but not from the startup sequence?

My question really has two sides: 1) How do I COMPLETELY remove gspca; and 2) In a general sense, how do I COMPLETELY remove a module?  I ask part 2 because, while trying to clean out the gspca stuff, I found some linuxant stuff remaining - and Linuxant didn't work happily on my system (killed audio and faxing just isn't mission critical to me), so I definitely don't need it.

Thanks for the help,
-John

---

### Post by utsuprainfra on 2008-06-09
is there a make uninstall for the source / makefile?

---

### Post by jreikes on 2008-06-10
I'll look, but remember the make process failed.  So I don't have a lot of faith that the make uninstall would work even if it's there.  I'd really like to know how to manually remove this and my linuxant modules without relying on their own uninstall processes.

---

