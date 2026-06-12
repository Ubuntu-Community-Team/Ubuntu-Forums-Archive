---
title: "Kubuntu - Removed /etc/sudoers"
date: 2007-07-01
forum: General Help
---

### Post by ikr1sse on 2007-07-01
I should've thought a bit longer. But, of a mistake, I removed /etc/sudoers. I was to replace it with another file, but now I can't sudo, and therefore I can't place the new file there...

Can this be solved in some way?

---

### Post by ikr1sse on 2007-07-01
Woot!
I fixed it.

For those who wants to know; I started up in recovery mode, and there I used visudo and wrote:
```
#
# Blah, blah
# must use visudo, check man pages and all that crap
#

# Defaults
Defaults !lecture,tty_tickets,!fqdn

# User privileges
root ALL=(ALL) ALL

# Admin group privileges
%admin ALL=(ALL) ALL
```

---

