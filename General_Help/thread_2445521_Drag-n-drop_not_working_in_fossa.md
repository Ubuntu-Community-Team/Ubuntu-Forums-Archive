---
title: "Drag-n-drop not working in fossa"
date: 2020-06-15
forum: General Help
---

### Post by avents on 2020-06-15
Drag-n-drop has been missing in fossa (but not always) and it can be replaced by copy/paste or cut/paste ,  but not on an outgoing email.


Tried to drag-n-drop a pic from desktop to an outgoing email, and it never worked; no problem sending as attachment.


Finally, I had to start the email in Windows and do the simple drag-n-drop.

Anyway to fix this?

---

### Post by avents on 2020-06-17
I found a solution:

1.  open the Extensions app , click on "Launch" and turn off the Desktop Icons extension.
2.   in terminal :  sudo apt install nemo
3.   in Startup Applications program click the "Launch"  then click "Add " button    and type "Nemo Desktop" as name   and type     "nemo-desktop"      in the command box and "Add".


Restart  and you are using the  Nemo Desktop which supports "drag and drop". 
It does not let you move around icons but right-clicking and enabling "Customize" will let you do that too.

---

### Post by avents on 2020-06-17
To avoid misunderstandings:   in the command line you need to type " nemo-desktop "  and not 
"  nemo desktop . "

---

