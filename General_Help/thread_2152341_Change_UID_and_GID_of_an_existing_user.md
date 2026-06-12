---
title: "Change UID and GID of an existing user"
date: 2013-06-07
forum: General Help
---

### Post by UserJB on 2013-06-07
I have an existing user on my machine and I want to change the UID and GID which were 1000, by default, to 500.  How can I do this?

---

### Post by CatKiller on 2013-06-07
Why do you want to? A whole bunch of things check that the UID is over 1000 as a means of separating out real users from system users as a sanity check.

If you really must, it's probably a usermod option.

---

