---
title: "Very strange - adduser"
date: 2022-05-09
forum: General Help
---

### Post by Hotchilli on 2022-05-09
I am in lubuntu 20.04 64 bit and l issuing command adduser l get
only two users allowed?
Bug?

---

### Post by GhX6GZMB on 2022-05-09
You're running the command without parameters, which won't work. The error message is a bit cryptic, I agree, but it's not Lubuntu specific. It means that you can't run the command with 0 names. You need at least a new user, and optionally also a new group.
In Lubuntu, I use the GUI to add users, much simpler.

---

### Post by Hotchilli on 2022-05-10
Sorry forgot to mention eg
adduser phil
Command comes back the only two users allowed- only other user is root
Hope this makes a little more clear

---

### Post by GhX6GZMB on 2022-05-10
"sudo adduser phil" should work.
If you're trying to do this using "su", you're heading for a cropper. Never do that in any ubuntu dialect.

---

