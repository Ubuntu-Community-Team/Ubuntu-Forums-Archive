---
title: "Query on Gnome-UI Warning"
date: 2006-12-27
forum: General Help
---

### Post by lucid on 2006-12-27
Hi,

When I enter ' gksudo gedit /etc/apt/sources.list' I get the following warning:

(gedit:16762): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I haven't experienced this before, and am unsure as to what precisely the problem is let alone what the the fix might be. Any ideas?

---

### Post by sean222 on 2007-01-29
Bump.

I also have this problem.

Using this: sudo gedit /etc/apt/sources.list
works fine...but I have heard that doing this messes up file permissions or something.

I guess I'll just use sudo nano -w /etc/apt/sources.list for now.

-Sean

---

### Post by Ramses de Norre on 2007-01-29
It's a known bug but it wont be fixed because it doesn't cause any harm and the developers focus on bugs that do cause real harm.
So don't worry about it.

---

### Post by sean222 on 2007-01-29
> **Ramses de Norre said:**
> It's a known bug but it wont be fixed because it doesn't cause any harm and the developers focus on bugs that do cause real harm.
So don't worry about it.

Thanks! I just stumbled upon a page saying that's it is a 'low-priority' bug. Glad to know it's nothing to worry about, it just looks so scary...especially when you're editing crucial system files :)

---

