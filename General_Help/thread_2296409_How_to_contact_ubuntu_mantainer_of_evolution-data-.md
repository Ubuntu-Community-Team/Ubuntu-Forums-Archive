---
title: "How to contact ubuntu mantainer of evolution-data-centre"
date: 2015-09-25
forum: General Help
---

### Post by claracc on 2015-09-25
Hello, 

Recently I had a problem with evolution 3.10 and an .ono server account in my ubuntu gnome shell 14.04.

I asked for help in the evolution-list archives of gnome.org, and the problem was identified. Unless they are not going to 
patch evolution data server 3.10 for the .ono server account, they have solved the problem for evolution 3.19.1+/3.18.1+ and asked for :

"You can ask your distribution maintainer of the evolution-data-server
to backport this commit:
[https://git.gnome.org/browse/evolution-data-server/commit/?id=3fc24c8](https://git.gnome.org/browse/evolution-data-server/commit/?id=3fc24c8)

It might be a smooth backport, I think.

this is the bug: https://bugzilla.gnome.org/show_bug.cgi?id=552425"

Could someone address me to the person who is in charge of mantaining evolution-data-server for ubuntu?or where to look for, please?

Thanks in advance

---

### Post by ian-weisser on 2015-09-25
Debian has specific humans (packagers and debian developers) who take responsibility.
Ubuntu does not. Ubuntu uses a snapshot system, with teams to handle the occasional bugfix or security fix.

Start at [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

---

### Post by claracc on 2015-09-26
Thank you

Regards

---

