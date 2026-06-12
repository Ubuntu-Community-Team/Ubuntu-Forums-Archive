---
title: "Plank default settings for all users?"
date: 2021-03-05
forum: General Help
---

### Post by wvoutlaw2k on 2021-03-05
I'm getting back into working on my customized Xubuntu remaster, and I'm trying to turn it into a clone of macOS.

I've gotten all the default settings working for all users except for Plank.

I've tried copying the "user" file from /home/username/.config/dconf to /etc/skel/.config/dconf, and every time I try creating a new user to see if the Plank settings work, it defaults to the default Plank settings as if it were a fresh install.

Any suggestions would be greatly appreciated. I'm making this remaster for a few friends who are migrating from macOS and want a similar desktop experience.

EDIT: Found it! Had to copy /home/username/.config/plank to /etc/skel/.config and created a new test user account and voila, it worked!

---

