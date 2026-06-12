---
title: "Remove program from start-up"
date: 2006-10-24
forum: General Help
---

### Post by zentehflash on 2006-10-24
Hey, I just installed beryl and I can't do anything with my menus at boot becasue I put beryl-manager in the sessions>startup programs list.  I was hoping someone could help me figure out how to remove an entry from this list from the terminal in recovery mode.  I don't know which file to remove it from.  Thanks in advance!

---

### Post by mitch.c on 2006-10-24
> **zentehflash said:**
> Hey, I just installed beryl and I can't do anything with my menus at boot becasue I put beryl-manager in the sessions>startup programs list.  I was hoping someone could help me figure out how to remove an entry from this list from the terminal in recovery mode.  I don't know which file to remove it from.  Thanks in advance!
See if there is something like a beryl-manager.desktop file in ~/.config/autostart/. If so try deleting it (at your own risk of course!)

---

### Post by dheerajsp on 2006-11-14
yes, i am having the same probelm. i added  beryl-manager and emerald in the startup programs and now my desktop hangs up! i can only restart X. 

will the above command work properly?

---

