---
title: "update-notifier-motd.timer...Do I Need It?"
date: 2024-11-21
forum: General Help
---

### Post by wyattwhiteeagle on 2024-11-21
I mean...
> update-notifier-motd.timer                                                               loaded    active   waiting   Check to see whether there is a new version of Ubuntu available
What are these versions it checks for?

Isn't there a new version of Ubuntu available EVERY 6 MONTHS?
I know of the 22.04.1 and 22.04.4, etc.

---

### Post by TheFu on 2024-11-21
"need"?  That's a subjective question.  It is useful for many people.  It isn't useful for others.  The choice is yours.

---

### Post by Rubi1200 on 2024-11-21
I would first want to know what dependencies there are or what services depend on it before considering whether it is needed or not:

```
systemctl list-dependencies update-notifier-motd.timer

systemctl list-dependencies --reverse update-notifier-motd.timer

```

---

