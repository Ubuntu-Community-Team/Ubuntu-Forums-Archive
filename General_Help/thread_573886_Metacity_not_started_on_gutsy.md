---
title: "Metacity not started on gutsy"
date: 2007-10-12
forum: General Help
---

### Post by Ramses de Norre on 2007-10-12
Hi

I installed ubuntu gutsy on one of the computers here and everything has ran fine for a week now, but all of a sudden when I start gnome, metacity isn't started anymore... This happened for the first time yesterday and all I can remember that I've done was removing all compiz stuff (I don't need it) which wasn't used I think since all "desktop effects" are turned of.
I fixed it temporary by putting **metacity --replace** in my start up programs but I'd like a better way, one that doesn't needs to be done for every user individually...

Anyone who knows how to fix this? Thanks.

---

### Post by Ramses de Norre on 2007-10-13
Anyone?

---

### Post by bsdemon on 2007-10-21
I have the same problem...

---

### Post by bsdemon on 2007-10-21
Ok, it seems to be that your default wm is compiz.
Change it with gconf-editor.

---

### Post by Ramses de Norre on 2007-10-22
Ubuntu's default wm is compiz??? I thought compiz wasn't stable? And it certainly isn't low on memory.
Thanks for the help though, I'll look around in gconf tomorrow. (I need to change that for every user individually, don't I?)

---

### Post by Bruce M. on 2008-02-20
> **Ramses de Norre said:**
> Ubuntu's default wm is compiz??? I thought compiz wasn't stable? And it certainly isn't low on memory.
Thanks for the help though, I'll look around in gconf tomorrow. (I need to change that for every user individually, don't I?)

I don't want (read: Can't use compiz .. old computer) and want to use metacity.

Did it work when you changed it in the config editor?

---

