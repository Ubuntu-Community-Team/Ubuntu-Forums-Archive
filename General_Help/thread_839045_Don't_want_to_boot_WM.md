---
title: "Don't want to boot WM"
date: 2008-06-24
forum: General Help
---

### Post by xodeus on 2008-06-24
Hi there.
I've isntalled a lighttpd/php/mysql server on my ubuntu machine. Now I want some more ressources and I've become very good friend with CLI. Now I would like to take the next step. I don't want any gdm, gnome, xfce or other at boot time. Just the CLI. How do I do that?
Can I unisntall xfce-4 and gnome stuff without breaking the system?

---

### Post by sdennie on 2008-06-24
If you still have gnome, you should be able to go to System->Administration->Services and disable gdm.  That will immediately kill X so do don't do it with documents open.  However, you will never be bothered with a graphical login again.  You can remove xfce and gnome stuff after that but, as long as you aren't short on disk space, you may want to keep them around in case you need them.

---

