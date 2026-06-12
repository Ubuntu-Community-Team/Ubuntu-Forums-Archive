---
title: "Software updates from the command line"
date: 2008-05-28
forum: General Help
---

### Post by bagm on 2008-05-28
Hi,

   I've been told that the following command is the same as software updates that appear automatically in my tray:

"sudo aptitude update && sudo aptitude safe-upgrade"

Is this correct? Can I add any other commands to keep my Ubuntu clean?

Any help will be greatly appreciated.
Thanks in advance.

---

### Post by macaholic on 2008-05-28
Ya that looks right, you could aptitude or apt-get, it doesn't really matter, and I'm not sure what the difference betweensafe-upgrade an a normal upgrade is, but they should both work.

---

### Post by bagm on 2008-05-28
Hi,

update-manager program found two software updates that

"sudo aptitude update && sudo aptitude safe-upgrade"

did not find.

What's wrong?

TIA.

---

### Post by LaRoza on 2008-05-28
> **bagm said:**
> Hi,

   I've been told that the following command is the same as software updates that appear automatically in my tray:

"sudo aptitude update && sudo aptitude safe-upgrade"

Is this correct? Can I add any other commands to keep my Ubuntu clean?

Any help will be greatly appreciated.
Thanks in advance.

I use:

```

sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean

```

---

### Post by ibutho on 2008-05-28
Another option you can try is 
```
aptitude full-upgrade
```
For differences on safe-upgrade and full-upgrade look [here]("http://pthree.org/2007/09/24/aptitude-full-upgrade-versus-safe-upgrade/").

---

