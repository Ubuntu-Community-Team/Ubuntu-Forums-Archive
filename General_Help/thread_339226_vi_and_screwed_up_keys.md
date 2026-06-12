---
title: "vi and screwed up keys"
date: 2007-01-15
forum: General Help
---

### Post by trash on 2007-01-15
I just did a fresh install on my mac of Edgy everything seems fine except when i try to use vi in the terminal then my keys seem to get all screwed up for example, no delete(backspace), arrow keys insert letters- <-=D, ->=C, arrows up and down do nothing, I to insert does nothing....

This is the first time i have ever seem this and did a search but found nothing similar... help i'm lost without vi lol

xubuntu, edgy, mac

---

### Post by Rippey on 2007-01-15
I've seen that on other machines, although I don't know a solution using the command vim instead of vi seems to work in some cases.

---

### Post by taurus on 2007-01-15
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install vim-full
```

---

### Post by trash on 2007-01-16
Thanks, found your post on another thread with the same problem, though it's just as easy to type sudo mousepad /.... rather than downloading 40mb to get vi working.... for now anyway.
I really think this is something that should be a default install since a lot of post on this forum use vi when giving commands and it would save a lot of time for people on dialup.

---

### Post by meng on 2007-01-16
Even without installing vim-full, it may be the case that
vim [name-of-file]
may work for you

---

### Post by trash on 2007-01-16
> **meng said:**
> Even without installing vim-full, it may be the case that
vim [name-of-file]
may work for you

I feel like a right idiot for not trying that before lol, yes it's perfect. cheers:)

---

### Post by meng on 2007-01-16
Although Rippey actually suggested it first.

---

### Post by trash on 2007-01-16
> **Rippey said:**
> I've seen that on other machines, although I don't know a solution using the command vim instead of vi seems to work in some cases.

Dunno why I didn't at least try it when you suggested it, all I can think is that i was frustrated and the saw the next post with the fix, while for me, actually using vim is the simplest fix.
thanks!

---

