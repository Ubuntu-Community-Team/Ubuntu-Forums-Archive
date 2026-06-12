---
title: "my desktop won't load"
date: 2006-11-28
forum: General Help
---

### Post by weird_c00kie on 2006-11-28
had another weird thing happen today. i booted my system up at the start of the day, logged in like normal, and discovered that gnome-desktop wouldn't load.
didn't come up with any error messages or anything like that. it just doesn't load.

i checked synaptic and saw that it had been uninstalled, even though i haven't installed or uninstalled anything in the last few days.
i reinstalled it, logged off and back on again, and it still doesn't load.
i tried restarting as well, but nothing happened.

i tried running it through the terminal by typing *gnome-desktop* but that didn't work either. comes up with command unknown.

everything else is working perfectly fine; it's just the desktop that's giving me trouble.
i can't right-click on it and i can't see any of the files that should be on it.


any ideas?

---

### Post by scxtt on 2006-11-28
gnome (.gnome*) related dirs/files in your $HOME directory got messed up? ... and other users having problems?  try making a new user in recovery mode [ **useradd** ] and doing a **startx** - to build it from scratch ...

---

### Post by taurus on 2006-11-28
Or remove ~/.gnome, ~/.gnome2, & ~/.gome2_private...

---

### Post by weird_c00kie on 2006-11-29
i don't know if any other 'users' are having problems. i'm the only user on my home PC :p

also, as my signature says, i'm a bit of a n00b. i'd be reluctant to mess with the users without slightly more specific instructions hehe

and taurus, while i have no doubt that your response would be really useful to someone who knows what you're suggesting, i wouldn't have a clue :p

unless you mean to delete those hidden directories from the root folder, which i guess i know how to do.
aren't they necessary though? don't they contain icons and themes and stuff?

---

### Post by taurus on 2006-11-29
No, you delete those directories in your $HOME directory which Gnome somehow messes it up.  If you remove it, the next time you log into Gnome, it will create the defaults for you!  Isn't that what you want?

---

### Post by weird_c00kie on 2006-11-29
pretty much, yeah. just sucks that i have to lose my settings :p

i'll give it a go now and hope it works :)

---

### Post by weird_c00kie on 2006-11-29
i deleted just the gnome2 and gnome2_private folders, relogged and now it works fine.
thanks :D

---

