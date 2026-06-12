---
title: "sudo over ssh gives X error"
date: 2008-02-21
forum: General Help
---

### Post by qperson1 on 2008-02-21
On an Ubuntu 7.10 box, I created a user who doesn't have any privileges. Then I edited /etc/sudoers (via visudo) to give them some commands that can be run as root.
Example:
foouser   ALL=/usr/bin/emacs*

When I ssh into the box as foouser, then do "sudo emacs foo", I get the error:
X11 connection rejected because of wrong authentication.
X connection to localhost:15.0 broken (explicit kill or server shutdown).

X forwards correctly when I start emacs without the "sudo".

Any help would be much appreciated... it works if the user is in the admin group, but I don't really want the user to have admin powers.

---

