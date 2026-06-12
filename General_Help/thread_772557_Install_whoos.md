---
title: "Install whoos"
date: 2008-04-28
forum: General Help
---

### Post by piromedic on 2008-04-28
I have up graded to 8.04.  Now when I try to install a program like frostwire I keep getting a message stating that: "Only one software management tool is allowed to run at the same time.  Please close the other application e.g. 'Update Manager',aptitude'or'Synaptic' first.  The only problem is that I have nothing else running.  Unless the new version 8.04 has something running in the background that I don't know about.

Any help please
Don

---

### Post by coolaj86 on 2008-04-28
Probably just a leftover lock file try (as root)
```
rm /var/lib/dpkg/lock -f
```

---

### Post by piromedic on 2008-04-28
I am new to Linux.  How do I sign in as root?

---

### Post by piromedic on 2008-04-28
I tried the rm /var/lib/dpkg/lock -f in terminal and was given the reply rm: cannot remove `/var/lib/dpkg/lock': Permission denied

---

### Post by arvevans on 2008-04-28
Try this:

[INDENT]sudo rm /var/lib/dpkg/lock -f[/INDENT]

which should run as root after asking you for your password.
_._

---

### Post by piromedic on 2008-04-28
That did nothing.  When I run update manager i get this There is another synaptic running in non-interactive mode. Please wait for it to finish first.

---

### Post by piromedic on 2008-04-28
Okay I got it I had to sudo apt-get -f install

---

