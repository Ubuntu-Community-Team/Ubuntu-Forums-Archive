---
title: "Can't (un)install sun-java5-bin"
date: 2006-10-19
forum: General Help
---

### Post by Bastanteroma on 2006-10-19
I tried to install sun-java5-bin in automatix, then from the command line, but when the license agreement appeared I hit enter and nothing happened and escape just made it reload.  How do I say "ok"?

I closed the window, ran dpkg --configure -a, then tried sudo apt-get remove sun-java5-bin, but it says the package is in bad shape and needs to be reinstalled before it can be removed.

This is in kubuntu 6.10.

---

### Post by Bastanteroma on 2006-10-19
I just ran a bunch of commands and finally sudo dpkg -r --force-remove-reinstreq sun-java5-bin sun-java5-jre seemed to remove the remains.

But I still can't figure out why I can just hit enter and have the package install.  Seems like I'm making a dopey mistake of some sort.

---

### Post by arnieboy on 2006-10-20
> **Bastanteroma said:**
> I tried to install sun-java5-bin in automatix, then from the command line, but when the license agreement appeared I hit enter and nothing happened and escape just made it reload.  How do I say "ok"?

I closed the window, ran dpkg --configure -a, then tried sudo apt-get remove sun-java5-bin, but it says the package is in bad shape and needs to be reinstalled before it can be removed.

This is in kubuntu 6.10.

use the "tab" key to highlight OK

---

### Post by Bastanteroma on 2006-10-21
Doh.

Thanks

---

### Post by sdf88 on 2006-10-21
Thanks i have spent the last few hrs trying to figure this out and all i had to do was press tab (sigh)](*,)

---

