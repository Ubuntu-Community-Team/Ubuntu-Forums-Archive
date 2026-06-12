---
title: "[SOLVED] Unresponsive programs"
date: 2008-04-19
forum: General Help
---

### Post by lost09 on 2008-04-19
How do I kill unresponsive programs/processes in Ubuntu 7.10? (e.g. What's the equivalent of Windows' ctrl + alt + del?)

---

### Post by mikewhatever on 2008-04-19
> **lost09 said:**
> How do I kill unresponsive programs/processes in Ubuntu 7.10? (e.g. What's the equivalent of Windows' ctrl + alt + del?)

<killall process_name>

The combination you wrote does not kill anything in Windows, but opens an equivalent of System>Admin>System Monitor.

---

### Post by lost09 on 2008-04-19
"Add/Remove Applications" refuses to respond to anything, and typing "ps" in the terminal doesn't return any process names.

---

### Post by noynac on 2008-04-19
You can add a "force kill" icon to a panel. Just click on the icon and then on the unresponsive program.

---

### Post by lost09 on 2008-04-19
Please clarify "force kill icon".

---

### Post by noynac on 2008-04-19
> **lost09 said:**
> Please clarify "force kill icon".
Right-click on a panel and select "add to panel." In Hardy, one item is called force quit (not kill--sorry). There's a similar icon in Gutsy, although it may have a different name. The purpose of this icon is to "force a misbehaving application to quit."

---

### Post by lost09 on 2008-04-19
Thanks. On the same note, is there a key combination that will allow me to force quit applications? Ctrl + alt + del only brings up the "Do you want to force quit?" dialog box 30% of the time. I expect there's a more efficient way of doing it than using "top" and "kill" in the terminal, but I may be wrong.

---

### Post by noynac on 2008-04-19
> **lost09 said:**
> Thanks. On the same note, is there a key combination that will allow me to force quit applications? ...

There may be, but I'm not aware of it.

---

### Post by mikewhatever on 2008-04-19
> **lost09 said:**
> "Add/Remove Applications" refuses to respond to anything, and typing "ps" in the terminal doesn't return any process names.

Try <killall gnome-app-install>.

---

