---
title: "Delete /var/cache/apt/archives contents?"
date: 2008-06-29
forum: General Help
---

### Post by change_mode on 2008-06-29
Is it safe to delete the contents of the folder /var/cache/apt/archives?

There are all the .deb files of packets I've downloaded.


edit
Sorry, should have used the search function... just in case someone has the same question:

sudo apt-get clean

---

### Post by tzulberti on 2008-06-29
There is also sudo apt-get autoclean, which deletes all the packages that aren't the newest version. 

Please, mark the post as solved.

---

