---
title: "Safe fsck"
date: 2006-11-26
forum: General Help
---

### Post by Ingla on 2006-11-26
Hello.

I've never run fsck deliberately ... only the automatic one which executes every 30 boots.

I've seen warnings that the file system must be mounted r/o, so i've held off as I don't know how to guarantee that it will be.

What's the correct way to do this? In Windows, Scandisk pretty much runs itself, including rebooting the machine. What's the procedure for Linux (type a command in the terminal and then reboot manually?).

Can someone walk me throught this the first time (especially making sure I don't mount the system r/w? (Breezy 5.10)

Thanks.

---

### Post by bapoumba on 2006-11-26
The automatic fsck every 30 boots will warn you if errors have been found, and will mount the file system read-only. You'll get a screen explaining all of this.

You should let the automatic fsck run every 30 boots, it is safe ;)

You can read **man fsck** and **man e2fsck** :)

---

### Post by tredegar on 2006-11-26
If you really want to run **fsck** now, then the easiest way to do this is to **shutdown -rF now**.
The **r** does a reboot and the **F** forces fsck to run at the next boot. 

HTH

---

