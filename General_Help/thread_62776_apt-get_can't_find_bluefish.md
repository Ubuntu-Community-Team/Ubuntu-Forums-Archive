---
title: "apt-get can't find bluefish"
date: 2005-09-05
forum: General Help
---

### Post by legit on 2005-09-05
hey all,
so i just installed hoary today and am working on getting my fav. apps up and running, however while trying to get bluefish installed i had troubles.
i first updated apt-get:
**sudo apt-get update**
it ran and then i tried installing bluefish:
**sudo apt-get install bluefish**

it said it wasn't found? any ideas, i have no clue why its not working
thanks
- legit

---

### Post by macgyver2 on 2005-09-05
Make certain you have the universe repository enabled.  In your /etc/apt/sources.list check for a line similar to
```
deb ftp://archive.ubuntu.com/ubuntu/ hoary main universe
```
If you find a line like that with just [font=Courier New]main[/font], add [font=Courier New]universe[/font] to it.  Re-update then try to install bluefish again.

---

