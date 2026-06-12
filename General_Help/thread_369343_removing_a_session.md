---
title: "removing a session"
date: 2007-02-24
forum: General Help
---

### Post by hippieh8er15 on 2007-02-24
how do i remove a session i accidentally added a session with a bad path and it wont let me add any more sessions.  So i need to remove the bad one to put the good one in its place 

Thanks

---

### Post by DagMan on 2007-02-24
It could be a file called something.desktop located in /usr/share/xsessions/
I'm not really sure but that's where you add a session according to the beryl wiki so it's a place to look.

---

### Post by hippieh8er15 on 2007-02-24
> **DagMan said:**
> It could be a file called something.desktop located in /usr/share/xsessions/
I'm not really sure but that's where you add a session according to the beryl wiki so it's a place to look.

Cool i found it but when i try to delete it i get this message;

Cannot move "/usr/share/...gl.desktop" to the trash because you do not have permissions to change it or its parent folder

---

### Post by DagMan on 2007-02-25
open a terminal and try this
```
 sudo rm /usr/share/xsessions/NAME-OF-FILE.desktop
```

---

