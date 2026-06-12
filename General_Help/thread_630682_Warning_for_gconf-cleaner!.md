---
title: "Warning for gconf-cleaner!"
date: 2007-12-03
forum: General Help
---

### Post by olskar on 2007-12-03
I recently used g-confcleaner([http://code.google.com/p/gconf-cleaner/](http://code.google.com/p/gconf-cleaner/)) to clean my g-conf-"registry".
Before the cleaning I was given the opportunity to make a backup if something should go wrong, so I did.

After the cleaning, some of my compiz-settings was totally gone and all the settings for avant-window-navigator..
No problem, I'll just restore the backup! Then I realized it was no place to restore the backup..


To first offer the user a chance to make a backup but not a chance to restore is really bad! :(:mad:

Does someone know if there is a way to restore this anyway?

---

### Post by cipher_nemo on 2007-12-03
That's a very small project by one individual. I'd post a comment about it on his google code web space if I were you. Here's the known issues with it: [http://code.google.com/p/gconf-cleaner/issues/list](http://code.google.com/p/gconf-cleaner/issues/list)

---

### Post by olskar on 2007-12-03
Thanks, managed to get the reginfo back I think.
I post the solution here if someone is interested

In the terminal:
gconftool --load backupfilename

---

### Post by cipher_nemo on 2007-12-03
Thanks for posting the solution! :) You never know who will Google this in the future.

---

