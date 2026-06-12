---
title: "Nautilus crashes when clicking Trashapplet"
date: 2007-12-09
forum: General Help
---

### Post by Showan2 on 2007-12-09
hello

I'm using Gutsy 64 bits

Sometimes when I want to access my trashcan via the Trashapplet my Nautilus completely locks up

restarting nautilus and trashapplet doesn't work. I have to reboot.

Does anyone have the same problem or a solution to this?

It's very annoying

thanks

---

### Post by Showan2 on 2008-01-05
Hello

After some time I have a partial solution to this.

It seems to have to do something with /home/xxx/.gnome/gnome-vfs/.trash_entry_cache

If you delete or rename this file and do "killall nautilus" the desktop reappears and I can re use nautilus
There is one problem though, when I try to delete something nautilus locks up and I have to do a killall nautilus

I guess I am getting close. Anyone with similar problems?

---

### Post by EricDB on 2008-02-17
I have similar same trouble with 7.10--when I try to delete files from my desktop (either by rightclicking and sending to trash, or by hitting the delete key), nautilus locks up and I have to "killall -9 nautilus" to get it back.

My workaround is to rm the files from the command line, but that gets old.

I haven't done anything yet to try to fix this, in particular I haven't messed with /home/xxx/.gnome/gnome-vfs/.trash_entry_cache.  AFAIK it's been this way since I installed, though maybe something I did early on while trying to get all the little bits working caused it.

---

### Post by Showan2 on 2008-02-17
it's safe to remove the .trash_entry_cache file when nautilus locks up. Then do a killall nautilus, and nautilus restarts and creates a new .trash_entry_cache file. Now you can use nautilus, but removing files by pressing delete on them results in a lock up. Solution: cut&paste the files you want to delete to the .trash folder then press Delete while you are on them.

---

