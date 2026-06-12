---
title: "Trying to install Kasablanca in Gnome"
date: 2007-02-26
forum: General Help
---

### Post by mjpatey on 2007-02-26
I'm trying to install a GUI-based ftp client, Kasablanca.  I'm running Ubuntu in the Gnome environment, though, so trying to install the .deb returns:

> ERROR: Dependency is not satisfiable:kdelibs4

Well, I thought, we'll just see about that.  From Synaptic, I installed:  kdelibs, kdelibs4c2a, kde4libs-data, and kdelibs-data.  (After trying to simply "sudo aptitude install kdelibs4", which wasn't found).

Still, when I try to install Kasablanca using the .deb file, I get the "not satisfiable" error, even after logging out/in, and then after a reboot.

Anybody know what I should try next?

Thanks!

-Mark

---

### Post by Maestro23 on 2007-02-26
Did you install kdelibs4-dev?

---

### Post by mjpatey on 2007-02-26
No, it seemed like something only for people who wanted to "roll their own" (not me).  But I'm installing it now!  I'll let you know what happens.

---

### Post by mjpatey on 2007-02-26
No, still didn't work.  :-(

---

### Post by Maestro23 on 2007-02-26
> **mjpatey said:**
> No, still didn't work.  :-(

I just installed kasablanca  0.4.0.2(I'm running Xubuntu) from the repositories via aptitude.  Is there some reason why you are using the .deb file?  Is it a newer version?

---

### Post by mjpatey on 2007-02-26
Well, you had to go and make sense!  That worked perfectly.  I was only using the .deb file because that's how I stumbled across the program (a link on a website to the .deb).

Thanks!  All's well.

-Mark

---

### Post by Maestro23 on 2007-02-26
> **mjpatey said:**
> Well, you had to go and make sense!  That worked perfectly.  I was only using the .deb file because that's how I stumbled across the program (a link on a website to the .deb).

Thanks!  All's well.

-Mark

ROFL.. Glad you are good-to-go now.

*Note:  Always check the Repositories first for a program.

Good luck in future Ubuntu adventures.:guitar:

---

