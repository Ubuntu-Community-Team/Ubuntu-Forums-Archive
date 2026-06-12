---
title: "GUI/Frontend for locate"
date: 2007-02-11
forum: General Help
---

### Post by PetePete on 2007-02-11
is there a good GUI for locate? I've got no problems with using the CLI but GUI's just look nicer :D

i've seen xlocate but when compling i get the error 

```

disklist.h:92: error: extra qualification ‘DiskEntry::’ on member ‘DiskEntry’
topwidget.h:147: error: extra qualification ‘HelpMenu::’ on member ‘HelpMenu’
make: *** [qt3/disklist.o] Error 1

```

is there any other alternatives?

ohh and also, whats the difference between locate and slocate? i've read that slocate is meant to be more secure, but i dont understand whats more secure about it, or how a find program could even be insecure?!!

TIA

---

### Post by kalikiana on 2007-02-11
May I suggest that you try catfish? It is a Gtk+2 frontend for file searching.

[http://software.twotoasts.de?page=catfish](http://software.twotoasts.de?page=catfish)

As for the difference between locate and slocate, the latter outputs only files which the current user has access to. That means if you create an index with root rights, locate would show all the files while slocate omits inaccessible files.

---

### Post by commonplace on 2007-02-20
Wow, why isn't Catfish built-in to Ubuntu (or Gnome/KDE itself)?! Thanks for the recommendation. I'm glad I found this tool!

/Kevin

---

