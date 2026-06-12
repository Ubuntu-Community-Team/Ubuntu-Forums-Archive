---
title: "Default settings for new users"
date: 2006-10-12
forum: General Help
---

### Post by Stevko on 2006-10-12
I want to make VLC deffault application for all users (and also for those I add later). How can I do it (Right click->properties->Open with changes only for current user)?
I want to add keyboard indicator to bottom panel for all users, add one or two another keyboards and make ALT+Shift default combination for switching them for all users (and for those I create later).
I want to install some firefox extensions for all users...
How can I do it?

---

### Post by ayoli on 2006-10-12
i don't see a real/clean solution, but here what you can try:
panel settings and mime type associations are stored in .gnome dirs and .gconf dirs. mozilla/firefox extensions are stored in .mozilla, so:
copy your ~/.gnome* and ~/.gconf* and ~/.mozilla to your new user home dir, then chown the new user home dir (ie: chown -R new_username:users /home/new_username)

---

### Post by CatKiller on 2006-10-12
The Home folder configuration for new users is stored in /etc/skel/. So if you identify configuration files that are needed in the Home folder of new users you can put them in this directory to have them automatically created.

I believe that GNOME defaults - panel entries and the like - are stored in /usr/share/gconf/defaults/. There is a tool, **update-gconf-defaults**, that lets you fiddle with these. I've never used it, so I don't know what it's like. **man update-gconf-defaults** may give you more information.

---

### Post by ayoli on 2006-10-12
> **CatKiller said:**
> The Home folder configuration for new users is stored in /etc/skel/. So if you identify configuration files that are needed in the Home folder of new users you can put them in this directory to have them automatically created.

I believe that GNOME defaults - panel entries and the like - are stored in /usr/share/gconf/defaults/. There is a tool, **update-gconf-defaults**, that lets you fiddle with these. I've never used it, so I don't know what it's like. **man update-gconf-defaults** may give you more information.

hey, nice hint, i didn't know about update-gconf-defaults :)

---

### Post by CatKiller on 2006-10-12
> **ayoli said:**
> hey, nice hint, i didn't know about update-gconf-defaults :)

It's amazing what a **man -k gconf** will get you.

---

