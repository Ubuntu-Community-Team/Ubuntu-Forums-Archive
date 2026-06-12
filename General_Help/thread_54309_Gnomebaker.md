---
title: "Gnomebaker"
date: 2005-08-04
forum: General Help
---

### Post by defkewl on 2005-08-04
Does ubuntu repository include gnomebaker? Because I've tried adding repositories but couldn't find any package for gnomebaker. Thanx in advance

---

### Post by SamH on 2005-08-04
I installed gnomebaker from the universe repositories.  Should be no problem finding it if you followed the Unofficial Ubuntu 5.04 Starter Guide.

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by SamH on 2005-08-04
Oops......

Sorry, I didn't notice this was in the Warty section.  I don't know if gnomebaker is in the Warty repositories.  But I would be surprised if it wasn't.

---

### Post by goedson on 2005-08-04
[QUOTE=SamH]Oops......

Sorry, I didn't notice this was in the Warty section.  I don't know if gnomebaker is in the Warty repositories.  But I would be surprised if it wasn't.[/QUOTE]

It is not in Warty's repository, but you may find packages for Warty in the repositories listed in [my GnomeBaker page](http://wiki.ubuntu.com/GnomeBaker) . Unfortunately, I didn't have the time to  build a Gnomebaker 0.4 package for Warty, yet.

---

### Post by defkewl on 2005-08-04
It didn't work. I've add up breezy repository. Perhaps I should add hoary repository?

---

### Post by goedson on 2005-08-05
[QUOTE=defkewl]It didn't work. I've add up breezy repository. Perhaps I should add hoary repository?[/QUOTE]

If you're using Warty, you should have added this:
```

deb http://people.debian.org/~goedson/packages/ubuntu/warty/gnomebaker/releases/i386/ ./

```

to your /etc/apt/sources.list

---

