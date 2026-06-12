---
title: "Shell keyboard shortcut problem"
date: 2007-06-27
forum: General Help
---

### Post by VHans on 2007-06-27
Hello,

I am using Ubuntu 7.04 and have following little problem: when I use the 'up arrow' key in the shell I get following characters: ^[[A in stead of scrolling through the command history. This only happens with my regular logon. I don't have this problem after tying su and the root password.

Any suggestions?

Hans

---

### Post by McNils on 2007-06-27
What is your  shell? Check /etc/passwd.  It should be /bin/bash.

I can repeat your problem when using /bin/sh.

---

### Post by VHans on 2007-06-28
> **McNils said:**
> What is your  shell? Check /etc/passwd.  It should be /bin/bash.

I can repeat your problem when using /bin/sh.

You solved my problem. Thanks a lot!

Hans

---

