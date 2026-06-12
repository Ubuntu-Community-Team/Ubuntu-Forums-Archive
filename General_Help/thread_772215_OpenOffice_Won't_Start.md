---
title: "OpenOffice Won't Start"
date: 2008-04-28
forum: General Help
---

### Post by nhandler on 2008-04-28
I was working with openoffice calc the other day, and it crashed ubuntu. I restarted with Ctrl+Alt+Backspace and logged back in. The issue is, I can no longer run openoffice. I've tried launching it from the Applications->Office menu, as well as from a terminal. Nothing works, and the terminal displays no output. Does anybody have any ideas on how to fix this?

---

### Post by squaregoldfish on 2008-04-28
Are there any soffice.bin processes left knocking around? If there are, OO will refuse to start.

If there aren't I can't think of anything else that might help, I'm afraid.

Steve.

---

### Post by Michael.Godawski on 2008-04-28
You can check with the command 
```
top
```
if there are some processes running which hinder open office from starting.

Do you have tried to re-install open office?

---

### Post by calc on 2008-04-28
If there are no remaining openoffice processes running and it still won't start moving ~/.openoffice.org2 out of the way might fix the problem.

---

### Post by Islington on 2008-04-28
if all else fails reinstall it.

---

### Post by calc on 2008-04-28
> **Islington said:**
> if all else fails reinstall it.

Reinstalling openoffice wouldn't fix the problem if there is something messed up in his ~/.openoffice.org2 dir, eg lock files, etc. But yea if neither killing soffice.bin and moving/removing ~/.openoffice.org2 works then reinstalling openoffice.org might fix the problem but would be unlikely to, unless his crash corrupted the files.

---

### Post by Islington on 2008-04-28
well synaptic can remove the config files cant it? if one does a complete uninstall?

---

### Post by calc on 2008-04-28
> **Islington said:**
> well synaptic can remove the config files cant it? if one does a complete uninstall?

No it only removes the configuration files under /etc during a complete uninstall, it never touches users dot files (eg ~/.openoffice.org2).

---

### Post by nhandler on 2008-04-28
> **squaregoldfish said:**
> Are there any soffice.bin processes left knocking around? If there are, OO will refuse to start.

If there aren't I can't think of anything else that might help, I'm afraid.

Steve.

That fixed it. I thought doing a Ctrl+Alt+Backspace would kill the processes. Looking back, I realize why that isn't the case. Ctrl+Alt+Backspace just restarts X. All the processes remain running. If I had just done a normal restart of the computer, all of the processes would have been killed, and it would have started working again.

Either way, the problem is fixed. Thanks for the help, and thanks to whoever came up with the document recovery feature in openoffice.

---

### Post by squaregoldfish on 2008-04-29
> I thought doing a Ctrl+Alt+Backspace would kill the processes. Looking back, I realize why that isn't the case. Ctrl+Alt+Backspace just restarts X. All the processes remain running.

Usually, killing X will kill all the programs you're running under X too, since they'll all be child processes. However, OpenOffice forks off separate processes when it starts, that aren't direct children of the X process, which is why they don't get killed.

---

### Post by free2useemail on 2008-04-29
Something could have been deleted. Are you running ubuntu as a virtual harddrive? Just reinstall it, it won't take long!

---

