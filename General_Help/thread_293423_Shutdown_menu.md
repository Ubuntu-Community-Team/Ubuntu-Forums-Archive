---
title: "Shutdown menu"
date: 2006-11-05
forum: General Help
---

### Post by Bou on 2006-11-05
Hi, I'm getting a shight problem with my shutdown menu: the thing is, it doesn't darken the screen or capture mouse clicks. I'll show you:

[[IMG]http://img446.imageshack.us/img446/5640/sinnombremp8.th.jpg[/IMG]](http://img446.imageshack.us/my.php?image=sinnombremp8.jpg)

Any idea why this is happening?

---

### Post by Bou on 2006-11-10
I have reinstalled the system and the problem persists, but I don't get it with other users so I assume I must have messed some gconf key up. Do you know where in gconf-editor I can modify the shutdown menu settings, or how I can reset EVERY key in gconf?

---

### Post by CatKiller on 2006-11-10
You **should** (I've never tried it) be able to get back to the default gconf setup by renaming the ~/.gconf file to something else and then logging out and logging back in. Hopefully, it will notice that the file isn't there, and make a new one for you.

Good luck.

---

### Post by Bou on 2006-11-11
> **CatKiller said:**
> You **should** (I've never tried it) be able to get back to the default gconf setup by renaming the ~/.gconf file to something else and then logging out and logging back in. Hopefully, it will notice that the file isn't there, and make a new one for you.

Good luck.

Yes, I did that yesterday following the advice of the kind folks in #ubuntu, and it fixed the issue. I was afraid that I would lose my bookmarks, evolution messages etc, but fortunately none of that happened.

The only thing that still bugs me is not knowing where the hell it went wrong, but oh well, I'll get over it.

---

