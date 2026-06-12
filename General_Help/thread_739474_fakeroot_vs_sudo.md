---
title: "fakeroot vs sudo"
date: 2008-03-29
forum: General Help
---

### Post by neurostu on 2008-03-29
Can anyone explain to me what fakeroot is and how using it differs from  using sudo?

---

### Post by SOULRiDER on 2008-03-29
Fakeroot sort of makes youa ct as if you were root but does not give you root permissions. Sudo gives you root permissions temporarily.

---

### Post by louieb on 2008-03-29
[http://www.fifi.org/cgi-bin/man2html/usr/share/man/man1/fakeroot.1.gz](http://www.fifi.org/cgi-bin/man2html/usr/share/man/man1/fakeroot.1.gz)

says
> **fakeroot**  was specifically written to enable users to create Debian GNU/Linux  packages (in the  **[deb]("http://www.fifi.org/cgi-bin/man2html?deb+5")(5)**  format) without giving them root privileges.also
> **fakeroot**  is a regular, non-setuid program. It does not enhance a user's privileges, or decrease the system's security.  [Google Linux Search]("http://www.google.com/linux") is your friend.

---

### Post by neurostu on 2008-03-30
I didn't know about [www.google.com/linux](www.google.com/linux)
Thanks!

---

