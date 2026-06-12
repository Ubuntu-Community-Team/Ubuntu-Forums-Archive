---
title: "[SOLVED] No privileges with root"
date: 2008-05-29
forum: General Help
---

### Post by chlhardy on 2008-05-29
Ok, so i just installed Hardy Heron and when I try to edit anything I can't because root owns it.

So I log in as root in the terminal "sudo -s" and still nothing.

I even try to edit sudousers but nothing.  sudo visudo shows me the file but I can't edit it.

And yes, it does show root@*username*

any idea?

---

### Post by todak on 2008-05-29
In a terminal, type "sudo filetoedit" minus quotes and when it asks for a password, type in YOUR password, as the person that installed ubuntu is the administrator.

---

### Post by aysiu on 2008-05-29
This should help: [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by chlhardy on 2008-05-31
Thanks aysiu, the information at that link really helped.

---

