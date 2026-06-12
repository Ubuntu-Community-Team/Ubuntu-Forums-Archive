---
title: "Clear recent documents and trash on logout?"
date: 2007-06-15
forum: General Help
---

### Post by wie6Ein0 on 2007-06-15
Is there a way to clear the "Recent Documents" and/or "Trash" on logout in Ubuntu 7.04 Feisty Fawn (Gnome; Not KDE)? I'm hoping that there is a terminal command that will clear the history so that it doesn't have to be done manually.

I'm aware that I can create another "secret" user account for those times I want to keep my history private from other users, but I'd really just like to do it the simple way without creating new user accounts.

---

### Post by kidders on 2007-06-17
Hi there,

It seems like you can figure the trash out already. With a little poking around, I discovered that Gnome's "Recent Documents" list lives in ~/.recently-used.xbel. Unfortunately it's an XML document (which has the potential to make messing with it irritating), but this particular one seems okay.

:-)

---

