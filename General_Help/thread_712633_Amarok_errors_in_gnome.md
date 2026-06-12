---
title: "Amarok errors in gnome"
date: 2008-03-01
forum: General Help
---

### Post by Roanoke on 2008-03-01
I am running gnome and do not have kde on my system besides what amarok depends on. When I start amarok, I get two errors in succession:

```
There was an error setting up inter-process communications for KDE. The message returned by the suystem was:

Could not read network connection list.
/home/sam/.DCOPserver_sam-laptop__0

Please check the "dcopserver" program is running!
```

After which I press "ok" and a new error message pops up:

```
Could not start process Unable to create io-slave: Permission denied.
```

After which I press "ok" and the attached window pops up. When I press on the symbol in the center, amarok starts up normally but there is no icon in the tray.

---

### Post by kodoku on 2008-03-01
did you try running dcopserver like it said to?

Try that, if it still doesn't work, try logging out and then back in.

Then run "kdeinit" in a terminal, and then try to run amarok again.

---

### Post by Roanoke on 2008-03-05
Error in terminal.

```

$ dcopserver
$ kdeinit
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/roanoke/.kde/socket-roanoke-laptop/kdeinit__0'
$ 

```

---

### Post by ameeno on 2008-06-14
i ran amarok in terminal as su (root)

and it worked finally since i had the same problem as u. i'm building my music db now but i'm not sure if amarok will run as a normal user afterwords.. is there any way to run it as a normal user?


also u can configure kdelook with kdecontrol app.

---

