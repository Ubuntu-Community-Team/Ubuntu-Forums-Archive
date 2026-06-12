---
title: "cant login as user..gdm dies and so on"
date: 2004-11-21
forum: General Help
---

### Post by Razvan on 2004-11-21
Hi all,

when my system boots up it tries to start gdm and fails with the error message, that there is already an x-server running...removing /tmp/X0-lock doesnt help...

but after i delete it i can at least do startx and use xdm to log in as root...when I try to login as user (startx as user or via xdm) it just dies...screen gets blcak...thinks a while about it and then goes back to where i was before

i would send some logfiles, but i dont know which ones (...am not too confident with xserverz)

any ideas?  :-k  thanx, Martin


...and sorry for my english ... or is it ok? ;-)

---

### Post by oddabe19 on 2004-11-21
next time that happens try /etc/init.d/gdm stop

once that's done, try /etc/init.d/gdm start

and see what happens, if you still have the same error, it sounds like there's a driver conflict, or something's wrong in your XFConfig file, what video driver do you use/card?

---

### Post by Razvan on 2004-11-21
[QUOTE=oddabe19]next time that happens try /etc/init.d/gdm stop

once that's done, try /etc/init.d/gdm start

and see what happens, if you still have the same error, it sounds like there's a driver conflict, or something's wrong in your XFConfig file, what video driver do you use/card?[/QUOTE]
 whoops...just notice, there is a thread about that already two lines down...

killing gdm and resuming it doesnt help either...

---

