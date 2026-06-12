---
title: "xf86OpenConsole:Cannot open virtual console 8(permission denied)"
date: 2013-08-03
forum: General Help
---

### Post by ihsankocak on 2013-08-03
Everything started with changing the ownership of /usr directory.I got several problems while using ```
startx
``` but finally i got this error while using startx:
**xf86OpenConsole:Cannot open virtual console 8(permission denied)**.Do you have any idea what the problem can be solved?But i can succesfully get in the system with sudo startx but this time sound is gone, vpn configuration disabled and it does not see the external hard disc  etc. problems occur.

---

### Post by ajgreeny on 2013-08-03
Who now owns the /usr directory?

It should be owned by root and if not you may be in big trouble.  Why did you change ownership in the first place?

---

### Post by ihsankocak on 2013-08-03
Thank you for your answer.I changed it to delete 2 folder that came with a program that i uninstalled.But after that i changed the ownership to root again.Before /usr was abc user's, sudo did not work but after i changed it to root it worked but this time while i want to use startx it says:**xf86OpenConsole:Cannot open virtual console 8(permission denied)**. sudo startx works but this time sound is gone, it does not see the external hard disc and vpn configuration is disabled etc.What can i do for this issue?

---

### Post by ajgreeny on 2013-08-03
Sorry, but I don't have a clue what to suggest.

I think this should be a warning to you not to change things in the root filesystem if you don't know the potential outcome.

The difficulty is probably because not all the files in /usr have exactly the same permissions, but in your case they probably now are all the same.

---

### Post by 1clue on 2013-08-03
Do you remember if the chmod command(s) you used to make it nonstandard was recursive or not?

If it was recursive, then IMO you'd just as well wipe off your hard disk and reinstall.

If it wasn't then it should be:
**chown root:root /usr**
**chmod 755 /usr**

That's true for all the directories directly under /usr too in my case, but it's absolutely NOT the case for all the files and folders.

There's no good reason to change permissions on a file or folder that Ubuntu installed.

---

### Post by ihsankocak on 2013-08-03
Thanks for your answer.I used recursive mode.

---

### Post by 1clue on 2013-08-04
OK your permissions are broken, and AFAIK there's no easy fix.  I'd pull your data off to a backup, and then reinstall.

---

