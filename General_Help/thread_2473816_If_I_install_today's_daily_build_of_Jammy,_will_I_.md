---
title: "If I install today's daily build of Jammy, will I need to reinstall later?"
date: 2022-04-14
forum: General Help
---

### Post by Tom_Carr on 2022-04-14
If I install today's (April 14), daily build of Jammy, will I need to reinstall when the LTS is  released on April 21, or can I just  do an update of the version I have already installed and set up?

---

### Post by deadflowr on 2022-04-14
No need to reinstall.
Just keep updating as you go.
You can periodically do some minor clean it up by running the apt clean and apt autoremove commands.
But keeping things clean(er) is purely optional.

---

### Post by ajgreeny on 2022-04-14
You should simply be able to keep updating and end up with the same OS as you would if you waited until next week.
Some people like to clean install again after release in order to ensure there is no "cruft" left behind but generally I am not sure if this is worth doing; certainly run **sudo apt autoremove ** to ensure any unnecessary packages are cleaned away, but a second clean install will probably not add a great deal to the system, nor take away a great deal either.

I have had Xubuntu 22.04 running now since it was first available as an installable .iso archive and it is, and has always been, performing very well with only an occasional problem that did not save itself in normal upgrades.

---

