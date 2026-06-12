---
title: "Cannot Update --Help?"
date: 2014-08-18
forum: General Help
---

### Post by Templarx88 on 2014-08-18
When I run sudo apt-get update I receive the following:

W: Duplicate sources.list entry [http://dl.google.com/linux/chrome-remote-desktop/deb/](http://dl.google.com/linux/chrome-remote-desktop/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome-remote-desktop_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

Ive tried locating this and removing it to no avail.

---

### Post by kc1di on 2014-08-18
It looks like you have google chrome in  your source list twice.

you need to remove on instance and try again.
you can do that by going to software center > edit> software sources under the other tab uncheck one of the google. com entries and try again.

---

