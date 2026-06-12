---
title: "Bypassing Trash"
date: 2008-03-02
forum: General Help
---

### Post by ~LoKe on 2008-03-02
I'm setting my computer up to be used by my brother while I'm gone, and I'm trying to make it as easy to use as possible.  

Basically, he's going to need to delete large files/folders often, and they add up in the trash and take up critical space.   I know the command line and shift+del are easy ways, but is there simply a setting I can change do that any method used to delete would skip the trash?

I could set up a cronjob to clear the trash periodically (which I'll do just in case), but I want something in place at all times.  Any suggestions?

---

### Post by fsamuels on 2008-03-02
I don't think there is a way to turn off Trash completely. There is a [Gnome bug]("http://bugzilla.gnome.org/show_bug.cgi?id=315022") for it since version 2.14 so it isn't looking promising.

You can also enable a context menu for "Delete" in addition to "Move to trash". Install 'gconf' and run the gconf-editor. Then enable apps/nautilus/preferences/enable_delete. I hope that helps some.

---

### Post by Anduu on 2008-03-02
Other than what has already been stated there isn't much else you can do short of putting a big sticky note for you brother on the monitor saying ***_[COLOR="Red"]"EMPTY THE TRASH DOOFUS!"[/COLOR]_*** :p

I think the cron job is your best bet.

---

### Post by Whiffle on 2008-03-02
In kde there is an option to bypass it (settings > configure konqueror > behavior), dunno about gnome.

---

