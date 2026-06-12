---
title: "[SOLVED] Clear Firefox cache for multiple users"
date: 2008-03-14
forum: General Help
---

### Post by Ardrias on 2008-03-14
My users are browsing. And that's a problem. ;)

On a serious note, is there any way I could force a emptying of the cache for all users from the CLI? It's not an option to tell all my users to clear the cache themselves, as it would probably have the adverse effect.

---

### Post by Ardrias on 2008-03-18
Hmmm. Could I perhaps use ```
sudo rm -rf /home/*/.mozilla/firefox/*/Cache
```?

It works when I enter ```
sudo rm -rf /home/UserName/.mozilla/firefox/*/Cache
``` but I need to be sure that it doesnt read the first * and then decides to delete everything below that, ie all the users homedirs. I like my head where it is too much ;)

I've tested it and it seems to work the way I want, but I'm still hesistant to use it on my live /home :|

---

### Post by Ardrias on 2008-03-18
For what it's worth, it works great. Marking this as solved :p

---

