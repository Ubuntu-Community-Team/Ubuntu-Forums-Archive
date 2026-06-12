---
title: "HELP! I deleted /var/* !!!"
date: 2007-10-27
forum: General Help
---

### Post by master5o1 on 2007-10-27
can anyone help? I deleted the contents of /var and now I can't fix it by an upgrade...


apt's not working because of it :(

---

### Post by master5o1 on 2007-10-27
ok... just read one of the ~auto searched~ threads and i will restart to see if it's fine :D

---

### Post by master5o1 on 2007-10-27
not yet fixed

---

### Post by SPr on 2007-10-27
Have you got no backups of root partition?

If upgrading doesn't work then I guess reinstalling would be the final option :(

I hope you don't mind me asking but how and why did you delete /var?

---

### Post by suchawato on 2007-10-27
Do you have another computer or partition?
if you can install the same version on another computer, you can copy the entire /var directory as root onto a USB or CD. then load that into the system you deleted it in and copy it in place as Root.

That should fix your system.

---

### Post by master5o1 on 2007-10-27
just stupid human error ... didn't include "www" there to the /var/www/* => /var/* ... damnit...




I suppose it would be easy to reinstall... Just a question, would it be possible to copy some stuff from the live cd session's /var into my /var? that could be fun to try :D

---

### Post by master5o1 on 2007-10-27
> **suchawato said:**
> Do you have another computer or partition?
if you can install the same version on another computer, you can copy the entire /var directory as root onto a USB or CD. then load that into the system you deleted it in and copy it in place as Root.

That should fix your system.

so /var doesn't contain "computer specific" stuff?

---

### Post by chrisccoulson on 2007-10-27
/var DOES contain lots of stuff specific to your computer. For example, /var/lib/dpkg contains information about packages installed on your machine. You might be best off reinstalling TBH

---

### Post by suchawato on 2007-10-27
Yeah, you might have to reinstall some/all user installed packages.
also, ideally would be if you can do an install on a different partion of your problem system, and get the /var copy from there.
there should be a way to set one up in the "most unused space
" in the manufacturers install option, or in the alternate CD. 
This would be the best solution, and then, still, you probably still would have to reinstall some or all user installed applications.

---

### Post by master5o1 on 2007-10-27
well copying from the live cd has "worked" to my statisfaction. I will just wait till i find problems. I understand that because it doesn't know what's installed anymore (other than base system) I will be prompted for updates I have done. I will also just "install" them... Meh. It's easy enough from now isn't it?

---

### Post by suchawato on 2007-10-27
Oh that's a good idea!
I didn't think of that.
I suppose it wouldn't be perfect, but if its good enough, Great!

---

