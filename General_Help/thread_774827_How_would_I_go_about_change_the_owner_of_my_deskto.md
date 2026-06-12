---
title: "How would I go about change the owner of my desktop? (owner: 501)"
date: 2008-04-29
forum: General Help
---

### Post by Lord Xeb on 2008-04-29
Currently the owner is 501. I have never encountered this problem. I have gone into root using a script and trying to change it, but that failed. Now what?

---

### Post by PinkFloyd102489 on 2008-04-29
What do you mean "owner"?

---

### Post by Lord Xeb on 2008-04-29
Thats what I said...If you go and check the properties of your desktop folder it should say you right? well mine says 501. How do you change that?

---

### Post by Lord Xeb on 2008-04-29
If you don't believe me, I attached a screen shot of the permissions to my desktop

---

### Post by Zorael on 2008-04-29
```
$ sudo chown (username) ~ -R
$ sudo chgrp (usergroup) ~ -R
```

Never done it myself, but should work. You need to know your group though. By default it's the same as your username. Enter 'groups' in a terminal to get a listing; it's usually the first one listed.
```
username@usergroup:~$ groups
**usergroup** adm dialout cdrom floppy lalal weee ... n+1
```

---

