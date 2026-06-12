---
title: "dkgp was interrupted- problem-- need solve"
date: 2008-04-15
forum: General Help
---

### Post by Treeckcold57 on 2008-04-15
Hi guys.

I got a problem. However, I have no idea how to fix it.

Take look this one.

[IMG]http://i3.photobucket.com/albums/y74/GiganticFreeze_6005/problem.png[/IMG]

:confused:

---

### Post by ibutho on 2008-04-15
Run gnome-terminal (Menu -> Accessories -> Terminal) and run the command
```
sudo dpkg --configure -a
```

---

### Post by Kemono on 2008-04-15
Have you tried running the command **dpkg --configure -a** in the terminal?

---

### Post by Treeckcold57 on 2008-04-15
```
treeck57@Treeck57-linux:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
treeck57@Treeck57-linux:~$ 

```

what's next to do?

---

### Post by ibutho on 2008-04-15
Did you try what I suggested in my post above? You need to have admin privileges and prefix the commands with sudo.

---

### Post by Treeckcold57 on 2008-04-15
It got fixed right now. Thanks, ibutho!

---

