---
title: "automounter going crazy"
date: 2007-07-30
forum: General Help
---

### Post by kelt65 on 2007-07-30
Running feisty.

when using gnome, every few minutes autofs consumes all cpu time, and causes the desktop to freeze for  about 30 seconds. This doesn't happen in KDE or any other desktop. I'd like to use gnome, though, at least for a while. I'm starting to like it.

I have several autofs mount points which get their maps from an ldap server.

I can only assume some sort of interaction with the desktop volume manager gunk is making it go haywire like that.

An strace of autofs doesn't turn up anything interesting, it's just reading through the list of mounts in the maps over and over when it's going nuts. Keep in mind this only happens in gnome.

UPDATE: I switched my automount maps to nis and this problem seems to have vanished. Weird.

---

