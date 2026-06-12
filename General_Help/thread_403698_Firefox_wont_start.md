---
title: "Firefox wont start"
date: 2007-04-07
forum: General Help
---

### Post by allforcarrie on 2007-04-07
I have problems with firefox stopping and not being able to get it started again. Whenever i try any of the kill commands, none of them work. I tryed top but i don't see any FF processes running.  The only thing that seems to work is restarting the system. Anyone have any ideas?

---

### Post by spin2cool on 2007-04-07
try this:
```
ps aux | grep firefox
```

Then kill it by doing:
```
kill -9 <processID>
```

That still doesn't tell you why it's craashing, though.  Usually firefox crashes are caused by conflicting extensions or add-ons otherwise run amok.  Try starting firefox with a clean profile ("firefox -p") and see if you can replicate the problem.  If not, copy your bookmarks over and add your extensions back in one at a time until you figure out which one is the culprit.

---

