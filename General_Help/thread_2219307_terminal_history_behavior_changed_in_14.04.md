---
title: "terminal history behavior changed in 14.04?"
date: 2014-04-23
forum: General Help
---

### Post by kurja on 2014-04-23
Have there been changed to how terminal history works between 12.04 and 14.04? I keep trying to type beginning of a command I've used earlier, for an example "sudo apt-get" and then hitting the up arrow to recall the previous command that started "sudo apt-get" but I get just the previous command which may have been ls or whatever. Is there a setting for this??

---

### Post by Habitual on 2014-04-23
I don't know the technical answer to this, however adding
```
bind '"\e[A": history-search-backward'
bind '"\e[B": history-search-forward'
```to your ~/.bashrc can restore this functionality for you.

---

### Post by kurja on 2014-04-23
Thanks, that works.

---

### Post by Habitual on 2014-04-23
Glad it worked out.
That 'tip' is indispensable for me, I use those on every machine where I have access.

---

