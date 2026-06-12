---
title: "location of firefox extensions"
date: 2007-01-22
forum: General Help
---

### Post by jarviser on 2007-01-22
Like several people my Firefox keeps closing when browsing Yahoo mail. Can someone tell me **where in the filesystem the Firefox extensions are all kept **so I can delete them before reinstalling Firefox? I have tried searching quite a few threads and my Ubuntu Hacks book doesnt tell me either.

---

### Post by Stemp on 2007-01-22
Why aren't you just uninstall or deactivate the extensions in Firefox ?

---

### Post by jarviser on 2007-01-22
> **Stemp said:**
> Why aren't you just uninstall or deactivate the extensions in Firefox ?
Yep, that's what I am trying to do. If there's a better way to clean out all the extensions then please let me know. I thought in Linux it could be done by deleting the *.so files out of the folders. I just can't find them using ctrl-F in Nautilus.

---

### Post by _simon_ on 2007-01-22
~/.mozilla/firefox/default/extensions/

Note 1 .mozilla is a hidden file.
Note 2 default actually has a bunch of letters and numbers in front of it.

---

### Post by jarviser on 2007-01-22
Ah that's where it was hiding (I seem to remember the .Trash file in my memory stick eluding me for the same reason - couldn't understand why it seemed to be full when it was really empty. Pesky hidden files).  Anyhoo I uninstalled Firefox "completely" in Synaptic, then deleted everything in the ./Mozilla folder,  and reinstalled Firefox (plus the gnome-app-instal and yelp that disappeared with the purge) and all is OK now. Cheers.

---

